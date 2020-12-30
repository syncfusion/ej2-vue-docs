---
title: "Hide sorting options on excel filter Dialog"
component: "Grid"
description: "Learn how to hide sorting options in excel filter Dialog."
---

# Hide sorting options on excel filter Dialog

You can hide the sorting options on the excel filter dialog by setting display as none for the following classes.

```css
    .e-excel-ascending,
    .e-excel-descending,
    .e-separator.e-excel-separator {
    display: none;
    }
```

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
            type: 'Excel'
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
    .e-excel-ascending,
    .e-excel-descending,
    .e-separator.e-excel-separator {
    display: none;
    }

</style>
```

{% endtab %}
