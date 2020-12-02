---
title: "How To"
component: "Gantt"
description: "Learn how to add custom fields in the General tab in Add/Edit in the JS 2 Gantt component."
---

# Add Custom Fields in the General Tab in Add/Edit Dialog

Generally in Gantt, Custom fields are displayed in the Custom Tab of the Add/Edit dialogs. However, they can be included in the General Tab of Add/Edit Dialog Box using `actionBegin` and `actionComplete` events. These events are used to append the custom field to the dialog box. The following code snippets demonstrate the solution.

{% tab template="gantt/how-to/customfields" %}

```html

<template>
  <div id="app">
    <ejs-gantt ref="gantt" :dataSource="data" id="GanttContainer" :taskFields="taskFields" :height="height" :editSettings="editSettings"
      :editDialogFields="editDialogFields" :addDialogFields= "addDialogFields" :toolbar= "toolbar" :actionBegin="actionBegin" :actionComplete="actionComplete" >
      <e-columns>
        <e-column field="TaskID" headerText="Task ID" textAlign="Left" width="100"></e-column>
        <e-column field="TaskName" headerText="Task Name" width="150"></e-column>
        <e-column field="StartDate" headerText="Start Date" width="150"></e-column>
        <e-column field="EndDate" headerText="End Date" width="150"></e-column>
        <e-column field="Duration" headerText="Duration" width="150"></e-column>
        <e-column field="Progress" headerText="Progress" width="150"></e-column>
        <e-column field="CustomField" headerText="CustomField" width="150"></e-column>
      </e-columns>
    </ejs-gantt>
  </div>
</template>

<script>
import Vue from "vue";
import { GanttPlugin, Edit, Toolbar, Selection } from "@syncfusion/ej2-vue-gantt";
import { CheckBox } from "@syncfusion/ej2-buttons";
import { TextBox, NumericTextBox, MaskedTextBox } from "@syncfusion/ej2-inputs";
import { DatePicker, DateTimePicker } from "@syncfusion/ej2-calendars";
import { DropDownList } from "@syncfusion/ej2-dropdowns";
import { editingData } from './data-source.js';

Vue.use(GanttPlugin);
var divElement;
var inputs = {
  booleanedit: CheckBox,
  dropdownedit: DropDownList,
  datepickeredit: DatePicker,
  datetimepickeredit: DateTimePicker,
  maskededit: MaskedTextBox,
  numericedit: NumericTextBox,
  stringedit: TextBox
};
export default {
  data: function() {
    return {
      data: editingData,
      height: "450px",
      taskFields: {
        id: "TaskID",
        name: "TaskName",
        startDate: "StartDate",
        endDate: "EndDate",
        duration: "Duration",
        progress: "Progress",
        child: "subtasks"
      },
      editSettings: {
        allowAdding: true,
        allowEditing: true,
        allowDeleting: true,
        mode: "Auto"
      },
      toolbar: ['Add', 'Edit', 'Update', 'Delete', 'Cancel', 'ExpandAll', 'CollapseAll'],
      editDialogFields: [
        { type: "General", headerText: "General" },
        { type: "Dependency" },
        { type: "Resources" },
        { type: "Notes" }
      ],
      addDialogFields : [
        { type: 'General', headerText: 'General' },
        { type: 'Dependency' },
        { type: "Resources" },
        { type: "Notes" }
       ],
      actionBegin: function(args) {
        if (args.requestType === "beforeOpenEditDialog" || args.requestType === "beforeOpenAddDialog" ) {
          var column = this.columnByField["CustomField"];
          divElement = this.createElement("div", {
            className: "e-edit-form-column"
          });
          var inputElement;
          inputElement = this.createElement("input", {
            attrs: {
              type: "text",
              id: this.controlId + "" + column.field,
              name: column.field,
              title: column.field
            }
          });
          divElement.appendChild(inputElement);
          var input = {
            enabled: true,
            floatLabelType: "Auto",
            placeholder: "CustomField",
            value: args.rowData.CustomField
          };
          var inputObj = new inputs[column.editType](input);
          inputObj.appendTo(inputElement);
        }
      },
      actionComplete: function(args) {
        if (args.requestType === "openEditDialog" || args.requestType === "openAddDialog") {
          var generalTab = document.getElementById(
            this.controlId + "GeneralTabContainer"
          );
          generalTab.appendChild(divElement);
        }
      }
    };
  },
  provide: {
    gantt: [Edit, Toolbar, Selection]
  },
  methods: {}
};
</script>

```

{% endtab %}