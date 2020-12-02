---
title: "Date Formats"
component: "DatePicker"
description: "Date picker supports to format date object into specific string format to simplify the date representation. It adapts to any culture specific date formats when it is globalized."
---

# Date Format

Date format is a way of representing the date value in different string format in the textbox.

By default, the DatePicker's format is based on the culture. You can also set the own
custom format by using the
[`format`](../api/datepicker#format)
property.

> Once the date format property has been defined it will be common to all the cultures.

To know more about the date format standards, refer to the
[Internationalization Date Format](http://ej2.syncfusion.com/documentation/base/internationalization/) section.

The following example demonstrates the DatePicker with the custom format (`yyyy-MM-dd`).

{% tab template="datepicker/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-datepicker :placeholder="waterMark" :value="dateVal" :format="dateFormat"></ejs-datepicker>
      </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DatePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(DatePickerPlugin);
export default {
data () {
    return {
      waterMark : 'Select a date',
      dateVal : new Date(),
      dateFormat : 'yyyy-MM-dd'
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
  .wrapper {
    max-width: 250px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}
