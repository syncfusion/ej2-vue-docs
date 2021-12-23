---
title: "Getting started"
component: "Gantt"
description: "This section describes on how to create a Gantt and to enable the features like Editing, filtering, sorting in Vue"
---

# Getting started

This section explains the steps required to create a Gantt and demonstrates the basic usage of the Gantt component.

## Dependencies

Following is the list of dependencies to use the Gantt with all features:

```javascript
|-- @syncfusion/ej2-gantt
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-calendars
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-dropdowns
    |-- @syncfusion/ej2-grids
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-layouts
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-richtexteditor
    |-- @syncfusion/ej2-treegrid
```

## Installation and configuration

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your Vue applications. To install Vue CLI use the following command:

```bash

npm install -g @vue/cli

npm install -g @vue/cli-init

```

Start a new project using following Vue CLI command:

```bash

vue init webpack-simple quickstart

cd quickstart

npm install

```

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry. You can choose the component that you want to install. For this application, we are going to use Gantt component.

To install Gantt component, use the following command:

```bash

npm install @syncfusion/ej2-vue-gantt –save

```

## Registering Vue component

For Registering Vue Component two ways are available. They are as follows:

* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the following code snippet:

```typescript

import { GanttPlugin } from '@syncfusion/ej2-vue-gantt';

Vue.use(GanttPlugin);

```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package, register the same using the Vue.component() with name of Component from ComponentPlugin and the EJ2 Vue Component as its arguments.

Refer the following code snippet:

```typescript

import { GanttComponent, GanttPlugin } from '@syncfusion/ej2-vue-gantt';

Vue.component(GanttPlugin.name, GanttComponent);

```

Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Initialize Gantt component

Add the EJ2 Vue Gantt using `<ejs-gantt>` to the `<template>` section of the `App.vue` file in src directory, the content attribute of the Gantt component is provided as name in data option in the `<script>` section.

```html

<template>
    <div id="app">
    <ejs-gantt></ejs-gantt>
  </div>
</template>
<script>
import Vue from 'vue';
import { GanttPlugin } from '@syncfusion/ej2-vue-gantt';

Vue.use(GanttPlugin);
export default Vue.extend ({});
</script>

```

## Adding CSS reference

Add Gantt component’s styles as following code under  `<style>`  section of the App.vue file.

```html

<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';  
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';  
@import '../node_modules/@syncfusion/ej2-calendars/styles/material.css';  
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';  
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-grids/styles/material.css';
@import '../node_modules/@syncfusion/ej2-richtexteditor/styles/material.css';
@import '../node_modules/@syncfusion/ej2-treegrid/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-gantt/styles/material.css";
</style>

```

`Note:` Use above CSS styles in `<style> </style>` tag for rendering all code snippets.

## Module injection

The Gantt components was segregated into individual feature-wise modules. To use its feature, you need to inject its feature service in the AppModule.
Find the relevant feature modules and descriptions as follows:

* [`Edit`](../api/gantt/#editmodule) : Inject this module to use the editing feature.
* [`Filter`](../api/gantt/#filtermodule) : Inject this module to use the filtering feature.
* [`Sort`](../api/gantt/#sortmodule) : Inject this module to use the sorting feature.
* [`Selection`](../api/gantt/#selectionmodule) : Inject this module to use the selection feature.
* [`Toolbar`](../api/gantt/#toolbar) : Inject this module to use the toolbar items.
* [`DayMarkers`](../api/gantt/#daymarkersmodule) : Inject this module to highlight the days.

Now, import the above-mentioned modules from the Gantt package and inject them using `provide`like following code:

```javascript

import Vue from "vue";
import { GanttPlugin , Edit, Filter, Sort } from "@syncfusion/ej2-vue-gantt";

Vue.use(GanttPlugin);

export default {
  provide: {
    gantt: [ Edit, Filter, Sort ]
  }
};

 ```

## Binding Gantt with data

Bind data with the Gantt component by using the [`dataSource`](../api/gantt/#datasource) property. It accepts an array of JavaScript object or the DataManager instance.

 ```html

<template>
     <div>
        <ejs-gantt ref='gantt' :dataSource="data"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
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
        };
  },
};
</script>

```

## Mapping task fields

The data source fields that are required to render the tasks are mapped to the Gantt control using the [`taskFields`](../api/gantt/#taskfields) property.

 {% tab template="gantt/getting-started" %}

 ```html

<template>
     <div>
        <ejs-gantt ref='gantt' :dataSource="data" id="GanttContainer" :taskFields = "taskFields" :height = "height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
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
                endDate: 'EndDate',
                duration: 'Duration',
                progress: 'Progress',
                child: 'subtasks'
            },
        };
  },
};
</script>

```

{% endtab %}

## Defining timeline

The Gantt has an option to define timeline using [`timelineSettings`](../api/gantt/timelineSettings/) property with various options. Using this property we can customize the Gantt timeline.

{% tab template="gantt/getting-started" %}

```html

<template>
     <div>
        <ejs-gantt id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :timelineSettings="timelineSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
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
                endDate: 'EndDate',
                duration: 'Duration',
                progress: 'Progress',
                dependency: 'Predecessor',
                child: 'subtasks'
            },
             timelineSettings: {
                topTier: {
                    format: 'MMM dd, yyyy',
                    unit: 'Week',
                },
                bottomTier: {
                    unit: 'Day',
                },
            },
      };
  },  
};
</script>

```

{% endtab %}

## Enabling toolbar

The [`toolbar`](../api/gantt/#toolbar) property is used to add the toolbar items like Add, Remove, Edit, Update, Delete, Expand All,Collapse All in Gantt.

To use toolbar, inject the `Toolbar` module in the `provide` section.

{% tab template="gantt/getting-started" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :toolbar="toolbar" :editSettings= "editSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Edit, Selection, Toolbar, DayMarkers  } from "@syncfusion/ej2-vue-gantt";
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
                endDate: 'EndDate',
                duration: 'Duration',
                progress: 'Progress',
                dependency: 'Predecessor',
                child: 'subtasks'
            },
            toolbar: ['Add', 'Edit', 'Update', 'Delete', 'Cancel', 'ExpandAll', 'CollapseAll'],
             editSettings: {
                allowAdding: true,
                allowEditing: true,
                allowDeleting: true,
                allowTaskbarEditing: true,
                showDeleteConfirmDialog: true
            },
      };
  },
  provide: {
      gantt: [ Edit, Selection, Toolbar, DayMarkers ]
  }
};
</script>

```

{% endtab %}

## Enabling editing

The editing feature enables you to edit the tasks in Gantt component. It can be enabled by using the [`editSettings.allowEditing`](../api/gantt/editSettings/#allowediting) and [`editSettings.allowTaskbarEditing`](../api/gantt/editSettings/#allowtaskbarediting) properties.

To use Editing, inject the [`Edit`](../api/gantt/#editmodule) module in the `provide` section.

The following editing options are available to update the tasks in Gantt:

* Cell
* Dialog
* Taskbar
* Connector line

### Cell editing

Modify the task details through cell editing by setting the edit [`mode`](../api/gantt/editSettings/#mode) property as `Auto`. To enable edit support [`Edit`](../api/gantt/#editmodule) module should be injected in Gantt. If [`Edit`](../api/gantt/#editmodule) module is not injected, you cannot do any editing action in Gantt.

{% tab template="gantt/getting-started" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :toolbar="toolbar" :columns = "columns" :editSettings= "editSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Edit  } from "@syncfusion/ej2-vue-gantt";
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
                endDate: 'EndDate',
                duration: 'Duration',
                progress: 'Progress',
                child: 'subtasks'
            },
            columns: [
                { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
                { field: 'TaskName', headerText: 'Task Name', width: '250' },
                { field: 'StartDate', headerText: 'Start Date', width: '150' },
                { field: 'Duration', headerText: 'Duration', width: '150' },
                { field: 'Progress', headerText: 'Progress', width: '150' },
            ],
            toolbar: ['Edit'],
            editSettings: {
                allowEditing: true,
                mode:"Auto"
            },
      };
  },
  provide: {
      gantt: [ Edit ]
  }
};
</script>

```

{% endtab %}

`Note:` When the edit mode is set to `Auto`, you can change the cells to editable mode by double-clicking anywhere at the TreeGrid and edit the task details in the edit dialog by double-clicking anywhere at the chart.

### Dialog editing

Modify the task details through dialog by setting edit [`mode`](../api/gantt/editSettings/#mode) property as `Dialog`.

{% tab template="gantt/getting-started" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :toolbar="toolbar" :columns = "columns" :editSettings= "editSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Edit  } from "@syncfusion/ej2-vue-gantt";
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
                endDate: 'EndDate',
                duration: 'Duration',
                progress: 'Progress',
                child: 'subtasks'
            },
            columns: [
                { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
                { field: 'TaskName', headerText: 'Task Name', width: '250' },
                { field: 'StartDate', headerText: 'Start Date', width: '150' },
                { field: 'Duration', headerText: 'Duration', width: '150' },
                { field: 'Progress', headerText: 'Progress', width: '150' },
            ],
            toolbar: ['Edit'],
             editSettings: {
                 allowEditing: true,
                 mode:"Dialog"
            },
      };
  },
  provide: {
      gantt: [ Edit ]
  }
};
</script>

```

{% endtab %}

`Note:` In dialog editing mode, the edit dialog will appear while performing double click action in both TreeGrid and chart sides.

### Taskbar editing

Modify the task details through user interaction such as resizing and dragging the taskbar by enabling the [`allowTaskbarEditing`](../api/gantt/editSettings/#allowtaskbarediting) property.

{% tab template="gantt/getting-started" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :toolbar="toolbar" :columns = "columns" :editSettings= "editSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Edit  } from "@syncfusion/ej2-vue-gantt";
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
                endDate: 'EndDate',
                duration: 'Duration',
                progress: 'Progress',
                child: 'subtasks'
            },
            columns: [
                { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
                { field: 'TaskName', headerText: 'Task Name', width: '250' },
                { field: 'StartDate', headerText: 'Start Date', width: '150' },
                { field: 'Duration', headerText: 'Duration', width: '150' },
                { field: 'Progress', headerText: 'Progress', width: '150' },
            ],
            toolbar: ['Edit'],
             editSettings: {
                allowTaskbarEditing:true
            },
      };
  },
  provide: {
      gantt: [ Edit ]
  }
};
</script>

```

{% endtab %}

### Dependency editing

Modify the task dependencies using mouse interactions by enabling the [`allowTaskbarEditing`](../api/gantt/editSettings/#allowtaskbarediting) property along with mapping the task dependency data source field to the [`dependency`](../api/gantt/taskFields/#dependency) property.

{% tab template="gantt/getting-started" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :toolbar="toolbar" :columns = "columns" :editSettings= "editSettings"></ejs-gantt>
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
            subtasks: [
                { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 0, Progress: 50 },
                { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50  },
                { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 4,Predecessor:"2FS", Progress: 50 },
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
                { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: 0,Predecessor:"6SS", Progress: 50 }
            ]
        },
    ],
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
            columns: [
                { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
                { field: 'TaskName', headerText: 'Task Name', width: '250' },
                { field: 'StartDate', headerText: 'Start Date', width: '150' },
                { field: 'Duration', headerText: 'Duration', width: '150' },
                { field: 'Progress', headerText: 'Progress', width: '150' },
            ],
            toolbar: ['Edit'],
             editSettings: {
                allowTaskbarEditing:true
            },
      };
  },
  provide: {
      gantt: [ Edit ]
  }
};
</script>

```

{% endtab %}

## Enabling predecessors or task relationships

Predecessor or task dependency in the Gantt component is used to depict the relationship between the tasks.

Start to Start (SS) : You cannot start a task until the dependent task starts.
Start to Finish (SF) : You cannot finish a task until the dependent task finishes.
Finish to Start (FS) : You cannot start a task until the dependent task completes.
Finish to Finish (FF) : You cannot finish a task until the dependent task completes.

You can show the relationship in tasks, by using the [`dependency`](../api/gantt/taskFields/#dependency) property as shown in the following code example:

{% tab template="gantt/getting-started" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" highlightWeekends='true'></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
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
            subtasks: [
                { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 0, Progress: 50 },
                { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50  },
                { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 4,Predecessor:"2FS", Progress: 50 },
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
                { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: 0,Predecessor:"6SS", Progress: 50 }
            ]
        },
    ],
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
      };
  },  
};
</script>

```

{% endtab %}

## Assigning resources

You can display and assign the resource for each task in the Gantt control.
Create a collection of JSON object, which contains id, name, unit and group of the resources and assign it to the [`resources`](../api/gantt/#resources) property.
Map these fields to the Gantt control using the [`resourceFields`](../api/gantt/#resourceFields) property.

{% tab template="gantt/getting-started" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields= "taskFields" :height= "height" :treeColumnIndex= "1" :resourceFields= "resourceFields" :resources= "resources" :highlightWeekends= "true" :labelSettings= "labelSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
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
                }
            ],
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                endDate: 'EndDate',
                duration: 'Duration',
                progress: 'Progress',
                dependency: 'Predecessor',
                child: 'subtasks',
                resourceInfo: 'resources'
            },
            height: '450px',

            resourceFields: {
                id: 'resourceId',
                name: 'resourceName',
            },

            resources: [
                { resourceId: 1, resourceName: 'Martin Tamer' },
                { resourceId: 2, resourceName: 'Rose Fuller' },
                { resourceId: 3, resourceName: 'Margaret Buchanan' },
                { resourceId: 4, resourceName: 'Fuller King' },
                { resourceId: 5, resourceName: 'Davolio Fuller' },
                { resourceId: 6, resourceName: 'Van Jack' },
                { resourceId: 7, resourceName: 'Fuller Buchanan' },
                { resourceId: 8, resourceName: 'Jack Davolio' },
                { resourceId: 9, resourceName: 'Tamer Vinet' },
                { resourceId: 10, resourceName: 'Vinet Fuller' },
                { resourceId: 11, resourceName: 'Bergs Anton' },
                { resourceId: 12, resourceName: 'Construction Supervisor' }
            ],
            labelSettings: {
                leftLabel: 'TaskName',
                rightLabel: 'resources'
            },
      };
  }
};
</script>

```

{% endtab %}

## Enable filtering

The filtering feature enables you to view reduced amount of records based on filter criteria. Gantt provides support for menu filtering support for each columns. It can be enabled by setting the [`allowFiltering`](../api/gantt/#allowfiltering) property to `true` along with injecting the `Filter` module module as shown in the following code example. Filtering feature can also be customized using the [`filterSettings`](../api/gantt/filterSettings/) property.

To use Filtering, inject the [`Filter`](../api/gantt/#filtermodule) module in the `provide` section.

{% tab template="gantt/getting-started" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns="columns" :toolbar="toolbar" :allowFiltering= "true" :timelineSettings="timelineSettings" :splitterSettings= "splitterSettings" :labelSettings= "labelSettings" :projectStartDate="projectStartDate" :projectEndDate= "projectEndDate"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Filter, Toolbar } from "@syncfusion/ej2-vue-gantt";
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
                endDate: 'EndDate',
                duration: 'Duration',
                dependency: 'Predecessor',
                child: 'subtasks',
            },
            columns: [
                { field: 'TaskName', headerText: 'Task Name', width: '250' , clipMode: 'EllipsisWithTooltip' },
                { field: 'StartDate', headerText: 'Start Date' },
                { field: 'Duration', headerText: 'Duration' },
                { field: 'EndDate', headerText: 'End Date' },
                { field: 'Predecessor', headerText: 'Predecessor' }
            ],
            toolbar: ['Search'],
            timelineSettings: {
                timelineUnitSize: 60,
                topTier: {
                    format: 'MMM dd, yyyy',
                    unit: 'Day',
                },
                bottomTier: {
                    unit: 'Hour',
                    format: 'h.mm a'
                },
            },
            splitterSettings: {
                columnIndex: 3
                },
            labelSettings: {
                rightLabel: 'TaskName',
            },
            projectStartDate: new Date('07/16/1969 01:00:00 AM'),
            projectEndDate: new Date('07/25/1969')  
      };
  },
  provide: {
      gantt: [ Filter, Toolbar ]
  }
};
</script>

```

{% endtab %}

## Enable sorting

The sorting feature enables you to order the records. It can be enabled by setting the [`allowSorting`](../api/gantt/#allowsorting) property to `true`. Provide the [`Sort`](../api/gantt/#sortmodule) module as follows. If [`Sort`](../api/gantt/#sortmodule) module is not provided, you cannot sort when a header is clicked. The sorting feature can be customized using the `sortSettings`(../api/gantt/sortSettings/) property.

To use Sorting, inject the [`Sort`](../api/gantt/#sortmodule) module in the `provide` section.

{% tab template="gantt/getting-started" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns="columns" :splitterSettings= "splitterSettings" :allowSorting= 'true'></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Sort } from "@syncfusion/ej2-vue-gantt";
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
            splitterSettings: {
                columnIndex: 3
                },
           columns: [
                { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
                { field: 'TaskName', headerText: 'Task Name', width: '250' },
                { field: 'StartDate', headerText: 'Start Date', width: '150' },
                { field: 'Duration', headerText: 'Duration', width: '150' },
                { field: 'Progress', headerText: 'Progress', width: '150' },
            ],
      };
  },
  provide: {
      gantt: [ Sort ]
  }
};
</script>

```

{% endtab %}

## Defining eventmarkers

The [`eventMarkers`](../api/gantt/#eventmarkers) property in Gantt component is used to highlight the important event in Gantt chart part. By using this feature, you can add the lines and label to highlight important days in your project.

To highlight the days, inject the `DayMarkers` module in the `provide` section.

{% tab template="gantt/getting-started" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :eventMarkers="eventMarkers"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, DayMarkers} from "@syncfusion/ej2-vue-gantt";
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
                endDate: 'EndDate',
                duration: 'Duration',
                progress: 'Progress',
                dependency: 'Predecessor',
                child: 'subtasks'
            },
             eventMarkers: [
                {
                    day: new Date('04/09/2019'),
                    label: 'Research phase'
                }, {
                    day: new Date('04/30/2019'),
                    label: 'Design phase'
                }, {
                    day: new Date('05/23/2019'),
                    label: 'Production phase'
                }, {
                    day: new Date('06/20/2019'),
                    label: 'Sales and marketing phase'
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

## Run the application

Now run the `npm run dev` command in the console, it will build your application and open in the web browser.

The following example shows a basic Gantt:

{% tab template="gantt/getting-started",isDefaultActive=true %}

```html
<template>
<div>
<ejs-gantt id="gantt" :dataSource="data" :taskFields = "taskFields" :height="height"></ejs-gantt>
</div>
</template>

<script>
import Vue from 'vue';
import { GanttPlugin } from '@syncfusion/ej2-vue-gantt';

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
                endDate: 'EndDate',
                duration: 'Duration',
                progress: 'Progress',
                dependency: 'Predecessor',
                child: 'subtasks'
            },
        };
  },
};
</script>

```

{% endtab %}
