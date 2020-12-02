---
title: "How To"
component: "Gantt"
description: "Learn how to change the non-working day in the JS 2 Gantt component."
---

# Open add/edit dialog dynamically

In the Gantt component, add and edit dialogs can be opened dynamically by using [`openAddDialog`](../../api/gantt/#openadddialog) and [`openEditDialog`](../../api/gantt/#openeditdialog) methods. The following code example shows how to open add and dialog on separate button click actions.

{% tab template="gantt/how-to/open-add-edit" %}

```html

<template>
     <div>
        <ejs-button id="editDialog" cssClass="e-info" v-on:click.native="edit">edit</ejs-button>
        <br><br>
       <ejs-button id="addDialog" cssClass="e-info" v-on:click.native="add">add</ejs-button>
       <br><br>
       <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields= "taskFields" :height="height" :editDialogFields="editDialogFields" :editSettings="editSettings" :resourceNameMapping= "resourceNameMapping" :resourceIDMapping="resourceIdMapping" :resources= "resources"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Edit, Selection } from "@syncfusion/ej2-vue-gantt";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { editingData , editingResources } from './data-source.js';
Vue.use(GanttPlugin);
Vue.use(ButtonPlugin);
export default {
  data: function() {
      return{
            data: editingData,
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                endDate: 'EndDate',
                duration: 'Duration',
                progress: 'Progress',
                dependency: 'Predecessor',
                child: 'subtasks',
                notes: 'info',
                resourceInfo: 'resources'
            },
            editDialogFields: [
                { type: 'General', headerText: 'General' },
                { type: 'Dependency' },
                { type: 'Resources' },
                { type: 'Notes' }
            ],
            height: '450px',
            resourceNameMapping: 'resourceName',
            resourceIdMapping: 'resourceId',
            resources: editingResources,
            editSettings: {
                allowEditing: true,
                allowTaskbarEditing: true
            }
      };
  },
  provide: {
      gantt: [ Edit,Selection ]
  },
  methods: {
      edit: function(e){
          var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
    ganttObj.editModule.dialogModule.openEditDialog();
      },
      add: function(e){
          var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
    ganttObj.editModule.dialogModule.openAddDialog();
      }
  }
});
</script>

```

{% endtab %}

>NOTE: You should select any one of the row in the Gantt to open the edit dialog.