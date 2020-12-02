---
title: "Render React component in a column"
component: "Grid"
description: "Learn how to Render React component in a column."
---

# Render Vue component in a column

You can render any component in a grid column using the [`template`](../../api/grid/column/#template) property.

{% tab template="grid/how-to/dropdown" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' height='315px' >
            <e-columns>
                <e-column headerText='Order Status' :template="dropdownTemplate" width=200></e-column>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
               <e-column field='ShipName' headerText='Ship Name' width=120></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
import { data } from './datasource.js';

Vue.use(GridPlugin);
Vue.use(DropDownListPlugin);

export default {
  data() {
    return {
      data: data,
      dropdownTemplate: function () {
        return {
          template: Vue.component('bindDropdown', {
            template: `<ejs-dropdownlist id='dropdownlist' :dataSource='dropData'> </ejs-dropdownlist>`,
            data() {
              return {
                dropData: ['Order Placed', 'Processing', 'Delivered']
              }
            }
          })
        }
      }
    };
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}
