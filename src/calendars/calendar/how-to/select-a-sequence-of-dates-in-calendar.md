---
title: "How To"
component: "Calendar"
description: "Miscellaneous aspects of customizing the calendar"
---

# Select a sequence of dates in Calendar

The following example demonstrates how to select the week dates of chosen date in the Calendar using [`values`](../../api/calendar#values) property, when [`isMultiSelection`](../../api/calendar#ismultiselection) property is enabled. Methods of Moment.js is used in this sample for calculating the start and end of week from the selected date.

{% tab template="calendar/multi-selection", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class="wrap" style="height:357px; display: inline-block;">
           <ejs-calendar id='calendar' ref="CalendarInstance" :isMultiSelection="isMultiSelection" :change="onChange"></ejs-calendar>
        </div>
         <div id="btncontainer">
            <ejs-button id="week" class="e-btn"  v-on:click.native="onweekChange"> Week </ejs-button>
            <ejs-button id="workweek" class="e-btn" v-on:click.native="onworkweekChange"> Work Week </ejs-button>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { CalendarPlugin } from "@syncfusion/ej2-vue-calendars";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import moment from "moment";

Vue.use(CalendarPlugin);
Vue.use(ButtonPlugin);
export default {
    data() {
        return {
            isMultiSelection: true
        }
    },
    methods: {
        onChange: function(args) {
            let startOfWeek = moment(args.value).startOf('week');
            let endOfWeek = moment(args.value).endOf('week');
            if (this.$refs.CalendarInstance.$el.classList.contains('workweek')) {
                this.getWeekArray(startOfWeek.day(1), endOfWeek.day(5));
            } else if (this.$refs.CalendarInstance.$el.classList.contains("week")) {
                this.getWeekArray(startOfWeek, endOfWeek);
            }
        },
        /*selected current week dates when click the button*/
        onweekChange: function() {
            if (this.$refs.CalendarInstance.$el.classList.contains('workweek')) {
                this.$refs.CalendarInstance.$el.classList.remove('workweek')
            }
            this.$refs.CalendarInstance.$el.classList.add('week');
        },
        onworkweekChange: function() {
            if (this.$refs.CalendarInstance.$el.classList.contains('week')) {
                this.$refs.CalendarInstance.$el.classList.remove('week')
            }
            this.$refs.CalendarInstance.$el.classList.add('workweek');
        },
        getWeekArray: function(startOfWeek, endOfWeek) {
            let days = [];
            let day = startOfWeek;
            while (day <= endOfWeek) {
                days.push(day.toDate());
                day = day.clone().add(1, 'd');
            }
            this.$refs.CalendarInstance.values = days;
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

#app{
    max-width: 550px;
}

#btncontainer{
    float:right;
    margin-left:30px;
    margin-top: 75px;
    margin-right: 10px;
}

button#workweek {
    margin-left: 15px;
}

</style>
```

{% endtab %}