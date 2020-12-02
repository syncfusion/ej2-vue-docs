---
title: "Two Way Binding"
component: "DateRangePicker"
description: "This section for Vue DateRangePicker component demonstrates two-way binding."
---

# Two-Way Binding

Two-way binding can be achieved by using the `v-model` directive in Vue. In the following sample, when you change the value in one DateRangePicker component, v-model will automatically update the value in the other DateRangePicker.

The following example demonstrates how to set the `two-way-binding` in the DateRangePicker.

{% tab template="daterangepicker/two-way", isDefaultActive = "true" %}

```html
<template>
<div id="app">
    <div id="wrapper1">
        <ejs-daterangepicker id="daterangepicker" :placeholder="waterMark" v-model="date"></ejs-daterangepicker>
    </div>
    <div id="wrapper2">
        <ejs-daterangepicker id="daterangepicker1" :placeholder="waterMark" v-model="date"></ejs-daterangepicker>
    </div>
</div>
</template>
<script>
import Vue from "vue";
import { DateRangePickerPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(DateRangePickerPlugin);
export default {
  data: function() {
    return {
        waterMark: "Select a Range",
        date: null
    };
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
#wrapper1{
    min-width: 250px;
    float: left;
    margin-left: 100px;
}
#wrapper2{
   min-width: 250px;
    float: right;
     margin-right: 100px;
}
</style>
```

{% endtab %}