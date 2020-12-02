---
title: "Time Range"
component: "TimePicker"
description: "Time picker has `min` and `max` properties which restricts the user from selecting a value out of given time range"
---

# Time Range

TimePicker provides an option to select a time value within a specified range by using the
[`min`](../api/timepicker#min)
and
[`max`](../api/timepicker#max)
properties.  The min value should always be lesser than the max value.

When the min and max properties are configured and the selected time value is out-of-range or
invalid, then the model value will be set to `out of range` time value or `null` respectively
with highlighted `error` class to indicates the time is out of range or invalid.

The value property depends on the min/max with respect to [`strictMode`](./strict-mode/) property.

The following example allows you to select a time value within a range of `9:00 AM` to `11:30 AM`.

{% tab template="timepicker/range", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-timepicker id='timepicker' :value='timeval' :min='minTime' :max='maxTime'></ejs-timepicker>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { TimePickerPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(TimePickerPlugin);
export default {
  data () {
    return{
        timeval:new Date('3/8/2017 11:00 AM'),
        minTime: new Date('3/8/2017 9:00 AM'),
        maxTime: new Date('3/8/2017 11:30 AM')
    }
  }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrap {
    margin: 35px auto;
    width: 240px;
}
</style>
```

{% endtab %}

> If the value of `min` or `max` property is changed through code behind you have
to update the `value` property to set within the range.