---
title: "Customize Pager DropDown"
component: "Grid"
description: "Learn how to Customize Pager DropDown."
---

# Customize Pager DropDown

To customize default values of pager dropdown, you need to define `pageSizes` as array of strings.

{% tab template="grid/how-to/pagerdropdown" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :allowPaging='true' :pageSettings='pageSettings' height='280px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' :isPrimaryKey='true' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Center' format='C2' width=80></e-column>
             <e-column field='ShipCountry' headerText='Ship Country' width=120></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin,Toolbar, Page } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);
export default {
  data: () => {
    return {
      data: data,
      pageSettings: {pageSizes: ['5','10','All']}
     };
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
