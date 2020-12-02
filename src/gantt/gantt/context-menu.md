---
title: "Context Menu"
component: "Gantt"
description: "Learn how to use the context menu and add custom context menu items in the Essential JS 2 Gantt control."
---

# Context menu

The Gantt control allows you to perform quick actions by using context menu. When right-clicking the context menu, the context menu options are shown. To enable this feature, set the [`enableContextMenu`](../api/gantt/#enablecontextmenu) to true. The default context menu options are enabled using the [`editSettings`](../api/gantt/#editsettings) property. The context menu options can be customized using the [`contextMenuItems`](../api/gantt/#contextmenuitems) property.

To use the context menu, inject the [`ContextMenu`](../api/gantt/#contextmenumodule) module in the `provide` section.

The default items are listed in the following table.

Items| Description
----|----
`AutoFit`|  Auto-fits the current column.
`AutoFitAll` | Auto-fits all columns.
`SortAscending` | Sorts the current column in ascending order.
`SortDescending` | Sorts the current column in descending order.
`TaskInformation`|  Edits the current task.
`Add` | Adds a new row to the Gantt.
`Indent` | Indent the selected record to one level.
`Outdent` | Outdent the selected record to one level.
`DeleteTask` | Deletes the current task.
`Save` | Saves the edited task.
`Cancel` | Cancels the edited task.
`DeleteDependency` | Deletes the current dependency task link.
`Convert` | Converts current task to milestone or vice-versa.

{% tab template="gantt/contextmenu" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="contextMenu" :dataSource="data" :taskFields = "taskFields" :height = "height" :editSettings="editSettings" :enableContextMenu="true" :allowSorting="true" :allowResizing= "true"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, ContextMenu, Edit, Sort, Resize, Selection } from "@syncfusion/ej2-vue-gantt";
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
            dependency: 'Predecessor',
            child: 'subtasks'
        },
        editSettings: {
        allowAdding: true,
        allowEditing: true,
        allowDeleting: true
        }
    };
  },
  provide: {
      gantt: [ ContextMenu, Edit, Sort, Resize, Selection]
  }
};
</script>

```

{% endtab %}

## Custom context menu items

The custom context menu items can be added by defining the [`contextMenuItems`](../api/gantt/#contextmenuitems) as a collection of [`contextMenuItemModel`](../api/grid/contextMenuItemModel/).
Actions for the customized items can be defined in the [`contextMenuClick`](../api/gantt/#contextmenuclick) event and the visibility of customized items can be defined in the [`contextMenuOpen`](../api/gantt/#contextmenuopen) event.

To create custom context menu items for header area, define the target property as `.e-gridheader`.

The following sample shows context menu item for parent rows to expand or collapse child rows in the content area and a context menu item to hide columns in the header area.

{% tab template="gantt/customContextMenu" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="customContextMenu" :dataSource="data" :taskFields = "taskFields" :height = "height" :editSettings="editSettings" :enableContextMenu="true" :allowSorting="true" :allowResizing= "true" :contextMenuItems="contextMenuItems" :contextMenuClick = "contextMenuClick" :contextMenuOpen="contextMenuOpen"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, ContextMenu, Edit, Sort, Resize, Selection } from "@syncfusion/ej2-vue-gantt";
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
            dependency: 'Predecessor',
            child: 'subtasks'
        },
        editSettings: {
        allowAdding: true,
        allowEditing: true,
        allowDeleting: true
        },
        contextMenuItems: ['AutoFitAll', 'AutoFit', 'TaskInformation', 'DeleteTask', 'Save', 'Cancel', 'SortAscending', 'SortDescending', 'Add', 'DeleteDependency', 'Convert',
        { text: 'Collapse the Row', target: '.e-content', id: 'collapserow' },
        { text: 'Expand the Row', target: '.e-content', id: 'expandrow' },
        { text: 'Hide Column', target: '.e-gridheader', id: 'hidecols' }
        ],
    };
  },
  provide: {
      gantt: [ ContextMenu, Edit, Sort, Resize, Selection]
  },
  methods: {
        contextMenuClick: function (args) {
        var record = args.rowData;
        var ganttObj = document.getElementById('customContextMenu').ej2_instances[0];
        if (args.item.id === 'collapserow') {
            ganttObj.collapseByID(Number(record.ganttProperties.taskId));
            }
        if (args.item.id === 'expandrow') {
            ganttObj.expandByID(Number(record.ganttProperties.taskId));
            }
        if (args.item.id === 'hidecols') {
            ganttObj.hideColumn(args.column.headerText);
        }
        },
        contextMenuOpen: function (args) {
        var record = args.rowData;
            if (args.type !== 'Header') {
                if (!record.hasChildRecords) {
                    args.hideItems.push('Collapse the Row');
                    args.hideItems.push('Expand the Row');
                } else {
                    if(record.expanded){
                    args.hideItems.push("Expand the Row");
                    } else {
                    args.hideItems.push("Collapse the Row");
                    }
                }
            }
        }
    }
};
</script>

```

{% endtab %}

> You can show an specific item in context menu for header/content area in the Gantt control by defining the `target` property.