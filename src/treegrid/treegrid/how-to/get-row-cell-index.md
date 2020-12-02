---
title: "Get specific row and cell index in Tree Grid"
component: "TreeGrid"
description: "Learn how to get specific row and cell index in Tree Grid."
---

# Get specific row and cell index in Tree Grid

You can get the specific row and cell index of the Tree Grid by using [`rowSelected`](../api/treegrid/#rowselected) event of the treegrid. Here, we can get the row and cell index by using *aria-rowindex* (get row Index from *tr* element) and *aria-colindex* (column index from *td* element) attribute.

{% tab template="treegrid/how-to/default" %}

```html
<template>
  <div id="app">
      <ejs-treegrid :dataSource="data" :treeColumnIndex="1" height='300px' idMapping='TaskID' parentIdMapping='parentID' :rowSelected='rowSelected' ref="treegrid">
        <e-columns>
          <e-column field="TaskID" headerText="Task ID" :isPrimaryKey='true' width="70" textAlign="Right"></e-column>
          <e-column field="TaskName" headerText="Task Name" width="100" ></e-column>
          <e-column field="StartDate" headerText="Start Date" format="yMd" width="100" textAlign="Right"></e-column>
          <e-column field="EndDate" headerText="End Date" width="100" format="yMd" textAlign="Right"></e-column>
          <e-column field="Duration" headerText="Duration" width="90" textAlign="Right"></e-column>
          <e-column field="Priority" headerText="Priority" width="90" textAlign="Left"></e-column>
        </e-columns>
       </ejs-treegrid>
  </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { projectData } from "./datasource.js";

Vue.use(TreeGridPlugin);
export default {
  data() {
    return {
      data: projectData,
    };
  },
  methods: {
    rowSelected(args) {
        alert("row index: "+args.row.getAttribute('aria-rowindex'));
        alert("column index: "+args.target.closest('td').getAttribute('aria-colindex'));
    }
  },
  provide: {
    treegrid: [Page]
  }
}
</script>

```

{% endtab %}
