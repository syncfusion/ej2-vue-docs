---
title: "Customize the icon for column menu"
component: "TreeGrid"
description: "Learn how to customize the icon for column menu."
---

# Customize the icon for column menu

You can customize the column menu icon by overriding the default Tree Grid class **.e-icons.e-columnmenu** with a custom property **content** as mentioned below,

```css
    .e-treegrid .e-columnheader .e-icons.e-columnmenu::before {
        content: "\e903";
    }
```

In the below sample, Tree Grid is rendered with a customized column menu icon.

{% tab template="treegrid/how-to/default" %}

```html
<template>
  <div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex="1" height='300px' :showColumnMenu='true' childMapping="subtasks" ref="treegrid">
        <e-columns>
          <e-column field="taskID" headerText="Task ID" width="70" textAlign="Right"></e-column>
          <e-column field="taskName" headerText="Task Name" width="100" ></e-column>
          <e-column field="startDate" headerText="Start Date" format="yMd" width="90" textAlign="Right"></e-column>
          <e-column field="endDate" headerText="End Date" width="90" format="yMd" textAlign="Center"></e-column>
          <e-column field="duration" headerText="Duration" width="90" textAlign="Right"></e-column>
          <e-column field="progress" headerText="progress" width="90" textAlign="Right"></e-column>
        </e-columns>
       </ejs-treegrid>
  </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, ColumnMenu} from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: sampleData,
    };
  },
   provide: {
    treegrid: [ColumnMenu ]
  }
}
</script>
<style>
   .e-treegrid .e-columnheader .e-icons.e-columnmenu::before {
        content: "\e903";
    }
</style>
```

{% endtab %}