---
title: "Customize Column Styles"
component: "TreeGrid"
description: "Learn how to Customize Column Styles."
---

# Customize column styles

You can customise the appearance of header and content of the particular column using the
[`customAttributes`](../../api/treegrid/column/#customattributes) property.

To customize the Tree Grid column, follow the given steps:

**Step 1**:

Create a css class with custom style to override the default style for rowcell and headercell.

```css

.e-treegrid .e-rowcell.customcss{
    background-color: #ecedee;
    font-family: 'Bell MT';
    color: 'red';
    font-size: '20px';
}

.e-treegrid .e-headercell.customcss{
    background-color: #2382c3;
    color: white;
    font-family: 'Bell MT';
    font-size: '20px';
}

```

**Step 2**:

Add the custom css class to particular column by using [`customAttributes`](../api/treegrid/column/#customattributes) property.

```typescript

<e-column field="taskName" headerText="Task Name" :customAttributes="{class: 'customcss'}"  width="100"></e-column>

```

{% tab template="treegrid/how-to/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' height='280px'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=70 textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' :customAttributes= "{class: 'customcss'}" width=100></e-column>
                <e-column field='startDate' headerText='Start Date' width=90 format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width=90 textAlign='Right'></e-column>
                <e-column field="progress" headerText="Progress" width="90" textAlign="Right" ></e-column>
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
}
</script>
<style>
.e-treegrid .e-rowcell.customcss{
    background-color: #ecedee;
    font-family: 'Bell MT';
    color: 'red';
    font-size: '20px';
}

.e-treegrid .e-headercell.customcss{
    background-color: #2382c3;
    color: white;
    font-family: 'Bell MT';
    font-size: '20px';
}
</style>

```

{% endtab %}
