---
title: "Custom Tooltip for columns"
component: "TreeGrid"
description: "Learn how to Custom Tooltip for columns."
---

# Custom Tooltip for columns

You can achieve the custom tooltip([`EJ2 Tooltip`](../../tooltip/getting-started)) for Tree Grid by using the [`queryCellInfo`](../api/treegrid/#querycellinfo) event.

Render the ToolTip component for the Tree Grid cells by using the following code in the
[`queryCellInfo`](../api/treegrid/#querycellinfo) event.

```typescript

  tooltip (args) {
    let tooltip = new Tooltip({
        content: args.data[args.column.field].toString();
    }, args.cell);
}

```

{% tab template="treegrid/how-to/default" %}

```html
<template>
<div id="app">
      <ejs-treegrid :dataSource="data" :treeColumnIndex="1" height='300px' :queryCellInfo='queryCellInfoEvent' childMapping="subtasks" ref="treegrid">
        <e-columns>
          <e-column field="taskID" headerText="Task ID" width="70" textAlign="Right"></e-column>
          <e-column field="taskName" headerText="Task Name" width="100"></e-column>
          <e-column field="startDate" headerText="Start Date" format="yMd" width="90" textAlign="Right"></e-column>
          <e-column field="endDate" headerText="Start Date" format="yMd" width="90" textAlign="Right"></e-column>
          <e-column field="duration" headerText="Duration" width="90" textAlign="Right"></e-column>
        </e-columns>
       </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { Tooltip } from "@syncfusion/ej2-popups";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: sampleData,
    };
  },
  methods: {
    queryCellInfoEvent: function (args) {
         let tooltip = new Tooltip({
          content: args.data[args.column.field].toString()
        }, args.cell);
      },
  }
}
</script>

```

{% endtab %}
