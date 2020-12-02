---
title: "Select grid rows based on certain condition"
component: "Grid"
description: "Learn how to select grid rows based on certain condition"
---

# Select grid rows based on certain condition

You can select the specific row in the grid based on a certain condition by using the [`selectRows`](../../api/grid/#selectrows) method in the [`dataBound`](../../api/grid/#databound) event of Grid.

In the below demo, we have selected the grid rows only when `EmployeeID` column value greater than `3`.

{% tab template="grid/edit/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='Grid' :dataSource='data' :allowPaging='true' height='280px' :rowDataBound='rowDataBound' :selectionSettings='selectionOptions' :dataBound='dataBound'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' :isPrimaryKey='true' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='EmployeeID' headerText='Employee ID' textAlign='Right' width=120></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=80></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' width=120></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin,Toolbar, Page } from "@syncfusion/ej2-vue-grids";
import { employeeData } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data: () => {
    return {
      data: employeeData,
      selectionOptions: { type: 'Multiple' },
      selIndex: []
     };
  },
  methods: {
    rowDataBound(args){
      if (args.data['EmployeeID'] > 3) {
          this.selIndex.push(parseInt(args.row.getAttribute('aria-rowindex')));
      }
    }
    dataBound(args){
      if (this.selIndex.length) {
          this.$refs.Grid.selectRows(this.selIndex);
          this.selIndex = [];
      }
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