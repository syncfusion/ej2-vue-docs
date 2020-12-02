---
title: "Strict Mode"
component: "DatePicker"
description: "The strictMode option allows the user to enter only the valid date value within the specified min/max range in textbox."
---

# Strict Mode

## Enable Strict Mode

The [`strictMode`](../api/datepicker#strictmode)
is an act, that allows the user to enter only the valid date within the specified min/max
range in textbox. If the date is invalid, then the component will stay with the previous value.
Else, if the date is
out of range, then the component will set the date to the min/max date.

The following example demonstrates the DatePicker in `strictMode` with min/max range of 5th to
25th in a month of May. Here, it allows to enter
only the valid date within the specified range. If you are trying to enter the out-of-range value as
like 28th of May,
then the value will set to the max date of 25th May. Since the value 28th is greater than to `max` value
of 25th. Or else if you are trying
to enter the invalid date, then the value will stay with the previous value.

{% tab template="datepicker/strict-mode", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-datepicker id='datepicker' :strictMode='strict' :value='dateVal' :min='minVal' :max='maxVal'></ejs-datepicker>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DatePickerPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(DatePickerPlugin);
export default {
  data () {
      return {
        strict:true,
        dateVal: new Date('5/28/2017'),
        minVal: new Date('5/5/2017'),
        maxVal: new Date('5/25/2017')
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

## Disable Strict Mode

By default, the DatePicker act in strictMode `false` state, that allows to enter the invalid or out-of-range date in textbox.

If the date is out-of-range or invalid, then the model value will be set to `out of range` date
value or `null` respectively with highlighted  `error` class to indicates the date is out of range or invalid.

The following example demonstrates the `strictMode` as `false`. Here, it allows to enter the
valid or invalid value in textbox.
If you are entering out-of-range or invalid date value, then the model value will be set to
`out of range` date value or `null` respectively with highlighted  `error` class to indicates
the date is out of range or invalid.

The following example demonstrates the DatePicker with strictMode `false`.

{% tab template="datepicker/strict-mode", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-datepicker id='datepicker' :value='dateVal' :min='minVal' :max='maxVal'></ejs-datepicker>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DatePickerPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(DatePickerPlugin);
export default {
  data () {
      return {
        dateVal: new Date('5/28/2017'),
        minVal: new Date('5/5/2017'),
        maxVal: new Date('5/25/2017')
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