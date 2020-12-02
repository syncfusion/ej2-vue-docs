---
title: "Get specific row and cell index in Grid"
component: "Grid"
description: "Learn how to get specific row and cell index in Grid."
---

# Get specific row and cell index in Grid

You can get the specific row and cell index of the grid by using `rowSelected` event of the grid. Here, we can get the row and cell index by using `aria-rowindex`(get row Index from `tr` element) and `aria-colindex`(column index from `td` element) attribute.

{% tab template="grid/group/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :rowSelected='rowSelected' height='267px'>
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
import { GridPlugin, Group } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  methods: {
    rowSelected: function(args) {
        alert("row index: "+args.row.getAttribute('aria-rowindex'));
        alert("column index: "+args.target.getAttribute('aria-colindex'));
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}