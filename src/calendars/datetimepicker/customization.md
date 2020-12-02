---
title: "Customization"
component: "DateTimePicker"
description: "Date time picker gives complete control to the user to customize overall appearance of the date time picker in their application."
---

# Customization

The DateTimePicker is available for UI customization that can be achieved by using available properties and events in the component.

## Day and Time Cell format

The DateTimePicker is available for UI customization based on your application requirements.
It can be achieved by using [`renderDayCell`](../api/datetimepicker/renderDayCellEventArgs#renderdaycelleventargs)
 event that provides an option to customize each day cell on rendering.

The following example disables the weekends of every month by using `renderDayCell` event.

{% tab template="datetimepicker/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-datetimepicker :renderDayCell="disableDate" :placeholder="waterMark"></ejs-datetimepicker>
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
           waterMark : 'Select a date and time'
        }
    },
   methods: {
       disableDate: function(args) {
            if (args.date.getDay() === 0 || args.date.getDay() === 6) {
               args.isDisabled = true;
            }
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

## See Also

* [How to disable the DateTimePicker component](./how-to/disable-the-datetimepicker-component)
* [How to customize the DateTimePicker day header](./how-to/customize-the-datetimepicker-day-header)