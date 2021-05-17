---
title: "How To"
component: "Gantt"
description: "Learn how to drag and drop a record from another component to Gantt with updating the record."
---

# Drag and Drop the Record from another component to Gantt

In Gantt, it is possible to drag a record from another component and drop it in Gantt chart with updating the Gantt record. Here, dragging an item from `TreeView` component to Gantt and that item is updated as a resource for the Gantt record, we can achieve this, by using [`nodeDragStop`](../../api/treeview/#nodedragstop) event of `TreeView` control.

{% tab template="gantt/how-to/draganddrop" %}

```html

<template>
    <div>
    <p><b>Gantt</b></p>
    <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height"
    :resourceFields= "resourceFields" :resources= "resources" :labelSettings= "labelSettings" :editSettings= "editSettings"></ejs-gantt>
    <p><b>List</b></p>
    <ejs-treeview id='treeview' :fields="fields" :allowDragAndDrop='true' :nodeDragStop="nodeDragStop"></ejs-treeview>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Edit, Selection } from "@syncfusion/ej2-vue-gantt";
import { TreeViewPlugin } from "@syncfusion/ej2-vue-navigations";
import { editingData, editingResources } from './data-source.js';
import { closest,addClass } from '@syncfusion/ej2-base';
Vue.use(GanttPlugin);
Vue.use(TreeViewPlugin);
export default {
  data: function() {
      return{
            data: editingData,
            resources: editingResources,
            fields: { dataSource: editingResources, id: 'resourceId', text: 'resourceName' },
            height: '450px',
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                progress: 'Progress',
                dependency: 'Predecessor',
                resourceInfo: 'resources',
                child: 'subtasks'
            },
            splitterSettings:{
                position: "30%"
            },
            labelSettings: {
                rightLabel: 'resources'
            },
            editSettings: {
                allowEditing: true
            },
            resourceFields: {
                id: 'resourceId',
                name: 'resourceName'
            },
        };
    },
    provide: {
      gantt: [Edit, Selection]
    },
    methods: {
        nodeDragStop: function (args) {
            var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
            var chartEle = closest(args.target, '.e-chart-row');
            var gridEle = closest(args.target, '.e-row');
            if(gridEle) {
            var index = ganttChart.treeGrid.getRows().indexOf(gridEle);
            ganttChart.selectRow(index);
            }
            var record= args.draggedNodeData;
            var selectedData = ganttChart.flatData[ganttChart.selectedRowIndex];
            var selectedDataResource = selectedData.taskData.resources;
            var resources = [];
            if (selectedDataResource) {
                for (var i = 0; i < selectedDataResource.length; i++) {
                resources.push(selectedDataResource[i].resourceId);
                }
            }
            resources.push(parseInt(record.id));
            if (chartEle || gridEle) {
                var data = {
                    TaskID: selectedData.taskData.TaskID,
                    resources: resources
                };
                ganttChart.updateRecordByID(data);
                var elements = document.querySelectorAll('.e-drag-item');
                while (elements.length > 0 && elements[0].parentNode) {
                    elements[0].parentNode.removeChild(elements[0]);
                }  
            }
        }
    }
};
</script>

```

{% endtab %}

The following screenshot shows dropping record from another component in to Gantt, and **Rose Fuller** is added as resource for the task **Develop floor plan estimation**.

![Dropping Record](../images/dropping.png)