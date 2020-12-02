---
title: "Hierarchical Binding"
component: "Grid"
description: "Learn how to display master-detail data in the Essential JS 2 DataGrid control in a hierarchical manner."
---

# Hierarchical Binding

The Grid allows display of table data in a hierarchical structure to visualize relations between parent and child records.
This feature is enabled by defining the [`childGrid`](../api/grid/#childgrid) and
[`childGrid.queryString`](../api/grid/#querystring).
The [`childGrid`](../api/grid/#childgrid) describes the options of grid and the
[`childGrid.queryString`](../api/grid/#querystring) describes the relation between parent and child grids.

To use hierarchical binding, inject the **DetailRow** in the **provide** section.

{% tab template="grid/hierarchy-grid/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='parentData' height='315px' :childGrid='childGrid'>
            <e-columns>
                <e-column field='EmployeeID' headerText='Employee ID' textAlign='Right' width=120></e-column>
                <e-column field='FirstName' headerText='FirstName' width=150></e-column>
                <e-column field='LastName' headerText='Last Name' width=150></e-column>
                <e-column field='City' headerText='City' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, DetailRow } from "@syncfusion/ej2-vue-grids";
import { data, employeeData } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      parentData: employeeData,
      childGrid: {
        dataSource: data,
        queryString: 'EmployeeID',
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
            { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
            { field: 'ShipCity', headerText: 'Ship City', width: 150 },
            { field: 'ShipName', headerText: 'Ship Name', width: 150 }
        ]
      }
    }
  },
  provide: {
      grid: [DetailRow]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> * Grid supports n level of child grids.
> * Hierarchical binding is not supported when [`DetailTemplate`](../api/grid/#detailtemplate) is enabled.

## ExpandAll by external button

By default, grid renders in collapsed state.
You can expand all child grid rows by invoking the [`expandAll`](../api/grid/detailRow/#expandall) method,
and collapse all grid rows by invoking the [`collapseAll`](../api/grid/detailRow/#collapseall) through an external button.

{% tab template="grid/hierarchy-grid/default" %}

```html
<template>
    <div id="app">
        <ejs-button @click.native='expand'>Expand All</ejs-button>
        <ejs-button @click.native='collapse'>Collapse All</ejs-button>
        <ejs-grid ref='grid' :dataSource='parentData' height='265px' :childGrid='childGrid'>
            <e-columns>
                <e-column field='EmployeeID' headerText='Employee ID' textAlign='Right' width=120></e-column>
                <e-column field='FirstName' headerText='FirstName' width=150></e-column>
                <e-column field='LastName' headerText='Last Name' width=150></e-column>
                <e-column field='City' headerText='City' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, DetailRow } from "@syncfusion/ej2-vue-grids";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { data, employeeData } from './datasource.js';

Vue.use(GridPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      parentData: employeeData,
      childGrid: {
        dataSource: data,
        queryString: 'EmployeeID',
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
            { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
            { field: 'ShipCity', headerText: 'Ship City', width: 150 },
            { field: 'ShipName', headerText: 'Ship Name', width: 150 }
        ]
      }
    }
  },
  methods: {
    expand: function() {
        this.$refs.grid.ej2Instances.detailRowModule.expandAll();
    },
    collapse: function() {
        this.$refs.grid.ej2Instances.detailRowModule.collapseAll();
    }
  },
  provide: {
      grid: [DetailRow]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Expand child grid initially

You can expand a particular child grid at initial rendering by invoking the
[`expand`](../api/grid/detailRow/#expand) method in the [`dataBound`](../api/grid/#databound) event.

{% tab template="grid/hierarchy-grid/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='parentData' height='265px' :childGrid='childGrid' :dataBound='onDataBound'>
            <e-columns>
                <e-column field='EmployeeID' headerText='Employee ID' textAlign='Right' width=120></e-column>
                <e-column field='FirstName' headerText='FirstName' width=150></e-column>
                <e-column field='LastName' headerText='Last Name' width=150></e-column>
                <e-column field='City' headerText='City' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, DetailRow } from "@syncfusion/ej2-vue-grids";
import { data, employeeData } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      parentData: employeeData,
      childGrid: {
        dataSource: data,
        queryString: 'EmployeeID',
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
            { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
            { field: 'ShipCity', headerText: 'Ship City', width: 150 },
            { field: 'ShipName', headerText: 'Ship Name', width: 150 }
        ]
      }
    }
  },
  methods: {
    onDataBound: function() {
        this.$refs.grid.ej2Instances.detailRowModule.expand(2); // initially 2nd chid Grid will expand.
    }
  },
  provide: {
      grid: [DetailRow]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Dynamically load child grid data

You can dynamically load child grid dataSource by using the
[`detailDataBound`](../api/grid/#detaildatabound) event.
This [`detailDataBound`](../api/grid/#detaildatabound)
event triggers when the child grid is expanded for the first time.

{% tab template="grid/hierarchy-grid/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='parentData' height='265px' :childGrid='childGrid' :detailDataBound='onDetailDataBound'>
                <e-columns>
                    <e-column field='EmployeeID' headerText='Employee ID' textAlign='Right' width=120></e-column>
                    <e-column field='FirstName' headerText='FirstName' width=150></e-column>
                    <e-column field='LastName' headerText='Last Name' width=150></e-column>
                    <e-column field='City' headerText='City' width=150></e-column>
                </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, DetailRow } from "@syncfusion/ej2-vue-grids";
import { data, employeeData } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      parentData: employeeData,
      childGrid: {
        queryString: 'EmployeeID',
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
            { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
            { field: 'ShipCity', headerText: 'Ship City', width: 150 },
            { field: 'ShipName', headerText: 'Ship Name', width: 150 }
        ]
      }
    }
  },
  methods: {
    onDetailDataBound(args) {
        args.detailElement.querySelector('.e-grid').ej2_instances[0].dataSource = data; // assign data source for child grid.
    }
  },
  provide: {
      grid: [DetailRow]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Bind hierarchy grid with different field

By default, Parent and child grid relation will be maintained by [`queryString`](../api/grid/#querystring) property. We should use the same field name to map both parent and child grid. To achieve parent and child relation with different fields, we need to change the mapping value in the child grid [`load`](../api/grid/#load) event.

In the below sample, we have bound the child and parent grid with different fields. Parent grid field name as **EmployeeID** and the child grid field name as **ID**. We need to define the mapping value of **parentKeyFieldValue** from the parent row data in the child grid [`load`](../api/grid/#load) event.

{% tab template="grid/hierarchy-grid/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='parentData' height='265px' :childGrid='childGrid'>
                <e-columns>
                    <e-column field='EmployeeID' headerText='Employee ID' textAlign='Right' width=120></e-column>
                    <e-column field='FirstName' headerText='FirstName' width=150></e-column>
                    <e-column field='LastName' headerText='Last Name' width=150></e-column>
                    <e-column field='City' headerText='City' width=150></e-column>
                </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, DetailRow } from "@syncfusion/ej2-vue-grids";
import { data, employeeData, childdata } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      parentData: employeeData,
      childGrid: {
        dataSource: childdata,
        queryString: 'ID',
        columns: [
            { field: 'ID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
            { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
            { field: 'ShipCity', headerText: 'Ship City', width: 150 },
            { field: 'ShipName', headerText: 'Ship Name', width: 150 }
        ],
        load: function (){
         this.parentDetails.parentKeyFieldValue = this.parentDetails.parentRowData['EmployeeID'];
        }
      }
    }
  },
  provide: {
      grid: [DetailRow]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Adding Record in ChildGrid

Parent and child grid are related by [`queryString`](../api/grid/#querystring) field value.
To maintain this relation in newly added record, You need to set value for [`queryString`](../api/grid/#querystring) field in the added data
by the [`actionBegin`](../api/grid/#actionbegin) event.

In the below demo, **EmployeeID** field relates the parent and child grids. To add a new record in child grid, We have to set the **EmployeeID** field
with parent record's [`queryString`](../api/grid/#querystring) field value in the [`actionBegin`](../api/grid/#actionbegin) event.

{% tab template="grid/hierarchy-grid/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='parentData' height='265px' :childGrid='childGrid'>
                <e-columns>
                    <e-column field='EmployeeID' headerText='Employee ID' textAlign='Right' width=120></e-column>
                    <e-column field='FirstName' headerText='FirstName' width=150></e-column>
                    <e-column field='LastName' headerText='Last Name' width=150></e-column>
                    <e-column field='City' headerText='City' width=150></e-column>
                </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, DetailRow, Edit, Toolbar } from "@syncfusion/ej2-vue-grids";
import { data, employeeData } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      parentData: employeeData,
      childGrid: {
        dataSource: data,
        queryString: 'EmployeeID',
        toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
        editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
        columns: [
            { field: 'OrderID', headerText: 'Order ID', isPrimaryKey:true, textAlign: 'Right', width: 120 },
            { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', allowEditing:false, width: 120 },
            { field: 'ShipCity', headerText: 'Ship City', width: 150 },
            { field: 'ShipName', headerText: 'Ship Name', width: 150 }
        ],
        actionBegin: function(args) {
        if (args.requestType === "add") {
        // `parentKeyFieldValue` refers to the queryString field value of the parent record.
        args.data.EmployeeID = this.parentDetails.parentKeyFieldValue;
           }
        }
      }
    }
  },
  provide: {
      grid: [DetailRow, Edit, Toolbar]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}
