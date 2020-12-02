---
title: "Change the Orientation of Header Text"
component: "TreeGrid"
description: "Learn how to Change the Orientation of Header Text."
---

# Change the orientation of header Text

You can change the orientation of the header text by using the [`customAttributes`](../api/treegrid/column/#customattributes) property.

Ensure the following steps:

**Step 1**:

Create a css class with orientation style for treegrid header cell.

```css
.orientationcss .e-headercelldiv {
    transform: rotate(90deg);
}

```

**Step 2**:

Add the custom css class to particular column by using [`customAttributes`](../api/treegrid/column/#customattributes) property.

```typescript
    <e-column field='endDate' headerText='End Date' width='90' format="yMd" :customAttributes= "{class: 'orientationcss'}" textAlign='Center'></e-column>

```

**Step 3**:

Resize the header cell height in [`create`](../api/treegrid/#create) event by using the following code.

```typescript
  setHeaderHeight: function(args) {
      let textWidth = document.querySelector(".orientationcss > div").scrollWidth; //Obtain the width of the headerText content.
      let headerCell = document.querySelectorAll(".e-headercell");
      for (let i = 0; i < headerCell.length; i++) {
        headerCell.item(i).style.height = textWidth + "px"; //Assign the obtained textWidth as the height of the headerCell.
      }
    }

```

{% tab template="treegrid/how-to/default" %}

```html
<template>
  <div id="app">
        <ejs-treegrid :dataSource="data" :treeColumnIndex="1" height='210px' :created='setHeaderHeight' childMapping="subtasks" ref="treegrid">
        <e-columns>
          <e-column field="taskID" headerText="Task ID" width="70" textAlign="Right"></e-column>
          <e-column field="taskName" headerText="Task Name" width="100" ></e-column>
          <e-column field="startDate" headerText="Start Date" format="yMd" textAlign="Right" width="90"></e-column>
          <e-column field="endDate" headerText="End Date" width="90" format="yMd" :customAttributes= "{class: 'orientationcss'}" textAlign="Center"></e-column>
          <e-column field="duration" headerText="Duration" width="90" textAlign="Right"></e-column>
          <e-column field="progress" headerText="progress" width="90" textAlign="Right"></e-column>
        </e-columns>
       </ejs-treegrid>
  </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: sampleData,
    };
  },
  methods: {
    setHeaderHeight: function(args) {
      let textWidth = document.querySelector(".orientationcss > div").scrollWidth; //Obtain the width of the headerText content.
      let headerCell = document.querySelectorAll(".e-headercell");
      for (let i = 0; i < headerCell.length; i++) {
        headerCell.item(i).style.height = textWidth + "px"; //Assign the obtained textWidth as the height of the headerCell.
      }
    },
  }
}
</script>
<style>
   .orientationcss .e-headercelldiv {
    transform: rotate(90deg);
    padding-top:5px;
}
</style>

```

{% endtab %}