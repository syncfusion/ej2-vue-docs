---
title: "ListBox toolbar support"
component: "ListBox"
description: "Vue ListBox supports dual list (i.e) reordering of items within the list box and between two list boxes."
---

# Dual list box

The dual list box allows the user to move items between two list boxes by clicking the toolbar buttons. Dual list box can be created by listing items in the
[`toolbarSettings`](../api/list-box/#toolbarsettings) along with the `scope` property.

The following operations can be performed in dual list box,

| Options | Description |
|------|-------------|
| moveUp | Move the selected item in the upward direction within the list box. |
| moveDown | Move the selected item in the downward direction within the list box. |
| moveTo |  Move the selected item to the another list box. |
| moveFrom | Move the selected item from one list box to the another list box. |
| moveAllTo | Move all the items to the another list box. |
| moveAllFrom |  Move all the items from one list box to the another list box. |

The following example illustrates how to move items from `Group A` to `Group B` list box.

{% tab template="list-box/getting-started/getting-started", isDefaultActive=true %}

```html
<template>
  <div id='container' style="margin:10px auto 0; width:430px;">
  <div class="listbox1">
    <h4>Group A</h4>
      <ejs-listbox :dataSource='groupA' :fields="fields" scope="#listbox" :toolbarSettings="toolbarSettings"></ejs-listbox>
  </div>
  <div class="listbox2">
    <h4>Group B</h4>
      <ejs-listbox id="listbox" :dataSource='groupB' :fields="fields" scope="combined-list"></ejs-listbox>
  </div>
</div>  
</template>
<script>
import Vue from 'vue';
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(ListBoxPlugin);
export default {
  data (){
    return {
groupA: [
    { "Name": "Australia", "Code": "AU" },
    { "Name": "Bermuda", "Code": "BM" },
    { "Name": "Canada", "Code": "CA" },
    { "Name": "Cameroon", "Code": "CM" },
    { "Name": "Denmark", "Code": "DK" },
    { "Name": "France", "Code": "FR" },
    { "Name": "Finland", "Code": "FI" },
    { "Name": "Germany", "Code": "DE" },
    { "Name": "Hong Kong", "Code": "HK" }
];

groupB: [
    { "Name": "India", "Code": "IN" },
    { "Name": "Italy", "Code": "IT" },
    { "Name": "Japan", "Code": "JP" },
    { "Name": "Mexico", "Code": "MX" },
    { "Name": "Norway", "Code": "NO" },
    { "Name": "Poland", "Code": "PL" },
    { "Name": "Switzerland", "Code": "CH" },
    { "Name": "United Kingdom", "Code": "GB" },
    { "Name": "United States", "Code": "US" }
];
fields: { text: "Name" }
toolbarSettings: { items: ['moveUp', 'moveDown', 'moveTo', 'moveFrom', 'moveAllTo', 'moveAllFrom'] }
    }
  }
}

</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";

.listbox1{
  float: left;
  width: 50%;
}

.listbox2{
  float: right;
  width: 44%;
}

</style>

```

{% endtab %}