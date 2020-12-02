---
title: "Choose a date in range"
component: "DatePicker"
description: "Date picker has `min` and `max` properties which restricts the user from selecting a value out of given min/max date range"
---

# Date Range

DatePicker provides an option to select a date value within a specified range by using the
[`min`](../api/datepicker#min)
and
[`max`](../api/datepicker#max)
properties. Always the min value has to be
lesser than the max value.

When the min and max properties are configured and the selected date value is out-of-range or
invalid, then the model value will be set to `out of range` date value or `null` respectively
with highlighted `error` class to indicates the date is out of range or invalid.

The value property depends on the min/max with respect to [`strictMode`](./strict-mode/) property.

The below example allows selecting a
date within the range from 7th to 27th day in
a month.

{% tab template="datepicker/min-max", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-datepicker id='datepicker' :value='calVal' :min='minVal' :max='maxVal'></ejs-datepicker>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DatePickerPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(DatePickerPlugin);
export default {
  data () {
    var today = new Date();
    var currentYear = today.getFullYear();
    var currentMonth = today.getMonth();
    var currentDay = today.getDate();
    return {
        calVal: new Date(new Date().setDate(14)),
        minVal: new Date(currentYear, currentMonth, 7),
        maxVal: new Date(currentYear, currentMonth, 27),
    }
  }
}
</script>
<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrap {
    margin: 35px auto;
    width: 240px;
}
</style>
```

{% endtab %}

> If the value of `min` or `max` properties
changed through code behind, then you have to
update the `value` property to set within the
range.
