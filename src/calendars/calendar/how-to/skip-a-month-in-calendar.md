---
title: "How To"
component: "Calendar"
description: "Miscellaneous aspects of customizing the calendar"
---

# Skip a month in the Calendar

The following example demonstrates how to skip a month in the Calendar while clicking the previous and next icons.
In the example below,  the [`navigated`](../../api/calendar#navigated) event is used to skip a month
with [`navigateTo`](../../api/calendar#navigateto) method.

{% tab template="calendar/min-max", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-calendar id='calendar' :navigated='onNavigate' ref='Calendar'></ejs-calendar>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { CalendarPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(CalendarPlugin);
export default {
    methods: {
        onNavigate: function(args){
            let date;
            if (args.event.currentTarget.classList.contains('e-next')) {
            //Increments the month while clicking the next icon.
            date = new Date(args.date.setMonth(args.date.getMonth() + 1));
            }
            if (args.event.currentTarget.classList.contains('e-prev')) {
            //Decrements the month while clicking the previous icon.
            date = new Date(args.date.setMonth(args.date.getMonth() - 1));
            }
            if (args.view == 'month') {+
                this.$refs.Calendar.navigateTo('month', date);
            }

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