---
title: "Filtering Cards"
component: "Kanban"
description: "This article demonstrates how to filter the collection of cards from the data source and display it on the Kanban board."
---

# Filtering Cards

You can filter the collection of cards from the dataSource and display it on the Kanban board by using the [`query`](../../api/kanban/#query) property.

In the below sample, you can filter the cards based on the ‘where’ query and display the filtered data to the Kanban board.

{% tab template="kanban/card-header", iframeHeight="588px" %}

```html
<template>
  <div id="app">
       <ejs-dropdownlist ref='PriorityDrop' id='priority_filter' :dataSource='priorityData' :change='change' value='None' placeholder='Select a priority'></ejs-dropdownlist>
       <ejs-kanban id="kanban" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings">
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
import { KanbanPlugin } from '@syncfusion/ej2-vue-kanban';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
import { extend } from '@syncfusion/ej2-base';
import { Query } from '@syncfusion/ej2-data';
import { kanbanData } from './datasource.js';
Vue.use(KanbanPlugin);
Vue.use(DropDownListPlugin);
export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id"
      },
      priorityData: ['None', 'High', 'Normal', 'Low']
    };
  },
  methods: {
    change: function (args) {
      let filterQuery = new Query();
      if (args.value !== 'None') {
          filterQuery = new Query().where('Priority', 'equal', args.value);
      }
      this.kanbanObj.query = filterQuery;
    },
  },
  mounted: function() {
    this.kanbanObj = this.$refs.KanbanObj.ej2Instances;
    this.priorityObj = this.$refs.PriorityDrop.ej2Instances;
  },
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-kanban/styles/material.css';
</style>

```

{% endtab %}