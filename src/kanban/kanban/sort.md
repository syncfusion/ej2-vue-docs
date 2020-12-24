---
title: "Kanban Sort"
component: "Kanban"
description: "This section explains how to sort the cards in a particular column and drag and drop the cards in the Kanban board."
---

# Sort

The Kanban provides built-in support to arrange the cards in their columns based on the JSON data order and drop the cards in the columns based on the dropped clone. Initially, users can change the arrangement of cards in the columns and position of the dropped card by using the [`sortBy`](../api/kanban/sortSettingsModel/#sortby) property. The [`sortBy`](../api/kanban/sortSettingsModel/#sortby) property contains three enumeration values as follows.

* Index
* DataSourceOrder
* Custom

## Index

SortBy `Index` property can be used with or without [`field`](../api/kanban/sortSettingsModel/#field) mapping.

### Index without field mapping

By default, SortBy `Index` property support without any [`field`](../api/kanban/sortSettingsModel/#field) mapping. In this behavior, cards are loaded based on the JSON data order and cards are dropped based on the dropped clone.

{% tab template="kanban/index", iframeHeight="588px" %}

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
        headerField: "Id"
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

### Index with field mapping

SortBy `Index` property also supports with [`field`](../api/kanban/sortSettingsModel/#field) mapping. In this behavior, cards are loaded based on mapping `field` values, and cards are dropped based on the dropped clone.

Cards are placed in a particular position in the columns where you can drop the cards by specifying the [`field`](../api/kanban/sortSettingsModel/#field) property, which is mapped from the data source. This property allows the users to drop the cards in the Kanban board where the dropped clone is created exactly. It is also helpful to render the cards based on the [`field`](../api/kanban/sortSettingsModel/#field) property value.

> The [`field`](../api/kanban/sortSettingsModel/#field) property mapping key value must be in `number` format.

The following cases will dynamically change their [`field`](../api/kanban/sortSettingsModel/#field) value when dropping the cards.

* If the cell has no cards, the dropped card [`field`](../api/kanban/sortSettingsModel/#field) value does not change.

* If the cell has one card and dropped a card to the last position or previous/next cards that do not have continuous order, then the dropped card [`field`](../api/kanban/sortSettingsModel/#field) value will be changed based on their previous card value.

* If the cell has one card and dropped a card on the previous position, then it will compare both the values, and the dropped card [`field`](../api/kanban/sortSettingsModel/#field) value will be changed if the cards have continuous order otherwise values will not be changed.

* When the previous and next cards do not have continuous order, the dropped card [`field`](../api/kanban/sortSettingsModel/#field) value will be changed based on the previous card value.

* When the previous and next cards have continuous order or odd/even value, then the [`field`](../api/kanban/sortSettingsModel/#field) value of the dropped card and the cards followed by the dropped card will be changed based on the **previous** card value with continuous order.

For Example,
**Continuous Order** -
Consider,  Column A has Card A with priority value `1`, Card B with priority value `2`, and Card C with priority value `3`.
and Column B has Card D with priority value `5`, then the dropped Card D will be placed between Card A and Card B. Now, the Cards D, B, and C will be dynamically changed to the priority values as `2, 3, and 4` respectively.

**Odd/Even order** -
Consider, Column A has Card A with priority value `1`, Card B with priority value `3`, and Card C with priority value `5`.
and Column B has Card D with priority value `5`, then the Dropped Card D will be placed between Card A and Card B. Now, the Cards D, B, and C will be dynamically changed to the priority values as `2, 3, and 5` respectively.

{% tab template="kanban/index-field", iframeHeight="588px" %}

```html
<template>
  <div id="app">
       <ejs-kanban id="kanban" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :sortSettings="sortSettings">
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
        headerField: "Id"
      },
      sortSettings: {
        sortBy: "Index",
        field: "RankId"
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

## DataSource Order

The SortBy `DataSourceOrder` property does not require any [`field`](../api/kanban/sortSettingsModel/#field) mapping. In this behavior, cards are loaded based on the JSON data order, and also cards are dropped based on the JSON data order.

{% tab template="kanban/data-source-order", iframeHeight="588px" %}

```html
<template>
  <div id="app">
       <ejs-kanban id="kanban" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :sortSettings="sortSettings">
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
        headerField: "Id"
      },
      sortSettings: {
        sortBy: "DataSourceOrder"
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

## Custom

### Custom with field mapping

The SortBy `Custom` property must require datasource [`field`](../api/kanban/sortSettingsModel/#field) mapping. In this behavior, cards are loaded based on the [`field`](../api/kanban/sortSettingsModel/#field) mapping value and also cards are dropped based on the [`field`](../api/kanban/sortSettingsModel/#field) mapping value.

{% tab template="kanban/custom-mapping", iframeHeight="588px" %}

```html
<template>
  <div id="app">
       <ejs-kanban id="kanban" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :sortSettings="sortSettings">
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
        headerField: "Id"
      },
      sortSettings: {
        sortBy: "Custom",
        field: "Summary"
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

## Change the direction

Kanban board also provides support for aligning the cards in the columns using the [`direction`](../api/kanban/sortSettingsModel/#direction) property inside the [`sortSettings`](../api/kanban/#sortsettings) property. Based on this, cards can be aligned in the columns either in `Ascending` or `Descending` order. Sorting direction will be performed based on [`sortBy`](../api/kanban/sortSettingsModel/#sortby) property.

> By default, cards are aligned in the columns based on `Ascending` order.

In the following sample, cards are aligned in `Descending` order.

{% tab template="kanban/sort-direction", iframeHeight="588px" %}

```html
<template>
  <div id="app">
       <ejs-kanban id="kanban" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :sortSettings="sortSettings">
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
        headerField: "Id"
      },
      sortSettings: {
        sortBy: "Custom",
        field: "Summary",
        direction: "Descending"
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
