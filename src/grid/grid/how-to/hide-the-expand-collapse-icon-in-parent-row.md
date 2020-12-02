---
title: "Hide the expand/collapse icon in parent row with no record in child grid"
component: "Grid"
description: "Learn how to Hide the expand/collapse icon in parent row with no record in child grid."
---

# Hide the expand/collapse icon in parent row with no record in child grid

By default, the expand/collapse icon will be visible even if the child grid is empty.

You can use [`rowDataBound`](../../api/grid/#rowdatabound) event to hide the icon when there are no records in child grid.

To hide the expand/collapse icon in parent row when no records in child grid, follow the given steps:

**Step 1**:

Create CSS class with custom style to override the default style of Grid.

```css
    .e-row[aria-selected="true"] .e-customizedExpandcell {
        background-color: #e0e0e0;
    }

    .e-grid.e-gridhover tr[role='row']:hover {
        background-color: #eee;
    }

```

**Step 2**:

Add the CSS class to the Grid in the [`rowDataBound`](../../api/grid/#rowdatabound) event handler of Grid.

```typescript
    rowDataBound(args){
      let filter:string = args.data.EmployeeID;
      let childrecord: any = new DataManager(this.$refs.Grid.childGrid.dataSource).executeLocal(new Query().where("EmployeeID", "equal", parseInt(filter), true));
      if(childrecord.length == 0) {
        //here hide which parent row has no child records
        args.row.querySelector('td').innerHTML=" ";
        args.row.querySelector('td').className = "e-customizedExpandcell";
      }
    }

```

In the below demo, the expand/collapse icon in the row with `EmployeeID` as `1` is hidden as it does not have record in child Grid.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid ref='Grid' :dataSource="data" height='315px' :childGrid='childGrid' :rowDataBound='rowDataBound'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='EmployeeID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
            <e-column field='OrderDate' headerText='Order Date' textAlign='Right' format='yMd' type='date' width=120></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, DetailRow } from "@syncfusion/ej2-vue-grids";
import { DataManager, Query } from '@syncfusion/ej2-data';
import { employeeData } from './datasource.js';

let dataManger: Object = [{Order:100, ShipName:'Berlin', EmployeeID:2},
                         {Order:101, ShipName:'Capte', EmployeeID:3},
                         {Order:102, ShipName:'Marlon', EmployeeID:4},
                         {Order:103, ShipName:'Black pearl', EmployeeID:5},
                         {Order:104, ShipName:'Pearl', EmployeeID:6},
                         {Order:105, ShipName:'Noth bay', EmployeeID:7},
                         {Order:106, ShipName:'baratna', EmployeeID:8},
                         {Order:107, ShipName:'Charge', EmployeeID:9}];

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: employeeData,
      childGrid: {
        dataSource: dataManger,
        queryString: 'EmployeeID',
        columns: [
            { field: 'Order', headerText: 'Order ID', textAlign: 'Right', width: 120 },
            { field: 'EmployeeID', headerText: 'Employee ID', width: 150 },
            { field: 'ShipName', headerText: 'Ship Name', width: 150 }
        ]
      }
    };
  },
  methods: {
    rowDataBound(args){
      let filter:string = args.data.EmployeeID;
      let childrecord: any = new DataManager(this.$refs.Grid.childGrid.dataSource).executeLocal(new Query().where("EmployeeID", "equal", parseInt(filter), true));
      if(childrecord.length == 0) {
        //here hide which parent row has no child records
        args.row.querySelector('td').innerHTML=" ";
        args.row.querySelector('td').className = "e-customizedExpandcell";
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
  .e-row[aria-selected="true"] .e-customizedExpandcell {
      background-color: #e0e0e0;
  }

  .e-grid.e-gridhover tr[role='row']:hover {
      background-color: #eee;
  }
</style>

```

{% endtab %}
