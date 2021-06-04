---
title: "Cards in Kanban"
component: "Kanban"
description: "This article demonstrates how to use the cards in Kanban board and demonstrate and customize the card layout."
---

# Cards

The cards are main elements in Kanban board, which represent the task information with header and content. The header and content of a card is fetched from the corresponding mapping fields. The card layout can be customized with template also.

## Drag-and-drop

Transit or change the card position using the drag-and-drop functionality. By default, the `allowDragAndDrop` property is enabled on the Kanban board, which is used to change the card position by column-to-column or within the column.

Added dotted border on Kanban cells except the dragged clone cells when dragging, which indicates the possible ways for dropping the cards into the cells.

## Header

The card header is achieved by mapping the `headerField` property, which is placed inside the `cardSettings` property. By default, the `showHeader` property enabled by Kanban board that is used to show the header at the top of the card.

> The `headerField` property of `cardSettings` is mandatory to render the cards in the Kanban board. It acts as a unique field that is used to avoid the duplication of card data. You can not change the `headerField` of mapped data value using the `updateCard` public method or server-side update of data.

In the following demo, the `showHeader` property is disabled on Kanban board.

{% tab template="kanban/card-header", iframeHeight="588px" %}

```html
<template>
  <div id="app">
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
import { extend } from '@syncfusion/ej2-base';
Vue.use(KanbanPlugin);

let kanbanData = [
  {
      'Id': 1,
      'Status': 'Open',
      'Summary': 'Analyze the new requirements gathered from the customer.',
      'Type': 'Story',
      'Priority': 'Low',
      'Tags': 'Analyze,Customer',
      'Estimate': 3.5,
      'Assignee': 'Nancy Davloio',
      'RankId': 1
  },
  {
      'Id': 2,
      'Status': 'InProgress',
      'Summary': 'Improve application performance',
      'Type': 'Improvement',
      'Priority': 'Normal',
      'Tags': 'Improvement',
      'Estimate': 6,
      'Assignee': 'Andrew Fuller',
      'RankId': 1
  },
  {
      'Id': 3,
      'Status': 'Testing',
      'Summary': 'Arrange a web meeting with the customer to get new requirements.',
      'Type': 'Others',
      'Priority': 'Critical',
      'Tags': 'Meeting',
      'Estimate': 5.5,
      'Assignee': 'Janet Leverling',
      'RankId': 2
  },
  {
      'Id': 4,
      'Status': 'Close',
      'Summary': 'Fix the issues reported in the IE browser.',
      'Type': 'Bug',
      'Priority': 'Release Breaker',
      'Tags': 'IE',
      'Estimate': 2.5,
      'Assignee': 'Janet Leverling',
      'RankId': 2
  },
  {
      'Id': 5,
      'Status': 'Open',
      'Summary': 'Fix the issues reported by the customer.',
      'Type': 'Bug',
      'Priority': 'Low',
      'Tags': 'Customer',
      'Estimate': '3.5',
      'Assignee': 'Steven walker',
      'RankId': 1
  },
  {
      'Id': 6,
      'Status': 'InProgress',
      'Summary': 'Arrange a web meeting with the customer to get the login page requirements.',
      'Type': 'Others',
      'Priority': 'Low',
      'Tags': 'Meeting',
      'Estimate': 2,
      'Assignee': 'Michael Suyama',
      'RankId': 1
  },
  {
      'Id': 7,
      'Status': 'Testing',
      'Summary': 'Validate new requirements',
      'Type': 'Improvement',
      'Priority': 'Low',
      'Tags': 'Validation',
      'Estimate': 1.5,
      'Assignee': 'Robert King',
      'RankId': 1
  },
  {
      'Id': 8,
      'Status': 'Close',
      'Summary': 'Login page validation',
      'Type': 'Story',
      'Priority': 'Release Breaker',
      'Tags': 'Validation,Fix',
      'Estimate': 2.5,
      'Assignee': 'Laura Callahan',
      'RankId': 2
  }
];

export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id",
        showHeader: false
      }
    };
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

## Content

The card's content is fetched from data source using the `contentField` property, which is placed inside the `cardSettings` property. If the `contentField` property is not used, card is rendered with empty content.

## Template

You can customize the default card layout using template as per your application needs. This can be achieved by template of the `cardSettings` property.

{% tab template="kanban/card-template", iframeHeight="588px" %}

```html
<template>
  <div id="app">
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
import { extend } from '@syncfusion/ej2-base';
import { kanbanData } from './datasource.js';
Vue.use(KanbanPlugin);
export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        headerField: "Id",
        template: function() {
          return {
          template: Vue.component('cardTemplate', {
            template: `<div class='e-card-content'>
                        <table class="card-template-wrap">
                            <tbody>
                                <tr>
                                    <td class="CardHeader">Id:</td>
                                    <td>{{data.Id}}</td>
                                </tr>
                                <tr>
                                    <td class="CardHeader">Type:</td>
                                    <td>{{data.Type}}</td>
                                </tr>
                                <tr>
                                    <td class="CardHeader">Priority:</td>
                                    <td>{{data.Priority}}</td>
                                </tr>
                                <tr>
                                    <td class="CardHeader">Summary:</td>
                                    <td>{{data.Summary}}</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>`,
            data() { }
          })
        }
        }
      }
    };
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

.e-kanban .card-template-wrap td {
    background: none !important;
}

.e-kanban .card-template-wrap .CardHeader {
    font-weight: 500;
}
</style>

```

{% endtab %}

## Selection

Kanban board allows to select single and multiple selection of cards when mouse or keyboard interactions using `selectionType` property. The property contains following types.

* **None**: No cards are allowed to select from Kanban board.
* **Single**: Only one card allowed to select at a time in the Kanban board.
* **Multiple**: Multiple cards are allowed to select in a board.

### Multiple Selection

Select the multiple cards randomly using Ctrl + mouse click and select the multiple cards continuously using Shift + mouse click action on Kanban board. Set `Multiple` in `selectionType` to enable the multiple selection in a board.

{% tab template="kanban/multiple-selection", iframeHeight="588px" %}

```html
<template>
  <div id="app">
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
import { extend } from '@syncfusion/ej2-base';
import { kanbanData } from './datasource.js';
Vue.use(KanbanPlugin);
export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id",
        selectionType: 'Multiple'
      }
    };
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
