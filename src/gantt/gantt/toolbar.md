---
title: "Toolbar"
component: "Gantt"
description: "Learn how to use the toolbar and add custom toolbar items in the Essential JS 2 Gantt component"
---

# Toolbar

The Gantt component provides the toolbar support to handle Gantt actions. The [`toolbar`](../api/gantt/#toolbar) property accepts the collection of built-in toolbar items and `ItemModel` objects for custom toolbar items.

To use toolbar feature, inject the `Toolbar` module in the `provide` section.

## Built-in toolbar items

Built-in toolbar items execute standard actions of the Gantt component, and these items can be added to toolbar by defining the [`toolbar`](../api/gantt/#toolbar) as a collection of built-in items. It renders the button with icon and text.

The following table shows built-in toolbar items and its actions.

| Built-in Toolbar Items | Actions |
|------------------------|---------|
| ExpandAll | Expands all the rows.|
| CollapseAll | Collapses all the rows.|
| Add | Adds a new record.|
| Edit | Edits the selected record.|
| Indent | Indent the selected record to one level.|
| Outdent | Outdent the elected record to one level.|
| Update | Updates the edited record.|
| Delete | Deletes the selected record.|
| Cancel | Cancels the edit state.|
| Search | Searches the records by the given key.|
| PrevTimeSpan | Navigate the Gantt timeline to previous time span.|
| NextTimeSpan | Navigate the Gantt timeline to Next time span.|

{% tab template="gantt/toolbar" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :toolbar="toolbar" :editSettings= "editSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Edit, Selection, Toolbar } from "@syncfusion/ej2-vue-gantt";
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
            toolbar: ['Add', 'Edit', 'Delete', 'Cancel', 'ExpandAll', 'CollapseAll','PrevTimeSpan','NextTimeSpan', 'Update', 'Indent', 'Outdent'],
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
      gantt: [ Edit, Selection, Toolbar ]
  }
};
</script>

```

{% endtab %}

> * The [`toolbar`](../api/gantt/#toolbar) has options to define both built-in and custom toolbar items.

## Custom toolbar items

Custom toolbar items can be added to the toolbar by defining the [`toolbar`](../api/gantt/#toolbar) property as a collection of `ItemModels`.
Actions for this customized toolbar items are defined in the [`toolbarClick`](../api/gantt/#toolbarclick) event.

By default, the custom toolbar items are at left position. You can change the position by using the `align` property. In the following sample, the `Quick Filter` toolbar item is positioned at right.

{% tab template="gantt/toolbar" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :toolbarClick="toolbarClick" :columns="columns" :toolbar="toolbar" :allowFiltering='true'></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, Filter } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
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
            toolbarClick: (args: ClickEventArgs) => {
                if (args.item.id === 'toolbarfilter') {
                    var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttObj.filterByColumn('TaskName', 'startswith', 'Identify');
                }
            },
            toolbar: [{text: 'Quick Filter', tooltipText: 'Quick Filter', id: 'toolbarfilter',align:'Right', prefixIcon: 'e-quickfilter' }],
      };
  },
  provide: {
      gantt: [ Toolbar, Filter  ]
  }
};
</script>
    <style>
        .e-quickfilter::before {
            content: '\e7ee';
        }
    </style>

```

{% endtab %}

> * The [`toolbar`](../api/gantt/#toolbar) has options to define both built-in and custom toolbar items.
> * If a toolbar item does not match the built-in items, it will be treated as a custom toolbar item.

## Built-in and custom items in toolbar

The Gantt component has an option to use both built-in and custom toolbar items at the same time.

In the following example, the `ExpandAll` and `CollapseAll` are built-in toolbar items and `Test` is the custom toolbar item.

{% tab template="gantt/toolbar" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns="columns" :toolbarClick="toolbarClick" :toolbar="toolbar" :allowFiltering='true'></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, Filter  } from "@syncfusion/ej2-vue-gantt";
import { EmitType } from '@syncfusion/ej2-base';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
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
            toolbarClick:  (args: ClickEventArgs) => {
                if (args.item.text === 'Click') {
                    alert("Custom toolbar click...");
                }
            },
            toolbar: ['ExpandAll', 'CollapseAll', { text: 'Click', tooltipText: 'Click',id: 'Click' }],
            };
  },
  provide: {
      gantt: [ Toolbar, Filter ]
  },
};
</script>

```

{% endtab %}

## Enable/disable toolbar items

You can enable or disable the toolbar items by using the `enableItems` method.

{% tab template="gantt/toolbar" %}

```html

<template>
     <div>
     <ejs-button id="enable" cssClass="e-info" v-on:click.native="enable">Enable</ejs-button>
     <ejs-button id="disable" cssClass="e-info" v-on:click.native="disable">Disable</ejs-button>
     <br>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowFiltering='true'></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, Filter  } from "@syncfusion/ej2-vue-gantt";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { editingData } from './data-source.js';
Vue.use(GanttPlugin);
Vue.use(ButtonPlugin);
export default {
  data: function() {
      return{
            data: editingData,
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
            toolbar: ['QuickFilter', 'ClearFilter'],
            toolbarClick:  (args: ClickEventArgs) => {
                if (args.item.text === 'QuickFilter') {
                    var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttChart.filterByColumn('TaskName', 'startswith', 'Identify');
                }
                if (args.item.text === 'ClearFilter') {
                    var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttChart.clearFiltering();
                }
            },
      };
  },
  provide: {
      gantt: [ Toolbar, Filter ]
  },
   methods: {
      enable: function(e){
          var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
          ganttChart.toolbarModule.enableItems([ganttChart.element.id + '_QuickFilter', ganttChart.element.id + '_ClearFilter'], true);// enable toolbar items.
      },
      disable: function(e){
          var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
          ganttChart.toolbarModule.enableItems([ganttChart.element.id + '_QuickFilter', ganttChart.element.id + '_ClearFilter'], false);// disable toolbar items.
      },
  },
};
</script>

```

{% endtab %}

## Add input elements in toolbar

In the Gantt toolbar, you can add EJ2 editor elements like numeric text box, drop-down list, and date picker controls. The following code snippets demonstrates how to add EJ2 editors to the Gantt toolbar.

{% tab template="gantt/toolbar" %}

```html

<template>
     <div>
     <ejs-numerictextbox id="inputEle" format='c2' value='1' width='150'></ejs-numerictextbox>
     <br>
    <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar } from "@syncfusion/ej2-vue-gantt";
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";
import { projectNewData } from './data-source.js';
Vue.use(GanttPlugin);
Vue.use(NumericTextBoxPlugin);
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
      };
  },
  provide: {
      gantt: [Toolbar ]
  }
};
</script>

```

{% endtab %}
