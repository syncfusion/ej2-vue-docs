---
title: "Holidays"
component: "Gantt"
description: "Learn how to highlight the non-working days in the Essential JS 2 Gantt component."
---

# Holidays

Non-working days in a project can be displayed in the Gantt component using the [`holidays`](../api/gantt/#holidays) property. Each holiday can be defined with the following properties:

* [`from`](../api/gantt/holiday/#from): Defines start date of the holiday(s).
* [`to`](../api/gantt/holiday/#to): Defines end date of the holiday(s).
* [`label`](../api/gantt/holiday/#label): Defines the description or label for the holiday.
* [`cssClass`](../api/gantt/holiday/#cssclass): Formats the holidays label in the Gantt chart.

To highlight the days, inject the [`DayMarkers`](../api/gantt/#daymarkersmodule) module in the `provide` section.

The following code example shows how to display the non-working days in the Gantt component.

{% tab template="gantt/holidays" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :holidays = "holidays"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, DayMarkers } from "@syncfusion/ej2-vue-gantt";
import { projectNewData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
        data: projectNewData,
        height:'450px',
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        holidays: [{
            from: "04/04/2019",
            to:"04/05/2019",
            label: " Public holidays",
            cssClass:"e-custom-holiday"
        },
        {
            from: "04/12/2019",
            to:"04/12/2019",
            label: " LOcal holidays",
            cssClass:"e-custom-holiday"
            }]
      };
  },
  provide: {
      gantt: [DayMarkers]
  }
};
</script>

```

{% endtab %}