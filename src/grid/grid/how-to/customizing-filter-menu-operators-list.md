---
title: "Customizing filter menu operators list"
component: "Grid"
description: "Learn how to customize filter menu operators list."
---

# Customizing filter menu operators list

 You can customize the default filter operator list by defining the
  [`filterSettings.operators`](../../api/grid/filterSettings/#operators) property. The available options are:

* `stringOperator`- defines customized string operator list.
* `numberOperator` - defines customized number operator list.
* `dateOperator` - defines customized date operator list.
* `booleanOperator` - defines customized boolean operator list.

In the following sample, we have customized string filter operators.
{% tab template="grid/how-to/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' allowFiltering='true' :filterSettings='filterOptions' height='273px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
             <e-column field='ShipCity' headerText='Ship City'  width=100></e-column>
             <e-column field='ShipName' headerText='Ship Name'  width=100></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin,Filter } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);
export default {
      data: () => {
        return {
          data: data,
          filterOptions: {
            type: 'Menu',
            operators: {
              stringOperator: [
                { value: 'startsWith', text: 'starts with' },
                { value: 'endsWith', text: 'ends with' },
                { value: 'contains', text: 'contains' }
              ],
            }
          },
        };
      },
      provide: {
        grid: [Filter],
      },
    }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}
