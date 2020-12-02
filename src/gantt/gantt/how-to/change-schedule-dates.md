---
title: "How To"
component: "Gantt"
description: "Learn how to change schedule start date and end date values dynamically in the JS 2 Gantt component."
---
# Change schedule start date and end date

In the Gantt component, you can change the schedule start and end dates by clicking the custom button programmatically using the [`updateProjectDates`](../../api/gantt/#updateprojectdates) method. You can pass the start and end dates as method arguments to the [`updateProjectDates`](../../api/gantt/#updateprojectdates) method. You can also pass the Boolean value as an additional parameter, which is used to round-off the schedule start and end dates displayed in Gantt timeline.

{% tab template="gantt/how-to/changescheduledates" %}

```html

<template>
     <div>
        <ejs-button id="changedate" cssClass="e-info" v-on:click.native="change">Change Date</ejs-button>
         <br><br><br>
        <ejs-gantt id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { editingData  } from './data-source.js';
Vue.use(GanttPlugin);
Vue.use(ButtonPlugin);
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
        };
    },
    methods: {
      change: function(e){
            var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
            ganttObj.updateProjectDates(new Date('03/10/2019'),new Date('06/20/2019'),true);
        }
    },
};
</script>

```

{% endtab %}