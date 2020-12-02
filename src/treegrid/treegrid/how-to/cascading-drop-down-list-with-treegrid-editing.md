---
title: "Cascading DropDownList with Tree Grid editing"
component: "TreeGrid"
description: "Learn how to Cascading DropDownList with Tree Grid editing."
---

# Cascading DropDownList with Tree Grid editing

You can achieve the Cascading DropDownList with Tree Grid Editing by using the Cell Edit Template feature.

In the below demo, Cascading DropDownList rendered for **Priority** and **Duration** column.

{% tab template="treegrid/how-to/default" %}

```html
<template>
  <div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex="1" height='250px' idMapping= 'TaskID' parentIdMapping='parentID' ref="treegrid" :editSettings="editSettings" :toolbar="toolbar">
        <e-columns>
          <e-column field="TaskID" headerText="Task ID" :isPrimaryKey='true' width="70" textAlign="Right"></e-column>
          <e-column field="TaskName" headerText="Task Name" width="100" ></e-column>
          <e-column field="StartDate" headerText="Start Date" format="yMd" editType= 'datepickeredit' width="100" textAlign="Right"></e-column>
          <e-column field="EndDate" headerText="End Date" width="100" format="yMd" editType='datepickeredit' textAlign="Right"></e-column>
          <e-column field="Priority" headerText="Priority" width="90" editType='dropdownedit' textAlign="Left" :edit="priorityParams"></e-column>
          <e-column field="Duration" headerText="Duration" width="90" editType= 'dropdownedit' textAlign="Right" :edit="durationParams"></e-column>
          <e-column field="Progress" headerText="Progress" width="90" textAlign="Right"></e-column>
        </e-columns>
       </ejs-treegrid>
  </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-treegrid";
import { projectData } from "./datasource.js";
import { DropDownList } from "@syncfusion/ej2-dropdowns";
import { Query } from '@syncfusion/ej2-data';

let priorityData = [
      { priorityName: 'Normal', priorityId: '1' },
      { priorityName: 'High', priorityId: '2' },
  ];

let durationData = [
    { durationValue: 2, priorityId: '1', durationId: 2 },
    { durationValue: 3, priorityId: '1', durationId: 3 },
    { durationValue: 4, priorityId: '1', durationId: 4 },
    { durationValue: 11, priorityId: '2', durationId: 11 },
    { durationValue: 15, priorityId: '2', durationId: 15 },
    { durationValue: 20, priorityId: '2', durationId: 20 }
  ];
let priorityElem, durationElem, priorityObj, durationObj;
Vue.use(TreeGridPlugin);
export default {
  data() {
    return {
      data: projectData,
      editSettings: { allowAdding:true, allowDeleting:true, allowEditing: true, mode: 'Row' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      priorityParams: {
        create: () => {
          priorityElem = document.createElement("input");
          return priorityElem;
        },
        read: () => {
          return priorityObj.text;
        },
        destroy: () => {
          priorityObj.destroy();
        },
        write: () => {
          priorityObj = new DropDownList({
            dataSource: priorityData,
            fields: { value: "priorityId", text: "priorityName" },
            floatLabelType: "Never",
            placeholder: "Select a Priority",
            change: () => {
              durationObj.enabled = true;
              let tempQuery = new Query().where(
                "priorityId",
                "equal",
                priorityObj.value
              );
              durationObj.query = tempQuery;
              durationObj.text = null;
              durationObj.dataBind();
            }
          });
          priorityObj.appendTo(priorityElem);
        }
      },
      durationParams: {
        create: () => {
          durationElem = document.createElement("input");
          return durationElem;
        },
        destroy: () => {
          durationObj.destroy();
        },
        read: () => {
          return durationObj.text;
        },
        write: () => {
          durationObj = new DropDownList({
            dataSource: durationData,
            enabled: false,
            fields: { value: "durationId", text: "durationValue" },
            floatLabelType: "Never",
            placeholder: "Select a duration"
          });
          durationObj.appendTo(durationElem);
        }
      },
    };
  },
  provide: {
    treegrid: [Page, Edit, Toolbar]
  }
}
</script>

```

{% endtab %}
