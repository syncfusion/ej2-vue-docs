---
title: "Collapse all grouped rows at initial render"
component: "Grid"
description: "Learn how to collapse all grouped rows at initial render."
---

# Collapse all grouped rows at initial render

You can collapse all the grouped rows at initial rendering by using `dataBound` event with  `collapseAll` method of the grid.

In the below demo, all the grouped rows are collapsed at initial rendering.

{% tab template="grid/group/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :allowGrouping='true' :groupSettings='groupOptions' :dataBound='dataBound' height='267px'>
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

var initial = true;
export default {
  data() {
    return {
      data: data,
      groupOptions: { columns: ['ShipCity'] }
    };
  },
  methods: {
    dataBound: function() {
        if(initial === true) {
            this.$refs.grid.ej2Instances.groupModule.collapseAll();
            initial = false;
        }
    }
  },
  provide: {
    grid: [Group]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}