---
title: "BaseLine"
component: "Gantt"
description: "Learn how to render the baseline in the Essential JS 2 Gantt component."
---

# Baseline

The baseline feature enables users to view the deviation between the planned dates and actual dates of the tasks in a project. Baseline dates or planned dates of a task may or may not be same as the actual task dates. The baseline can be enabled by setting the [`renderBaseline`](../api/gantt/#renderbaseline) property to `true` and the baseline color can be changed using the [`baselineColor`](../api/gantt/#baselinecolor) property. To render the baseline, you should map the baseline start and end date values from the data source. This can be done using the [`baselineStartDate`](../api/gantt/taskFields/#baselinestartdate) and [`baselineEndDate`](../api/gantt/taskFields/#baselineenddate) properties. The following code example shows how to enable a baseline in the Gantt component.

{% tab template= "gantt/baseline" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :renderBaseline="true" baselineColor='red' :taskFields="taskFields" :columns="columns" :treeColumnIndex="1" :allowSelection="true" :includeWeekend="true" :timelineSettings="timelineSettings" :height="height" :dayWorkingTime="dayWorkingTime" :projectStartDate="projectStartDate" :projectEndDate="projectEndDate"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Selection } from "@syncfusion/ej2-vue-gantt";
import { baselineData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: baselineData,
            taskFields: {
                id: 'TaskId',
                name: 'TaskName',
                startDate: 'StartDate',
                endDate: 'EndDate',
                baselineStartDate: 'BaselineStartDate',
                baselineEndDate: 'BaselineEndDate'
            },
            columns: [
                { field: 'TaskName', headerText: 'Service Name', width: '250', clipMode: 'EllipsisWithTooltip' },
                { field: 'BaselineStartDate', headerText: 'Planned start time' },
                { field: 'BaselineEndDate', headerText: 'Planned end time' },
                { field: 'StartDate', headerText: 'Start time' },
                { field: 'EndDate', headerText: 'End time' },
            ],
            timelineSettings: {
                timelineUnitSize: 65,
                topTier: {
                    unit: 'None',
                },
                bottomTier: {
                    unit: 'Minutes',
                    count: 15,
                    format: 'hh:mm a'
                },
            },
            dateFormat: 'hh:mm a',
            height: '450px',
            dayWorkingTime: [{ from: 1, to: 24 }],
            projectStartDate: new Date('03/05/2018 09:30:00 AM'),
            projectEndDate: new Date('03/05/2018 07:00:00 PM'),
        };
  },
  provide: {
      gantt: [ Selection ]
  }
};
</script>

```

{% endtab %}