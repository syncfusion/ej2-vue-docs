---
title: "Provide custom data source and enabling filtering to DropDownList"
component: "TreeGrid"
description: "Learn how to Provide custom data source and enabling filtering to DropDownList."
---

# Provide custom data source and enabling filtering to DropDownList

You can provide data source to the DropDownList by using the **params** of [`columns.edit`](../api/treegrid/column/#edit) property.

While setting new data source using edit params, you must specify a new **query** property for the DropDownList as follows,

```typescript
    priorityParams: {
        params: {
          allowFiltering: true,
          dataSource: priorityData,
          fields: { text: "priorityName", value: "priorityName" },
          query: new Query(),
          actionComplete: () => false
        }
    };
```

You can also enable filtering for the DropDownList by passing the [`allowFiltering`](../../api/drop-down-list/#allowfiltering) as **true** to the edit params.

In the below demo, DropDownList is rendered with custom [`dataSource`](../../api/drop-down-list/#datasource) for the *Priority* column and enabled filtering to search DropDownList items.

{% tab template="treegrid/how-to/default" %}

```html
<template>
  <div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex="1" height='250px' idMapping='TaskID' parentIdMapping='parentID' ref="treegrid" :editSettings="editSettings" :toolbar="toolbar">
        <e-columns>
          <e-column field="TaskID" headerText="Task ID" :isPrimaryKey='true' width="70" textAlign="Right"></e-column>
          <e-column field="TaskName" headerText="Task Name" width="100" ></e-column>
          <e-column field="StartDate" headerText="Start Date" format="yMd" editType= 'datepickeredit' width="100" textAlign="Right"></e-column>
          <e-column field="EndDate" headerText="End Date" width="100" format="yMd" editType='datepickeredit' textAlign="Right"></e-column>
          <e-column field="Priority" headerText="Priority" width="90" editType= 'dropdownedit' textAlign="Left" :edit="priorityParams"></e-column>
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
      { priorityName: 'Low', priorityId: '3' },
      { priorityName: 'Critical', priorityId: '4' },
      { priorityName: 'Breaker', priorityId: '5' }
  ];
Vue.use(TreeGridPlugin);
export default {
  data() {
    return {
      data: projectData,
      editSettings: { allowAdding:true, allowDeleting:true, allowEditing: true, mode: 'Row' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      priorityParams: {
        params: {
          allowFiltering: true,
          dataSource: priorityData,
          fields: { text: "priorityName", value: "priorityName" },
          query: new Query(),
          actionComplete: () => false
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