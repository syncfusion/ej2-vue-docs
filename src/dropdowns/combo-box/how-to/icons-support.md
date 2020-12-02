---
title: "Combo box How to show the list items with icons"
component: "ComboBox"
description: "This section explains how to add icons with combo box options."
---

# Show the list items with icons

You can render **icons** to the list items by mapping the
the [iconCss](../../api/combo-box/#fields) &nbsp;fields.
This `iconCss` field create a span in the list item with mapped class name
to allow styling as per your need.

In the following sample, icon classes are mapped with `iconCss` field.

{% tab template="combobox/icons", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' :dataSource='sortFormatData' :fields='fields' placeholder='Select a format'></ejs-combobox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ComboBoxPlugin);

export default {
  data () {
    return {
      sortFormatData: [
        { Class: 'sort', Type: 'Sort A to Z', Id: '1' },
        { Class: 'filter', Type: 'Filter', Id: '2' },
        { Class: 'clear', Type: 'Clear', Id: '3' }
      ],
      fields : { text: 'Type', iconCss: 'Class', value: 'Id' }
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  .e-list-icon{
    line-height: 1.3;
    padding-right: 10px;
    text-indent: 5px;
}
.sort:before {
    content: '\e890';
    font-family: 'e-icons';
    font-size: 15px;

}
.filter:before {
    content: '\e7ee';
    font-family: 'e-icons';
    font-size: 15px;
    opacity: 0.78;
}
.clear:before {
    content: '\e7fc';
    font-family: 'e-icons';
    font-size: 15px;
}
</style>
```

{% endtab %}