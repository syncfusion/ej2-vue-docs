---
title: "How To"
component: "DateRangePicker"
description: "Miscellaneous aspects of customizing the date range picker"
---

# Set the placeholder

The following example demonstrates how to set [`placeholder`](../../api/daterangepicker#placeholder) in the DateRangePicker control.

Using `placeholder` you can display a short hint in the input element.

{% tab template="daterangepicker/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-daterangepicker :placeholder="waterMark"></ejs-daterangepicker>
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
            waterMark:'Select a Range',
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