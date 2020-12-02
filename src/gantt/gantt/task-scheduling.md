---
title: "Task scheduling"
component: "Gantt"
description: "Learn how to schedule the tasks in the Essential JS 2 Gantt control."
---

# Task Scheduling

The Gantt provides support for automatic and manual task scheduling modes. It is used to indicate whether the start date and end date of all the tasks will be automatically validated or not. [`taskMode`](../api/gantt/#taskmode) is the property used to change the schedule mode of a task.

The Gantt control supports three types of mode. They are:

* `Auto`: All the tasks are automatically validate.
* `Manual`: All the tasks are manually validate by the user.
* `Custom`: Both Auto and Manual tasks are render by mapped from data source.

>Note: The default value of [`taskMode`](../api/gantt/#taskmode) is `Auto`.

## Automatically Scheduled Tasks

When the [`taskMode`](../api/gantt/#taskmode) property is set as `Auto`, the start date and end date of all the tasks in the project will be automatically validated. That is, dates are validated based on various factors such as working time, holidays, weekends and predecessors.

{% tab template= "gantt/task-scheduling" %}

```html

<template>
    <div>
    <ejs-gantt ref = 'gantt' id = "GanttContainer" :dataSource = "data" :taskFields = "taskFields" :treeColumnIndex = "1" :height = "height" :editSettings = "editSettings" :toolbar = "toolbar" :taskMode= "taskMode" > </ejs-gantt>
        </div>
        </template>
        <script>
import Vue from "vue";
import { GanttPlugin, Edit, Selection, Toolbar } from "@syncfusion/ej2-vue-gantt";
Vue.use(GanttPlugin);
export default {
    data: function () {
        return {
            data: [
    {
        TaskID: 1,
        TaskName: 'Project initiation',
        StartDate: new Date('03/29/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {
                TaskID: 2, TaskName: 'Identify site location', StartDate: new Date('03/29/2019'), Duration: 2,
                Progress: 30, Work: 16, resources: [{ resourceId: 1, Unit: 70 }, 6]
            },
            {
                TaskID: 3, TaskName: 'Perform soil test', StartDate: new Date('03/29/2019'), Duration: 4,
                resources: [2, 3, 5], Work: 96
            },
            {
                TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('03/29/2019'), Duration: 1,
                Work: 16, resources: [8, { resourceId: 9, Unit: 50 }], Progress: 30
            },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project estimation', StartDate: new Date('03/29/2019'), EndDate: new Date('04/21/2019'),
        subtasks: [
            {
                TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('03/29/2019'),
                Duration: 3, Progress: 30, resources: [{ resourceId: 4, Unit: 50 }], Work: 30
            },
            {
                TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/01/2019'), Duration: 3,
                Work: 48, resources: [4, 8]
            },
            {
                TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/01/2019'),
                Duration: 2, Work: 60, resources: [12, { resourceId: 5, Unit: 70 }]
            }
        ]
    },
    {
        TaskID: 9, TaskName: 'Sign contract', StartDate: new Date('04/01/2019'), Duration: 1,
        Progress: 30, resources: [12], Work: 24
    }
],
            height: '450px',
            taskMode: 'Auto',
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                progress: 'Progress',
                endDate: 'EndDate',
                dependency: 'Predecessor',
                child: 'subtasks'
            },
            editSettings: {
                allowEditing: true,
                allowDeleting: true,
                allowTaskbarEditing: true,
                showDeleteConfirmDialog: true
            },
            toolbar: ['Add', 'Edit', 'Update', 'Delete', 'Cancel', 'ExpandAll', 'CollapseAll', 'Search'],
        };
    },
    provide: {
        gantt: [Edit, Selection, Toolbar]
    }
};
</script>

```

{% endtab %}

## Manually Scheduled Tasks

When the [`taskMode`](../api/gantt/#taskmode) property is set as `Manual`, the start date and end date of all the tasks in the project will be same as given in the data source. That is, dates are not validated based on various factors such as dependencies between tasks, holidays, weekends, working time.
We can restrict this mode in predecessor validation alone. That is, we can automatically validate the dates based on predecessor values by enabling the [`validateManualTasksOnLinking`](../api/gantt/#validatemanualtasksonlinking) property.

{% tab template= "gantt/task-scheduling" %}

```html

<template>
    <div>
    <ejs-gantt ref = 'gantt' id = "GanttContainer" :dataSource = "data" :taskFields = "taskFields" :treeColumnIndex = "1" :height = "height" :editSettings = "editSettings" :toolbar = "toolbar" :taskMode= "taskMode" > </ejs-gantt>
        </div>
        </template>
        <script>
import Vue from "vue";
import { GanttPlugin, Edit, Selection, Toolbar } from "@syncfusion/ej2-vue-gantt";
Vue.use(GanttPlugin);
export default {
    data: function () {
        return {
            data: [
    {
        TaskID: 1,
        TaskName: 'Project initiation',
        StartDate: new Date('03/29/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {
                TaskID: 2, TaskName: 'Identify site location', StartDate: new Date('03/29/2019'), Duration: 2,
                Progress: 30, Work: 16, resources: [{ resourceId: 1, Unit: 70 }, 6]
            },
            {
                TaskID: 3, TaskName: 'Perform soil test', StartDate: new Date('03/29/2019'), Duration: 4,
                resources: [2, 3, 5], Work: 96
            },
            {
                TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('03/29/2019'), Duration: 1,
                Work: 16, resources: [8, { resourceId: 9, Unit: 50 }], Progress: 30
            },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project estimation', StartDate: new Date('03/29/2019'), EndDate: new Date('04/21/2019'),
        subtasks: [
            {
                TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('03/29/2019'),
                Duration: 3, Progress: 30, resources: [{ resourceId: 4, Unit: 50 }], Work: 30
            },
            {
                TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/01/2019'), Duration: 3,
                Work: 48, resources: [4, 8]
            },
            {
                TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/01/2019'),
                Duration: 2, Work: 60, resources: [12, { resourceId: 5, Unit: 70 }]
            }
        ]
    },
    {
        TaskID: 9, TaskName: 'Sign contract', StartDate: new Date('04/01/2019'), Duration: 1,
        Progress: 30, resources: [12], Work: 24
    }
],
            height: '450px',
            taskMode: 'Manual',
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                progress: 'Progress',
                endDate: 'EndDate',
                dependency: 'Predecessor',
                child: 'subtasks'
            },
            editSettings: {
                allowEditing: true,
                allowDeleting: true,
                allowTaskbarEditing: true,
                showDeleteConfirmDialog: true
            },
            toolbar: ['Add', 'Edit', 'Update', 'Delete', 'Cancel', 'ExpandAll', 'CollapseAll', 'Search'],
        };
    },
    provide: {
        gantt: [Edit, Selection, Toolbar]
    }
};
</script>

```

{% endtab %}

## Custom

When the [`taskMode`](../api/gantt/#taskmode) property is set as `Custom`, the scheduling mode for each tasks will be mapped from the data source field. The `Boolean` property [`taskFields.manual`](../api/gantt/taskFields/#manual) is used to map the manual scheduling mode field from the data source.

{% tab template= "gantt/task-scheduling" %}

```html

<template>
    <div>
    <ejs-gantt ref = 'gantt' id = "GanttContainer" :dataSource = "data" :taskFields = "taskFields" :columns= "columns" :treeColumnIndex = "1" :height = "height" :editSettings = "editSettings" :toolbar = "toolbar" :taskMode= "taskMode" > </ejs-gantt>
        </div>
        </template>
        <script>
import Vue from "vue";
import { GanttPlugin, Edit, Selection, Toolbar } from "@syncfusion/ej2-vue-gantt";
Vue.use(GanttPlugin);
export default {
    data: function () {
        return {
            data: [
    {
                    'TaskID': 1,
                    'TaskName': 'Parent Task 1',
                    'StartDate': new Date('02/27/2017'),
                    'EndDate': new Date('03/03/2017'),
                    'Progress': '40',
                    'isManual': true,
                    'Children': [
                        {
                            'TaskID': 2, 'TaskName': 'Child Task 1', 'StartDate': new Date('02/27/2017'),
                            'EndDate': new Date('03/03/2017'), 'Progress': '40'
                        },
                        {
                            'TaskID': 3, 'TaskName': 'Child Task 2', 'StartDate': new Date('02/26/2017'),
                            'EndDate': new Date('03/03/2017'), 'Progress': '40', 'isManual': true
                        },
                        {
                            'TaskID': 4, 'TaskName': 'Child Task 3', 'StartDate': new Date('02/27/2017'),
                            'EndDate': new Date('03/03/2017'), 'Duration': 5, 'Progress': '40',
                        }
                    ]
                },
                {
                    'TaskID': 5,
                    'TaskName': 'Parent Task 2',
                    'StartDate': new Date('03/05/2017'),
                    'EndDate': new Date('03/09/2017'),
                    'Progress': '40',
                    'isManual': true,
                    'Children': [
                        {
                            'TaskID': 6, 'TaskName': 'Child Task 1', 'StartDate': new Date('03/06/2017'),
                            'EndDate': new Date('03/09/2017'), 'Progress': '40'
                        },
                        {
                            'TaskID': 7, 'TaskName': 'Child Task 2', 'StartDate': new Date('03/06/2017'),
                            'EndDate': new Date('03/09/2017'), 'Progress': '40',
                        },
                        {
                            'TaskID': 8, 'TaskName': 'Child Task 3', 'StartDate': new Date('02/28/2017'),
                            'EndDate': new Date('03/05/2017'), 'Progress': '40', 'isManual': true
                        },
                        {
                            'TaskID': 9, 'TaskName': 'Child Task 4', 'StartDate': new Date('03/04/2017'),
                            'EndDate': new Date('03/09/2017'), 'Progress': '40', 'isManual': true
                        }
                    ]
                },
                {
                    'TaskID': 10,
                    'TaskName': 'Parent Task 3',
                    'StartDate': new Date('03/13/2017'),
                    'EndDate': new Date('03/17/2017'),
                    'Progress': '40',
                    'Children': [
                        {
                            'TaskID': 11, 'TaskName': 'Child Task 1', 'StartDate': new Date('03/13/2017'),
                            'EndDate': new Date('03/17/2017'), 'Progress': '40'
                        },
                        {
                            'TaskID': 12, 'TaskName': 'Child Task 2', 'StartDate': new Date('03/13/2017'),
                            'EndDate': new Date('03/17/2017'), 'Progress': '40',
                        },
                        {
                            'TaskID': 13, 'TaskName': 'Child Task 3', 'StartDate': new Date('03/13/2017'),
                            'EndDate': new Date('03/17/2017'), 'Progress': '40',
                        },
                        {
                            'TaskID': 14, 'TaskName': 'Child Task 4', 'StartDate': new Date('03/12/2017'),
                            'EndDate': new Date('03/17/2017'), 'Progress': '40', 'isManual': true
                        },
                        {
                            'TaskID': 15, 'TaskName': 'Child Task 5', 'StartDate': new Date('03/13/2017'),
                            'EndDate': new Date('03/17/2017'), 'Progress': '40'
                        }
                    ]
                }
],
            height: '450px',
            taskMode: 'Custom',
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                progress: 'Progress',
                endDate: 'EndDate',
                dependency: 'Predecessor',
                child: 'Children',
                manual: 'isManual'
            },
            editSettings: {
                allowEditing: true,
                allowDeleting: true,
                allowTaskbarEditing: true,
                showDeleteConfirmDialog: true
            },
            toolbar: ['Add', 'Edit', 'Update', 'Delete', 'Cancel', 'ExpandAll', 'CollapseAll', 'Search'],
        columns: [
            { field: 'TaskID', visible: false },
            { field: 'TaskName' },
            { field: 'isManual' }
        ],
        };
    },
    provide: {
        gantt: [Edit, Selection, Toolbar]
    }
};
</script>

```

{% endtab %}

## Unscheduled Tasks

Unscheduled tasks are planned for a project without any definite schedule dates. The Gantt control supports rendering the unscheduled tasks. You can create or update the tasks with anyone of start date, end date, and duration values or none. You can enable or disable the unscheduled tasks by using the [`allowUnscheduledTasks`](../api/gantt/#allowunscheduledtasks) property. The following images represent the various types of unscheduled tasks in Gantt.

Taskbar state |Auto |Manual
-----|-----|-----
`Start Date Only` | ![Alt text](images/startDate-only.png) | ![Alt text](images/startDate-manual.png)
`End Date Only` | ![Alt text](images/endDate-only.png) | ![Alt text](images/endDate-manual.png)
`Duration Only` | ![Alt text](images/duration-only.png) | ![Alt text](images/duration-manual.png)
`Milestone`| ![Alt text](images/milestone.png) | ![Alt text](images/milestone.png)

>Note: A milestone is a task that has no start and end dates, but it has a duration value of zero

## Define unscheduled tasks in data source

You can define the various types of unscheduled tasks in the data source as follows

{% tab template= "gantt/task-scheduling" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :editSettings= "editSettings" :allowUnscheduledTasks='true'></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Edit } from "@syncfusion/ej2-vue-gantt";
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: [
        {
            TaskID: 1,
            TaskName: 'Project Initiation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            isParent:true,
            subtasks: [
                { TaskID: 2, TaskName: 'Identify Site location', Duration: 3, Progress: 50},
                { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Progress: 50   },
                { TaskID: 4, TaskName: 'Soil test approval', EndDate: new Date('04/08/2019'), Progress: 50 },
            ]
        },
        {
            TaskID: 5,
            TaskName: 'Project Estimation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            isParent:true,
            subtasks: [
                { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'), Progress: 50, resources: [4],isParent:false  },
                { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Progress: 50  },
                { TaskID: 8, TaskName: 'Estimation approval',Duration: 0,Progress: 50}
            ]
        },
    ],
            height: '450px',
            taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            endDate:'EndDate',
            duration:'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        editSettings: {
            allowEditing:true,
            allowTaskbarEditing:true
        }
    };
  },
  provide: {
      gantt: [ Edit ]
  }
};
</script>

```

{% endtab %}

> NOTE
> If the [`allowUnscheduledTasks`](../api/gantt/#allowunscheduledtasks) property is set to false, then the Gantt control automatically calculates the scheduled date values with a default value of duration 1 and the project start date is considered as the start date for the task.

## Working Time Range

In the Gantt control, working hours in a day for a project can be defined by using the [`dayWorkingTime`](../api/gantt/dayWorkingTime/) property. Based on the working hours, automatic date scheduling and duration validations for a task are performed.

The following code snippet explains how to define the working time range for the project in Gantt.

{% tab template= "gantt/task-scheduling" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :highlightWeekends='true' :splitterSettings= "splitterSettings" :dayWorkingTime="dayWorkingTime" :timelineSettings="timelineSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Edit, DayMarkers } from "@syncfusion/ej2-vue-gantt";
import { editingData } from './data-source.js';
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
            splitterSettings: {
                columnIndex: 1
                },
            dayWorkingTime: [
                {from: 9,
                to: 18 }
             ],
             timelineSettings:{
           timelineViewMode:'Day'
           }
           };
  },
  provide: {
      gantt: [ DayMarkers, Edit ]
  },
};
</script>

```

{% endtab %}

> NOTE
>* Individual tasks can lie between any time within the defined working time range of the project.
>* The [`dayWorkingTime`](../api/gantt/dayWorkingTime/) property is used to define the working time for the whole project.

## Weekend/Non-working days

Non-working days/weekend are used to represent the non-productive days in a project. You can define the non-working days in a week using the [`workWeek`](../api/gantt/#workweek) property in Gantt.

{% tab template= "gantt/task-scheduling" %}

```html

<<template>
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
> In the Gantt control, you can make weekend as working day by setting the [`includeWeekend`](../api/gantt/#includeweekend) property to `true`.