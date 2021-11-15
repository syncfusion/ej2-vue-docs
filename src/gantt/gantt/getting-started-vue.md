---
title: "Getting Started with Vue 3"
component: "Gantt"
description: "Learn how to use Gantt component in Vue 3 application and enable features like Editing, filtering and sorting."
---

# Getting Started

This section explains how to use Gantt component in Vue 3 application.

## Prerequisites

* `vue` : `3+`
* `node` : `10.15+`
* `vue-class-component` : `8.0.0-rc.1`

## Creating Vue application using Vue CLI

The easiest way to create a Vue application is to use the [`Vue CLI`](https://github.com/vuejs/vue-cli). Vue CLI versions above [`4.5.0`](https://v3.vuejs.org/guide/migration/introduction.html#vue-cli) are mandatory for creating applications using Vue 3. Use the following command to uninstall older versions of the Vue CLI.

```bash
npm uninstall vue-cli -g

```

Use the following commands to install the latest version of Vue CLI.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

Create a new project using the command below.

```bash
vue create quickstart

```

Initiating a new project prompts us to choose the type of project to be used for the current application. Select the option `Default (Vue 3 Preview)` from the menu.

![Reference](./images/vue3-terminal.png)

## Adding Syncfusion Gantt package in the application

Syncfusion Vue packages are maintained in the [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.

To install Gantt component, use the following command

```bash
npm install @syncfusion/ej2-vue-gantt --save
```

> The **--save** will instruct NPM to include the Gantt package inside of the `dependencies` section of the `package.json`.

## Adding CSS reference for Syncfusion Vue Gantt component

The Gantt has different themes. They are:
* Material
* Fabric
* Bootstrap
* High Contrast

Import the needed css styles for the Gantt component along with dependency styles in the `<script>` section of the `src/App.vue` file as follows.

```js
<script>
<!-- Material theme used for this sample -->
import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
import "../../node_modules/@syncfusion/ej2-calendars/styles/material.css";
import "../../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
import "../../node_modules/@syncfusion/ej2-navigations/styles/material.css";
import "../../node_modules/@syncfusion/ej2-popups/styles/material.css";
import "../../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
import "../../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
import "../../node_modules/@syncfusion/ej2-vue-gantt/styles/material.css";
</script>

```

Note: Gantt component use other Syncfusion components too, the dependent component's CSS references need to be added for using all the Gantt functionalities.

## Adding Syncfusion Vue Gantt component in the application

You have completed all the necessary configurations needed for rendering the Syncfusion Vue component. Now, you are going to add the Gantt component using following steps.

1. Import the Gantt component in the `<script>` section of the `src/App.vue` file.

   ```html
   <script>
   import { GanttComponent, ColumnsDirective, ColumnDirective } from '@syncfusion/ej2-vue-gantt';
   </script>
  
   ```

2. Register the Gantt component along with the required child directives which are used in this example. Find the list of child directives and the tag names that can be used in the Gantt component in the following table.
  
   | Directive Name   | Tag Name    |
   |------------------|-------------|
   | `ColumnsDirective` | `e-columns` |
   | `ColumnDirective`  | `e-column`  |

   ```js

   import { GanttComponent, ColumnsDirective, ColumnDirective } from '@syncfusion/ej2-vue-gantt';
     //Component registeration
   export default {
       name: "App",
       components: {
         'ejs-gantt' : GanttComponent,
         'e-columns' : ColumnsDirective,
         'e-column' : ColumnDirective
        }
   }

   ```

   In the above code snippet, you have registered Gantt and the column directives. Column directives are used to define the column definition for the Gantt component.

3. Add the Vue Gantt by using `<ejs-gantt>` selector in `<template>` section.

   ```html
   <template>
       <ejs-gantt :dataSource='data' :treeColumnIndex='1' child='subtasks'>
           <e-columns>
               <e-column field='taskID' headerText='Task ID' textAlign='Right' width=70></e-column>
               <e-column field='taskName' headerText='Task Name' textAlign='Left' width=200></e-column>
               <e-column field='startDate' headerText='Start Date' textAlign='Right' format='yMd' width=90></e-column>
               <e-column field='duration' headerText='Duration' textAlign='Right' width=80></e-column>
          </e-columns>
       </ejs-gantt>
   </template>
  
   ```

   In the above code example for Gantt component definition, with `dataSource` property binding and columns definitions. In the `dataSource` property binding, we represent the hierarchical data binding in which [`child`](../api/gantt/#child)  property denotes the hierarchy relationship; whereas in self-referencing data binding and [`parentId`](../api/gantt/#parentid) denotes the hierarchy relationship.

4. Declare the bound properties in the `script` section. Declare the collection `data` which is bound for the `dataSource` property.

   ```js
   data() {
     return {
       data:  [{
            TaskID: 1,
            TaskName: 'Planning',
            StartDate: new Date('02/03/2017'),
            EndDate: new Date('02/07/2017'),
            Progress: 100,
            Duration: 5,
            subtasks: [
                { TaskID: 2, TaskName: 'Plan timeline', StartDate: new Date('02/03/2017'), EndDate: new Date('02/07/2017'), Duration: 5, Progress: 100,},
                { TaskID: 3, TaskName: 'Plan budget', StartDate: new Date('02/03/2017'), EndDate: new Date('02/07/2017'), Duration: 5, Progress: 100, },
                { TaskID: 4, TaskName: 'Allocate resources', StartDate: new Date('02/03/2017'), EndDate: new Date('02/07/2017'), Duration: 5, Progress: 100, },
                { TaskID: 5, TaskName: 'Planning complete', StartDate: new Date('02/07/2017'), EndDate: new Date('02/07/2017'), Duration: 0, Progress: 0, }
            ]
        },
        {
            TaskID: 6,
            TaskName: 'Design',
            StartDate: new Date('02/10/2017'),
            EndDate: new Date('02/14/2017'),
            Duration: 3,
            Progress: 86,
            subtasks: [
                { TaskID: 7, TaskName: 'Software Specification', StartDate: new Date('02/10/2017'), EndDate: new Date('02/12/2017'), Duration: 3, Progress: 60, },
                { TaskID: 8, TaskName: 'Develop prototype', StartDate: new Date('02/10/2017'), EndDate: new Date('02/12/2017'), duration: 3, Progress: 100,},
                { TaskID: 9, TaskName: 'Get approval from customer', startDate: new Date('02/13/2017'), EndDate: new Date('02/14/2017'), Duration: 2, Progress: 100, },
                { TaskID: 10, TaskName: 'Design Documentation', startDate: new Date('02/13/2017'), endDate: new Date('02/14/2017'), duration: 2, Progress: 100, },
                { TaskID: 11, TaskName: 'Design complete', StartDate: new Date('02/14/2017'), EndDate: new Date('02/14/2017'), Duration: 0, Progress: 0,  }
            ]
        }]
     };
   }
   ```

5. To create Gantt with additional features, inject the required modules. The following modules are used to extend Gantt's basic functionality.

* [`Edit`](../api/gantt/#editmodule) : Inject this module to use the editing feature.
* [`Filter`](../api/gantt/#filtermodule) : Inject this module to use the filtering feature.
* [`Sort`](../api/gantt/#sortmodule) : Inject this module to use the sorting feature.
* [`Selection`](../api/gantt/#selectionmodule) : Inject this module to use the selection feature.
* [`Toolbar`](../api/gantt/#toolbar) : Inject this module to use the toolbar items.
* [`DayMarkers`](../api/gantt/#daymarkersmodule) : Inject this module to highlight the days.
  Register the required array of modules under the key `gantt` in the `provide` section.

  > Additional feature modules are available [here](./module)

## Binding Gantt with data

Bind data with the Gantt component by using the [`dataSource`](../api/gantt/#datasource) property. It accepts an array of JavaScript object or the DataManager instance.

```html

<template>
     <div>
        <ejs-gantt ref='gantt' :dataSource="data"></ejs-gantt>
    </div>
</template>
<script>
import { GanttComponent,ColumnsDirective, ColumnDirective, Edit} from '@syncfusion/ej2-vue-gantt';
import "../node_modules/@syncfusion/ej2-base/styles/material.css";
import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-gantt/styles/material.css";

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
import { GanttComponent,ColumnsDirective, ColumnDirective, Edit} from '@syncfusion/ej2-vue-gantt';
import "../node_modules/@syncfusion/ej2-base/styles/material.css";
import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-gantt/styles/material.css";

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
import { GanttComponent,ColumnsDirective, ColumnDirective, Edit} from '@syncfusion/ej2-vue-gantt';
import "../node_modules/@syncfusion/ej2-base/styles/material.css";
import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-gantt/styles/material.css";

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

## Enable Toolbar

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
import { GanttComponent,ColumnsDirective, ColumnDirective,Edit, Selection, Toolbar, DayMarkers} from '@syncfusion/ej2-vue-gantt';
import "../node_modules/@syncfusion/ej2-base/styles/material.css";
import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-gantt/styles/material.css";

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

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :toolbar="toolbar" :columns = "columns" :editSettings= "editSettings"></ejs-gantt>
    </div>
</template>
<script>
import { GanttComponent,ColumnsDirective, ColumnDirective, Edit } from '@syncfusion/ej2-vue-gantt';
import "../node_modules/@syncfusion/ej2-base/styles/material.css";
import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-gantt/styles/material.css";
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
import { GanttComponent, Edit} from '@syncfusion/ej2-vue-gantt';
import "../node_modules/@syncfusion/ej2-base/styles/material.css";
import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-gantt/styles/material.css";
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
import { GanttComponent, ColumnsDirective, ColumnDirective, Edit } from '@syncfusion/ej2-vue-gantt';
import "../node_modules/@syncfusion/ej2-base/styles/material.css";
import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-gantt/styles/material.css";
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
import { GanttComponent,ColumnsDirective, ColumnDirective, Edit} from '@syncfusion/ej2-vue-gantt';
import "../node_modules/@syncfusion/ej2-base/styles/material.css";
import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-gantt/styles/material.css";
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
import { GanttComponent, ColumnsDirective, ColumnDirective} from '@syncfusion/ej2-vue-gantt';
import "../node_modules/@syncfusion/ej2-base/styles/material.css";
import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-gantt/styles/material.css";
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
import { GanttComponent, ColumnsDirective, ColumnDirective, Sort } from '@syncfusion/ej2-vue-gantt';
import "../node_modules/@syncfusion/ej2-base/styles/material.css";
import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-gantt/styles/material.css";
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

## Enable filtering

The filtering feature enables you to view reduced amount of records based on filter criteria. Gantt provides support for menu filtering support for each columns. It can be enabled by setting the [`allowFiltering`](../api/gantt/#allowfiltering) property to `true` along with injecting the `Filter` module module as shown in the following code example. Filtering feature can also be customized using the [`filterSettings`](../api/gantt/filterSettings/) property.

To use Filtering, inject the [`Filter`](../api/gantt/#filtermodule) module in the `provide` section.

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns="columns" :toolbar="toolbar" :allowFiltering= "true" :timelineSettings="timelineSettings" :splitterSettings= "splitterSettings" :labelSettings= "labelSettings" :projectStartDate="projectStartDate" :projectEndDate= "projectEndDate"></ejs-gantt>
    </div>
</template>
<script>
import { GanttComponent, ColumnsDirective, ColumnDirective, Filter, Toolbar } from '@syncfusion/ej2-vue-gantt';
import "../node_modules/@syncfusion/ej2-base/styles/material.css";
import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-gantt/styles/material.css";
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

## Enable Sorting

The sorting feature enables the user to order the records.
It can be enabled by setting [`allowSorting`](../api/gantt/#allowsorting) property to true.
Also, need to inject the `Sort` module in the `provide` section as follow.
If we didn't inject the `Sort` module, then user not able to sort when click on headers.
Sorting feature can be customized using [`sortSettings`](../api/gantt/sortSettings) property.

```html
<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns="columns" :splitterSettings= "splitterSettings" :allowSorting= 'true'></ejs-gantt>
    </div>
</template>
<script>
import { GanttComponent, ColumnsDirective, ColumnDirective, Sort } from '@syncfusion/ej2-vue-gantt';
import "../node_modules/@syncfusion/ej2-base/styles/material.css";
import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-gantt/styles/material.css";

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

## Defining eventmarkers

The [`eventMarkers`](../api/gantt/#eventmarkers) property in Gantt component is used to highlight the important event in Gantt chart part. By using this feature, you can add the lines and label to highlight important days in your project.

To highlight the days, inject the `DayMarkers` module in the `provide` section.

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :eventMarkers="eventMarkers"></ejs-gantt>
    </div>
</template>
<script>
import { GanttComponent, ColumnsDirective, ColumnDirective, Edit, Sort, Filter, Toolbar,DayMarkers } from '@syncfusion/ej2-vue-gantt';
import "../node_modules/@syncfusion/ej2-base/styles/material.css";
import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
import "../node_modules/@syncfusion/ej2-vue-gantt/styles/material.css";
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

## Running the application

Run the application using the following command.

```bash
npm run serve
```

Web server will be initiated, Open the quick start app in the browser at port [`localhost:8080`](http://localhost:8080/).
