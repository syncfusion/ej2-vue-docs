---
title: "Strict Mode"
component: "DateTimePicker"
description: "The strictMode option allows the user to enter only the valid date and time value within the specified min/max time range in textbox."
---

# Strict Mode

## Enable Strict Mode

The [`strictMode`](../api/datetimepicker#strictmode)
is an act, that allows the user to enter only the valid date and time within the specified min/max
range in textbox. If the input entered is invalid, then the component will stay with the previous value.
Else, if the date and time is
out of range, then the component will set the date to the min/max value.

The following example demonstrates the DateTimePicker in `strictMode` with min/max range of `5/5/2019 2:00 AM` to
`5/25/2019 2:00 AM`. Here, it allows to enter
only the valid date and time within the specified range. If you are trying to enter the out-of-range value as
like `5/28/2019`,
then the value will set to the `max` value as `5/25/2019 2:00 AM`. Since the value 28 is greater than to `max` value
of 25. Or else if you are trying
to enter the invalid date, then the value will stay with the previous value.

{% tab template="datetimepicker/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-datetimepicker :min="minDate" :max="maxDate" :value="dateVal" :strictMode="mode" ></ejs-datetimepicker>
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
           minDate : new Date('5/5/2019 2:00 AM'),
           maxDate : new Date('5/25/2019 2:00 AM'),
           dateVal : new Date('5/10/2019 2:00 AM'),
           mode : true
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

## Disable Strict Mode

By default, the DateTimePicker act in strictMode `false` state, that allows to enter the invalid or out-of-range datetime in textbox.

If the datetime is out-of-range or invalid, then the model value will be set to `out of range`
datetime value or `null` respectively with highlighted `error` class to indicates the datetime is out of range or invalid.

The following example demonstrates the `strictMode` as `false`. Here, it allows to enter the
valid or invalid value in textbox.
If you are entering the out-of-range or invalid datetime value, then the model value will be
set to `out of range` datetime value or `null` respectively with highlighted `error` class to
indicates the datetime is out of range or invalid.

{% tab template="datetimepicker/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-datetimepicker :min="minDate" :max="maxDate" :value="dateVal" :placeholder="waterMark" ></ejs-datetimepicker>
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
           minDate : new Date('5/5/2017 2:00 PM'),
           maxDate : new Date('5/25/2017 3:00 PM'),
           dateVal : new Date('5/25/2017 4:00 PM'),
           waterMark: "Select a date and time"
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
