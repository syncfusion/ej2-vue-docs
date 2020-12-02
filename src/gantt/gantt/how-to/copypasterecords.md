---
title: "How To"
component: "Gantt"
description: "Learn how to copy and paste records in Gantt control."
---

# Copy and Paste records in Gantt

You can copy and paste a record in the Gantt chart by using the `addRecord` method and `custom context menu`. It is also possible to copy and paste the parent record with multiple hierarchical child records on the required position.

{% tab template="gantt/how-to/copypasterecords" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="customContextMenu" :dataSource="data" :taskFields = "taskFields" :height = "height" :editSettings="editSettings" :enableContextMenu="true" :contextMenuItems="contextMenuItems" :contextMenuClick = "contextMenuClick" :contextMenuOpen= "contextMenuOpen" :addChildRecords= "addChildRecords"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, ContextMenu, Edit, Selection } from "@syncfusion/ej2-vue-gantt";
import { editingData } from './data-source.js';
Vue.use(GanttPlugin);
var copiedRecord;
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
        contextMenuItems: [{ text: 'Copy', target: '.e-content', id: 'copy' },
        { text: 'Paste', target: '.e-content', id: 'paste' }
        ],
    };
  },
  provide: {
      gantt: [ ContextMenu, Edit, Selection]
  },
  methods: {
        contextMenuClick: function (args) {
        var gantt = document.getElementById('customContextMenu').ej2_instances[0];
        if (args.item.id === 'copy') {
            copiedRecord = args.rowData;
            copiedRecord.taskData.TaskID = gantt.currentViewData.length + 1;
        }
        if (args.item.id === 'paste') {
            gantt.addRecord(copiedRecord.taskData,'Below',args.rowData.index);
            if(copiedRecord.hasChildRecords) {
                addChildRecords(copiedRecord, args.rowData.index + 1);
            }
            copiedRecord = undefined;
        }
        },
        contextMenuOpen: function (args) {
        if (args.type !== 'Header') {
            if (copiedRecord) {
                args.hideItems.push('Copy');
            } else {
                args.hideItems.push('Paste');
             }
        }
        },
        addChildRecords(record, index) {
          for(var i=0; i<record.childRecords.length; i++) {
          var childRecord = record.childRecords[i];
          childRecord.taskData.TaskID = gantt.currentViewData.length + 1;
          gantt.addRecord(childRecord.taskData,'Child',index);
          if(childRecord.hasChildRecords) {
              addChildRecords(childRecord, index + (i+1));
          }
    }
  }
    }
};
</script>

```

{% endtab %}