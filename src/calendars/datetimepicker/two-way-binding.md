---
title: "Two Way Binding"
component: "DateTimePicker"
description: "This section for Vue DateTimePicker component demonstrates two-way binding."
---

# Two-Way Binding

Two-way binding can be achieved by using the `v-model` directive in Vue. In the following sample, when you change the value in one DateTimePicker component, v-model will automatically update the value in the other DateTimePicker.

The following example demonstrates how to set the `two-way-binding` in the DateTimePicker.

{% tab template="datetimepicker/two-way", isDefaultActive = "true" %}

```html
<template>
<div id="app">
    <div id="wrapper1">
        <ejs-datetimepicker id="datetimepicker" v-model="date"></ejs-datetimepicker>
    </div>
    <div id="wrapper2">
        <ejs-datetimepicker id="datetimepicker1" v-model="date"></ejs-datetimepicker>
    </div>
</div>
</template>
<script>
import Vue from "vue";
import { DateTimePickerPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(DateTimePickerPlugin);
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