---
title: "Dynamically change Kanban columns"
component: "Kanban"
description: "This article demonstrates how to dynamically change the particular column or complete column in the Kanban board."
---

# Change Kanban columns dynamically

You can dynamically change the Kanban columns by using the [`columns`](../../api/kanban#columns) property.

In the below sample, you can dynamically change the [`allowToggle`](../../api/kanban/columnsModel/#allowtoggle) property at the particular column when you click on the button. You can also change the initially created columns to the new Kanban columns by using the [`columns`](../../api/kanban#columns) property when you click on the button.

{% tab template="kanban/card-header", iframeHeight="588px" %}

```html
<template>
  <div id="app">
    <ejs-button
      id="particular_column"
      class="e-btn"
      v-on:click.native="particularColumnClick"
      >Enable Allow Toggle</ejs-button
    >
    <ejs-button id="column" class="e-btn" v-on:click.native="columnClick"
      >Change Columns</ejs-button
    >
    <ejs-kanban
      ref="KanbanObj"
      id="kanban"
      keyField="Status"
      :dataSource="kanbanData"
      :cardSettings="cardSettings"
    >
      <e-columns>
        <e-column headerText="To Do" keyField="Open"></e-column>
        <e-column headerText="In Progress" keyField="InProgress"></e-column>
        <e-column headerText="Testing" keyField="Testing"></e-column>
        <e-column headerText="Done" keyField="Close"></e-column>
      </e-columns>
    </ejs-kanban>
  </div>
</template>

<script>
import Vue from "vue";
import { KanbanPlugin } from "@syncfusion/ej2-vue-kanban";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { extend } from "@syncfusion/ej2-base";
import { kanbanData } from "./datasource.js";
Vue.use(KanbanPlugin);
Vue.use(ButtonPlugin);
export default {
  data: function () {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id",
      },
    };
  },
  mounted: function () {
    this.kanbanObj = this.$refs.KanbanObj.ej2Instances;
  },
  methods: {
    particularColumnClick: function () {
      this.kanbanObj.columns[1].allowToggle = true;
    },
    columnClick: function () {
      this.kanbanObj.columns = [
        { headerText: "To Do", keyField: "Open" },
        { headerText: "Done", keyField: "Close" },
      ];
    },
  },
};
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-layouts/styles/material.css";
@import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-kanban/styles/material.css";
</style>

```

{% endtab %}