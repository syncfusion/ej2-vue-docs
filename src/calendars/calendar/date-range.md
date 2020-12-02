---
title: "Date Range"
component: "Calendar"
description: "Calendar has `min` and `max` properties which restricts the user from selecting a value out of given min/max date range"
---

# Date Range

Calendar provides an option to select a date value within a specified range by defining the min and max properties.
The min date should always be lesser than the max date. If the value of `min` or `max` properties are changed through code behind,
then update the `value` property to be set within the specified range.  Or else, if the value is out of specified date range and less than min date, value property will be updated with the `min` date or, if the value is higher than max date, value property will be updated with the `max` date.

The following example allows you to select a date within the range of 7th to 27th days in a month.

{% tab template="calendar/min-max", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-calendar id='calendar' :value='dateVal' :min='minVal' :max='maxVal' placeholder='Select a Date'></ejs-calendar>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { CalendarPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(CalendarPlugin);
export default {
  data () {
    var today = new Date();
    var currentYear = today.getFullYear();
    var currentMonth = today.getMonth();
    var currentDay = today.getDate();
    return {
        dateVal: new Date(new Date().setDate(14)),
        minVal: new Date(currentYear, currentMonth, 7),
        maxVal: new Date(currentYear, currentMonth, 27),
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrap {
    margin: 35px auto;
    width: 240px;
}
</style>
```

{% endtab %}