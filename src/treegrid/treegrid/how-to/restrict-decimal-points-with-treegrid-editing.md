---
title: "Restrict to type decimal points in a NumericTextBox while editing the numeric column"
component: "TreeGrid"
description: "Learn how restrict to type decimal points in a NumericTextBox while editing the numeric column."
---

# Restrict to type decimal points in a NumericTextBox while editing the numeric column

By default, the number of decimal places will be restricted to two in the NumericTextBox while editing the numeric column. We can restrict to type the decimal points in a NumericTextBox by using the **validateDecimalOnType** and **decimals** properties of NumericTextBox.

In the below demo, while editing the row we have restricted to type the decimal point value in the NumericTextBox of **Price** column.

{% tab template="treegrid/how-to/default" %}

```html
<template>
  <div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex="1" height='250px' childMapping='subtasks' ref='treegrid' :editSettings='editSettings' :toolbar="toolbar">
        <e-columns>
          <e-column field="orderID" headerText="Order ID" :isPrimaryKey='true' width="70" textAlign="Right"></e-column>
          <e-column field="orderName" headerText="Order Name" width="100" ></e-column>
          <e-column field="orderDate" headerText="Order Date" format="yMd" editType= 'datepickeredit' width="100" textAlign="Right"></e-column>
          <e-column field="units" headerText="Units" width="90" textAlign="Right"  editType= "numericedit"></e-column>
          <e-column field="price" headerText="Price" width="100" :edit="numericParams" editType="numericedit" width="90" format="c2" textAlign="Right"></e-column>
         </e-columns>
       </ejs-treegrid>
  </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-treegrid";
import { stackedData } from "./datasource.js";

Vue.use(TreeGridPlugin);
export default {
  data() {
    return {
      data: stackedData,
      editSettings: { allowAdding:true, allowDeleting:true, allowEditing: true, mode: 'Row' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      numericParams: {
        params: {
           decimals: 0,
           format: "N",
           validateDecimalOnType: true
        }
      },
    };
  },
  provide: {
    treegrid: [Page, Edit, Toolbar]
  }
}
</script>

```

{% endtab %}
