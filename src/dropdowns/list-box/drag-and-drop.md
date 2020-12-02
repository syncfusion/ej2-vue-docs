---
title: "ListBox drag and drop"
component: "ListBox"
description: "Vue ListBox supports drag and drop with in single list box and between two list boxes."
---

# Drag and drop

The ListBox has support to drag an item or a group of selected items and drop it within the same list box or into another list box.

The elements can be customized on drag and drop by using the following events,

| Events | Description |
|------|------|
| [`dragStart`](../api/list-box/#dragstart) | Triggers when the selected element is being dragged. |
| [`drag`](../api/list-box/#drag) | Triggers when the selected element is being dragged. |
| [`drop`](../api/list-box/#drop) | Triggers when the selected element is being dropped. |

## Single listbox

To drag and drop an item or group of item within the list box can be achieved by setting [`allowDragAndDrop`](../api/list-box/#allowdraganddrop) property as `true`.

The following sample illustrates how to drag and drop an item within the same list box by enabling `allowDragAndDrop` property.

{% tab template="list-box/getting-started/getting-started", isDefaultActive=true %}

```html
<template>
  <div id='container' style="margin:10px auto 0; width:250px;">
      <ejs-listbox :dataSource='data' :allowDragAndDrop="true" :fields="fields"></ejs-listbox>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(ListBoxPlugin);
export default {
  data (){
    return {
       data: [
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
fields: { text: "Name" }
    }
  }
}

</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>

```

{% endtab %}

## Multiple listbox

To drag and drop an item or group of item between two list boxes can be achieved by setting `allowDragAndDrop` property as `true` and [`scope`](../api/list-box/#scope) property should be set to both the list boxes.

In the following sample, the `allowDragAndDrop` property is set as `true` and `scope` is set as `combined-list` to enable drop and drop in both list boxes.

{% tab template="list-box/getting-started/getting-started", isDefaultActive=true %}

```html
<template>
<div id='container' style="margin:10px auto 0; width:250px;">
  <div class="listbox1">
    <h4>Group A</h4>
      <ejs-listbox id="listbox1" :dataSource='groupA' :allowDragAndDrop="true" :fields="fields" scope="combined-list"></ejs-listbox>
  </div>
  <div class="listbox2">
    <h4>Group B</h4>
      <ejs-listbox id="listbox2" :dataSource='groupB' :allowDragAndDrop="true" :fields="fields" scope="combined-list"></ejs-listbox>
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
  width: 48%;
}

.listbox2{
  float: right;
  width: 48%;
}

</style>

```

{% endtab %}