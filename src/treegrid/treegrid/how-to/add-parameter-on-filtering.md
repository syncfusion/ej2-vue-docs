---
title: "Customizing Filter Dialog by using additional Parameter"
component: "TreeGrid"
description: "Learn how to customize the filter dialog in Tree Grid by using an additional Parameter."
---

# Customizing filter dialog by using an additional Parameter

You can customize the default settings of the components which are used in Menu filter by using params of filter property in column definition.
In the below sample, TaskID and Duration Columns are numeric columns, while open the filter dialog then you can see that NumericTextBox with spin button is displayed to change/set the filter value. Now using the params option we hide the spin button in NumericTextBox for TaskID Column.

{% tab template="treegrid/how-to/default" %}

```html

<template>
  <div id="app">
      <ejs-treegrid :dataSource="data" :treeColumnIndex="1" height='300px' idMapping='TaskID' parentIdMapping='parentID' :allowFiltering='true' :filterSettings='filterOptions' ref="treegrid">
        <e-columns>
          <e-column field="TaskID" headerText="Task ID" :isPrimaryKey='true' width="70" :filter='filterParams' textAlign="Right"></e-column>
          <e-column field="TaskName" headerText="Task Name" width="100" ></e-column>
          <e-column field="StartDate" headerText="Start Date" format="yMd" width="100" textAlign="Right"></e-column>
          <e-column field="EndDate" headerText="End Date" width="100" format="yMd" textAlign="Right"></e-column>
          <e-column field="Duration" headerText="Duration" width="90" :filter='filterParams' textAlign="Right"></e-column>
          <e-column field="Priority" headerText="Priority" width="90" textAlign="Left"></e-column>
        </e-columns>
       </ejs-treegrid>
  </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Filter } from "@syncfusion/ej2-vue-treegrid";
import { projectData } from "./datasource.js";

Vue.use(TreeGridPlugin);
export default {
  data() {
    return {
      data: projectData,
      filterOptions: {
           type: 'Menu'
      },
      filterParams: { params: {showSpinButton: false}}
    };
  },
  provide: {
    treegrid: [Page, Filter]
  }
}
</script>

```

{% endtab %}
