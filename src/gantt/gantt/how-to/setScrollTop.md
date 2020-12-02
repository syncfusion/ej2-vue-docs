---
title: "How To"
component: "Gantt"
description: "Learn how to set the setScrollTop position in Gantt chart side."
---

# Set the vertical scroll position

In the Gantt component, you can set the vertical scroller position dynamically by clicking the custom button using the [`setScrollTop`](../../api/gantt/#setscrolltop) method.

{% tab template="gantt/how-to/setscrolltop" %}

```html

<template>
     <div>
        <ejs-gantt id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :splitterSettings="splitterSettings"><ejs-gantt>
        <br><br><br>
        <ejs-button id="scrolltop" cssClass="e-info" v-on:click.native="changep">Set Scroll Top</ejs-button>
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
            splitterSettings:{
                position: "50%"
                }
        };
    },
    methods: {
      changep: function(e){
            var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
            ganttChart.ganttChartModule.scrollObject.setScrollTop(500);
        }
    }  
};
</script>

```

{% endtab %}