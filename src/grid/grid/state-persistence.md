---
title: "State Persistence"
component: "Grid"
description: "Learn how to persist the DataGrid state and model in the browser’s local storage."
---

# State Persistence

State persistence refers to the Grid's state maintained in the browser's
[`localStorage`](https://www.w3schools.com/html/html5_webstorage.asp#)
even if the browser is refreshed or if you move to the next page within the browser.
State persistence stores grid’s model object in the local storage when the
[`enablePersistence`](../api/grid/#enablepersistence) is defined as true.

## Maintaining Custom Query in State Persistence

Grid does not maintain the query params after page load event when
[`enablePersistence`](../api/grid/#enablepersistence) is set to true.
This is because the Grid refreshes its query params for every page load. You can maintain the custom query params by resetting the
`addParams`
method in the [`actionBegin`](../api/grid/#actionbegin) event.

{% tab template="grid/sort/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref="grid" :dataSource='data' :allowSorting='true' :enablePersistence='true' :allowPaging='true' :allowFiltering='true' height='210px' :actionBegin='actionHandler'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Sort, Page, Filter } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  methods: {
    actionHandler: function (){
        this.$refs.grid.ej2Instances.query.addParams('$filter', 'EmployeeID eq 1');
    }
  }
  provide: {
    grid: [Sort, Page, Filter]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## How to get or set localStorage value

If the [`enablePersistence`](../api/grid/#enablepersistence) property set as true,
The Grid property value is saved in the `window.localStorage` for reference. You can get/set the localStorage value by using the
`getItem`/`setItem` method in `window.localStorage`.

```typescript
//get the Grid model.
let value = window.localStorage.getItem('gridGrid'); //"gridGrid" is component name + component id.
let model = JSON.parse(model);

```

```typescript
//set the Grid model.
window.localStorage.setItem('gridGrid', JSON.stringify(model)); //"gridGrid" is component name + component id.

```

## Restore initial Grid state

When the [`enablePersistence`](../api/grid/#enablepersistence) property is set to **true**, the Grid will keep its state even if the page is reloaded. In some cases, you may be required to retain the Grid in its initial state. The Grid will not retain its initial state now since the [`enablePersistence`](../api/grid/#enablepersistence) property has been enabled.

You can achieve this by destroying the grid after disabling the [`enablePersistence`](../api/grid/#enablepersistence) property and clearing the local storage data, as shown in the sample below.

{% tab template="grid/sort/default" %}

```html
<template>
    <div id="app">
       <button id="restore"  @click="clickRestore">Restore to initial state</button>
      <br /><br />
        <ejs-grid ref="grid" :dataSource='data' :enablePersistence='true' :allowPaging='true' :allowFiltering='true' height='230px' id="Grid">
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Filter } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  methods: {
    clickRestore: function () {
        this.$refs.grid.ej2Instances.enablePersistence = false;
        window.localStorage.setItem("gridGrid", "");
        this.$refs.grid.ej2Instances.destroy();
        location.reload();
    }
  },
  provide: {
    grid: [Page, Filter]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## How to add a new column while using enablePersistence

The Grid columns can be persisted when the [enablePersistence](../api/grid/#enablepersistence) property is set to true. If you want to add the new columns with the existing persist state, you can use the Grid inbuilt method such as `column.push` and call the [refreshColumns()](../api/grid/#refreshcolumns) method for UI changes. Please refer to the following sample for more information.

{% tab template="grid/sort/default" %}

```html
<template>
    <div id="app">
       <button id="add"  @click="clickAdd">Add Columns</button>
      <br /><br />
        <ejs-grid ref="grid" :dataSource='data' :enablePersistence='true' :allowPaging='true' height='230px' id="Grid">
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
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
      data: data
    };
  },
  methods: {
     clickAdd: function () {
        let obj = { field: "Freight", headerText: 'Freight', width: 120 }
        this.$refs.grid.ej2Instances.columns.push(obj as any); //you can add the columns by using the Grid columns method
        this.$refs.grid.ej2Instances.refreshColumns();
    }
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

## How to prevent columns from persisting

When the [enablePersistence](../api/grid/#enablepersistence) property is set to true, the Grid properties such as [Grouping](../api/grid/groupSettingsModel/), [Paging](../api/grid/pageSettingsModel/), [Filtering](../api/grid/pageSettingsModel/), [Sorting](../api/grid/sortSettingsModel/), and [Columns](../api/grid/columnModel/) will persist. You can use the `addOnPersist` method to prevent these Grid properties from persisting.

The following example demonstrates how to prevent Grid columns from persisting. In the [dataBound](../api/grid/#databound) event of the Grid, you can override the `addOnPersist` method and remove the columns from the key list given for persistence.

>**Note:** When the [enablePersistence](../api/grid/#enablepersistence) property is set to true, the Grid properties such as column template, column formatter, header text, and value accessor will not persist.

{% tab template="grid/sort/default" %}

```html
<template>
    <div id="app">
       <button id="add"  @click="clickAdd">Add Columns</button>
       <button id="remove"  @click="clickRemove">Remove Columns</button>
      <br /><br />
        <ejs-grid ref="grid" :dataSource='data' :enablePersistence='true' :allowPaging='true' height='230px' id="Grid" :dataBound='dataBound'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
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
      data: data
    };
  },
  methods: {
    dataBound: function () {
        let cloned =  this.$refs.grid.ej2Instances.addOnPersist;
        this.$refs.grid.ej2Instances.addOnPersist = function (key: any) {
            key = key.filter((item: string)  => item !== "columns");
            return cloned.call(this, key);
        };
    },
     clickAdd: function () {
        let obj = { field: "Freight", headerText: 'Freight', width: 120 }
        this.$refs.grid.ej2Instances.columns.push(obj as any); //you can add the columns by using the Grid columns method
        this.$refs.grid.ej2Instances.refreshColumns();
    },
     clickRemove: function () {
        this.$refs.grid.ej2Instances.columns.pop();
        this.$refs.grid.ej2Instances.refreshColumns();
    }
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

## Persist the Grid column template, header template, and headerText

By default, the Grid properties such as column template, header text, header template, column formatter, and value accessor will not persist when [enablePersistence](../api/grid/#enablepersistence) is set to true. Because the column template and header text can be customized at the application level.

If you wish to restore all these column properties, then you can achieve it by cloning the grid’s columns property using JavaScript Object’s assign method and storing this along with the persist data manually. While restoring the settings, this column object must be assigned to the grid’s columns property to restore the column settings as demonstrated in the following sample.

{% tab template="grid/sort/default" %}

```html
<template>
    <div id="app">
       <button id="restore"  @click="clickRestore">Restore</button>
      <br /><br />
        <ejs-grid ref="grid" :dataSource='data' :enablePersistence='true' :allowPaging='true' height='230px' id="Grid">
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150 :headerTemplate="hTemplate"></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=150 :template='cTemplate'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
 <script id="template" type="text/x-template">
        <a rel='nofollow' href=https://en.wikipedia.org/wiki/${ShipName}><span class="e-icons e-column"></span></a>
    </script>
  
    <script id="customertemplate" type="text/x-template">
        <span class="e-icons e-header" ></span>
        Customer ID
    </script>
<script>
import Vue from "vue";
import { GridPlugin, Page } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

var headTemplate = Vue.component("header", {
    template: '<span class="e-icons e-header">CustomerID</span>',
    data() {
    return {
        data: {}
    };
    }
});

var columnTemplate = Vue.component("column", {
     template: '<a rel="nofollow" href="https://en.wikipedia.org/wiki/${ShipName}"><span class="e-icons e-column"></span></a>',
     data() {
     return {
         data: {}
     };
     }
});

export default {
  data() {
    return {
      data: data,
      hTemplate: function (e) {
          return {
              template: headTemplate
          };
      },
      cTemplate: function (e) {
          return {
              template: columnTemplate
          };
      }
    };
  },
  methods: {
    clickRestore: function () {
        let savedProperties = JSON.parse(this.$refs.grid.ej2Instances.getPersistData());
        let gridColumnsState = Object.assign([], this.$refs.grid.ej2Instances.getColumns());
        savedProperties.columns.forEach((col: {
            field: any;
            headerText: any;
            template: any;
            headerTemplate: any;
        }) => {
            let headerText = gridColumnsState.find((colColumnsState) => colColumnsState.field === col.field)['headerText'];
            let colTemplate = gridColumnsState.find((colColumnsState) => colColumnsState.field === col.field)['template'];
            let headerTemplate = gridColumnsState.find((colColumnsState) => colColumnsState.field === col.field)['headerTemplate'];
            col.headerText = 'Text Changed';
            col.template = colTemplate;
            col.headerTemplate = headerTemplate; //likewise you can restore required column properties as per your wants.
        }
        );
       console.log(savedProperties);
       this.$refs.grid.ej2Instances.setProperties(savedProperties);
    }
  },
  provide: {
    grid: [Page]
  }
}
</script>
<style>
   .e-column:before {
      content: '\e815';
    }

    .e-header:before {
      content: '\ea9a';
    }
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}