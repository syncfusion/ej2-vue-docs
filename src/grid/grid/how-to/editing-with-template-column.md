---
title: "Editing with template column"
component: "Grid"
description: "Learn how to editing with template column."
---

# Editing with template column

You can edit template column value by defining `field` for that particular column.

In the below demo, the `ShipCountry` column is rendered with the template.

{% tab template="grid/how-to/default" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='280px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' :isPrimaryKey='true' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Center' format='C2' editType='numericedit' width=80></e-column>
             <e-column field='ShipCountry' headerText='Ship Country' :template='editTemplate' editType='dropdownedit'  width=120></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin,Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);
export default {
  data: () => {
    return {
      data: data,
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      editTemplate: function () {
        return {
          template: Vue.component('editOption', {
            template: '<a href="#">{{data.ShipCountry}}</a>',
            data() { return { data: { data: {} } }; }
          })
        }
      },
    };
  },
  provide: {
    grid: [Edit, Toolbar]
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}