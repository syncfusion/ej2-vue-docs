---
title: "Customize Pager DropDown"
component: "TreeGrid"
description: "Learn how to Customize Pager DropDown."
---

# Customize pager DropDown

To customize default values of pager dropdown, you need to define [`pageSizes`](../api/treegrid/pageSettings/#pagesizes) as array of strings.

{% tab template="treegrid/how-to/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex="1" height='250px' childMapping="subtasks" ref="treegrid" :allowPaging="true"
        :pageSettings="pageSettings">
        <e-columns>
          <e-column field="taskID" headerText="Task ID" width="70" textAlign='Right'></e-column>
          <e-column field="taskName" headerText="Task Name" width="100" ></e-column>
          <e-column field="startDate" headerText="Start Date" format="yMd" width="90" textAlign='Right'></e-column>
          <e-column field="endDate" headerText="Start Date" format="yMd" width="90" textAlign='Right'></e-column>
          <e-column field="duration" headerText="Duration" width="90" textAlign='Right'></e-column>
          <e-column field="progress" headerText="Progress" width="90" textAlign='Right'></e-column>
          <e-column field="priority" headerText="Priority" width="90"></e-column>
        </e-columns>
       </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: sampleData,
      pageSettings: {pageSizes: ['5','10','All']}
    };
  },
  provide: {
    treegrid: [Page]
  }
}
</script>

```

{% endtab %}
