---
title: "How To"
component: "Calendar"
description: "Miscellaneous aspects of customizing the calendar"
---

# Change the first day of the week

The Calendar provides an option to change the first day of the week by using the [`firstDayOfWeek`](../../api/calendar#firstdayofweek)
property. Generally, the day of the week starts from 0 (Sunday) and ends with 6 (Saturday).

> By default, the first day of the week is culture specific.

The following example shows the Calendar with `Tuesday` as the first day of the week.

{% tab template="calendar/getting-started", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-calendar id='calendar' :firstDayOfWeek='firstDay'></ejs-calendar>
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
           firstDay : 2
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