---
title: "How To"
component: "Gantt"
description: "Learn how to maintain zoomtofit."
---

# Maintain zoomToFit

In the Gantt control, While performing edit actions or dynamically change dataSource, the timeline gets refreshed. When zoomToFit toolbar item is clicked and perform editing actions or dynamically change dataSource, the timeline gets refreshed. So that, the timeline will not fit to the project any more.

## Maintain zoomToFit after edit actions

We can maintain `zoomToFit` after editing actions(cell edit,dialog edit,taskbar edit) by using [`fitToProject`](../api/gantt/#fittoproject) method in `actionComplete` and `taskbarEdited` event.

{% tab template="gantt/how-to/maintainzoomtofit" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :toolbar="toolbar" :editSettings= "editSettings" :actionComplete="actionComplete" :taskbarEdited="taskbarEdited"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, Edit, Selection } from "@syncfusion/ej2-vue-gantt";
import { projectNewData } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: projectNewData,
            height: '450px',
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                progress: 'Progress',
                dependency: 'Predecessor',
                child: 'subtasks'
            },
            toolbar: ['Edit','ZoomToFit'],
            editSettings: {
              allowEditing: true,
              allowTaskbarEditing: true
            },
            actionComplete: function(args) {
              if ((args.action === "CellEditing" || args.action === "DialogEditing") && args.requestType === "save") {
                var obj = document.getElementById("GanttContainer").ej2_instances[0];
                obj.dataSource = projectNewData;
                obj.fitToProject();
              }
            },
            taskbarEdited: function(args) {
              if (args) {
                var obj = document.getElementById("GanttContainer").ej2_instances[0];
                obj.dataSource = projectNewData;
                obj.fitToProject();
              }
            }
        };
  },
  provide: {
      gantt: [Toolbar, Edit, Selection ]
  }
};
</script>

```

{% endtab %}

## Maintain zoomToFit after change dataSource dynamically

We can maintain `zoomToFit` after change dataSource dynamically, by calling [`fitToProject`](../api/gantt/#fittoproject) method in dataBound event.

{% tab template="gantt/how-to/maintainzoomtofitdatasource" %}

```html

<template>
     <div>
        <ejs-button id="changeData" cssClass="e-info" v-on:click.native="changeData">Change Data</ejs-button>
        <br><br><br>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :toolbar="toolbar" :dataBound="dataBound"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar } from "@syncfusion/ej2-vue-gantt";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { projectNewData, data } from './data-source.js';
Vue.use(GanttPlugin);
Vue.use(ButtonPlugin);
export default {
  data: function() {
      return{
            data: projectNewData,
            height: '450px',
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                progress: 'Progress',
                dependency: 'Predecessor',
                child: 'subtasks'
            },
            toolbar: ['ZoomToFit'],
            dataBound: function(args) {
              var obj = document.getElementById('GanttContainer').ej2_instances[0];
              obj.fitToProject();
            },
        };
  },
  methods: {
      changeData: function(e){
        var obj = document.getElementById('GanttContainer').ej2_instances[0];
        obj.dataSource = data;
      }
  }
  provide: {
      gantt: [Toolbar]
  }
};
</script>

```

{% endtab %}