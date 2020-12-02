---
title: "Filtering"
component: "Gantt"
description: "Learn how to filter rows in the Gantt using the menu filtering. Also learn how to use custom filter components in the Essential JS 2 Gantt component."
---

# Filtering

Filtering allows you to view specific or related records based on filter criteria. This can be done in the Gantt Component by using the filter menu support and toolbar search support. To enable filtering in the Gantt Component, set the [`allowFiltering`](../api/gantt/#allowfiltering) to `true`. Menu filtering support can be configured using the [`filterSettings`](../api/gantt/filterSettings/) property and toolbar searching can be configured using the [`searchSettings`](../api/gantt/searchSettings/) property.

To use the filter, inject the [`Filter`](../api/gantt/#filtermodule) module in the `provide` section.

## Menu filtering

The Gantt Component provides the menu filtering support for each column. You can enable the filter menu by setting the [`allowFiltering`](../api/gantt/#allowfiltering) to `true`. The filter menu UI will be rendered based on its column type, which allows you to filter data. You can filter the records with different operators.

{% tab template="gantt/filtering" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns="columns" :splitterSettings = "splitterSettings" :filterSettings="filterSettings" :allowFiltering= ""></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Filter, } from "@syncfusion/ej2-vue-gantt";
import { projectNewData } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: [
    {
        TaskID: 1,
        TaskName: 'Project initiation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {TaskID: 2, TaskName: 'Identify site location', StartDate: new Date('04/02/2019'), Duration: 0,Progress: 50, resources: [1]},
            {TaskID: 3, TaskName: 'Perform soil test', StartDate: new Date('04/02/2019'), Duration: 4, Predecessor: '2',Progress: 50, resources: [2, 3, 5]},
            {TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 0, Predecessor: '3', Progress: 50 },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project estimation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'),Duration: 3, Predecessor: '4', Progress: 50, resources: [4]},
            {TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'),Duration: 3, Predecessor: '6', resources: [4, 8],Progress: 50},
            {TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'),Duration: 0, Predecessor: '7', resources: [12, 5]}
        ]
    }],
            height: '450px',
            columns: [
            { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '250' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        splitterSettings:{
            columnIndex:3
            },
        filterSettings: {
            type:'Menu'
        },
        };
  },
  provide: {
      gantt: [ Filter]
  }
};
</script>

```

{% endtab %}

>[`allowFiltering`](../api/gantt/#allowfiltering) must be set as `true` to enable filter menu.
>Setting [`columns.allowFiltering`](../api/gantt/column/#allowfiltering) as `false` will prevent filter menu rendering for a particular column.

### Filter hierarchy modes

The Gantt supports a set of filtering modes with the [`filterSettings.hierarchyMode`](../api/gantt/filterSettings/#hierarchymode) property. The following are the types of filter hierarchy modes available in the Gantt component:

* `Parent`: This is the default filter hierarchy mode in Gantt. The filtered records are displayed with its parent records. If the filtered records do not have any parent record, then only the filtered records will be displayed.

* `Child`: Displays the filtered records with its child record. If the filtered records do not have any child record, then only the filtered records will be displayed.

* `Both`: Displays the filtered records with its both parent and child records. If the filtered records do not have any parent and child records, then only the filtered records will be displayed.

* `None`: Displays only the filtered records.

{% tab template="gantt/filtering" %}

```html

<template>
     <div>
     <table>
            <tr>
                <td style="width: 70%">
                    <ejs-dropdownlist id="filter-type" value='Parent' :dataSource="dataSource" :fields = "fields" :change ="change"> Filter Hierarchy </ejs-dropdownlist>
                </td>
            </tr>
        </table>
         <br> <br>  
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height="height" :columns="columns" :splitterSettings = "splitterSettings" :allowFiltering= "true"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Filter, Toolbar } from "@syncfusion/ej2-vue-gantt";
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
import { projectNewData } from './data-source.js';
Vue.use(GanttPlugin);
Vue.use(DropDownListPlugin);
export default {
  data: function() {
      return{
            data: projectNewData,
            height: '450px',
            columns: [
            { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '250' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        splitterSettings:{
            columnIndex:3
            },
        dataSource: [
            { id: 'Parent', mode: 'Parent' },
            { id: 'Child', mode: 'Child' },
            { id: 'Both', mode: 'Both' },
            { id: 'None', mode: 'None' },
        ],
        fields: { text: 'mode', value: 'id' },
      };
  },
  provide: {
      gantt: [ Filter ]
  },
  methods: {
        change: function (e) {
            var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
            var mode = e.value;
            ganttChart.filterSettings.hierarchyMode = mode;
            ganttChart.clearFiltering();
        }
  },
};
</script>

```

{% endtab %}

### Initial filter

To apply the filter at initial rendering, set the filter to predicate object in the [`filterSettings.columns`](../api/gantt/filterSettings/#columns) property.

{% tab template="gantt/filtering" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns="columns" :splitterSettings = "splitterSettings" :filterSettings="filterSettings" :allowFiltering= "true"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Filter } from "@syncfusion/ej2-vue-gantt";
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: [
    {
        TaskID: 1,
        TaskName: 'Project initiation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {TaskID: 2, TaskName: 'Identify site location', StartDate: new Date('04/02/2019'), Duration: 0,Progress: 50, resources: [1]},
            {TaskID: 3, TaskName: 'Perform soil test', StartDate: new Date('04/02/2019'), Duration: 4, Predecessor: '2',Progress: 50, resources: [2, 3, 5]},
            {TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 0, Predecessor: '3', Progress: 50 },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project estimation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'),Duration: 3, Predecessor: '4', Progress: 50, resources: [4]},
            {TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'),Duration: 3, Predecessor: '6', resources: [4, 8],Progress: 50},
            {TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'),Duration: 0, Predecessor: '7', resources: [12, 5]
            }
        ]
    }];
            height: '450px',
            columns: [
            { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '250' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        splitterSettings:{
            columnIndex:3
            },
        filterSettings: {
            columns: [{ field: 'TaskName', matchCase: false, operator: 'startswith', predicate: 'and', value: 'Identify' },
               { field: 'TaskID', matchCase: false, operator: 'equal', predicate: 'and', value: 2 }]
               },
      };
  },
  provide: {
      gantt: [ Filter ]
  }
};
</script>

```

{% endtab %}

### Filter operators

The filter operator for a column can be defined in the `filterSettings.columns.operator` property.

The available operators and its supported data types are:

Operator |Description |Supported Types
-----|-----|-----
startswith |Checks whether the value begins with the specified value. |String
endswith |Checks whether the value ends with the specified value. |String
contains |Checks whether the value contains the specified value. |String
equal |Checks whether the value is equal to the specified value. |String &#124; Number &#124; Boolean &#124; Date
notequal |Checks for values not equal to the specified value. |String &#124; Number &#124; Boolean &#124; Date
greaterthan |Checks whether the value is greater than the specified value. |Number &#124; Date
greaterthanorequal|Checks whether a value is greater than or equal to the specified value. |Number &#124; Date
lessthan |Checks whether the value is less than the specified value. |Number &#124; Date
lessthanorequal |Checks whether the value is less than or equal to the specified value. |Number &#124; Date

> By default, the `filterSettings.columns.operator` value is `equal`.

### Diacritics

By default, the Gantt component ignores the diacritic characters while filtering. To include diacritic characters, set the [`filterSettings.ignoreAccent`](../api/gantt/filterSettings/#ignoreaccent) to `true`.

In the following sample, type **Project** in the `TaskName` column to filter diacritic characters.

{% tab template="gantt/filtering" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns="columns" :splitterSettings = "splitterSettings" :filterSettings="filterSettings" :allowFiltering= "true"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Filter } from "@syncfusion/ej2-vue-gantt";
import { projectNewData } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: [
    {
        TaskID: 1,
        TaskName: 'Projéct initiàtion',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {TaskID: 2, TaskName: 'Identify site locàtion', StartDate: new Date('04/02/2019'), Duration: 0,Progress: 50, resources: [1]},
            {TaskID: 3, TaskName: 'Perförm soil test', StartDate: new Date('04/02/2019'), Duration: 4, Predecessor: '2',Progress: 50, resources: [2, 3, 5]},
            {TaskID: 4, TaskName: 'Soil tëst appröval', StartDate: new Date('04/02/2019'), Duration: 0, Predecessor: '3', Progress: 50 },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project estimation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {TaskID: 6, TaskName: 'Develöp floor plan for estimàtion', StartDate: new Date('04/04/2019'),Duration: 3, Predecessor: '4', Progress: 50, resources: [4]},
            {TaskID: 7, TaskName: 'List matërials', StartDate: new Date('04/04/2019'),Duration: 3, Predecessor: '6', resources: [4, 8],Progress: 50},
            {TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'),Duration: 0, Predecessor: '7', resources: [12, 5]
            }
        ]
    }],
            height: '450px',
            columns: [
            { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '250' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        splitterSettings:{
            columnIndex:3
            },
        filterSettings: {
            ignoreAccent:true
            },
      };
  },
  provide: {
      gantt: [ Filter ]
  }
};
</script>

```

{% endtab %}

### Filtering a specific column by method

You can filter the columns dynamically by using the [`filterByColumn`](../api/gantt/#filterbycolumn) method.

{% tab template="gantt/filtering" %}

```html

<template>
     <div>
       <ejs-button id="filterRecord" cssClass="e-info" v-on:click.native="filter">Filter</ejs-button>
         <br><br><br>
          <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :splitterSettings = "splitterSettings" :columns="columns" :allowFiltering= "true"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Filter } from "@syncfusion/ej2-vue-gantt";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { projectNewData } from './data-source.js';
Vue.use(GanttPlugin);
Vue.use(ButtonPlugin);
export default {
  data: function() {
      return{
            data: [
        {
            TaskID: 1,
            TaskName: 'Project Initiation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            subtasks: [
                { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
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
            columns: [
            { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '250' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        splitterSettings:{
            columnIndex:3
            },
      };
  },
  provide: {
      gantt: [ Filter ]
  },
  methods: {
      filter: function(e){
            var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
            ganttObj.filterByColumn('TaskName','startswith','Iden','and');
        }
    }
};
</script>

```

{% endtab %}

### Clear filtered columns

You can clear all the filtering condition done in the Gantt component by using the [`clearFiltering`](../api/gantt/#clearfiltering) method.

The following code snippet explains the above behavior.

{% tab template="gantt/filtering" %}

```html

<template>
     <div>
        <ejs-button id="ClearfilterRecord" cssClass="e-info" v-on:click.native="filter">Clear Filter</ejs-button>
    <br><br><br>
    <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns="columns" :splitterSettings = "splitterSettings" :filterSettings="filterSettings" :allowFiltering= "true"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Filter } from "@syncfusion/ej2-vue-gantt";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { projectNewData } from './data-source.js';
Vue.use(GanttPlugin);
Vue.use(ButtonPlugin);
export default {
  data: function() {
      return{
            data: [
        {
            TaskID: 1,
            TaskName: 'Project Initiation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            subtasks: [
                { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50 },
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
           columns: [
            { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '250' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        splitterSettings:{
            columnIndex:3
            },
        filterSettings: {
            columns: [{ field: 'TaskName', matchCase: false, operator: 'startswith', predicate: 'and', value: 'Identify' },
            { field: 'Progress', matchCase: false, operator: 'equal', predicate: 'and', value: 50 }]
        }
      };
  },
  provide: {
      gantt: [ Filter ]
  },
   methods: {
      filter: function(e){
            var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
            ganttObj.clearFiltering();
        }
    }
};
</script>

```

{% endtab %}

## Search

You can search records in the Gantt component by using the [`search`](../api/gantt/#search) method with search key as a parameter. The Gantt component provides an option to integrate the search text box in the toolbar by adding the search item to the [`toolbar`](../api/gantt/#toolbar) property.

To search records, inject the [`Filter`](../api/gantt/#filtermodule) module in the `provide` section.

{% tab template="gantt/filtering" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :splitterSettings = "splitterSettings" :toolbar="toolbar"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, Filter } from "@syncfusion/ej2-vue-gantt";
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: [
    {
        TaskID: 1,
        TaskName: 'Project initiation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {TaskID: 2, TaskName: 'Identify site location', StartDate: new Date('04/02/2019'), Duration: 0,Progress: 50, resources: [1]},
            {TaskID: 3, TaskName: 'Perform soil test', StartDate: new Date('04/02/2019'), Duration: 4, Predecessor: '2',Progress: 50, resources: [2, 3, 5]},
            {TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 0, Predecessor: '3', Progress: 50 },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project estimation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'),Duration: 3, Predecessor: '4', Progress: 50, resources: [4]},
            {TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'),Duration: 3, Predecessor: '6', resources: [4, 8],Progress: 50},
            {TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'),Duration: 0, Predecessor: '7', resources: [12, 5]}
        ]
    }],
            height: '450px',
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                endDate: 'EndDate',
                duration: 'Duration',
                progress: 'Progress',
                dependency: 'Predecessor',
                child: 'subtasks'
            },
            toolbar: ['Search'],
            splitterSettings:{
            columnIndex:3
            },
      };
  },
  provide: {
      gantt: [ Toolbar, Filter ]
  }
};
</script>

```

{% endtab %}

### Initial search

In the Gantt component, you can load a task with some search criteria and this can be done by using the [`searchSettings`](../api/gantt/searchSettings/) property.
To apply search at initial rendering, set the value for [`fields`](../api/gantt/searchSettings/#fields), [`operator`](../api/gantt/searchSettings/#operator), [`key`](../api/gantt/searchSettings/#key), and [`ignoreCase`](../api/gantt/searchSettings/#ignorecase) in the [`searchSettings`](../api/gantt/searchSettings/) property.

{% tab template="gantt/filtering" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :splitterSettings = "splitterSettings" :columns="columns" :toolbar="toolbar" :searchSettings="searchSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, Filter } from "@syncfusion/ej2-vue-gantt";
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: [
    {
        TaskID: 1,
        TaskName: 'Project initiation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {TaskID: 2, TaskName: 'Identify site location', StartDate: new Date('04/02/2019'), Duration: 0,Progress: 50, resources: [1]},
            {TaskID: 3, TaskName: 'Perform soil test', StartDate: new Date('04/02/2019'), Duration: 4, Predecessor: '2',Progress: 50, resources: [2, 3, 5]},
            {TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 0, Predecessor: '3', Progress: 50 },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project estimation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'),Duration: 3, Predecessor: '4', Progress: 50, resources: [4]},
            {TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'),Duration: 3, Predecessor: '6', resources: [4, 8],Progress: 50},
            {TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'),Duration: 0, Predecessor: '7', resources: [12, 5]}
        ]
    }],
            height: '450px',
            columns: [
                { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
                { field: 'TaskName', headerText: 'Task Name', width: '250' },
                { field: 'StartDate', headerText: 'Start Date', width: '150' },
                { field: 'Duration', headerText: 'Duration', width: '150' },
                { field: 'Progress', headerText: 'Progress', width: '150' },
            ],
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                progress: 'Progress',
                child: 'subtasks'
            },
            toolbar: ['Search'],
            splitterSettings:{
            columnIndex:3
            },
            searchSettings: { fields: ['TaskName'], operator: 'contains', key: 'List', ignoreCase: true }    };
  },
  provide: {
      gantt: [ Toolbar, Filter ]
  }
};
</script>

```

{% endtab %}

> By default, Gantt searches all the bound column values. To customize this behavior, define the [`searchSettings.fields`](../api/gantt/searchSettings/#fields) property.

### Search operators

The search operator can be defined in the [`searchSettings.operator`](../api/gantt/searchSettings/#operator) property to configure specific searching.

The following operators are supported in searching:

Operator |Description
-----|-----
startsWith |Checks whether a value begins with the specified value.
endsWith |Checks whether a value ends with the specified value.
contains |Checks whether a value contains the specified value.
equal |Checks whether a value is equal to the specified value.
notEqual |Checks for values not equal to the specified value.

> By default, the [`searchSettings.operator`](../api/gantt/searchSettings/#operator) value is `contains`.

### Search by external button

To search the Gantt records from an external button, invoke the [`search`](../api/gantt/#search) method.

{% tab template="gantt/filtering" %}

```html

<template>
     <div>
        <ejs-button id="searchRecord" cssClass="e-info" v-on:click.native="search">Search</ejs-button>
         <br><br><br>
         <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :toolbar="toolbar" :splitterSettings = "splitterSettings" :columns="columns" :allowFiltering='true'></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, Filter } from "@syncfusion/ej2-vue-gantt";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
Vue.use(GanttPlugin);
Vue.use(ButtonPlugin);
export default {
  data: function() {
      return{
            data: [
    {
        TaskID: 1,
        TaskName: 'Project initiation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {TaskID: 2, TaskName: 'Identify site location', StartDate: new Date('04/02/2019'), Duration: 0,Progress: 50, resources: [1]},
            {TaskID: 3, TaskName: 'Perform soil test', StartDate: new Date('04/02/2019'), Duration: 4, Predecessor: '2',Progress: 50, resources: [2, 3, 5]},
            {TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 0, Predecessor: '3', Progress: 50 },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project estimation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'),Duration: 3, Predecessor: '4', Progress: 50, resources: [4]},
            {TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'),Duration: 3, Predecessor: '6', resources: [4, 8],Progress: 50},
            {TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'),Duration: 0, Predecessor: '7', resources: [12, 5]}
        ]
    }],
            height: '450px',
            columns: [
                { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
                { field: 'TaskName', headerText: 'Task Name', width: '250' },
                { field: 'StartDate', headerText: 'Start Date', width: '150' },
                { field: 'Duration', headerText: 'Duration', width: '150' },
                { field: 'Progress', headerText: 'Progress', width: '150' },
            ],
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                progress: 'Progress',
                child: 'subtasks'
            },
            toolbar: ['Search'],
            splitterSettings:{
            columnIndex:3
            },
        };
  },
  provide: {
      gantt: [ Toolbar, Filter ]
  },
   methods: {
      search: function(e){
            var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
            var searchText = document.getElementById('GanttContainer_searchbar').value;
            ganttObj.search(searchText);
        }
    }
};
</script>

```

{% endtab %}

>Note: You should set the [`allowFiltering`](../api/gantt/#allowfiltering) property to `true` for searching the content externally.

### Search specific columns

By default, the Gantt component searches all the columns. You can search specific columns by defining the specific column's field names in the [`searchSettings.fields`](../api/gantt/searchSettings/#fields) property.

{% tab template="gantt/filtering" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :toolbar="toolbar" :splitterSettings = "splitterSettings" :columns="columns" :searchSettings="searchSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, Filter } from "@syncfusion/ej2-vue-gantt";
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: [
    {
        TaskID: 1,
        TaskName: 'Project initiation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {TaskID: 2, TaskName: 'Identify site location', StartDate: new Date('04/02/2019'), Duration: 0,Progress: 50, resources: [1]},
            {TaskID: 3, TaskName: 'Perform soil test', StartDate: new Date('04/02/2019'), Duration: 4, Predecessor: '2',Progress: 50, resources: [2, 3, 5]},
            {TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 0, Predecessor: '3', Progress: 50 },
        ]
    },
    {
        TaskID: 5,
        TaskName: 'Project estimation',
        StartDate: new Date('04/02/2019'),
        EndDate: new Date('04/21/2019'),
        subtasks: [
            {TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'),Duration: 3, Predecessor: '4', Progress: 50, resources: [4]},
            {TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'),Duration: 3, Predecessor: '6', resources: [4, 8],Progress: 50},
            {TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'),Duration: 0, Predecessor: '7', resources: [12, 5]}
        ]
    }],
            height: '450px',
            columns: [
                { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
                { field: 'TaskName', headerText: 'Task Name', width: '250' },
                { field: 'Duration', headerText: 'Duration', width: '150' },
                { field: 'StartDate', headerText: 'Start Date', width: '150' },
                { field: 'Progress', headerText: 'Progress', width: '150' },
            ],
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                progress: 'Progress',
                child: 'subtasks'
            },
            toolbar: ['Search'],
            searchSettings: { fields: ['TaskName', 'Duration'] },
            splitterSettings:{
            columnIndex:3
            },
        };
  },
  provide: {
      gantt: [ Toolbar, Filter ]
  },
};
</script>

```

{% endtab %}

> In above sample, you can search only `TaskName` and `Duration` column values.