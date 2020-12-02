---
title: "Autocomplete How to show the list items with icons"
component: "AutoComplete"
description: "This section explains how to add icons with autocomplete options."
---

# Show the list items with icons

You can render icons to the list items by mapping the [`iconCss`](../../api/auto-complete/#fields) field. This iconCss
field create a span in the list item with mapped class name to allow styling as per
your need.

In the following sample, the icon classes are mapped with iconCss field.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-autocomplete :dataSource='sortFormatData' :fields='fields' :placeholder="waterMark" ></ejs-autocomplete>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';

Vue.use(AutoCompletePlugin);
export default {
  name: 'app',
   data () {
    return {
      waterMark : 'Find a format',
      sortFormatData: [
        { Class: 'sort', Type: 'Sort A to Z', Id: '1' },
        { Class: 'filter', Type: 'Filter', Id: '2' },
        { Class: 'clear', Type: 'Clear', Id: '3' }
        ],
      fields: { value: 'Type', iconCss: 'Class' }
    }
  }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    left: 35%;
    position: absolute;
    top: 35%;
    width: 30%;
  }
  #container {
    visibility: hidden;
}
#loader {
  color: #008cff;
  height: 40px;
  width: 30%;
  position: absolute;
  top: 45%;
  left: 45%;
}
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