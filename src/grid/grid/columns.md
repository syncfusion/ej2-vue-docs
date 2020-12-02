---
title: "Columns"
component: "Grid"
description: "Documentation on column reordering, resizing, header templates (custom header content), and column templates (custom cell content) in the Essential JS 2 DataGrid control."
---

# Columns

The column definitions are used as the [`dataSource`](../api/grid/#datasource) schema in the Grid.
This plays a vital role in rendering column values in the required format.
The grid operations such as sorting, filtering and grouping etc. are performed based on column definitions.
The [`field`](../api/grid/column/#field) property of the [`columns`](../api/grid/column/)
is necessary to map the data source values in Grid columns.

> 1. If the column with [`field`](../api/grid/column/#field) is not specified in the dataSource, then the column values will be  empty.
> 2. If the [`field`](../api/grid/column/#field) name contains “dot” operator, it is considered as complex binding.

## Auto generation

The [`columns`](../api/grid/column/) are automatically generated when
[`columns`](../api/grid/column/)
declaration is empty or undefined while initializing the grid. All the columns in the [`dataSource`](../api/grid/#datasource)
are bound as grid columns.

{% tab template="grid/column/default" %}

```html
<template>
  <div id="app">
      <ejs-grid :dataSource="data"> </ejs-grid>
  </div>
</template>
<script>
import Vue from 'vue';
import { GridPlugin } from '@syncfusion/ej2-vue-grids';

Vue.use(GridPlugin);
export default {
  data () {
    return {
      data: [
      { OrderID: 10248, CustomerID: 'VINET', EmployeeID: 5 },
      { OrderID: 10249, CustomerID: 'TOMSP', EmployeeID: 6 },
      { OrderID: 10250, CustomerID: 'HANAR', EmployeeID: 4 }]
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> When the columns are auto-generated then the column [`type`](../api/grid/column/#type)
will be determined from the first record of the
[`dataSource`](../api/grid/#datasource).

### How to set isPrimaryKey for auto generated columns when editing is enabled

Primary key can be defined in the declaration of column object of the grid. When we didn't declare the columns, the grid will generate the columns automatically. For these auto generated columns, you can set `isPrimaryKey` column property as true by using the following ways,

If Primary key "column index" is known then refer the following code example

{% tab template="grid/column/default" %}

```html
<template>
  <div id="app">
      <ejs-grid ref='grid' :dataSource="data" :editSettings='editSettings' :dataBound='dataBound'> </ejs-grid>
  </div>
</template>
<script>
import Vue from 'vue';
import { GridPlugin, Edit } from '@syncfusion/ej2-vue-grids';

Vue.use(GridPlugin);
export default {
  data () {
    return {
      data: [
      { OrderID: 10248, CustomerID: 'VINET', EmployeeID: 5 },
      { OrderID: 10249, CustomerID: 'TOMSP', EmployeeID: 6 },
      { OrderID: 10250, CustomerID: 'HANAR', EmployeeID: 4 }],
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
    }
  },
  provide: {
    grid: [Edit]
  },
  methods: {
    dataBound: function() {
        this.$refs.grid.ej2Instances.columns[0].isPrimaryKey = true;
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> If Primary key "column fieldname" is known then you can get the column by using `var column = grid.getColumnByField('OrderID')` and then set primary key by defining `column.isPrimaryKey = 'true'`

### Set column options to auto generated columns

You can set column options such as `format`, `width` to the auto generated columns by using `dataBound` event of the grid.

In the below example, `width` is set for `OrderID` column, `date` type is set for `OrderDate` column and `numeric` type is set for `Freight` column.

{% tab template="grid/column/default" %}

```html
<template>
  <div id="app">
      <ejs-grid ref='grid' :dataSource="data" :dataBound='dataBound'> </ejs-grid>
  </div>
</template>
<script>
import Vue from 'vue';
import { GridPlugin } from '@syncfusion/ej2-vue-grids';

Vue.use(GridPlugin);
export default {
  data () {
    return {
      data: [
    { OrderID: 10248, CustomerID: 'VINET', Freight: 32.3800, OrderDate: "1996-07-02T00:00:00.000Z" },
    { OrderID: 10249, CustomerID: 'TOMSP', Freight: 32.3800, OrderDate: "1996-07-19T00:00:00.000Z" },
    { OrderID: 10250, CustomerID: 'HANAR', Freight: 32.3800, OrderDate: "1996-07-22T00:00:00.000Z" }]
    }
  },
  methods: {
      dataBound: function() {
        for (var i = 0; i < this.$refs.grid.ej2Instances.columns.length; i++) {
            this.$refs.grid.ej2Instances.columns[0].width = 120;
            if(this.$refs.grid.ej2Instances.columns[i].field === "OrderDate"){
                this.$refs.grid.ej2Instances.columns[i].type="date";
            }
            if (this.$refs.grid.ej2Instances.columns[i].type === "date") {
                this.$refs.grid.ej2Instances.columns[i].format = { type: "date", format: "dd/MM/yyyy" };
            }
            this.$refs.grid.ej2Instances.columns[2].format = "P2";
        }
        this.$refs.grid.ej2Instances.refreshColumns();
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### How to auto-generate columns from complex column fields to flat columns

By default, the auto-generated columns will create multiple column fields when grid has complex datasource. Hereby using [`ValueAccessor`](../api/grid/valueAccessor) property, complex columns data are combined and generated in a single column.

In the below example, we set the **ValueAccessor** property to those columns whose field type is **Object**.

{% tab template="grid/column/generate" %}

```html
<template>
  <div id="app">
      <ejs-grid
        :dataSource="data"
        id="Grid"
        ref="grid"
        :pageSettings="pageSettings"
        :allowPaging="true"
        :editSettings="editSettings"
        :toolbar="toolbar"
        :dataBound="dataBound"
      ></ejs-grid>
  </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Edit, Toolbar, Page } from "@syncfusion/ej2-vue-grids";
import { data } from "./datasource.js";
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
      flag: true,
      editSettings: {
        allowEditing: true,
        allowAdding: true,
        allowDeleting: true
      },
      pageSettings: { pageSize: 5 },
      toolbar: ["Add", "Edit", "Delete", "Update", "Cancel"]
    };
  },
  methods: {
    dataBound: function() {
      if (this.flag) {
        this.flag = false;
        var cols = Object.keys(this.$refs.grid.getCurrentViewRecords()[0]);
        var length = cols.length;
        var col = [];
        for (var i = 0; i < length; i++) {
          var field = cols[i];
          var obj = {};
          obj["field"] = field;
          var mon = this.$refs.grid.getCurrentViewRecords()[i][field];
          var type = typeof mon;
          if (type === "object") {
            obj["valueAccessor"] = (field, data, column) => {
              return (
                data[field].Name +
                " , " +
                data[field].Unit +
                " , " +
                data[field].VSetMax
              );
            };
          }
          col.push(obj);
        }
        this.$refs.grid.setProperties({ columns: col });
      }
    }
  },
  provide: {
    grid: [Edit, Toolbar, Page]
  }
};
</script>

<style>
@import "https://cdn.syncfusion.com/ej2/material.css";
</style>
```

{% endtab %}

## Header Text

By default, column header title is displayed from column [`field`](../api/grid/column/#field) value.
To override the default header title, you have to define the [`headerText`](../api/grid/column/#headertext) value.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data"  height='315px'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' width=90></e-column>
            <e-column field='ShipCity' headerText='Ship City' width=120></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> If both the [`field`](../api/grid/column/#field) and [`headerText`](../api/grid/column/#headertext)
are not defined in the column, the column renders with “empty” header text.

## Format

To format cell values based on specific culture, use the [`columns.format`](../api/grid/column/#format)
property. The grid uses `Internalization` library to format `number` and
`date`
values.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data"  height='315px'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
            <e-column field='OrderDate' headerText='Order Date' textAlign='Right' format='yMd' type='date' width=120></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> By default, the `number` and `date` values are formatted in `en-US` locale.

### Number formatting

The number or integer values can be formatted using the below format strings.

Format |Description |Remarks
-----|-----
N | Denotes numeric type. | The numeric format is followed by integer value as N2, N3. etc which denotes the number of precision to be allowed.
C | Denotes currency type. | The currency format is followed by integer value as C2, C3. etc which denotes the number of precision to be allowed.
P | Denotes percentage type | The percentage format expects the input value to be in the range of 0 to 100. For example the cell value `0.2` is formatted as `20%`. The percentage format is followed by integer value as P2, P3. etc which denotes the number of precision to be allowed.

### Date formatting

You can format date values either using built-in date format string or custom format string.

For built-in date format you can specify [`columns.format`](../api/grid/column/#format) property as string   (Example: `yMd`).

You can also use custom format string to format the date values. Some of the custom formats and the formatted date values are given in the below table.

Format | Formatted value
-----|-----
{ type:'date', format:'dd/MM/yyyy' } | 04/07/1996
{ type:'date', format:'dd.MM.yyyy' } | 04.07.1996
{ type:'date', skeleton:'short' } | 7/4/96
{ type: 'dateTime', format: 'dd/MM/yyyy hh:mm a' } | 04/07/1996 12:00 AM
{ type: 'dateTime', format: 'MM/dd/yyyy hh:mm:ss a' } | 07/04/1996 12:00:00 AM

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data"  height='315px'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
            <e-column field='OrderDate' headerText='Order Date' textAlign='Right' :format='formatOptions' type='date' width=120></e-column>
            <e-column field='OrderDate' headerText='Ship Date' textAlign='Right' :format='shipFormat' type='date' width=180></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      formatOptions: {type:'date', format:'dd/MM/yyyy'},
      shipFormat: { type: 'dateTime', format: 'dd/MM/yyyy hh:mm a' }
    };
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Visibility

You can hide any particular column in Grid before rendering by defining `visible` property as false. In the below sample `ShipCity` column is defined as visible false.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data"  height='315px'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' width=90></e-column>
            <e-column field='ShipCity' :visible=false headerText='Ship City' width=120></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## AutoFit specific columns

The [`autoFitColumns`](../api/grid/#autofitcolumns) method resizes the column to fit the widest
cell's content without wrapping. You can autofit specific columns at initial rendering by invoking
the [`autoFitColumns`](../api/grid/#autofitcolumns) method in [`dataBound`](../api/grid/#databound) event.

To autofit a column, you need to inject `Resize` module in the `provide` section.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource="data" :dataBound='dataBound' height='315px'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=150></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=150></e-column>
            <e-column field='OrderDate' headerText='Order Date' textAlign='Right' format='yMd' type='date' width=120></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Resize } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  methods: {
      dataBound: function() {
        this.$refs.grid.autoFitColumns(['OrderDate', 'CustomerID']);
    }
  },
  provide: {
      grid: [Resize]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> You can autofit all columns, by invoking the [`autoFitColumns`](../api/grid/#autofitcolumns)
method without column name.

## Reorder

Reordering can be done by drag and drop of a particular column header from one index to another index within the grid.
To enable reordering, set the [`allowReordering`](../api/grid/#allowreordering) to true.

To use Reordering, you need to inject `Reorder` module in the `provide` section.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :allowReordering='true' height='315px'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
            <e-column field='OrderDate' headerText='Order Date' textAlign='Right' format='yMd' type='date' width=120></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Reorder } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  provide: {
      grid: [Reorder]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> * You can disable reordering a particular column by setting the [`columns.allowReordering`](../api/grid/column/#allowreordering) to false.
> * In RTL mode, you can click and drag the left edge of the header cell to resize the column.

### Reorder Single Column

Grid have option to reorder Columns either by Interaction or by using the `reorderColumns` method. In the below sample, `ShipCity` column is reordered to last column position by using the method.

In the below sample, `Ship City` and `Ship Region` column is reordered to last column position.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-button id='reorderSingleCol' @click.native='reorder'>Reorder Ship City to Last</ejs-button>
        <ejs-grid ref='grid' :dataSource="data" :allowReordering='true' height='315px'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='ShipCity' headerText='Ship City' width=100></e-column>
            <e-column field='ShipRegion' headerText='Ship Region' width=80></e-column>
            <e-column field='ShipName' headerText='Ship Name' width=80></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Reorder } from "@syncfusion/ej2-vue-grids";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { data } from './datasource.js';

Vue.use(GridPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  provide: {
      grid: [Reorder]
  },
  methods: {
      reorder: function() {
          this.$refs.grid.reorderColumns('ShipCity','ShipName');
      }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";

 #reorderSingleCol {
     text-transform: none;
 }
</style>
```

{% endtab %}

### Reorder Multiple Columns

User can reorder a single column at a time by Interaction. Sometimes we need to have reorder multiple columns at the same time, It can be achieved through programmatically by using `reorderColumns` method.

In the below sample, `Ship City` and `Ship Region` column is reordered to last column position.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-button id='reorderMultipleCols' @click.native='reorder'>Reorder Ship City and Ship Region to Last</ejs-button>
        <ejs-grid ref='grid' :dataSource="data" :allowReordering='true' height='315px'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='ShipCity' headerText='Ship City' width=100></e-column>
            <e-column field='ShipRegion' headerText='Ship Region' width=80></e-column>
            <e-column field='ShipName' headerText='Ship Name' width=80></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Reorder } from "@syncfusion/ej2-vue-grids";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { data } from './datasource.js';

Vue.use(GridPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  provide: {
      grid: [Reorder]
  },
  methods: {
      reorder: function() {
          this.$refs.grid.reorderColumns(['ShipCity','ShipRegion'],'ShipName');
      }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";

 #reorderMultipleCols {
     text-transform: none;
 }
</style>
```

{% endtab %}

### Reorder Events

During the reorder action, the grid component triggers the below three events.

1. The `columnDragStart` event triggers when column header element drag (move) starts.
2. The `columnDrag` event triggers when column header element is dragged (moved) continuously.
3. The `columnDrop` event triggers when a column header element is dropped on the target column.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource="data" :allowReordering='true' :columnDrag='columnDrag' :columnDrop='columnDrop' :columnDragStart='columnDragStart' height='315px'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='ShipCity' headerText='Ship City' width=100></e-column>
            <e-column field='ShipRegion' headerText='Ship Region' width=80></e-column>
            <e-column field='ShipName' headerText='Ship Name' width=80></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Reorder } from "@syncfusion/ej2-vue-grids";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { data } from './datasource.js';

Vue.use(GridPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  provide: {
      grid: [Reorder]
  },
  methods: {
    columnDragStart: function() {
        alert('columnDragStart event is Triggered');
    },
    columnDrag: function() {
        alert('columnDrag event is Triggered');
    },
    columnDrop: function() {
        alert('columnDrop event is Triggered');
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";

 #reorderMultipleCols {
     text-transform: none;
 }
</style>
```

{% endtab %}

## Lock Columns

You can lock columns by using [`column.lockColumn`](../api/grid/column/#lockcolumn) property. The locked columns will be moved to the first position. Also you can’t reorder its position.

In the below example, Ship City column is locked and its reordering functionality is disabled.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :allowReordering='true' :allowSelection='false' height='315px'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='ShipCity' width=90 :lockColumn='true' :customAttributes="customAttributes"></e-column>
            <e-column field='ShipName' width=120></e-column>
            <e-column field='ShipPostalCode' width=120></e-column>
            <e-column field='ShipRegion' width=120></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Reorder } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      customAttributes : {class: 'customcss'}
    };
  },
  provide: {
      grid: [Reorder]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
 .e-grid .e-rowcell.customcss{
  background-color: #ecedee;
}
.e-grid .e-headercell.customcss{
  background-color: #ecedee;
}
</style>
```

{% endtab %}

## Column Resizing

Columns width can be resized by clicking and dragging at the right edge of the column header.
While dragging, the width of a respective column will be resized immediately.
Each column can be auto resized by double-clicking at the right edge of the column header.
It will fit the width of that column based on widest cell content.
To enable the column resize, set the [`allowResizing`](../api/grid/#allowresizing) property to true.

To use the column resize, inject `Resize` module in the `provide` section.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :allowResizing='true' height='315px'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='ShipCity' headerText='Ship City' width=100></e-column>
            <e-column field='ShipName' headerText='Ship Name' width=80></e-column>
            <e-column field='ShipCountry' headerText='Ship Country' textAlign='Right' width=100></e-column>
            <e-column field='ShipAddress' headerText='Ship Address' width=120></e-column>
            <e-column field='Freight' headerText='Freight' width=80></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Resize } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  provide: {
      grid: [Resize]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> You can disable Resizing for a particular column,
by specifying [`columns.allowResizing`](../api/grid/column/#allowresizing) to false.
> In RTL mode, you can click and drag the left edge of header cell to resize the column.

### Min and Max width

Columns can be restricted to resize in between minimum and maximum width by defining the
[`columns.minWidth`](../api/grid/column/#minwidth) and [`columns.maxWidth`](../api/grid/column/#maxwidth).

In the below sample, `OrderID`, `Ship Name` and `Ship Country` columns are defined with minimum and maximum width.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :allowResizing='true' height='315px'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' minWidth= 100 width=150 maxWidth=250 ></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='ShipCity' headerText='Ship City' width=100></e-column>
            <e-column field='ShipName' headerText='Ship Name'  minWidth= 150 width=200 maxWidth=300></e-column>
            <e-column field='ShipCountry' headerText='Ship Country' textAlign='Right'  minWidth= 120 width=150 maxWidth=280></e-column>
            <e-column field='ShipAddress' headerText='Ship Address' width=120></e-column>
            <e-column field='Freight' headerText='Freight' width=80></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Resize } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  provide: {
      grid: [Resize]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### Resize Stacked Column

Stacked columns can be resized by clicking and dragging the right edge of the stacked column header. While dragging, the width of the respective child columns will be resized at the same time. You can disable resize for any particular stacked column by setting `allowResizing` as `false` to its columns.

In this example, we have disabled resize for `Ship City` column.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :allowResizing='true'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' width='100' textAlign="Center" minWidth='10'></e-column>
                <e-column headerText='Order Details' :columns='orderColumns'></e-column>
                <e-column headerText='Ship Details' :columns='shipColumns'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Resize } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      orderColumns: [
            {
                field: 'OrderDate',
                headerText: 'Order Date',
                format: 'yMd',
                width: 120,
                textAlign: 'Right',
                minWidth: 10
            },
            {
                field: 'Freight',
                headerText: 'Freight ($)',
                width: 100,
                format: 'C1',
                textAlign: 'Right',
                minWidth: 10
            }
        ],
        shipColumns: [
            {
                field: 'ShipCity',
                headerText: 'Ship City',
                width: 100,
                minWidth: 10
            },
            {
                field: 'ShipCountry',
                headerText: 'Ship Country',
                width: 120,
                minWidth: 10
            }
        ]
    };
  },
  provide: {
      grid: [Resize]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### Touch Interaction

When you tap at the right edge of header cell, a floating handler will be visible over the right border of the column.
To resize the column, tap and drag the floating handler as much you need. You can also autoFit a column by using the Column menu of the grid.

The following screenshot represents the column resizing on the touch device.

![Touch Interaction](images/column-resizing.jpg)

### Resizing Events

During the resizing action, the grid component triggers the below three events.

1. The `resizeStart` event triggers when column resize starts.
2. The `resizing` event triggers when column header element is dragged (moved) continuously..
3. The `resizeStop` event triggers when column resize ends.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :allowResizing='true' height='315px' :resizeStart='resizeStart' :resizing='resizing' :resizeStop='resizeStop'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='ShipCity' headerText='Ship City' width=100></e-column>
            <e-column field='ShipName' headerText='Ship Name' width=80></e-column>
            <e-column field='ShipCountry' headerText='Ship Country' textAlign='Right' width=100></e-column>
            <e-column field='ShipAddress' headerText='Ship Address' width=120></e-column>
            <e-column field='Freight' headerText='Freight' width=80></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Resize } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  provide: {
      grid: [Resize]
  },
  methods: {
    resizeStart: function() {
        alert('resizeStart event is Triggered');
    },
    resizing: function() {
        alert('resizing event is Triggered');
    },
    resizeStop: function() {
        alert('resizeStop event is Triggered');
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Column Template

The column [`template`](../api/grid/column/#template) has options to display custom element instead of a field value in the column.

The `template` property should be a function which returns an object. The object should contain a Vue component which should be assigned to the `template` property. The grid will look for the template property and render it as new Vue instance.

{% tab template="grid/column/template" %}

```html
<template>
    <div id="app">
         <ejs-grid :dataSource="data" height=310>
            <e-columns>
                <e-column headerText='Employee Image' width='150' textAlign='Center' :template='cTemplate'></e-column>
                <e-column field='EmployeeID' headerText='Employee ID' width='125' textAlign='Right'></e-column>
                <e-column field='FirstName' headerText='Name' width='120'></e-column>
                <e-column field='Title' headerText='Title' width='170'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { employeeData } from "./datasource.js";

Vue.use(GridPlugin);

export default {
  data: () => {
    return {
      data: employeeData,
      cTemplate: function () {
          return { template : Vue.component('columnTemplate',{
             template: `<div class="image">
                    <img :src="image" :alt="altImage"/>
                </div>`,
                data: function() {
                    return {
                        data: {}
                    }
                },
                computed: {
                    image: function() {
                        return './' + this.data.EmployeeID + '.png';
                    },
                    altImage: function() {
                        return this.data.EmployeeID;
                    }
                }
          })}
      }
    };
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";

 .image img {
        height: 55px;
        width: 55px;
        border-radius: 50px;
        box-shadow: inset 0 0 1px #e0e0e0, inset 0 0 14px rgba(0,0,0,0.2);
    }
</style>
```

{% endtab %}

### Using condition template

You can render the template elements based on condition.

In the following code, checkbox is rendered based on `Discontinued` field value.

{% tab template="grid/column/condition-template" %}

```html
<template>
    <div id="app">
         <ejs-grid :dataSource="data" height=310>
            <e-columns>
                <e-column headerText='Discontinued' width='150' textAlign='Center' :template='cTemplate'></e-column>
                <e-column field='ProductID' headerText='Product ID' width='125'></e-column>
                <e-column field='ProductName' headerText='Name' width='120'></e-column>
                <e-column field='SupplierID' headerText='Supplier ID' width='170'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { productData } from "./datasource.js";

Vue.use(GridPlugin);

export default {
  data: () => {
    return {
      data: productData,
      cTemplate: function () {
          return { template : Vue.component('columnTemplate',{
             template: `<div v-if=cData class="template_checkbox">
                    <input type="checkbox" checked />
                </div>
                <div v-else class="template_checkbox">
                    <input type="checkbox" />
                </div>`,
                data: function() {
                    return {
                        data: {}
                    }
                },
                computed: {
                    cData: function() {
                        return this.data.Discontinued;
                    }
                }
          })}
      }
    };
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Column Type

Column type can be specified using the [`columns.type`](../api/grid/column/#type) property. It specifies the type of data the column binds.

If the [`format`](../api/grid/column/#format)  is defined for a column,
the column uses [`type`](../api/grid/column/#type) to select the appropriate format option (`number`
 or `date`).

Grid column supports the following types:
* string
* number
* boolean
* date
* datetime

> If the [`type`](../api/grid/column/#type) is not defined, then it will be determined from the first record of the [`dataSource`](../api/grid/#datasource).
> Incase if the first record of the [`dataSource`](../api/grid/#datasource) is null/blank value for a column then it is necessary to define the [`type`](../api/grid/column/#type) for that column.

## Column chooser

The column chooser has options to show or hide columns dynamically. It can be enabled by defining the
[`showColumnChooser`](../api/grid/#showcolumnchooser) as true.

To use column chooser, inject `ColumnChooser` in the `provide` section.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :showColumnChooser='true' :toolbar='toolbarOptions' height='272px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' width='120' textAlign="Right"></e-column>
                <e-column field='CustomerID' headerText='Customer Name' width='150' :showInColumnChooser='false'></e-column>
                <e-column field='Freight' headerText='Freight' width='120' format='C2' textAlign="Right"></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' :visible='true' width='150'></e-column>
                <e-column field='ShipCity' headerText='Ship City' :visible='false' width='150'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, ColumnChooser, Toolbar } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      toolbarOptions: ['ColumnChooser']
    };
  },
  provide: {
      grid: [ColumnChooser, Toolbar]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> You can hide the column names in column chooser by defining the
[`columns.showInColumnChooser`](../api/grid/column/#showincolumnchooser) as false.

### Open column chooser by external button

The Column chooser can be displayed on a page through external button by invoking
the [`openColumnChooser`](../api/grid/columnChooser/#opencolumnchooser) method with `X` and `Y` axis positions.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-button @click.native="show">open Column Chooser </ejs-button>
        <ejs-grid ref='grid' :dataSource="data" :showColumnChooser='true' height='272px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' width='120' textAlign="Right"></e-column>
                <e-column field='CustomerID' headerText='Customer Name' width='150' :showInColumnChooser='false'></e-column>
                <e-column field='OrderDate' headerText='Order Date' width='130' format="yMd" textAlign="Right" type='date'></e-column>
                <e-column field='Freight' headerText='Freight' width='120' format='C2' textAlign="Right"></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' :visible='false' width='150'></e-column>
                <e-column field='ShipCity' headerText='Ship City' :visible='false' width='150'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, ColumnChooser } from "@syncfusion/ej2-vue-grids";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { data } from './datasource.js';

Vue.use(GridPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  methods: {
    show: function() {
        this.$refs.grid.ej2Instances.columnChooserModule.openColumnChooser(200, 50); // give X and Y axis
    }
  },
  provide: {
      grid: [ColumnChooser]
  }
});
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Column menu

The column menu has options to integrate features like sorting, grouping, filtering, column chooser, and autofit.
It will show a menu with the integrated feature when users click on multiple icon of the column.
To enable column menu, you need to define the [`showColumnMenu`](../api/grid/#showcolumnmenu) property as true.

To use the column menu, inject the `ColumnMenu` in the `provide` section.

The default items are displayed in following table.

| Item | Description |
|-----|-----|
| `SortAscending` | Sort the current column in ascending order. |
| `SortDescending` | Sort the current column in descending order. |
| `Group` | Group the current column. |
| `Ungroup` | Ungroup the current column. |
| `AutoFit` | Auto fit the current column. |
| `AutoFitAll` | Auto fit all columns. |
| `ColumnChooser` | Choose the column visibility. |
| `Filter` | Show the filter option as given in `filterSettings.type` |

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" id="gridcomp" :allowPaging='true' :allowGrouping='true' :allowSorting='true' :showColumnMenu='true'
        :groupSettings='groupOptions' :allowFiltering='true' :filterSettings='filterSettings'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' width='120' textAlign='Right'></e-column>
                <e-column field='Freight' headerText='Freight' format='C2' textAlign='Right' width='120'></e-column>
                <e-column field='ShippedDate' headerText='Shipped Date' width='130' format="yMd" textAlign='Right' type='date'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' :visible='false' width='150'></e-column>
                <e-column field='ShipCity' headerText='Ship City' width='150'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Group, Sort, Resize, ColumnMenu, Page } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      groupOptions: { showGroupedColumn: true },
      filterSettings: { type: "CheckBox" }
    };
  },
  provide: {
      grid: [Group, Sort, Resize, ColumnMenu, Page]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> You can disable column menu for a particular column by defining the
[`columns.showColumnMenu`](../api/grid/column/#showcolumnmenu) as false.
> You can customize the default items by defining the
[`columnMenuItems`](../api/grid/#columnmenuitems) with required items.

### Column menu events

During the resizing action, the grid component triggers the below two events.

1. The `columnMenuOpen` event triggers before the column menu opens.
2. The `columnMenuClick` event triggers when the user clicks the column menu of the grid.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" id="gridcomp" :allowPaging='true' :allowGrouping='true' :allowSorting='true' :showColumnMenu='true'
        :groupSettings='groupOptions' :allowFiltering='true' :filterSettings='filterSettings'
        :columnMenuClick='columnMenuClick' :columnMenuOpen='columnMenuOpen'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' width='120' textAlign='Right'></e-column>
                <e-column field='Freight' headerText='Freight' format='C2' textAlign='Right' width='120'></e-column>
                <e-column field='ShippedDate' headerText='Shipped Date' width='130' format="yMd" textAlign='Right' type='date'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' :visible='false' width='150'></e-column>
                <e-column field='ShipCity' headerText='Ship City' width='150'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Group, Sort, Resize, ColumnMenu, Page } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      groupOptions: { showGroupedColumn: true },
      filterSettings: { type: "CheckBox" }
    };
  },
  provide: {
      grid: [Group, Sort, Resize, ColumnMenu, Page]
  },
  methods: {
      columnMenuOpen: function(){
          alert('columnMenuOpen event is Triggered');
      },
      columnMenuClick: function(){
          alert('columnMenuClick event is Triggered');
      }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### Custom Column Menu Item

Custom column menu items can be added by defining the
[`columnMenuItems`](../api/grid/#columnmenuitems) as collection of
the [`columnMenuItemModel`](../api/grid/columnMenuItemModel/).
Actions for this customized items can be defined in the
[`columnMenuClick`](../api/grid/#columnmenuclick) event.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource="data" id="gridcomp" :allowPaging='true' :allowSorting='true' :showColumnMenu='true' :sortSettings='sortSettings' :columnMenuItems='columnMenuItems'  :columnMenuClick='columnMenuClick'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' width='140' textAlign="Right"></e-column>
                <e-column field='CustomerID' headerText='Customer Name' :showInColumnChooser='false'></e-column>
                <e-column field='Freight' headerText='Freight' format='C2' textAlign="Right"></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' :visible='false' width='150'></e-column>
                <e-column field='ShipCity' headerText='Ship City' width='150'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Sort, ColumnMenu, Page } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      columnMenuItems: [{text:'Clear Sorting', id:'gridclearsorting'}],
      sortSettings: {columns:[{direction: "Ascending", field: "OrderID"}]}
    };
  },
  methods: {
      columnMenuClick: function(args) {
        if(args.item.id === 'gridclearsorting'){
            this.$refs.grid.clearSorting();
        }
    }
  },
  provide: {
      grid: [Sort, ColumnMenu, Page]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### Customize menu items for particular columns

Sometimes, you have a scenario that to hide an item from column menu for particular columns. In that case, you need to define the
[`columnMenuOpenEventArgs.hide`](../api/grid/columnMenuOpenEventArgs/) as true in the
[`columnMenuOpen`](../api/grid/#columnmenuopen) event.

The following sample, `Filter` item was hidden in column menu when opens for the `OrderID` column.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource="data" id="gridcomp" :allowPaging='true' :allowSorting='true' :showColumnMenu='true' :filterSettings='filterSettings' :columnMenuOpen='columnMenuOpen' :allowFiltering='true' :allowGrouping='true'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' width='140' textAlign="Right"></e-column>
                <e-column field='CustomerID' headerText='Customer Name' :showInColumnChooser='false'></e-column>
                <e-column field='Freight' headerText='Freight' format='C2' textAlign="Right"></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' :visible='false' width='150'></e-column>
                <e-column field='ShipCity' headerText='Ship City' width='150'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Sort, ColumnMenu, Page, Group, Filter } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      filterSettings: {type: 'Menu'}
    };
  },
  methods: {
      columnMenuOpen: function (args) {
        for (let item of args.items) {
            if (item.text === 'Filter' && args.column.field === 'OrderID') {
                item.hide = true;
            } else {
                item.hide = false;
            }
        }
    }
  },
  provide: {
      grid: [Sort, ColumnMenu, Page, Group, Filter]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>s
```

{% endtab %}

## Column Spanning

The grid has option to span the adjacent cells. You need to define the
[`colSpan`](../api/grid/queryCellInfoEventArgs/#colspan) attribute to span cells in the
[`QueryCellInfo`](../api/grid/queryCellInfoEventArgs/) event.

In the following demo, Employee `Davolio` doing analysis from 9.00 AM to 10.00 AM, so that cells have spanned.

{% tab template="grid/column/spanning" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" height='auto' width='auto' gridLines='Both' :allowTextWrap='true' :queryCellInfo='queryCellInfoEvent'>
            <e-columns>
                <e-column field='EmployeeID' headerText='Employee ID' width='150' textAlign='Right' isPrimaryKey={true}></e-column>
                <e-column field='EmployeeName' headerText='Employee Name' width='200'></e-column>
                <e-column field='9:00' headerText='9:00 AM' width='120'></e-column>
                <e-column field='9:30' headerText='9:30 AM' width='120'></e-column>
                <e-column field='10:00' headerText='10:00 AM' width='120'></e-column>
                <e-column field='10:30' headerText='10:30 AM' width='120'></e-column>
                <e-column field='11:00' headerText='11:00 AM' width='120'></e-column>
                <e-column field='11:30' headerText='11:30 AM' width='120'></e-column>
                <e-column field='12:00' headerText='12:00 PM' width='120'></e-column>
                <e-column field='12:30' headerText='12:30 PM' width='120'></e-column>
                <e-column field='2:30' headerText='2:30 PM' width='120'></e-column>
                <e-column field='3:00' headerText='3:00 PM' width='120'></e-column>
                <e-column field='3:30' headerText='3:30 PM' width='120'></e-column>
                <e-column field='4:00' headerText='4:00 PM' width='120'></e-column>
                <e-column field='4:30' headerText='4:30 PM' width='120'></e-column>
                <e-column field='5:00' headerText='5:00 PM' width='120'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from 'vue';
import { GridPlugin } from '@syncfusion/ej2-vue-grids';
import { data  } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data: () => {
      return {
        data: data
        }
  },
  methods: {
    queryCellInfoEvent: function(args) {
        let data = args.data;
        switch (data.EmployeeID) {
            case 10001:
                if (args.column.field === '9:00' || args.column.field === '2:30' || args.column.field === '4:30') {
                    args.colSpan = 2;
                } else if (args.column.field === '11:00') {
                    args.colSpan = 3;
                }
                break;
            case 10002:
                if (args.column.field === '9:30' || args.column.field === '2:30' ||
                    args.column.field === '4:30') {
                    args.colSpan = 3;
                } else if (args.column.field === '11:00') {
                    args.colSpan = 4;
                }
                break;
            case 10003:
                if (args.column.field === '9:00' || args.column.field === '11:30') {
                    args.colSpan = 3;
                } else if (args.column.field === '10:30' || args.column.field === '3:30' ||
                    args.column.field === '4:30' || args.column.field === '2:30') {
                    args.colSpan = 2;
                }
                break;
            case 10004:
                if (args.column.field === '9:00') {
                    args.colSpan = 3;
                } else if (args.column.field === '11:00') {
                    args.colSpan = 4;
                } else if (args.column.field === '4:00' || args.column.field === '2:30') {
                    args.colSpan = 2;
                }
                break;
            case 10005:
                if (args.column.field === '9:00') {
                    args.colSpan = 4;
                } else if (args.column.field === '11:30') {
                    args.colSpan = 3;
                } else if (args.column.field === '3:30' || args.column.field === '4:30' || args.column.field === '2:30') {
                    args.colSpan = 2;
                }
                break;
            case 10006:
                if (args.column.field === '9:00' || args.column.field === '4:30' ||
                    args.column.field === '2:30' || args.column.field === '3:30') {
                    args.colSpan = 2;
                } else if (args.column.field === '10:00' || args.column.field === '11:30') {
                    args.colSpan = 3;
                }
                break;
            case 10007:
                if (args.column.field === '9:00' || args.column.field === '3:00' || args.column.field === '10:30') {
                    args.colSpan = 2;
                } else if (args.column.field === '11:30' || args.column.field === '4:00') {
                    args.colSpan = 3;
                }
                break;
            case 10008:
                if (args.column.field === '9:00' || args.column.field === '10:30' || args.column.field === '2:30') {
                    args.colSpan = 3;
                } else if (args.column.field === '4:00') {
                    args.colSpan = 2;
                }
                break;
            default:
                this.extendQueryCellEvent(args, data.EmployeeID);
        }
    },
    extendQueryCellEvent: function(args, value) {
        switch (value) {
            case 10009:
                if (args.column.field === '9:00' || args.column.field === '11:30') {
                    args.colSpan = 3;
                } else if (args.column.field === '4:30' || args.column.field === '2:30') {
                    args.colSpan = 2;
                }
                break;
            case 100010:
                if (args.column.field === '9:00' || args.column.field === '2:30' ||
                    args.column.field === '4:00' || args.column.field === '11:30') {
                    args.colSpan = 3;
                } else if (args.column.field === '10:30') {
                    args.colSpan = 2;
                }
                break;
        }
    }
    }
  });
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Responsive columns

You can toggle column visibility based on media queries which are defined
at the [`hideAtMedia`](../api/grid/column/#hideatmedia).
The [`hideAtMedia`](../api/grid/column/#hideatmedia) accepts valid
[Media Queries]( http://cssmediaqueries.com/what-are-css-media-queries.html ). In the below sample, for `OrderID` column, `hideAtMedia` property value is set as `(min-width: 700px)` so that `OrderID` column will gets hidden when the browser screen width is lessthan 700px.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' height='315px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120 hideAtMedia='(min-width: 700px)'>
                </e-column> //  column visibility hide when browser screen width lessthan 700px;
                <e-column field='CustomerID' headerText='Customer ID' width=140 hideAtMedia='(max-width: 700px)'>
                </e-column> // column Visibility show when browser screen width  500px or less;
                <e-column field='Freight' headerText='Freight' textAlign='Right' format='C' width=120
                hideAtMedia='(min-width: 500px)'>
                </e-column> // column visibility hide when browser screen width lessthan 500px;
                <e-column field='OrderDate' headerText='Order Date' textAlign='Right' format='yMd' type='date' width=140>
                </e-column> // it always shown
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Controlling Grid Actions

You can enable or disable grid action for a particular column by setting the [`allowFiltering`](../api/grid/columnModel/#allowfiltering),
[`allowGrouping`](../api/grid/columnModel/#allowgrouping),[`allowReordering`](../api/grid/columnModel/#allowreordering), [`allowEditing`](../api/grid/columnModel/#allowediting) and [`allowSorting`](../api/grid/columnModel/#allowsorting) properties.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :allowReordering="true" :editSettings='editSettings' :allowSorting="true" :allowFiltering="true" :allowGrouping="true" height="220px">
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90 :allowGrouping="false" :allowReordering="false"></e-column>
                <e-column field='CustomerID' headerText='Customer ID' :allowEditing="false" width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90 :allowFiltering="false"></e-column>
                <e-column field='OrderDate' headerText='Order Date' textAlign='Right' type='date' format='yMd' width=120 :allowSorting="false"></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Sort, Group, Filter, Reorder, Edit } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
    };
  },
  provide: {
      grid: [Sort, Group, Filter, Reorder, Edit]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Show/Hide Columns by External Button

You can show or hide the grid columns dynamically through external buttons by invoking the [`showColumns`](../api/grid/#showcolumns)/[`hideColumns`](../api/grid/#hidecolumns)
methods.

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-button @click.native="show"> Show </ejs-button>
        <ejs-button @click.native="hide"> Hide </ejs-button>
        <ejs-grid ref='grid' :dataSource='data' :height='280'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
                <e-column field='OrderDate' headerText='Order Date' textAlign='Right' format='yMd' width=120 type='date'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { data } from './datasource.js';

Vue.use(GridPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  methods: {
    show: function() {
        this.$refs.grid.showColumns(['Customer ID', 'Ship Name']); // show by HeaderText
    },
    hide: function() {
        this.$refs.grid.hideColumns(['Customer ID', 'Ship Name']); // hide by HeaderText
    }

  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Complex Data Binding

You can achieve complex data binding in the grid by using the dot(.) operator in the [`column.field`](../api/grid/column/#field).

{% tab template="grid/column/complex" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :height='315'>
            <e-columns>
                <e-column field='EmployeeID' headerText='Employee ID' textAlign='Right' width=120></e-column>
                <e-column field='Name.FirstName' headerText='First Name' width=120></e-column>
                <e-column field='Name.LastName' headerText='Last Name' width=120></e-column>
                <e-column field='Title' headerText='Title' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## ValueAccessor

The [`valueAccessor`](../api/grid/column/#valueaccessor) is used to access/manipulate the value of display data.
You can achieve custom value formatting by using [`valueAccessor`](../api/grid/column/#valueaccessor).

{% tab template="grid/column/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' height='315'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Right' :valueAccessor='currencyFormatter' width=80></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=130 :valueAccessor='valueAccess' ></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  methods: {
    currencyFormatter: function(field, data, column) {
        return '€' + data['Freight'];
    },
    valueAccess: function (field, data, column) {
        return data[field] + '-' + data['ShipRegion'];
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### Display Array type Columns

You can bind an Array of Objects in a column by using [`valueAccessor`](../api/grid/column/#valueaccessor) property.
In this example, The Name field has an array of two objects FirstName and LastName. These two objects are joined and bind to a column using
[`valueAccessor`](../api/grid/column/#valueaccessor).

{% tab template="grid/column/arraytypecolumn" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' height='315'>
            <e-columns>
                <e-column field='EmployeeID' headerText='Employee ID' textAlign='Right' width=90></e-column>
                <e-column field='Name' headerText='Full Name' :valueAccessor= 'valueAccess' width=120></e-column>
                <e-column field='Title' headerText='Title' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  methods: {
    valueAccess: function(field, data, column) {
        return data[field].map((s) => { return s.LastName || s.FirstName; }).join(' ');
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### Expression Column

You can achieve the expression column by using [`valueAccessor`](../api/grid/column/#valueaccessor) property.

{% tab template="grid/column/expression" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :height='315'>
            <e-columns>
                <e-column field='FoodName' headerText='Food Name' width=150></e-column>
                <e-column field='Protein' headerText='Protein' textAlign='Right' width=120></e-column>
                <e-column field='Fat' headerText='Fat' textAlign='Right' width=80></e-column>
                <e-column field='Carbohydrate' headerText='Carbohydrate' textAlign='Right' width=120></e-column>
                <e-column headerText='Calories Intake' textAlign='Right' :valueAccessor='totalCalories' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  methods: {
    totalCalories: function(field, data, column) {
        return data.Protein * 4 + data.Fat * 9 + data.Carbohydrate * 4;
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Foreign Key Column

Foreign key column can be enabled by using [`column.dataSource`](../api/grid/column/#datasource),
[`column.foreignKeyField`](../api/grid/column/#foreignkeyfield) and
[`column.foreignKeyValue`](../api/grid/column/#foreignkeyvalue) properties.

* [`column.dataSource`](../api/grid/column/#datasource) - Defines the foreign data.
* [`column.foreignKeyField`](../api/grid/column/#foreignkeyfield) - Defines the mapping column name to the foreign data.
* [`column.foreignKeyValue`](../api/grid/column/#foreignkeyvalue) - Defines the display field from the foreign data.

In the following example, `Employee Name` is a foreign column which shows `FirstName` column from foreign data.

{% tab template="grid/column/foreigncolumn" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' height='315'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='EmployeeID' headerText='Employee Name' width=120 foreignKeyValue='FirstName' :dataSource='employeeData'></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Right' width=80></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=130  ></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, ForeignKey } from "@syncfusion/ej2-vue-grids";
import { data, employeeData } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      employeeData: employeeData
    };
  },
  provide: {
      grid: [ForeignKey]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> * For remote data, the sorting and grouping is done based on [`column.foreignKeyField`](../api/grid/column/#foreignkeyfield) instead of
[`column.foreignKeyValue`](../api/grid/column/#foreignkeyvalue).
> * If [`column.foreignKeyField`](../api/grid/column/#foreignkeyfield) is not defined, then the column uses [`column.field`](../api/grid/column/#field).

## How to render boolean values as checkbox

To render boolean values as checkbox in columns, you need to set `displayAsCheckBox` property as `true`.

{% tab template="grid/column/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' height='315'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign= 'Right' width=120 format= 'C2'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' width=150></e-column>
                <e-column field='ShippedDate' headerText='Shipped Date' width=150></e-column>
                <e-column field='Verified' headerText='Verified' displayAsCheckBox='true' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
    };
  },
  provide: {
    grid: [Page]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

{% endtab %}

## See Also

* [How to Change Column Header Text Dynamically](./how-to/change-orientation-of-header-text)
* [Customize Column Styles](./how-to/customize-column-styles)
* [Custom Tooltip for Columns](./how-to/custom-tool-tip-for-columns)
* [How to Render Other Component in a Column](./how-to/render-other-components-in-column)
* [Group Column by Format](./grouping/#group-by-format)
* [How to Use Edit Template in Foreign Key Column](./how-to/use-edit-template-in-foreign-key-column)
* [How to Create and use custom Filter UI in Foreign Key Column](./how-to/customize-filter-ui-in-foreign-key)
* [How to Use Filter Bar Template in Foreign Key Column](./how-to/use-edit-template-in-foreign-key-column)
* [How to Perform aggregation in Foreign Key Column](./how-to/perform-aggregation-in-foreign-key-column)
* [How to set complex column as Foreignkey column](./how-to/complex-column-as-foreign-key-column)
* [Complex Data Binding with list of Array Of Objects](./how-to/list-of-array-of-objects)