---
title: "Display ForeignKey value at initial rendering in Tree Grid"
component: "TreeGrid"
description: "Learn how to display ForeignKey value at initial rendering in Tree Grid."
---

# Display ForeignKey value at initial rendering in Tree Grid

Since Tree Grid Databinding concept is of hierarchy relationship, we do not provide in-built support for foreignkey datasource.

To display the foreignKey value at initial rendering, we can use the [`queryCellInfo`](../api/treegrid/#querycellinfo) event of the treegrid and also by using the [`editType`](../api/treegrid/column/#edittype) and [`columns.edit`](../api/treegrid/column/#edit) properties of TreeGrid Column, we can render Dropdownlist with external or foreign dataSource.

{% tab template="treegrid/how-to/default" %}

```html
<template>
  <div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex="1" height='260px' :allowSorting='true' :queryCellInfo='queryCellInfo' childMapping='Children' :editSettings="editSettings" :toolbar="toolbar"  ref="treegrid">
        <e-columns>
         <e-column field="EmpID" headerText="Emp ID" :isPrimaryKey='true' width="70" textAlign="Right"></e-column>
          <e-column field="Name" headerText="Employee Name" width="70" ></e-column>
          <e-column field="Contact" headerText="Contact" width="90" textAlign="Right"></e-column>
          <e-column field="DOB" headerText="DOB" width="100" format="yMd" editType='datepickeredit' textAlign="Right"></e-column>
          <e-column field="EmployeeID" headerText="EmployeeID" width="70" editType= 'dropdownedit' :edit="employeeParams" ></e-column>
          <e-column field="Country" headerText="Country" width="90" textAlign="Left"></e-column>
       </ejs-treegrid>
  </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-treegrid";
import { textData, dropData } from "./datasource.js";
import { DropDownList } from "@syncfusion/ej2-dropdowns";
import { Query } from '@syncfusion/ej2-data';

Vue.use(TreeGridPlugin);
export default {
   data() {
    return {
      data: textData,
      editSettings: { allowAdding:true, allowDeleting:true, allowEditing: true },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      employeeParams: {
        params: {
          dataSource: dropData,
          fields: { text: "EmployeeName", value: "EmployeeID"},
          query: new Query()
        }
      },
    };
  },
  methods: {
    queryCellInfo: function(args) {
      if (args.column.field === "EmployeeID") {
       for (var i = 0; i < dropData.length; i++) {
          let data = args.data;
          if ((data[args.column.field]).toString() === dropData[i]["EmployeeID"]) {
            args.cell.innerText = dropData[i]["EmployeeName"]; // assign the foreignkey field value to the innertext
          }
        }
      }
    }
  },
  provide: {
    treegrid: [Page,Edit, Toolbar]
  }
</script>

```

{% endtab %}
