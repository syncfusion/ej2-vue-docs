---
title: "Sorting"
component: "TreeGrid"
description: "Learn how to sort rows in the Essential JS 2 TreeGrid control, perform initial sorting, and customize sorting logic."
---

# Sorting

Sorting enables you to sort data in the `Ascending` or `Descending` order.
To sort a column, click the column header.

To sort multiple columns, press and hold the CTRL key and click the column header.  You can clear sorting of any one of the multi-sorted columns by pressing and holding the SHIFT key and clicking the specific column header.

To enable sorting in the TreeGrid, set the [`allowSorting`](../api/treegrid/#allowsorting) to true. Sorting options can be configured through the [`sortSettings`](../api/treegrid/sortSettings).

To sort, inject the [`Sort`](../api/treegrid/#sortmodule) module in the treegrid.

{% tab template="treegrid/sorting/default" %}

```html
<template>
    <div id="app">
          <ejs-treegrid  :dataSource='data' :allowSorting='true' height='315px' childMapping='subtasks' :treeColumnIndex='0'>
            <e-columns>
              <e-column field='Category' headerText='Category' width='140'></e-column>
                <e-column field='orderName' headerText='Order Name' width='200'></e-column>
                <e-column field='orderDate' headerText='Order Date' width='150' format="yMd" textAlign='Right'></e-column>
                <e-column field='units' headerText='Units' width='90' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
        </div>
      </template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Sort } from "@syncfusion/ej2-vue-treegrid";
import { sortData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data () {
    return {
      data: sortData
    };
  },
  provide: {
      treegrid: [ Sort ]
    },
}
</script>

```

{% endtab %}

> * TreeGrid columns are sorted in the `Ascending` order. If you click the already sorted column, the sort direction toggles.
> * You can apply and clear sorting by invoking [`sortByColumn`](../api/treegrid/#sortbycolumn) and
[`clearSorting`](../api/treegrid/#clearsorting) methods.
> * To disable sorting for a particular column, set the [`columns.allowSorting`](../api/treegrid/column/#allowSorting) to false.

## Initial sort

To sort at initial rendering, set the [`field`](../api/treegrid/sortDescriptorModel/#field) and
[`direction`](../api/treegrid/sortDescriptorModel/#direction) in the `sortSettings.columns`.

{% tab template="treegrid/sorting/default" %}

```html
<template>
    <div id="app">
          <ejs-treegrid  :dataSource='data' :allowSorting='true' :sortSettings='sortSettings' childMapping='subtasks' :treeColumnIndex='1'>
            <e-columns>
              <e-column field='Category' headerText='Category' width='140'></e-column>
                <e-column field='orderName' headerText='Order Name' width='200'></e-column>
                <e-column field='orderDate' headerText='Order Date' width='120' format="yMd" textAlign='Right'></e-column>
                <e-column field='units' headerText='Units' width='90' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
    </div>
      </template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Sort } from "@syncfusion/ej2-vue-treegrid";
import { sortData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data () {
    return {
      data: sortData,
      sortSettings: { columns: [{ field: 'Category', direction: 'Ascending' }, { field: 'orderName', direction: 'Ascending' }] }
    };
    },
  provide: {
      treegrid: [ Sort ]
    },
}
</script>

```

{% endtab %}

## Sorting events

During the sort action, the treegrid component triggers two events. The [`actionBegin`](../api/treegrid/#actionbegin) event triggers before the sort action starts, and the [`actionComplete`](../api/treegrid/#actioncomplete) event triggers after the sort action is completed. Using these events you can perform the needed actions.

{% tab template="treegrid/sorting/default" %}

```html
<template>
    <div id="app">
          <ejs-treegrid :dataSource='data' :allowSorting='true' height='315px' childMapping='subtasks' :treeColumnIndex='1'  :actionComplete='actionHandler' :actionBegin='actionHandler'>
            <e-columns>
                <e-column field='Category' headerText='Category' width='140'></e-column>
                <e-column field='orderName' headerText='Order Name' width='200'></e-column>
                <e-column field='orderDate' headerText='Order Date' width='120' format="yMd" textAlign='Right'></e-column>
                <e-column field='units' headerText='Units' width='90' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
    </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Sort } from "@syncfusion/ej2-vue-treegrid";
import { sortData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data () {
    return {
      data: sortData
    };
  },
  provide: {
      treegrid: [ Sort ]
    },
    methods: {
    actionHandler: function(args) {
        alert(args.requestType + ' ' + args.type); // custom Action
    }
  },
}
</script>

```

{% endtab %}

> The `args.requestType` is the current action name. For example, in sorting the `args.requestType` value is 'sorting'.

## Touch interaction

When you tap the treegrid header on touchscreen devices, the selected column header is sorted. A popup ![Multi column sorting](/images/sorting.jpg) is displayed for multi-column sorting. To sort multiple columns, tap the popup![Multi sorting](/images/msorting.jpg) and then tap the desired treegrid headers.

The following screenshot shows treegrid touch sorting.

<!-- markdownlint-disable MD033 -->
<img src="../images/touch-sorting.jpg" alt="Touch interaction image" style="width:320px;height: 620px">
<!-- markdownlint-enable MD033 -->
