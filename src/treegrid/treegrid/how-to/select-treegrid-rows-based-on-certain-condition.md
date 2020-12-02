---
title: "Select Tree Grid rows based on certain condition"
component: "TreeGrid"
description: "Learn how to select rows in Tree Grid based on certain condition"
---

# Select Tree Grid rows based on certain condition

You can select the specific row in the Tree Grid based on a certain condition by using the [`selectRows`](../api/treegrid/#selectrows) method in the [`dataBound`](../api/treegrid/#databound) event of Tree Grid.

In the below demo, we have selected the Tree Grid rows only when *Duration* column value greater than *4*.

{% tab template="treegrid/how-to/default" %}

```html
<template>
  <div id="app">
      <ejs-treegrid :dataSource="data" :treeColumnIndex="1" height='300px' idMapping='TaskID' parentIdMapping='parentID' :rowDataBound="rowDataBound" :selectionSettings="selectionOptions"
        :dataBound="dataBound" ref="treegrid">
        <e-columns>
          <e-column field="TaskID" headerText="Task ID" :isPrimaryKey='true' width="70" textAlign="Right"></e-column>
          <e-column field="TaskName" headerText="Task Name" width="100" ></e-column>
          <e-column field="StartDate" headerText="Start Date" format="yMd" width="100" textAlign="Right"></e-column>
          <e-column field="EndDate" headerText="End Date" width="100" format="yMd" textAlign="Right"></e-column>
          <e-column field="Duration" headerText="Duration" width="90" textAlign="Right"></e-column>
          <e-column field="Priority" headerText="Priority" width="90" textAlign="eft"></e-column>
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
      selIndex: [],
      selectionOptions: { type: "Multiple" },
      data: projectData,
    };
  },
  methods: {
    rowDataBound(args) {
       if (args.data["Duration"] > 3) {
        this.selIndex.push(parseInt(args.row.getAttribute("aria-rowindex")));
      }
    },
    dataBound(args) {
      if (this.selIndex.length) {
        this.$refs.treegrid.selectRows(this.selIndex);
        this.selIndex = [];
      }
    }
  },
  provide: {
    treegrid: [Page]
  }
}
</script>

```

{% endtab %}