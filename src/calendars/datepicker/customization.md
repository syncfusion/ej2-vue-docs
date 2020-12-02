---
title: "Customization"
component: "DatePicker"
description: "Date picker gives complete control to the user to customize overall appearance of the date picker in their application."
---

# Customization

You can customize the  entire appearance of the input element and Calendar by using
custom
[`cssClass`](../api/datepicker#cssclass)
property.
and also you can use the calendar's
[`renderDayCell`](../api/datepicker/renderDayCellEventArgs#renderdaycelleventargs)
event to customize the appearance of the each day cell.

Below is the list of classes that provides flexible way to customize the DatePicker component.

| **Class Name** | **Description** |
| --- | --- |
| e-date-wrapper | Applied to DatePicker wrapper |
| e-datepicker | Applied to the DatePicker element.|
| e-float-text | Applied to the floating label.  |
| e-date-icon | Applied to the DatePicker icon. |
| e-popup-wrapper | Applied to DatePicker popup wrapper.|
| e-calendar | Applied to Calendar element. |
| e-header | Applied to Calendar header.|
| e-title |Applied to Calendar title. |
| e-icon-container | Applied to Calendar previous and next icon container.|
| e-prev |  Applied to Calendar previous icon.|
| e-next | Applied to Calendar next icon.|
| e-weekend | Applied to Calendar weekend dates.|
| e-other-month |  Applied to Calendar other month dates.|
| e-day | Applied to each day cell of the Calendar.|
| e-selected | Applied to Calendar selected dates.|
| e-disabled | Applied to Calendar disabled dates.|

The following example disables the weekends of every month using `renderDayCell` event.
Here we have used the `e-disabled` class to highlight the disabled date.

{% tab template="datepicker/min-max", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-datepicker id='datepicker' :renderDayCell="disableDate" placeholder='Select a Date'></ejs-datepicker>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DatePickerPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(DatePickerPlugin);
export default {
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
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrap {
    margin: 35px auto;
    width: 240px;
}
</style>
```

{% endtab %}

## See Also

* [How to disable the DatePicker component](./how-to/disabled-the-datepicker-component)
* [How to set read-only for DatePicker](./how-to/set-the-readonly)
* [How to customize the DatePicker day header](./how-to/customize-the-datepicker-day-header)