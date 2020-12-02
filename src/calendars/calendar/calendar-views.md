---
title: "Calendar Views"
component: "Calendar"
description: "Pre-defined views in calendar allows to perform easy navigation to select any date."
---

# Calendar Views

The Calendar has the following predefined views
that provide a flexible way to navigate back and forth when selecting dates.

| **View** | **Description** |
| --- | --- |
| month (default) | Displays the days in a month. |
| year | Displays the months in a year. |
| decade | Displays the years in a decade. |

When view is defined to the [`start`](../api/calendar#start)
property of the Calendar, it allows you to set the initial view on rendering.

The following example demonstrates how to set the `year` as the start view of the Calendar.

{% tab template="calendar/min-max", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-calendar id='calendar' :value='calVal' start='Year'></ejs-calendar>
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
        calVal: new Date()
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrap {
    margin: 35px auto;
    width: 240px;
}
</style>
```

{% endtab %}

## View restriction

By defining the [`start`](../api/calendar#start) and [`depth`](../api/calendar#depth) property with the different view, drill-
down and drill-up views navigation can be limited to the user. Calendar views will be drill-down up to the view which is set in `depth` property and drill-up up to the view which is set in `start` property.

The following example displays the Calendar in `decade` view, and allows you to select a date in `month` view.

> Depth view should always be smaller than the start view. If the views are the same, then the Calendar view remains unchanged

{% tab template="calendar/min-max", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-calendar id='calendar' start='Decade' depth='Year'></ejs-calendar>
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
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrap {
    margin: 35px auto;
    width: 240px;
}
</style>
```

{% endtab %}