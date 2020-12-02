---
title: "Two Way Binding"
component: "DatePicker"
description: "This section for Vue DatePicker component demonstrates two-way binding."
---

# Two-Way Binding

Two-way binding can be achieved by using the `v-model` directive in Vue. In the following sample, when you change the value in one DatePicker component, v-model will automatically update the value in the other DatePicker.

The following example demonstrates how to set the `two-way-binding` in the DatePicker.

{% tab template="datepicker/two-way", isDefaultActive = "true" %}

```html
<template>
<div id="app">
    <div id="wrapper1">
        <ejs-datepicker id="datepicker" v-model="date"></ejs-datepicker>
    </div>
    <div id="wrapper2">
        <ejs-datepicker id="datepicker1" v-model="date"></ejs-datepicker>
    </div>
</div>
</template>
<script>
import Vue from "vue";
import { DatePickerPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(DatePickerPlugin);
export default {
  data: function() {
    return {
      date: new Date()
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