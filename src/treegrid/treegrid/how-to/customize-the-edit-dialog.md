---
title: "Customize the Edit Dialog"
component: "TreeGrid"
description: "Learn how to customize the Edit Dialog."
---

# Customize the Edit dialog

You can customize the appearance of the edit dialog in the [`actionComplete`](../api/treegrid/#actioncomplete) event based on **requestType** as **beginEdit** or **add**.

In the below example, we have changed the dialog's header text for editing and adding records.

{% tab template="treegrid/how-to/default" %}

```html

<template>
    <div id="app">
        <div>
             <ejs-treegrid :dataSource="data" :treeColumnIndex="1" height='250px' :actionComplete='actionComplete' childMapping="subtasks" ref="treegrid" :editSettings="editSettings" :toolbar="toolbar">
               <e-columns>
                <e-column field="taskID" :isPrimaryKey="true" headerText="Task ID" width="70" textAlign="Right"></e-column>
                <e-column field="taskName" headerText="Task Name" width="100"></e-column>
                <e-column field="startDate" headerText="Start Date" format="yMd" width="90" textAlign="Right"></e-column>
                <e-column field="endDate" headerText="Start Date" format="yMd" width="90" textAlign="Right"></e-column>
                <e-column field="duration" headerText="Duration" width="90" textAlign="Right"></e-column>
               </e-columns>
             </ejs-treegrid>
            </div>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from './datasource.js';

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: sampleData,
      editSettings: { allowAdding:true, allowDeleting:true, allowEditing: true, mode: 'Dialog' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
  },
  methods: {
    actionComplete(args) {
        if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {
            let dialog = args.dialog;
            dialog.height = 400;
            // change the header of the dialog
            dialog.header = args.requestType === 'beginEdit' ? 'Record of ' + args.rowData['taskName'] : 'New Record';
        }
    }
  },
  provide: {
    treegrid: [Page, Edit, Toolbar]
  }
}
</script>

```

{% endtab %}