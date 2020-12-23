---
title: "How To"
component: "Gantt"
description: "Learn how to set new row position while adding new records in Gantt control."
---

# Set new row position in Gantt

In Gantt, a new row can be added in one of the following positions: Top, Bottom, Above, Below and Child. This position can be specified through the `newRowPostion` property. We can make use of the toolbarClick event to create a context menu that specifies the position in which the new row is to be added when adding a record through toolbar click.

The following code snippets demonstrate how to achieve this.

{% tab template="gantt/how-to/new-row-position" %}

```html

<template>
     <div>
     <ejs-contextmenu id='cmenu' :items='menuItems' :select="select"></ejs-contextmenu>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :toolbar="toolbar" :toolbarClick="toolbarClick" :editSettings= "editSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Edit, Toolbar } from "@syncfusion/ej2-vue-gantt";
import { ContextMenuPlugin } from "@syncfusion/ej2-vue-navigations";
Vue.use(GanttPlugin);
Vue.use(ContextMenuPlugin);
export default {
  data: function() {
      return{
          menuItems:[
                {
                    text: 'Bottom'
                },
                {
                    text: 'Above'
                },
                {
                    text: 'Below'
                },
                {
                    text: 'Child'
                },
                {
                    text: 'Top'
                }
            ],
            data: [
            {
                TaskID: 1,
                TaskName: 'Project Initiation',
                StartDate: new Date('04/02/2019'),
                EndDate: new Date('04/21/2019'),
                subtasks: [
                    {  TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
                    { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50  },
                    { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
                ]
            },
            {
                TaskID: 5,
                TaskName: 'Project Estimation',
                StartDate: new Date('04/02/2019'),
                EndDate: new Date('04/21/2019'),
                subtasks: [
                    { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 },
                    { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 },
                    { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 }
                ]
            },
        ],
            height: '450px',
            taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        editSettings:{
            allowAdding:true
            },
            toolbar: ['Add'],
            toolbarClick: (args) => {
               if (args.item.id === 'GanttContainer_add') {
                   document.getElementById('cmenu').ej2_instances[0].open(40, 20);
                   alert("open");
                }
            },
            select: function(args) {
                var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
                if (args.item.text === "Bottom") {
            ganttObj.editSettings.newRowPosition = "Bottom";
            ganttObj.openAddDialog();
        } else if (args.item.text === "Above") {
            if (ganttObj.selectedRowIndex == -1) {
                alert("Please select any row");
            } else {
                ganttObj.editSettings.newRowPosition = "Above";
                ganttObj.openAddDialog();
            }
        } else if (args.item.text === "Below") {
            if (ganttObj.selectedRowIndex == -1) {
                alert("Please select any row");
            } else {
                ganttObj.editSettings.newRowPosition = "Below";
                ganttObj.openAddDialog();
            }
        } else if (args.item.text === "Child") {
            if (ganttObj.selectedRowIndex == -1) {
                alert("Please select any row");
            } else {
                ganttObj.editSettings.newRowPosition = "Child";
                ganttObj.openAddDialog();
            }
        } else if (args.item.text === "Top") {
            ganttObj.editSettings.newRowPosition = "Top";
            ganttObj.openAddDialog();
        }
            }
      };
  },
  provide: {
      gantt: [ Edit, Toolbar ]
  }
};
</script>

```

{% endtab %}