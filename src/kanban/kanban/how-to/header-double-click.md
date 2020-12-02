---
title: "Header double click"
component: "Kanban"
description: "This article demonstrates how to bind the double click event on Kanban header cells and how to get the header information."
---

# Add header double click

You can bind the header double click event by using the [`dataBound`](../../api/kanban#dataBound) event at the initial rendering. You can get the column header text when you double click on the headers.

{% tab template="kanban/card-header", iframeHeight="588px" %}

```html
<template>
  <div id="app">
       <ejs-kanban id="kanban" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :dataBound="OnDataBound">
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
import { extend } from '@syncfusion/ej2-base';
import { DialogUtility } from '@syncfusion/ej2-popups';
import { kanbanData } from './datasource.js';
Vue.use(KanbanPlugin);
Vue.use(DialogUtility);
export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id"
      }
    };
  },
  methods: {
    OnDataBound: function() {
        var headerEle: HTMLElement = document.querySelector('.e-header-row');
        headerEle.addEventListener("dblclick", function (e: Event) {
            var target = closest(e.target, '.e-header-cells');
            DialogUtility.alert({
                title: 'Header',
                content: "Double clicked on " + target.querySelector('.e-header-text').innerText + " header",
                showCloseIcon: true,
                closeOnEscape: true,
                animationSettings: { effect: 'Zoom' }
            });
        });
    },
  }
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