---
title: "Display null date values at always"
component: "Grid"
description: "Learn how to display null date values at always."
---

# Display the null date values at bottom of the Grid while perform sorting

By default the null values are displayed at bottom of the Grid row while perform sorting in ascending order. As well as this values are displayed at top of the Grid row while perform sorting with descending order. But you can customize this default order to display the null values at always bottom row of the Grid by using [`column.sortComparer`](../../api/grid/column/#sortcomparer) method.

In the below demo we have displayed the null date values at bottom of the Grid row while sorting the **OrderDate** column in both ways.

{% tab template="grid/how-to/null-date-value" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :allowSorting='true' :actionBegin='actionBegin'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='OrderDate' headerText='Order Date' format='yMd'  :sortComparer='sortComparer' width=120></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Sort } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);
let action;

export default {
  data: () => {
    return {
      data: data
    };
  },
  methods: {
    sortComparer: function(reference, comparer) {
        let sortAsc = action === "Ascending" ? true : false;
        if (sortAsc && reference === null) {
            return 1;
        }
        else if (sortAsc && comparer === null) {
            return -1;
        }
        else if (!sortAsc && reference === null) {
            return -1;
        }
        else if (!sortAsc && comparer === null) {
            return 1;
        } else {
            return reference - comparer;
        }
    },
    actionBegin: function(args) {
        if (args.requestType == "sorting") {
            action = args.direction;
        }
    }
  },
  provide: {
    grid: [Sort]
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}
