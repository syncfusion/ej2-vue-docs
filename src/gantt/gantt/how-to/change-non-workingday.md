---
title: "How To"
component: "Gantt"
description: "Learn how to change the non-working day in the JS 2 Gantt component."
---

# Weekend / Non-working days

Non-working days/weekend are used to represent the non-productive days in a project. You can define the non-working days in a week using the `workWeek` property in Gantt.

{% tab template="gantt/how-to/changenonworkingday" %}

```html

<template>
     <div>
        <ejs-gantt id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :highlightWeekends='true' :workWeek="workWeek"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, DayMarkers } from "@syncfusion/ej2-vue-gantt";
import { editingData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: editingData,
            height: '450px',
                taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                progress: 'Progress',
                child: 'subtasks'
            },
            workWeek: ["Sunday","Monday","Tuesday","Wednesday","Thursday"],
            };
    },
    provide: {
      gantt: [ DayMarkers ]
    }  
};
</script>

```

{% endtab %}

> By default, Saturdays and Sundays are considered as non-working days/weekend in a project.
> In the Gantt component, you can make weekend as working day by setting the `includeWeekend` property to true.