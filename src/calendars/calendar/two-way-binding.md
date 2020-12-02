---
title: "Two Way Binding"
component: "Calendar"
description: "This section for Vue Calendar component demonstrates two-way binding."
---

# Two-Way Binding

Two-way binding can be achieved by using the `v-model` directive in Vue. In the following sample, when you change the value in one Calendar component, v-model will automatically update the value in the other Calendar.

The following example demonstrates how to set the `two-way-binding` in the Calendar.

{% tab template="calendar/two-way", isDefaultActive = "true" %}

```html
<template>
<div id="app">
    <div id="wrapper1">
        <ejs-calendar id="calendar" v-model="date"></ejs-calendar>
    </div>
    <div id="wrapper2">
        <ejs-calendar id="calendar1" v-model="date"></ejs-calendar>
    </div>
</div>
</template>
<script>
import Vue from "vue";
import { CalendarPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(CalendarPlugin);
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
    max-width: 300px;
    float: left;
    margin-left: 100px;
}
#wrapper2{
    max-width: 300px;
    float: right;
     margin-right: 100px;
}
</style>
```

{% endtab %}