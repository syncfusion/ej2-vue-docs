---
title: "Date Time Range"
component: "DateTimePicker"
description: "Date time picker has `min` and `max` properties which restricts the user from selecting a value out of given min/max datetime range"
---

# DateTime Range

DateTimePicker provides an option to select a date and time value within a specified range by using the
[`min`](../api/datetimepicker#min)
and
[`max`](../api/datetimepicker#max)
properties. Always the min value has to be
lesser than the max value.

When the min and max properties are configured and the selected datetime value is out-of-range
or invalid, then the model value will be set to `out of range` datetime value or `null`
respectively with highlighted `error` class to indicates the datetime is out of range or invalid.

The value property depends
on the min/max with respect to [`strictMode`](./strict-mode/) property.

The below example allows selecting a
date within the range from 7th to 27th day in
a month.
{% tab template="datetimepicker/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-datetimepicker :min="minDate" :max="maxDate" :placehoder="waterMark" :value="dateVal"></ejs-datetimepicker>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { DateTimePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(DateTimePickerPlugin);
export default {
   data () {
        return {
        minDate :  new Date(new Date().getFullYear(), new Date().getMonth(), 7, 0, 0, 0),
        maxDate :  new Date(new Date().getFullYear(), new Date().getMonth(), 27, new Date().getHours(), new Date().getMinutes(), new Date().getSeconds()),
        dateVal : new Date(new Date().setDate(14)),
        waterMark : 'Select a datetime'
        }
    }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
   .wrapper {
    max-width: 250px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

> If the value of `min` or `max` properties
changed through code behind, then you have to
update the `value` property to set within the
range.