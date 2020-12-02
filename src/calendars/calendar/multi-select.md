---
title: "Multi Selection"
component: Calendar
description: "Calendar supports multiple date selection to allow users to select more than one date."
---

# Multi Selection

Calendar provides an option to select **single** or **multiple dates** by using `isMultiSelection` and `values` properties. By default, `isMultiSelection` property will be in disabled state.

| API | Type | Description |
|------|------|----------------------|
| `isMultiSelection`| **Boolean**| Enables the multi-selection option in the Calendar control |
|`values`| **Date[]** | Gets or sets the date range values in multi-selection option |

The following example demonstrates the functionality of  `isMultiSelection` property and `values` properties in the Calendar control.

{% tab template="calendar/multi-selection", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-calendar id='calendar' ref="CalendarInstance" :isMultiSelection="isMultiSelection" :values="values" ></ejs-calendar>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { CalendarPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(CalendarPlugin);
export default {
      data () {
        return {
          isMultiSelection: true,
            values: [new Date('1/1/2020'), new Date('1/15/2020'), new Date('1/3/2020'), new Date('1/25/2020')]
        }
    }
    }
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";

.wrap {
    margin: 0px auto;
    max-width: 250px;
}
</style>
```

{% endtab %}
