---
title: "VueJS Scheduler - Getting Started"
component: "Scheduler"
description: "This article demonstrates how to create a simple Scheduler and configure its available features."
---

# Getting Started

This section briefly explains how to create [**Vue Scheduler**](https://www.syncfusion.com/vue-ui-components/vue-scheduler) component and configure its available functionalities in VueJS Environment.

## Installation and Configuration

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications.
To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

Create a new Vue project using the following `Vue CLI` command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install

```

## Adding Syncfusion Scheduler Package

All the available Essential JS 2 packages are published in `npmjs.com` registry.

Install the `Scheduler` component by using the below npm command.

```bash
npm install @syncfusion/ej2-vue-schedule --save
```

> The **--save** will instruct NPM to include the Scheduler package inside of the `dependencies` section of the `package.json`.

## Adding CSS Reference

Scheduler CSS files are available in the `ej2-vue-schedule` and its sub-component package folder. It should be referenced as given below within the `<style>` section of `App.vue` file.

```css
@import '/node_modules/@syncfusion/ej2-base/styles/material.css';
@import '/node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '/node_modules/@syncfusion/ej2-calendars/styles/material.css';
@import '/node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '/node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '/node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '/node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '/node_modules/@syncfusion/ej2-vue-schedule/styles/material.css';
```

## Registering Scheduler Component

Import the Scheduler plugin in your application from the `ej2-vue-schedule` package as given below and register the same using `Vue.use()`.

```html
import { SchedulePlugin } from '@syncfusion/ej2-vue-schedule';

Vue.use(SchedulePlugin);
```

> By Registering Scheduler plugin in Vue, all its child directives are also globally registered.

## Initialize the Schedule

Add the EJ2 Vue Scheduler using `<ejs-schedule>` to the `<template>` section of the `App.vue` file in src directory.

```html
<template>
  <div id='app'>
    <ejs-schedule ></ejs-schedule>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin } from '@syncfusion/ej2-vue-schedule';
Vue.use(SchedulePlugin);
export default { }
</script>
```

## Module injection

The crucial step on creating a Schedule with specific views, is to inject the required modules. The modules that are available with common Schedule basic functionality are as follows.

* **Day** - Inject this module for displaying day view.
* **Week** - Inject this module for displaying week view.
* **WorkWeek** - Inject this module for displaying work week view.
* **Month** - Inject this module for displaying month view.
* **Agenda** - Inject this module for  displaying agenda view.
* **MonthAgenda** - Inject this module for displaying month agenda view.
* **TimelineViews** - Inject this module for displaying timeline day, timeline week, timeline work week view.
* **TimelineMonth** - Inject this module for displaying timeline month view.

These modules should be injected into the Schedule using the `provide` method within the `app.vue` file as shown below. On doing so, only the injected views will be loaded and displayed on the Schedule.

`[src/app/app.vue]`

```html
<template>
  <div id='app'>
    <ejs-schedule ></ejs-schedule>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-vue-schedule';

Vue.use(SchedulePlugin);
export default {
  provide: {
    schedule: [Day, Week, WorkWeek, Month, Agenda]
  }
}
</script>
```

## Run the Application

Now, run the `npm run dev` command in the console. It will build your application and open in the browser.

```sh
npm run dev
```

The output will display the empty Scheduler.

## Populating appointments

To populate the empty Scheduler with appointments, define either the local JSON data or remote data through the `dataSource` property available within the `eventSettings` option. To define any appointments, start and end time fields are mandatory. In the following example, you can see the appointment defined with default fields such as Id, Subject, StartTime and EndTime.

```html
<template>
  <div id='app'>
      <ejs-schedule height='550px' :selectedDate='selectedDate' :eventSettings='eventSettings'></ejs-schedule>
  </div>
</template>
<script>
  import Vue from 'vue';
  import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-vue-schedule';
  Vue.use(SchedulePlugin);
  export default {
      data () {
        return {
          selectedDate: new Date(2018, 1, 15),
          eventSettings: {
            dataSource: [{
              Id: 1,
              Subject: 'Meeting',
              StartTime: new Date(2018, 1, 15, 10, 0),
              EndTime: new Date(2018, 1, 15, 12, 30)
            }]
          }
        }
      },
      provide: {
        schedule: [Day, Week, WorkWeek, Month, Agenda]
      }
  }
</script>
```

You can also provide different names to these default fields, for which the custom names of those fields must be mapped appropriately within fields property as shown below.

```html
<template>
  <div id='app'>
      <ejs-schedule height='550px' :selectedDate='selectedDate' :eventSettings='eventSettings'></ejs-schedule>
  </div>
</template>
<script>
  import Vue from 'vue';
  import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-vue-schedule';
  
  Vue.use(SchedulePlugin);
  let data = [{
    Id: 2,
    EventName: 'Meeting',
    StartTime: new Date(2018, 1, 15, 10, 0),
    EndTime: new Date(2018, 1, 15, 12, 30),
    IsAllDay: false
  }];

  export default {
    data () {
      return {
        selectedDate: new Date(2018, 1, 15),
        eventSettings: {
          dataSource: data,
          fields: {
            id: 'Id',
            subject: { name: 'EventName' },
            isAllDay: { name: 'IsAllDay' },
            startTime: { name: 'StartTime' },
            endTime: { name: 'EndTime' }
          }
        }
      }
    },
    provide: {
      schedule: [Day, Week, WorkWeek, Month, Agenda]
    }
  }
</script>
```

The other fields available in Scheduler can be referred from [here](./appointments#event-fields).

## Setting date

Scheduler usually displays the system date as its current date. To change the current date of Scheduler with specific date, define the `selectedDate` property.

`[src/app/app.vue]`

```html
<template>
  <div id='app'>
      <ejs-schedule height='550px' :selectedDate='selectedDate'></ejs-schedule>
  </div>
</template>
<script>
  import Vue from 'vue';
  import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-vue-schedule';
  Vue.use(SchedulePlugin);

  export default {
    data (){
      return {
        selectedDate: new Date(2018, 1, 15)
      }
    },
    provide: {
      schedule: [Day, Week, WorkWeek, Month, Agenda]
    }
  }
</script>
```

## Setting view

Scheduler displays `week` view by default. To change the current view, define the applicable view name to the `currentView` property. The applicable view names are,

* Day
* Week
* WorkWeek
* Month
* Year
* Agenda
* MonthAgenda
* TimelineDay
* TimelineWeek
* TimelineWorkWeek
* TimelineMonth
* TimelineYear

```html
<template>
    <div id='app'>
        <ejs-schedule height='550px' :selectedDate='selectedDate' :currentView='currentView'>
        </ejs-schedule>
    </div>
</template>
<script>
  import Vue from 'vue';
  import { SchedulePlugin, Day, WorkWeek, Agenda, Month, Week } from '@syncfusion/ej2-vue-schedule';
  Vue.use(SchedulePlugin);
  export default {
    data () {
      return {
        selectedDate: new Date(2018, 1, 15),
        currentView: 'Month',
      }
    },
    provide: {
      schedule: [Day, WorkWeek, Agenda, Month, Week]
    }
  }
</script>
```

## Individual view customization

Each individual Scheduler views can be customized with its own options such as setting different start and end hour on Week and Work Week views, whereas hiding the weekend days on Month view alone.
This can be achieved by defining views property to accept the array of object type, where each object depicts the individual view customization.

The output will display the Scheduler with the specified view configuration.

{% tab template="schedule/view", isDefaultActive=true, iframeHeight="588px" %}

```html
<template>
  <div id='app'>
      <ejs-schedule height='550px' width='100%' :selectedDate='selectedDate'
      :eventSettings= 'eventSettings'>
        <e-views>
          <e-view option='Week' startHour='07:00' endHour='15:00' ></e-view>
          <e-view option='WorkWeek' startHour='10:00' endHour='18:00' ></e-view>
          <e-view option='Month' showWeekend=false></e-view>
        </e-views>
      </ejs-schedule>
  </div>
</template>
<script>
  import Vue from 'vue';
  import { scheduleData } from './datasource.js';
  import { extend } from '@syncfusion/ej2-base';
  import { SchedulePlugin,  WorkWeek, Month, Week } from '@syncfusion/ej2-vue-schedule';
  Vue.use(SchedulePlugin);
  export default {
    data () {
      return {
        eventSettings: { dataSource: extend([], scheduleData, null, true) },
        selectedDate: new Date(2018, 1, 15)
      }
    },
    provide: {
      schedule: [ WorkWeek, Month, Week]
    }
  }
</script>
<style>
@import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-calendars/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css';
</style>
```

{% endtab %}

> You can also explore our [Vue Scheduler example](https://ej2.syncfusion.com/vue/demos/#/material/schedule/overview.html) that shows how to use the toolbar buttons to play with Scheduler functionalities.