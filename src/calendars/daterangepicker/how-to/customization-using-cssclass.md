---
title: "How To"
component: "DateRangePicker"
description: "Miscellaneous aspects of customizing the date range picker"
---

# Customization using cssClass

To customize UI, you can make use of [`cssClass`](../../api/daterangepicker#cssclass)
that will be added to the DateRangePicker component as the root CSS class.
With this CSS class, you can override existing styles of DateRangePicker.

Following is the list of classes that provides flexible way to customize the DateRangePicker component.

| **Class Name** | **Description** |
| --- | --- |
| e-date-range-wrapper | Applied to DateRangePicker wrapper. |
| e-range-icon | Applied to DateRangePicker icon. |
| e-popup | Applied to DateRangePicker popup wrapper.|
| e-calendar | Applied to both Calendar element. |
| e-right-calendar | Applied to right Calendar element. |
| e-left-calendar | Applied to left Calendar element. |
| e-start-label | Applied to start label in a popup. |
| e-end-calendar | Applied to end label in a popup. |
| e-day-span | Applied to day span details label in a popup. |
| e-footer | Applied to footer elements in a popup. |
| e-apply | Applied to apply button in footer in a popup. |
| e-cancel | Applied to cancel button in footer in a popup. |
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

{% tab template="daterangepicker/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-daterangepicker :placeholder="waterMark" :cssClass="classVal"></ejs-daterangepicker>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { DateRangePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(DateRangePickerPlugin);
export default {
   data () {
        return {
            waterMark: "Select a Range",
            classVal: "customCSS"
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
.customCSS .e-calendar .e-content .e-selected span.e-day, /* csslint allow: adjoining-classes*/
.customCSS .e-calendar .e-content .e-selected span.e-day:hover, /* csslint allow: adjoining-classes*/
.customCSS .e-calendar .e-content .e-today.e-selected:hover span.e-day, /* csslint allow: adjoining-classes*/
.customCSS .e-calendar .e-content .e-today.e-selected span.e-day, /* csslint allow: adjoining-classes*/
.customCSS .e-calendar .e-content .e-selected:hover span.e-day /* csslint allow: adjoining-classes*/
{
background-color: #35b86b;
}
.customCSS .e-calendar .e-content .e-today span.e-day, /* csslint allow: adjoining-classes*/
.customCSS .e-calendar .e-content .e-focused-date.e-today span.e-day { /* csslint allow: adjoining-classes*/
border: 1px solid #35b86b;
color: #ff3337;

}
.customCSS .e-calendar .e-content .e-weekend span { /* csslint allow: adjoining-classes*/
color: #ff3337;
}
.customCSS.e-date-range-wrapper .e-input-group-icon.e-icons.e-active, /* csslint allow: adjoining-classes*/
.customCSS .e-btn.e-flat, /* csslint allow: adjoining-classes*/
.customCSS .e-btn.e-flat:hover { /* csslint allow: adjoining-classes*/
color: #35b86b;
}

</style>
```

{% endtab %}