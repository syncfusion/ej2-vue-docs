---
title: "Kanban Priority"
component: "Kanban"
description: "This section explains how to drop a card on the particular position in Kanban board and also dynamically update the priority mapping fields value."
---

# Card Order

By default, the Kanban cards are initially placed and drop the card inside the columns based on JSON data orders.

Cards are placed in a particular position in the columns when you drop the cards by specifying the `priority` property, which is mapped from the datasource. This property allows the users to drop the cards in the Kanban board where exactly created on dropped clone. It is also helpful to render the cards based on the `priority` property value.

The following cases are dynamically changed their `priority` value when drop the cards.

* If the cell has no cards, the dropped card `priority` value does not change.

* If the cell has one card and dropped a card to last position or previous/next cards that do not have continuous order, then the dropped card `priority` value changed based on their previous card value.

* If the cell has one card and dropped a card on previous position, then compare both values and the dropped card `priority` value is changed if the cards have continuous order otherwise not changed their value.

* When the previous and next cards does not have continuous order, the dropped card `priority` value changed based on the previous card value.

* When previous and next cards have continuous order or odd/even value, then the dropped card followed by next all cards up to **continuous value** are dynamically changed their `priority` value based on the **previous** card value.

For Example,
**Continuous Order** -
Column A having Card A with priority value `1`, Card B with priority value `2` and Card C with priority value `3`.
Column B having Card D with priority value `5`. Dropped Card D between Card A and Card B. Now, Card D, B and C dynamically changed their priority value to `2, 3, 4`.

**Odd/Even order** -
Column A having Card A with priority value `1`, Card B with priority value `3` and Card C with priority value `5`.
Column B having Card D with priority value `5`. Dropped Card D between Card A and Card B. Now, Card D, B and C dynamically changed their priority value to `2, 3, 5`.

> The `priority` property mapping key value must be `number` format.

{% tab template="kanban/priority", iframeHeight="588px" %}

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
        priority: 'RankId'
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
