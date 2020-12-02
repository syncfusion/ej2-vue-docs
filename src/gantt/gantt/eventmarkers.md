---
title: "Event Marker"
component: "Gantt"
description: "Learn how to highlight the important event in Gantt chart part in the Essential JS 2 Gantt component."
---

# Event markers

The event markers in the Gantt component is used to highlight the important events in a project. Event markers can be initialized by using the [`eventMarkers`](../api/gantt/#eventmarkers) property, and you can define date and label for the event markers using the [`day`](../api/gantt/eventMarker/#day) and [`label`](../api/gantt/eventMarker/#label) properties. You can also customize it using the [`cssClass`](../api/gantt/eventMarker/#cssclass) properties. The following code example shows how to add event markers in the Gantt component.

To highlight the days, inject the [`DayMarkers`](../api/gantt/#daymarkersmodule) module in the `provide` section.

{% tab template= "gantt/eventmarkers"%}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :eventMarkers = "eventMarkers"></ejs-gantt>
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
        height:'450px',
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            resourceInfo: 'resources',
            duration: 'Duration',
            progress: 'Progress',
            dependency: 'Predecessor',
            child: 'subtasks'
        },
        eventMarkers: [
            {
                day: '04/10/2019',
                cssClass: 'e-custom-event-marker',
                label: 'Project approval and kick-off'
            }
        ]
      };
  },
  provide: {
      gantt: [DayMarkers]
  }
};
</script>

```

{% endtab %}