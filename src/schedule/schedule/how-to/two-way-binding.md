---
title: "Two-Way Binding"
component: "Scheduler"
description: "This section demonstrates how to use two-way binding properties with Vue Scheduler."
---

# Two-Way Binding

We can achieve two-way binding with Vue Scheduler by using the `v-model` directive in Vue. The following Vue Scheduler properties support two-way binding.

* selectedDate
* currentView

## Two-Way Binding with Vue Scheduler Component's selectedDate Property

In the following example, when you change the `selectedDate` value in the Vue Scheduler component, `v-model` will automatically update the value in the Date picker component, and if you change the value in the Date picker component, it will automatically update the value in the Vue Scheduler.

The following example demonstrates how to set the two-way-binding with the `selectedDate` property in the Vue Scheduler.

{% tab template="schedule/two-way-binding",  iframeHeight="640px" %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <div class='date-picker-container'>
            <ejs-datepicker id='date-picker' placeholder='Selected date' floatLabelType="Always"  :value='selectedDate' :showClearButton='false' v-model='selectedDate'>
            </ejs-datepicker>
        </div>
        <div class="schedule-container">
            <ejs-schedule :height='height' :selectedDate='selectedDate' v-model='selectedDate' :eventSettings='eventSettings'></ejs-schedule>
        </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-vue-schedule';
import { DatePickerPlugin } from '@syncfusion/ej2-vue-calendars';

let currentYear = new Date().getFullYear();
let data = [{
    Id: 1,
    Subject: 'Paris',
    StartTime: new Date(currentYear, 1, 15, 10, 0),
    EndTime: new Date(currentYear, 1, 15, 12, 30),
    IsAllDay: false,
    RecurrenceRule: 'FREQ=DAILY;INTERVAL=1;COUNT=5'
}];

Vue.use(SchedulePlugin);
Vue.use(DatePickerPlugin);

export default {
  data (){
    return {
      height: '550px',
      views: ['Day', 'Week', 'WorkWeek', 'Month', 'Agenda'],
      eventSettings: {
        dataSource: data
      },
      selectedDate: new Date(currentYear, 1, 15),
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek, Month, Agenda]
  }
}

</script>
<style>
  @import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css';

  .date-picker-container {
    width: 20%;
    margin: auto;
  }
</style>

```

{% endtab %}

## Two-Way Binding with Vue Scheduler Component's currentView Property

In the following example, when you change the `currentDate` value in the Vue Scheduler component, `v-model` will automatically update the value in the Dropdown component, and if you change the value in the Dropdown component, it will automatically update the value in the Vue Scheduler.

The following example demonstrates how to set the two-way-binding with the `currentView` property in the Vue Scheduler.

{% tab template="schedule/two-way-binding",  iframeHeight="640px" %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <div class='drop-down-container'>
            <ejs-dropdownlist id='current-view-drop-down' placeholder="Current view" floatLabelType="Always"  :dataSource='views' :value='currentView' v-model="currentView">
            </ejs-dropdownlist>
        </div>
        <div class="schedule-container">
            <ejs-schedule :height='height' :selectedDate='selectedDate' :currentView='currentView' v-model='currentView' :eventSettings='eventSettings'></ejs-schedule>
        </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-vue-schedule';
import { DropDownListPlugin } from '@syncfusion/ej2-vue-dropdowns';

let currentYear = new Date().getFullYear();
let data = [{
    Id: 1,
    Subject: 'Paris',
    StartTime: new Date(currentYear, 1, 15, 10, 0),
    EndTime: new Date(currentYear, 1, 15, 12, 30),
    IsAllDay: false,
    RecurrenceRule: 'FREQ=DAILY;INTERVAL=1;COUNT=5'
}];

Vue.use(SchedulePlugin);
Vue.use(DropDownListPlugin);

export default {
  data (){
    return {
      height: '550px',
      currentView: 'Week',
      views: ['Day', 'Week', 'WorkWeek', 'Month', 'Agenda'],
      eventSettings: {
        dataSource: data
      },
      selectedDate: new Date(currentYear, 1, 15),
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek, Month, Agenda]
  }
}

</script>
<style>
  @import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css';

  .drop-down-container {
    width: 20%;
    margin: auto;
  }
</style>

```

{% endtab %}

> You can refer to our [Vue Scheduler](https://www.syncfusion.com/vue-ui-components/vue-scheduler) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Scheduler example](https://ej2.syncfusion.com/vue/demos/#/material/schedule/overview.html) to knows how to present and manipulate data.