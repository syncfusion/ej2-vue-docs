---
title: "Timeline header rows in VueJS Scheduler"
component: "Scheduler"
description: "This section explains how to display the additional header rows on timeline view of Scheduler."
---

# Timeline header rows

The Timeline views can have additional header rows other than its default date and time header rows. It is possible to show individual header rows for displaying year, month and week separately using the `headerRows` property. This property is applicable only on the timeline views. The possible rows which can be added using `headerRows` property are as follows.

* `Year`
* `Month`
* `Week`
* `Date`
* `Hour`

> The `Hour` row is not applicable for Timeline month view.

The following example shows the Scheduler displaying all the available header rows on timeline views.

{% tab template="schedule/header-rows", iframeHeight="588px" %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :selectedDate='selectedDate' :eventSettings='eventSettings' :views='views' :startHour='startHour' :endHour='endHour' :headerRows='headerRows'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, TimelineViews } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);
export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      startHour: '09:00',
      endHour: '13:00',
      headerRows: [
        { option: 'Year' },
        { option: 'Month' },
        { option: 'Week' },
        { option: 'Date' },
        { option: 'Hour' }
      ],
      views: ['TimelineWeek'],
      selectedDate: new Date(2018, 11, 31),
      eventSettings: { dataSource: scheduleData }
    }
  },
  provide: {
    schedule: [TimelineViews]
  }
}

</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
</style>
```

{% endtab %}

## Display year and month rows in timeline views

To display the timeline Scheduler simply with year and month names alone, define the option `Year` and `Month` within the `headerRows` property.

{% tab template="schedule/header-rows", iframeHeight="588px" %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :selectedDate='selectedDate' :eventSettings='eventSettings' :views='views' :currentView='currentView' :headerRows='headerRows'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, TimelineMonth } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);
export default {
  data (){
    return {
      width: '100%',
      height: '550px',
      selectedDate: new Date(2018, 11, 31),
      headerRows: [{ option: 'Year' }, { option: 'Month' }],
      currentView: 'TimelineMonth',
      views: [{ option: 'TimelineMonth', interval: 24 }],
      eventSettings: { dataSource: scheduleData }
    }
  },
  provide: {
    schedule: [TimelineMonth]
  }
}

</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
</style>
```

{% endtab %}

## Display week numbers in timeline views

The week number can be displayed in a separate header row of the timeline Scheduler by setting `Week` option within `headerRows` property.

{% tab template="schedule/header-rows", iframeHeight="588px" %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :selectedDate='selectedDate' :eventSettings='eventSettings' :views='views' :currentView='currentView' :headerRows='headerRows'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, TimelineMonth, TimelineViews } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);
export default {
  data (){
    return {
      width: '100%', height: '550px',
      selectedDate: new Date(2018, 11, 31),
      headerRows: [{ option: 'Week' }, { option: 'Date' }, { option: 'Hour' }],
      currentView: 'TimelineMonth',
      views: [
          { option: 'TimelineMonth', interval: 24 },
          { option: 'TimelineWeek', interval: 3 },
          { option: 'TimelineDay', interval: 4 }
      ],
      eventSettings: { dataSource: scheduleData }
    }
  },
  provide: {
    schedule: [TimelineViews, TimelineMonth]
  }
}

</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
</style>
```

{% endtab %}

## Timeline view displaying dates of a complete year

It is possible to display a complete year in a timeline view by setting `interval` value as 12 and defining **TimelineMonth** view option within the `views` property of Scheduler.

{% tab template="schedule/header-rows", iframeHeight="588px" %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :selectedDate='selectedDate' :eventSettings='eventSettings' :views='views' :headerRows='headerRows'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, TimelineMonth, TimelineViews } from '@syncfusion/ej2-vue-schedule';
import { eventData } from './datasource.js';

Vue.use(SchedulePlugin);
export default {
  data (){
    return {
      width: '100%', height: '550px',
      selectedDate: new Date(2018, 0, 1),
      headerRows: [{ option: 'Month' }, { option: 'Date' }],
      views: [{ option: 'TimelineMonth', interval: 12 }],
      eventSettings: { dataSource: eventData }
    }
  },
  provide: {
    schedule: [TimelineMonth]
  }
}

</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
</style>
```

{% endtab %}

## Customizing the header rows using template

You can customize the text of the header rows and display any images or formatted text on each individual header rows using the built-in `template` option available within the `headerRows` property.

{% tab template="schedule/header-rows", iframeHeight="588px" %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :width='width' :selectedDate='selectedDate' :eventSettings='eventSettings' :views='views' :headerRows='headerRows'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, TimelineMonth, getWeekNumber } from '@syncfusion/ej2-vue-schedule';
import { Internationalization } from '@syncfusion/ej2-base';
import { eventData } from './datasource.js';

Vue.use(SchedulePlugin);

var instance = new Internationalization();

var yearHeaderVue = Vue.component('year-header', {
    template: '<span class="year">{{getYearDetails(data)}}</span>',
    data() {
        return {
            data: {}
        };
    },
    methods: {
        getYearDetails: function (value) {
            return 'Year: ' + instance.formatDate(value.date, { skeleton: 'y' });
        }
    }
});
var monthHeaderVue = Vue.component('month-header', {
    template: '<span class="month">{{getMonthDetails(data)}}</span>',
    data() {
        return {
            data: {}
        };
    },
    methods: {
        getMonthDetails: function (value) {
            return 'Month ' + instance.formatDate(value.date, { skeleton: 'M' });
        }
    }
});

var weekHeaderVue = Vue.component('week-header', {
    template: '<span class="week">{{getWeekDetails(data)}}</span>',
    data() {
        return {
            data: {}
        };
    },
    methods: {
        getWeekDetails: function (value) {
            return 'Week: ' + getWeekNumber(value.date);
        }
    }
});

export default {
  data (){
    return {
      width: '100%',
      height: '550px',
      selectedDate: new Date(2018, 0, 1),
      headerRows: [
        {
            option: 'Year',
            template: function (e) {
                return {
                    template: yearHeaderVue
                };
            }
        },
        {
            option: 'Month',
            template: function (e) {
                return {
                    template: monthHeaderVue
                };
            },
        },
        {
            option: 'Week',
            template: function (e) {
                return {
                    template: weekHeaderVue
                };
            }
        },
        { option: 'Date' }
      ],
      views: [{ option: 'TimelineMonth' }],
      eventSettings: { dataSource: eventData }
    }
  },
  provide: {
    schedule: [TimelineMonth]
  }
}

</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";
</style>
```

{% endtab %}