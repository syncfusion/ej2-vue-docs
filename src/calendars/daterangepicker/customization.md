---
title: "Customization"
component: "DateRangePicker"
description: "Date range picker gives complete control to the user to customize overall appearance of the date range picker in their application."
---

# Customization

The DateRangePicker is available for UI customization that can be achieved by using available properties and events in the component.

## Day cell format

The DateRangePicker is available for UI customization based on your application requirements. It can be achieved by using [`renderDayCell`](../api/daterangepicker/renderDayCellEventArgs#renderdaycelleventargs)
 event that provides an option to customize each day cell on rendering.

The following example disables the weekends of every month by using `renderDayCell` event.

{% tab template="daterangepicker/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-daterangepicker :placeholder="waterMark" :renderDayCell="disableDate" ></ejs-daterangepicker>
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
         waterMark : 'Select a Range'
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

## Preset Ranges

DateRangePicker provides an option to set the predefined ranges via [`presets`](../api/daterangepicker#presets)
property with the corresponding label. This property will accept the values in the order of label, start date (date object),
end date (date object), and append these ranges in the component for quick selection.
In the following sample, you can easily choose the frequently used range options from the list of ranges.

{% tab template="daterangepicker/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
       <ejs-daterangepicker :placeholder="waterMark">
            <e-presets>
                <e-preset label="This Week" :start='weekStart' :end='weekEnd'></e-preset>
                <e-preset label="This Month" :start='monthStart' :end='monthEnd'></e-preset>
                <e-preset label="Last Month" :start='lastStart' :end='lastEnd'></e-preset>
                <e-preset label="Last Year" :start='yearStart' :end='yearEnd'></e-preset>
            </e-presets>
        </ejs-daterangepicker>
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
           waterMark : 'Selct a Range',
           weekStart :  new Date(new Date(new Date().setDate(new Date().getDate() - (new Date().getDay() + 7) % 7)).toDateString()),

           weekEnd : new Date(new Date(new Date().setDate(new Date(new Date().setDate((new Date().getDate()
           - (new Date().getDay() + 7) % 7))).getDate() + 6)).toDateString()),

           monthStart :  new Date(new Date(new Date().setDate(1)).toDateString()),

           monthEnd : new Date(new Date(new Date(new Date().setMonth(new Date().getMonth() + 1)).setDate(0)).toDateString()),

           lastStart : new Date(new Date(new Date(new Date().setMonth(new Date().getMonth() - 1)).setDate(1)).toDateString()),

           lastEnd : new Date(new Date(new Date().setDate(0)).toDateString()),
           yearStart : new Date(new Date(new Date().getFullYear() - 1, 0, 1).toDateString()),
           yearEnd  :  new Date(new Date(new Date().getFullYear() - 1, 11, 31).toDateString())
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

## First day of week

Start day in a week will differ based on the culture, but you can also customize this based on the application needs.
For this, you have to make use of [`firstDayOfWeek`](../api/daterangepicker#firstdayofweek) property.
By default, first day of a week in en-US is Sunday. In the following example it is customized to Monday with the help of this property.

{% tab template="daterangepicker/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-daterangepicker :firstDayOfWeek="week" :placeholder="waterMark"></ejs-daterangepicker>
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
           waterMark : 'Select a Range',
           week : 1
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

* [How to customize DateRangePicker using cssClass](./how-to/customization-using-cssclass)
* [How to disable DateRangePicker component](./how-to/disable-the-daterangepicker-component)
* [How to customize the DateRangePicker day header](./how-to/customize-the-daterangepicker-day-header)