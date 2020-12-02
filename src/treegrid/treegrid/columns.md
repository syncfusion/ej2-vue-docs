---
title: "Columns"
component: "TreeGrid"
description: "Documentation on column reordering, resizing, header templates (custom header content), and column templates (custom cell content) in the Essential JS 2 TreeGrid control."
---

# Columns

The column definitions are used as the [`dataSource`](../api/treegrid#dataSource) schema in the TreeGrid. This plays a vital role in rendering column values in the required format.
The treegrid operations such as sorting, filtering and searching etc. are performed based on column definitions. The [`field`](../api/treegrid/column#field) property of the [`columns`](../api/treegrid#column)
is necessary to map the data source values in TreeGrid columns.

> 1. If the column [`field`](../api/treegrid/column#field) is not specified in the dataSource, the column values will be empty.
> 2. If the [`field`](../api/treegrid/column#field) name contains “dot” operator, it is considered as complex binding.

[`treeColumnIndex`](../api/treegrid#treecolumnindex) property denotes the column that is used to expand and collapse child rows.

## Header Template

You can customize the header element by using the [`headerTemplate`](../api/treegrid/column#headerTemplate) property.

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='subtasks' :treeColumnIndex='0' height='315px'>
            <e-columns>
                <e-column field='taskName' :headerTemplate='projectName' width=180></e-column>
                <e-column field='startDate' :headerTemplate='dateTemplate' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' :headerTemplate='durationTemplate' textAlign='Right'></e-column>
                <e-column field='progress' :headerTemplate='progressTemplate' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { headerData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: headerData,
       projectName: function () {
          return { template : Vue.component('columnTemplate',{
             template: `<div class="image">
                    <img :src="image" width=20 height=20 class="e-image"/> Task Name
                </div>`,
                data: function() {
                    return {
                        data: {}
                    }
                },
                computed: {
                    image: function() {
                        return "Taskname.png";
                    }
                }
          })}
      },
     dateTemplate: function () {
          return { template : Vue.component('columnTemplate',{
             template: `<div class="image">
                    <img :src="image" width=20 height=20 class="e-image"/> Start Date
                </div>`,
                data: function() {
                    return {
                        data: {}
                    }
                },
                computed: {
                    image: function() {
                        return "Startname.png";
                    }
                }
          })}
      },
      durationTemplate: function () {
          return { template : Vue.component('columnTemplate',{
             template: `<div class="image">
                    <img :src="image" width=20 height=20 class="e-image"/> Duration
                </div>`,
                data: function() {
                    return {
                        data: {}
                    }
                },
                computed: {
                    image: function() {
                        return "Duration.png";
                    }
                }
          })}
      },
      progressTemplate: function () {
          return { template : Vue.component('columnTemplate',{
             template: `<div class="image">
                    <img :src="image" width=20 height=20 class="e-image"/> Progress
                </div>`,
                data: function() {
                    return {
                        data: {}
                    }
                },
                computed: {
                    image: function() {
                        return "progress.png" ;
                    }
                }
          })}
      }
    };
  },
}
</script>

```

{% endtab %}

## Header text

By default, column header title is displayed from column [`field`](../api/treegrid/column#field) value. To override the default header title, you have to define the [`headerText`](../api/treegrid/column#headertext) value.

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='subtasks' :treeColumnIndex='1' height='315px'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90 textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width=180></e-column>
                <e-column field='startDate' headerText='Start Date' width=90 format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: sampleData,
    };
  },
}
</script>

```

{% endtab %}

> * If both the [`field`](../api/treegrid/column#field) and [`headerText`](../api/treegrid/column#headertext)
are not defined in the column, the column renders with “empty” header text.

## Format

To format cell values based on specific culture, use the [`columns.format`](../api/treegrid/column#format) property. The TreeGrid uses [Internalization](../common/internationalization/) library to format [`number`](../common/internationalization/#number-formatting) and [`date`](../common/internationalization/#manipulating-datetime)
values.

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='subtasks' :treeColumnIndex='1' height='315px'>
            <e-columns>
                <e-column field='orderID' headerText='Order ID' width=90 textAlign='Right'></e-column>
                <e-column field='orderName' headerText='Order Name' width=220></e-column>
                <e-column field='price' headerText='Price' format='C2' width=80 textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { formatData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: formatData,
    };
  },
}
</script>

```

{% endtab %}

> By default, the [`number`](../common/internationalization/#number-formatting) and [`date`](../common/internationalization/#manipulating-datetime) values are formatted in `en-US` locale.

### Number formatting

The number or integer values can be formatted using the below format strings.

Format |Description |Remarks
-----|-----
N | Denotes numeric type. | The numeric format is followed by integer value as N2, N3. etc which denotes the number of precision to be allowed.
C | Denotes currency type. | The currency format is followed by integer value as C2, C3. etc which denotes the number of precision to be allowed.
P | Denotes percentage type | The percentage format expects the input value to be in the range of 0 to 100. For example the cell value `0.2` is formatted as `20%`. The percentage format is followed by integer value as P2, P3. etc which denotes the number of precision to be allowed.

Please refer to the link to know more about [`Number formatting`](../common/internationalization/#number-formatting).

### Date formatting

You can format date values either using built-in date format string or custom format string.

For built-in date format you can specify [`columns.format`](../api/treegrid/column#format) property as string   (Example: `yMd`). Please refer to the link to know more about [`Date formatting`](../common/internationalization/#manipulating-datetime).

You can also use custom format string to format the date values. Some of the custom formats and the formatted date values are given in the below table.

Format | Formatted value
-----|-----
{ type:'date', format:'dd/MM/yyyy' } | 04/07/1996
{ type:'date', format:'dd.MM.yyyy' } | 04.07.1996
{ type:'date', skeleton:'short' } | 7/4/96
{ type: 'dateTime', format: 'dd/MM/yyyy hh:mm a' } | 04/07/1996 12:00 AM
{ type: 'dateTime', format: 'MM/dd/yyyy hh:mm:ss a' } | 07/04/1996 12:00:00 AM

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='subtasks' :treeColumnIndex='1' height='315px'>
            <e-columns>
                <e-column field='orderID' headerText='Order ID' width=90 textAlign='Right'></e-column>
                <e-column field='orderName' headerText='Order Name' width=100></e-column>
                <e-column field='orderDate' headerText='Order Date' width=160 :format='formatOptions' type='date' textAlign='Right'></e-column>
                <e-column field='price' headerText='Price' width=90 format='C2' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { formatData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: formatData,
      formatOptions: {type:'date', format:'dd/MM/yyyy'},
    };
  },
}
</script>

```

{% endtab %}

## Reorder

Reordering can be done by drag and drop of a particular column header from one index to another index within the treegrid. To enable reordering, set the [`allowReordering`](../api/treegrid/#allowreordering) to true.

To use reordering, inject the [`Reorder`](../api/treegrid/#reordermodule) module in the treegrid.

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='subtasks' :allowReordering='true' :treeColumnIndex='1' height='285px'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90 textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width=180></e-column>
                <e-column field='startDate' headerText='Start Date' width=90 format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Reorder } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: sampleData,
    };
  },
   provide: {
      treegrid: [ Reorder ]
    }
}
</script>

```

{% endtab %}

> You can disable reordering a particular column by setting the [`columns.allowReordering`](../api/treegrid/column/#reordermodule) to false.

### Reorder Multiple Columns

Multiple columns can be reordered at a time by using the [`reorderColumns`](../api/treegrid/column#reordercolumns) method.

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
    <ejs-button id='reorderMultipleCols' @click.native='reorder'>Reorder TASK ID AND DURATION TO LAST</ejs-button>
        <ejs-treegrid ref='treegrid' :dataSource="data" childMapping='subtasks' :allowReordering='true' :treeColumnIndex='1' height='285px'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90 textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width=180></e-column>
                <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
                <e-column field='progress' headerText='Progress' width=80 textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Reorder } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(TreeGridPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      data: sampleData,
    };
  },
   provide: {
      treegrid: [ Reorder ]
    },
     methods:{
       reorder: function() {
          this.$refs.treegrid.reorderColumns(['taskID','duration'],'progress');
      }
  }
}
</script>

```

{% endtab %}

## Lock Columns

You can lock columns by using [`column.lockColumn`](../api/treegrid/column/#lockcolumn) property. The locked columns will be moved to the first position. Also you can’t reorder its position.

In the below example, duration column is locked and its reordering functionality is disabled.

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='subtasks' :treeColumnIndex='1' :allowReordering='true' :allowSelection='false' height='315px'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90 textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width=180></e-column>
                <e-column field='startDate' headerText='Start Date' width=90 format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width=80 textAlign='Right' :lockColumn='true' :customAttributes="customAttributes"></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Reorder } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: sampleData,
      customAttributes : {class: 'customcss'}
    };
  },
  provide: {
      treegrid: [ Reorder ]
    },
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-treegrid/styles/material.css";
 .e-grid .e-rowcell.customcss{
  background-color: #ecedee;
}
.e-grid .e-headercell.customcss{
  background-color: #ecedee;
}
</style>
```

{% endtab %}

## Column resizing

Column width can be resized by clicking and dragging the right edge of the column header. While dragging, the width of the respective column will be resized immediately. Each column can be auto resized by double-clicking the right edge of the column header to fit the width of that column based on the widest cell content. To enable column resize, set the [`allowResizing`](../api/treegrid/#allowresizing) property to true.

To use the column resize, inject `Resize` module in the treegrid.

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='subtasks' :treeColumnIndex='1' :allowResizing='true' height='315px'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90 textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width=180></e-column>
                <e-column field='startDate' headerText='Start Date' width=90 format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Resize } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: sampleData,
    };
  },
   provide: {
      treegrid: [ Resize ]
    },
}
</script>

```

{% endtab %}

> * You can disable resizing for a particular column by setting the [`columns.allowResizing`](../api/treegrid/column/#allowresizing) to false.
> * In RTL mode, you can click and drag the left edge of the header cell to resize the column.

### Min and max width

Column resize can be restricted between minimum and maximum width by defining the [`columns->minWidth`](../api/treegrid/column/#minwidth) and [`columns->maxWidth`](../api/treegrid/column/#maxwidth).

In the following sample, minimum and maximum width are defined for `Duration`, and `Task Name` columns.

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='subtasks' :treeColumnIndex='1' :allowResizing='true' height='315px'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90 textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name'minWidth= 170 width=180 maxWidth=250></e-column>
                <e-column field='duration' headerText='Duration' minWidth= 50 width=80 maxWidth=150 textAlign='Right'></e-column>
                <e-column field='progress' headerText='Progress'  width=80 textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Resize } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: sampleData,
    };
  },
   provide: {
      treegrid: [ Resize ]
    },
}
</script>

```

{% endtab %}

### Resize Stacked Column

Stacked columns can be resized by clicking and dragging the right edge of the stacked column header. While dragging, the width of the respective child columns will be resized at the same time. You can disable resize for particular stacked column by setting `allowResizing` as `false` to its columns.

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='subtasks' :treeColumnIndex='1' :allowResizing='true' height='260px'>
             <e-columns>
                <e-column headerText='Order Details' :columns='orderColumns'></e-column>
                <e-column headerText='Shipment Details' :columns='shipColumns'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Resize } from "@syncfusion/ej2-vue-treegrid";
import { stackedData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: stackedData,
        orderColumns : [
            { field: 'orderID', headerText: 'Order ID', textAlign: 'Right', width: 90 },
            { field: 'orderName', headerText: 'Order Name', textAlign: 'Left', width: 170 },
        ],
        shipColumns : [
            { field: 'shipMentCategory', headerText: 'Shipment Category', textAlign: 'Left', width: 90 },
            { field: 'shippedDate', headerText: 'Shipped Date', textAlign: 'Right', format: 'yMd', width: 90 }
        ]
    };
  },
   provide: {
      treegrid: [ Resize ]
    },
}
</script>

```

{% endtab %}

### Touch interaction

When the right edge of the header cell is tapped, a floating handler will be visible over the right border of the column. To resize the column, tap and drag the floating handler as needed.

The following screenshot represents the column resizing in touch device.

<!-- markdownlint-disable MD033 -->
<img src="/treegrid/images/column-resizing.png" alt="Touch interaction image" style="width:320px;height: 620px">
<!-- markdownlint-enable MD033 -->

## Column template

The column [`template`](../api/treegrid/column/#template) has options to display custom element instead of a field value in the column.

{% tab template="treegrid/column-template/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex='0' :height='260' :rowHeight='83' childMapping='Children'>
            <e-columns>
                <e-column field='EmpID' headerText='Employee ID' width=95></e-column>
                <e-column field='Name' headerText='Name' width=110></e-column>
                <e-column field='DOB' headerText=' Start Date' textAlign='Right' format='yMd' width=90></e-column>
                <e-column field='Year GR' textAlign='Center' :template='template1'  width=120></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { SparklinePlugin } from "@syncfusion/ej2-vue-charts";
import { sparkdata, getSparkData, textData } from "./datasource.js";
import { RowDataBoundEventArgs, getObject } from '@syncfusion/ej2-grids';
import { EmitType } from '@syncfusion/ej2-base';
import { Sparkline, ISparklineLoadEventArgs, SparklineTheme } from '@syncfusion/ej2-charts';

Vue.use(TreeGridPlugin);
Vue.use(SparklinePlugin);

let winloss: Sparkline;

export default {
 data() {
    return {
      data: textData,
       template1: function () {
          return { template : Vue.component('columnTemplate',{
             template: `<ejs-sparkline :id='elemid' height='50px' width='150px' type='WinLoss' valueType='Numeric' fill='#3C78EF' negativePointColor='#f7a816' tiePointColor='darkgray'  :dataSource='sparkData(data.EmployeeID)'></ejs-sparkline> `,
                data: function() {
                    return {
                        data: {},
                    }
                },
                methods:{
                    sparkData: function(id: number){
                        return getSparkData('column', id);
                    }
                },
                computed: {
                    elemid: function() {
                        return 'spkwl' + this.data.EmployeeID;
                     },
          })}
    };
    };
  }
}
</script>

```

{% endtab %}

> TreeGrid actions such as editing, filtering and sorting etc. will depend upon the column [`field`](../api/treegrid/column/#field). If the [`field`](../api/treegrid/column/#field) is not specified in the
template column, the treegrid actions cannot be performed.

### Using condition template

You can render the template elements based on condition.

In the following code, checkbox is rendered based on `Approved` field value.

```html
  <script id="template" type="text/x-template">
            `<div v-if=cData class="template_checkbox">
                    <input type="checkbox" checked />
                </div>
                <div v-else class="template_checkbox">
                    <input type="checkbox" />
                </div>`
        </script>
```

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='subtasks' :treeColumnIndex='1' height='315px' >
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90 textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width=180></e-column>
                <e-column field='approved' headerText='Approved' width=120 textAlign='Centre' :template='approvedtemplate'></e-column>
                <e-column field='progress' headerText='Progress' width=80 textAlign='Right'></e-column>
                </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
 data() {
    return {
      data: sampleData,
      approvedtemplate: function () {
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
                        return this.data.approved;
                    }
                }
          })}
    };
  }
}
}
</script>

```

{% endtab %}

## Column type

Column type can be specified using the [`columns.type`](../api/treegrid/column/#type) property. It specifies the type of data the column binds.

If the [`format`](../api/treegrid/column/#format)  is defined for a column, the column uses [`type`](../api/treegrid/column/#type) to select the appropriate format option ([number](../common/internationalization/#number-formatting)
 or [date](../common/internationalization/#manipulating-datetime)).

TreeGrid column supports the following types:
* string
* number
* boolean
* date
* datetime

> If the [`type`](../api/treegrid/column/#type) is not defined, it will be determined from the first record of the [`dataSource`](../api/treegrid/column/#datasource).

## Column menu

The column menu has options to integrate features like sorting, filtering, and autofit. It will show a menu with the integrated feature when users click on multiple icon of the column. To enable column menu, you need to define the [`showColumnMenu`](../api/treegrid/#showcolumnmenu) property as true.

To use the column menu, inject the `ColumnMenu` module in the treegrid.

The default items are displayed in following table.

| Item | Description |
|-----|-----|
| `SortAscending` | Sort the current column in ascending order. |
| `SortDescending` | Sort the current column in descending order. |
| `AutoFit` | Auto fit the current column. |
| `AutoFitAll` | Auto fit all columns. |
| `Filter` | Show the filter option as given in `filterSettings.type` |

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex='1' :allowPaging='true' :showColumnMenu='true' childMapping='subtasks'
         :allowFiltering='true' :filterSettings='filterSettings' :allowResizing='true' :pageSettings='pageSettings'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' textAlign='Right' width=90></e-column>
                <e-column field='taskName' headerText='Task Name' width=180></e-column>
                <e-column field='startDate' headerText=' Start Date' textAlign='Right' format='yMd' type='date' width=90></e-column>
                <e-column field='duration' headerText='Duration' textAlign='Right'  width=80></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Sort, Resize, ColumnMenu, Page, Filter } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
 data() {
    return {
      data: sampleData,
      filterSettings: { type: "Menu" },
      pageSettings: { pageCount: 4, pageSize: 10 }
    };
  },
  provide: {
      treegrid: [Sort, Resize, ColumnMenu, Page, Filter]
  }
}
</script>

```

{% endtab %}

> * You can disable column menu for a particular column by defining the [`columns.showColumnMenu`](../api/treegrid/column/#showcolumnmenu) as false.

## Checkbox Column

To render checkboxes in existing column, you need to set [`columns.showCheckbox`] property as `true`.

It is also possible to select the rows hierarchically using checkboxes in TreeGrid by enabling [`autoCheckHierarchy`] property. When we check on any parent record checkbox then the child record checkboxes will get checked.

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex='1' :autoCheckHierarchy='true' childMapping='subtasks' :height='400'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' textAlign='Right' width=90></e-column>
                <e-column field='taskName' headerText='Task Name' width=180 :showCheckbox='true'></e-column>
                <e-column field='startDate' headerText=' Start Date' textAlign='Right' format='yMd' type='date' width=90></e-column>
                <e-column field='duration' headerText='Duration' textAlign='Right'  width=80></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
 data() {
    return {
      data: sampleData,
    };
  },
  provide: {
      treegrid: [Page]
  }
}
</script>

```

{% endtab %}

## Responsive columns

You can toggle column visibility based on media queries which are defined
at the [`hideAtMedia`](../api/treegrid/column/#hideatmedia).
The [`hideAtMedia`](../api/treegrid/column/#hideatmedia) accepts valid
[Media Queries]( http://cssmediaqueries.com/what-are-css-media-queries.html ).

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex='1' childMapping='subtasks' height='315px'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' textAlign='Right'  hideAtMedia='(min-width: 700px)' width=90></e-column>
                <e-column field='taskName' headerText='Task Name' width=180></e-column>
                <e-column field='startDate' headerText=' Start Date' textAlign='Right'  hideAtMedia='(max-width: 500px)' format='yMd' type='date' width=90></e-column>
                <e-column field='duration' headerText='Duration' textAlign='Right' width=80></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: sampleData,
    };
  },
}
</script>

```

{% endtab %}

## Controlling TreeGrid actions

You can enable or disable treegrid action for a particular column by setting the [`allowFiltering`](../api/treegrid/column/#allowfiltering), and [`allowSorting`](../api/treegrid/column/#allowsorting) properties.

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='subtasks' :treeColumnIndex='1' :allowFiltering="true" :allowSorting="true" :height='270'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90 :allowSorting="false" textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width=180></e-column>
                <e-column field='startDate' headerText='Start Date' width=90 :allowFiltering="false" format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Sort , Filter } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
 data() {
    return {
      data: sampleData
    };
  },
  provide: {
      treegrid: [Sort, Filter]
  }
}
</script>

```

{% endtab %}

## Show/hide columns by external button

You can show or hide treegrid columns dynamically using external buttons by invoking the [`showColumns`](../api/treegrid/#showcolumns) or [`hideColumns`](../api/treegrid/#hidecolumns) method.

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-button @click.native="show"> Show </ejs-button>
        <ejs-button @click.native="hide"> Hide </ejs-button>
        <ejs-treegrid ref=treegrid :dataSource="data" childMapping='subtasks' :treeColumnIndex='1' :height='270'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90 textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width=180></e-column>
                <e-column field='startDate' headerText='Start Date' width=90 format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(TreeGridPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      data: sampleData
    };
  },
   methods:{
       show: function() {
        this.$refs.treegrid.showColumns(['Task ID', 'Duration']); // show by HeaderText
    },
    hide: function() {
        this.$refs.treegrid.hideColumns(['Task ID', 'Duration']); // hide by HeaderText
    }
  }

}
</script>

```

{% endtab %}

## Complex data binding

You can achieve complex data binding in the treegrid by using the dot(.) operator in the [`column.field`](../api/treegrid/column/#field).

{% tab template="treegrid/columns/default" %}

```html

<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :height='315'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90  textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width=180></e-column>
                <e-column field='assignee.firstName' headerText='Assignee' width=90></e-column>
                <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { complexData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
   data() {
    return {
      data: complexData
    };
  },
}
</script>

```

{% endtab %}

## ValueAccessor

The [`valueAccessor`](../api/treegrid/column/#valueaccessor) is used to access/manipulate the value of display data. You can achieve custom value formatting by using the [`valueAccessor`](../api/treegrid/column/#valueaccessor).

{% tab template="treegrid/columns/default" %}

```html

<template>
<div id="app">
        <ejs-treegrid  :dataSource="data" childMapping='subtasks' :treeColumnIndex='1' height='315px'>
            <e-columns>
                <e-column field='orderID' headerText='Order ID' width=100 textAlign='Right'></e-column>
                <e-column field='orderName' headerText='Order Name'  :valueAccessor='orderFormatter' width=215></e-column>
                <e-column field='orderDate' headerText='Order Date' width=110 :format='formatOptions' type='date' textAlign='Right'></e-column>
                <e-column field='price' headerText='Price' width=100  :valueAccessor='currencyFormatter' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { formatData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
   data() {
    return {
      data: formatData,
      formatOptions: {type:'date', format:'dd/MM/yyyy'},
    };
    },
    methods:{
        currencyFormatter: function(field, data, column) {
            return '€' + data['price'];
        },
    orderFormatter: function (field, data, column) {
        return data[field] + '-' + data['Category'];
    }
  }
}
</script>

```

{% endtab %}

### Display array type columns

You can bind an array of objects in a column by using the [`valueAccessor`](../api/treegrid/column/#valueaccessor) property.
In this example, the name field has an array of two objects, FirstName and LastName. These two objects are joined and bound to a column using the
[`valueAccessor`](../api/treegrid/column/#valueaccessor).

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid  :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' height='315px'>
            <e-columns>
               <e-column field='taskID' headerText='Task ID' width=110 textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width=180></e-column>
                <e-column field='name' headerText='Assignee' width=150 :valueAccessor='valueAccess' textAlign='Left'></e-column>
                <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { stringData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: stringData,
    };
    },
    methods:{
          valueAccess: function(field, data, column) {
              return data[field].map((s) => { return s.lastName || s.firstName; }).join(' ');
              }
  }
}
</script>

```

{% endtab %}

### Expression column

You can achieve the expression column by using the [`valueAccessor`](../api/treegrid/column/#valueaccessor) property.

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid  :dataSource="data" childMapping='subtasks' :treeColumnIndex='1' height='315px'>
            <e-columns>
                <e-column field='orderID' headerText='Order ID' width=110 textAlign='Right'></e-column>
                <e-column field='orderName' headerText='Order Name' width=210></e-column>
                <e-column field='units' headerText='Units' width=120 textAlign='Right'></e-column>
                <e-column field='unitPrice' headerText='Unit Price' width=120 textAlign='Right'></e-column>
                <e-column field='price' headerText='Price' width=120 :valueAccessor='totalPrice'
                textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { formatData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: formatData,
    };
    },
    methods:{
        totalPrice: function (field, data, column) {
            return data.units * data.unitPrice;
    }
  }
}
</script>

```

{% endtab %}

## How to render boolean values as checkbox

To render boolean values as checkbox in columns, you need to set [`displayAsCheckBox`](../api/treegrid/column/#displayascheckbox) property as `true`.

{% tab template="treegrid/columns/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='subtasks' :treeColumnIndex='1' height='315px'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90 textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width=180></e-column>
                <e-column field='approved' headerText='Approved' width=90 displayAsCheckBox='true'></e-column>
                <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: sampleData,
    };
  },
}
</script>

```

{% endtab %}