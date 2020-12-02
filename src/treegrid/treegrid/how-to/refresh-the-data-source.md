---
title: "How To"
component: "TreeGrid"
description: "Learn how to customize the Essential JS 2 Tree Grid."
---

# How To

## How to refresh the datasource

You can add/delete the datasource records through an external button. To reflect the datasource changes in Tree Grid, you need to assign the modified data to dataSource property.

Please follow the below steps to refresh the Tree Grid after datasource change.

**Step 1**:

Add/delete the datasource record by using the following code.

```typescript

    let customData = {
        TaskID: 99,
        TaskName: "New Data",
        StartDate: new Date("02/03/2017"),
        EndDate: new Date("02/03/2017"),
        Duration: 10
      };

    // Added New Record.
    this.data.unshift(customData);

    // Delete record.
    this.data.splice(selectedRow, 1);

```

**Step 2**:

Refresh the Tree Grid after the datasource change by assign the modified data to dataSource property.

```typescript
      this.data = [...this.data];  // Refresh the TreeGrid.

```

{% tab template="treegrid/how-to/default" %}

```html

<template>
    <div id="app">
        <div>
            <ejs-button  iconCss="e-icons e-play-icon" cssClass="e-flat" :isPrimary="true" :isToggle="true" v-on:click.native="Add">Add</ejs-button>
            <ejs-button  iconCss="e-icons e-play-icon" cssClass="e-flat" :isPrimary="true" :isToggle="true" v-on:click.native="Delete">Delete</ejs-button>
             <ejs-treegrid :dataSource="data" :treeColumnIndex="1" height='210px' idMapping= 'TaskID' parentIdMapping='parentID' ref="treegrid" :editSettings="editSettings" :toolbar="toolbar">
              <e-columns>
               <e-column field="TaskID" headerText="Task ID" :isPrimaryKey='true' width="70" textAlign="Right"></e-column>
               <e-column field="TaskName" headerText="Task Name" width="100" ></e-column>
               <e-column field="StartDate" headerText="Start Date" format="yMd" width="100" textAlign="Right"></e-column>
               <e-column field="EndDate" headerText="Start Date" format="yMd" width="100" textAlign="Right"></e-column>
               <e-column field="Duration" headerText="Duration" width="90" textAlign="Right"></e-column>
              </e-columns>
            </ejs-treegrid>
          </div>
    </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-treegrid";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { projectData } from './datasource.js';

Vue.use(TreeGridPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      data: projectData,
      editSettings: { allowAdding:true, allowDeleting:true, allowEditing: true },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
  },
  methods: {
    Add() {
      let customData = {
        TaskID: 99,
        TaskName: "New Data",
        StartDate: new Date("02/03/2017"),
        EndDate: new Date("02/03/2017"),
        Duration: 10
      };
      this.data.unshift(customData);
      this.data = [...this.data];
    }
    Delete(){
     let selectedRow = this.$refs.treegrid.getSelectedRowIndexes().length;
     let selectedRowIndex = this.$refs.treegrid.getSelectedRowIndexes()[0];
       if (selectedRow > 0) {
         this.data.splice(selectedRowIndex, 1);
        }
       else {
          alert("No records selected for delete operation");
       }
       this.data = [...this.data];
      }
    }
  provide: {
    treegrid: [Page, Edit, Toolbar]
  },
}
</script>


```

{% endtab %}
