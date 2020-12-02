---
title: "Strict Mode"
component: "TimePicker"
description: "The strictMode option allows the user to enter only the valid time value within the specified min/max time range in textbox."
---

# Strict mode

## Enable Strict Mode

The [`strictMode`](../api/timepicker#strictmode)
is an act that allows you to enter only valid time value within the specified min/max
range in the textbox. If the time value is invalid, the component value sets to the previous value.
If the time value is
out of range, the component sets the time value to min/max value.

The following example demonstrates the TimePicker in `strictMode` with min/max range of `10:00 AM` to
`4:00 PM` . It allows you to enter
only valid time within the specified range. If you enter the out-of-range value like
`8:00 PM`,
the value sets to the max time `4:00 PM` as the value `8:00 PM` is greater than `max` value
of `4:00 PM`. If you enter invalid time value like `9:00 tt`, the value sets to the previous value.

{% tab template="timepicker/strict", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-timepicker id='timepicker' :strictMode='Strict' :value='timeval' :min='minTime' :max='maxTime'></ejs-timepicker>
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
        Strict: true,
        timeval:new Date('7/18/2017 3:00 PM'),
        minTime: new Date('7/18/2017 10:00 AM'),
        maxTime: new Date('7/18/2017 4:00 PM')
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

## Disable Strict Mode

By default, the TimePicker act in strictMode `false` state, that allows to enter the invalid or out-of-range time in textbox.

If the time is out-of-range or invalid, then the model value will be set to `out of range` time
value or `null` respectively with highlighted `error` class to indicates the time is out of range or invalid.

The following example demonstrates the `strictMode` as `false`. Here, it allows to enter the
valid or invalid value in textbox.
If you are entering the out-of-range or invalid time value, then the model value will be set to
`out of range` time value or `null` respectively with highlighted `error` class to indicates the time is out of range or invalid.

{% tab template="timepicker/strict", isDefaultActive = "true" %}

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
        timeval:new Date('7/18/2017 3:00 PM'),
        minTime: new Date('7/18/2017 10:00 AM'),
        maxTime: new Date('7/18/2017 4:00 PM')
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

> If the value of `min` or `max` property is changed through code behind, update the `value`
property to set within the range.
