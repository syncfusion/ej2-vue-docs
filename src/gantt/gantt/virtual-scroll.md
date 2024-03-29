---
title: "Virtual Scrolling"
component: "Gantt"
description: "Learn how to work with Virtual Scrolling support in Essential JS 2 Gantt control."
---

# Virtual Scrolling

Virtual Scroll support in Gantt allows you to load large amount of data without performance degradation. To enable Virtual Scrolling, you need to inject `VirtualScroll` module in Gantt.

## Row Virtualization

Row virtualization allows you to load and render a large number of tasks in Gantt with effective performance. In this mode, all tasks are fetched initially from the datasource and rendered in the DOM within a compact viewport area.

The number of records displayed in the Gantt is determined by the height.

This mode can be enable by setting the `enableVirtualization` property to `true`.

{% tab template="gantt/virtual-scroll" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt'
            :dataSource= "data"
            :taskFields= "taskFields"
            :allowSelection= "true"
            :enableVirtualization= "true"
            :labelSettings= "labelSettings"
            :height= "height"
            :treeColumnIndex= "1"
            :highlightWeekends= "true"
            :columns= "columns"
            :splitterSettings= "splitterSettings">
        </ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Selection, VirtualScroll } from "@syncfusion/ej2-vue-gantt";
Vue.use(GanttPlugin);
export default Vue.extend({
  data: function() {
      return{
            data: [
    {
        TaskID: 1, TaskName: 'Product concept',StartDate: new Date('04/02/2019'), EndDate: new Date('04/21/2019'),
        parentID: 0
    },
    {
        TaskID: 2, TaskName: 'Defining the product and its usage', StartDate: new Date('04/02/2019'),
        Duration: 3, Progress: 30, parentID: 1
    },
    {
        TaskID: 3, TaskName: 'Defining target audience', StartDate: new Date('04/02/2019'),
        parentID: 1, Duration: 3
    },
    {
        TaskID: 4, TaskName: 'Prepare product sketch and notes', StartDate: new Date('04/05/2019'),
        Duration: 2, parentID: 1, Progress: 30
    },
    {
        TaskID: 5, TaskName: 'Concept approval', StartDate: new Date('04/08/2019'),
        parentID: 0, Duration: 0
    },
    {
        TaskID: 6, TaskName: 'Market research', StartDate: new Date('04/02/2019'),
        parentID: 0, EndDate: new Date('04/21/2019')
    },
    {
        TaskID: 7, TaskName: 'Demand analysis', StartDate: new Date('04/04/2019'),
        EndDate: new Date('04/21/2019'), parentID: 6
    },
    {
        TaskID: 8, TaskName: 'Customer strength', StartDate: new Date('04/09/2019'),
        Duration: 4, parentID: 7, Progress: 30
    },
    {
        TaskID: 9, TaskName: 'Market opportunity analysis', StartDate: new Date('04/09/2019'),
        Duration: 4, parentID: 7
    },
    {
        TaskID: 10, TaskName: 'Competitor analysis', StartDate: new Date('04/15/2019'),
        Duration: 4, parentID: 6, Progress: 30
    },
    {
        TaskID: 11, TaskName: 'Product strength analsysis', StartDate: new Date('04/15/2019'),
        Duration: 4, parentID: 6
    },
    {
        TaskID: 12, TaskName: 'Research complete', StartDate: new Date('04/18/2019'),
        Duration: 0, parentID: 6
    },
    {
        TaskID: 13, TaskName: 'Product design and development', StartDate: new Date('04/04/2019'),
        parentID: 0, EndDate: new Date('04/21/2019')
    },
    {
        TaskID: 14, TaskName: 'Functionality design', StartDate: new Date('04/19/2019'),
        Duration: 3, parentID: 13, Progress: 30
    },
    {
        TaskID: 15, TaskName: 'Quality design', StartDate: new Date('04/19/2019'),
        Duration: 3, parentID: 13
    },
    {
        TaskID: 16, TaskName: 'Define reliability', StartDate: new Date('04/24/2019'),
        Duration: 2, Progress: 30, parentID: 13
    },
    {
        TaskID: 17, TaskName: 'Identifying raw materials', StartDate: new Date('04/24/2019'),
        Duration: 2, parentID: 13
    },
    {
        TaskID: 18, TaskName: 'Define cost plan', StartDate: new Date('04/04/2019'),
        parentID: 13, EndDate: new Date('04/21/2019')
    },
    {
        TaskID: 19, TaskName: 'Manufacturing cost', StartDate: new Date('04/26/2019'),
        Duration: 2, Progress: 30, parentID: 18
    },
    {
        TaskID: 20, TaskName: 'Selling cost', StartDate: new Date('04/26/2019'),
        Duration: 2, parentID: 18
    },
    {
        TaskID: 21, TaskName: 'Development of the final design', StartDate: new Date('04/30/2019'),
        parentID: 13, EndDate: new Date('04/21/2019')
    },
    {
        TaskID: 22, TaskName: 'Defining dimensions and package volume', StartDate: new Date('04/30/2019'),
        Duration: 2, parentID: 21, Progress: 30
    },
    {
        TaskID: 23, TaskName: 'Develop design to meet industry standards', StartDate: new Date('05/02/2019'),
        Duration: 2, parentID: 21
    },
    {
        TaskID: 24, TaskName: 'Include all the details', StartDate: new Date('05/06/2019'),
        Duration: 3, parentID: 21
    },
    {
        TaskID: 25, TaskName: 'CAD computer-aided design', StartDate: new Date('05/09/2019'),
        Duration: 3, parentID: 13, Progress: 30
    },
    {
        TaskID: 26, TaskName: 'CAM computer-aided manufacturing', StartDate: new Date('09/14/2019'),
        Duration: 3, parentID: 13
    },
    {
        TaskID: 27, TaskName: 'Design complete', StartDate: new Date('05/16/2019'),
        Duration: 0, parentID: 13
    },
    {
        TaskID: 28, TaskName: 'Prototype testing', StartDate: new Date('05/17/2019'),
        Duration: 4, Progress: 30, parentID: 0
    },
    {
        TaskID: 29, TaskName: 'Include feedback', StartDate: new Date('05/17/2019'),
        Duration: 4, parentID: 0
    },
    {
        TaskID: 30, TaskName: 'Manufacturing', StartDate: new Date('05/23/2019'),
        Duration: 5, Progress: 30, parentID: 0
    },
    {
        TaskID: 31, TaskName: 'Assembling materials to finsihed goods', StartDate: new Date('05/30/2019'),
        Duration: 5, parentID: 0
    },
    {
        TaskID: 32, TaskName: 'Feedback and testing', StartDate: new Date('04/04/2019'),
        parentID: 0, EndDate: new Date('04/21/2019'),
    },
    {
        TaskID: 33, TaskName: 'Internal testing and feedback', StartDate: new Date('06/06/2019'),
        Duration: 3, parentID: 32, Progress: 45
    },
    {
        TaskID: 34, TaskName: 'Customer testing and feedback', StartDate: new Date('06/11/2019'),
        Duration: 3, parentID: 32, Progress: 50
    },
    {
        TaskID: 35, TaskName: 'Final product development', StartDate: new Date('04/04/2019'),
        parentID: 0, EndDate: new Date('04/21/2019'),
    },
    {
        TaskID: 36, TaskName: 'Important improvements', StartDate: new Date('06/14/2019'),
        Duration: 4, Progress: 30, parentID: 35
    },
    {
        TaskID: 37, TaskName: 'Address any unforeseen issues', StartDate: new Date('06/14/2019'),
        Duration: 4, Progress: 30, parentID: 35
    },
    {
        TaskID: 38, TaskName: 'Final product', StartDate: new Date('04/04/2019'),
        parentID: 0, EndDate: new Date('04/21/2019'),
    },
    {
        TaskID: 39, TaskName: 'Branding product', StartDate: new Date('06/20/2019'),
        Duration: 4, parentID: 38
    },
    {
        TaskID: 40, TaskName: 'Marketing and presales', StartDate: new Date('06/26/2019'), Duration: 4,
        Progress: 30, parentID: 38
    }
];

let virtualData = [];
let projId: number = 1;
for (let i: number = 0; i < 50; i++) {
    let x: number = virtualData.length + 1;
    let parent: any = {};
    /* tslint:disable:no-string-literal */
    parent['TaskID'] = x;
    parent['TaskName'] = 'Project ' + (i + 1);
    virtualData.push(parent);
    for (let j: number = 0; j < tempData.length; j++) {
        let subtasks: any = {};
        /* tslint:disable:no-string-literal */
        subtasks['TaskID'] = tempData[j].TaskID + x;
        subtasks['TaskName'] = tempData[j].TaskName;
        subtasks['StartDate'] = tempData[j].StartDate;
        subtasks['Duration'] = tempData[j].Duration;
        subtasks['Progress'] = tempData[j].Progress;
        subtasks['parentID'] = tempData[j].parentID + x;
        virtualData.push(subtasks);
    }
},
data: virtualData,
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                endDate: 'EndDate',
                duration: 'Duration',
                progress: 'Progress',
                parentID: 'parentID'
            },
            columns: [
               { field: 'TaskID' },
                { field: 'TaskName' },
                { field: 'StartDate' },
                { field: 'Duration' },
                { field: 'Progress' }
            ],
            height: '450px',
            labelSettings: {
               taskLabel: 'Progress'
            },
            splitterSettings: {
                columnIndex: 2
            }
      };
  },
  provide: {
      gantt: [ Selection, VirtualScroll]
  }
});
</script>

```

{% endtab %}

## Limitations for Virtual Scroll

* Due to the element height limitation in browsers, the maximum number of records loaded is limited by the browser capacity.
* Cell selection will not be persisted.
* The number of records rendered will be determined by the `height` property.
* It is necessary to mention the height of the Gantt in pixels when enabling Virtual Scrolling.
* Currently, we do not have support for Row Drag and Drop when virtualization is enabled.
* Virtual Scroll does not support Multi Taskbar support in Resource View.