---
title: "Display null date values at always"
component: "TreeGrid"
description: "Learn how to display null date values at always."
---

# Display the null date values at bottom of the TreeGrid while perform sorting

By default the null values are displayed at bottom of the Tree Grid row while perform sorting in ascending order. As well as this values are displayed at top of the Tree Grid row while perform sorting with descending order. But you can customize this default order to display the null values at always bottom row of the Tree Grid by using [`column.sortComparer`](../api/treegrid/column/#sortcomparer) method.

In the below demo we have displayed the null date values at bottom of the Grid row while sorting the **StartDate** column in both ways.

{% tab template="treegrid/how-to/default" %}

```html
<template>
  <div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex="1" height='300px' :allowSorting='true' :actionBegin='actionBegin' idMapping='TaskID' parentIdMapping='parentID' ref="treegrid">
        <e-columns>
          <e-column field="TaskID" headerText="Task ID" :isPrimaryKey='true' width="70" textAlign="Right"></e-column>
          <e-column field="TaskName" headerText="Task Name" width="70" ></e-column>
          <e-column field="StartDate" headerText="Start Date" format="yMd" width="70" :sortComparer='sortComparer' textAlign="Right"></e-column>
          <e-column field="EndDate" headerText="End Date" width="100" format="yMd" textAlign="Right"></e-column>
          <e-column field="Duration" headerText="Duration" width="90" textAlign="Right"></e-column>
          <e-column field="Priority" headerText="Priority" width="90" textAlign="Right"></e-column>
        </e-columns>
       </ejs-treegrid>
  </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Sort } from "@syncfusion/ej2-vue-treegrid";
import { Data } from "./datasource.js";

Vue.use(TreeGridPlugin);
let action;

export default {
  data() {
    return {
      data: Data,
    };
  },
  methods: {
    sortComparer: function(reference, comparer) {
        let sortAsc = action === "Ascending" ? true : false;
        if (sortAsc && reference === null) {
            return 1;
        }
        else if (sortAsc && comparer === null) {
            return -1;
        }
        else if (!sortAsc && reference === null) {
            return -1;
        }
        else if (!sortAsc && comparer === null) {
            return 1;
        } else {
            return reference - comparer;
        }
    },
    actionBegin: function(args) {
        if (args.requestType === "sorting") {
            action = args.direction;
        }
    }
  },
  provide: {
    treegrid: [Page, Sort]
  }
}
</script>

```

{% endtab %}
