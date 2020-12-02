---
title: "Paging"
component: "TreeGrid"
description: "Learn how to add and customize the pager in the Essential JS 2 TreeGrid control."
---

# Paging

Paging provides an option to display TreeGrid data in page segments. To enable paging, set the [`allowPaging`](../api/treegrid/#allowpaging) to true. When paging is enabled, pager component renders at the bottom of the treegrid.
Paging options can be configured through the [`pageSettings`](../api/treegrid/#pagesettings).

To use paging, inject the [`Page`](../api/treegrid/#pagermodule) module in the grid.

{% tab template="treegrid/paging/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      pageSettings: { pageSize: 7 }
    };
  },
  provide: {
      treegrid: [ Page ]
    }
}
</script>

```

{% endtab %}

> You can achieve better performance by using treegrid paging to fetch only a pre-defined number of records from the data source.

## Page Size Mode

Two behaviors are available in TreeGrid paging to display certain number of records in a current page. Following are the two types of [`pageSizeMode`](../api/treegrid/pageSettingsModel/#pagesizemode).

* **All** : This is the default mode. The number of records in a page is based on [`pageSize`](../api/treegrid/pageSettingsModel/#pagesize) property.
* **Root** : The number of root nodes or the 0th level records to be displayed per page is based on [`pageSize`](../api/treegrid/pageSettingsModel/#pagesize) property.

With [`pageSizeMode`](../api/treegrid/pageSettingsModel/#pagesizemode) property as `Root`, only the root level or the 0th level records are considered in records count.

{% tab template="treegrid/paging/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' height='265px' >
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      pageSettings: { pageSize: 2, pageSizeMode: 'Root'}
    };
  },
  provide: {
      treegrid: [ Page ]
    },
}
</script>

```

{% endtab %}

## Pager with Page Size Dropdown

The pager Dropdown allows you to change the number of records in the TreeGrid dynamically. It can be enabled by defining the [`pageSettings.pageSizes`](../api/treegrid/pageSettingsModel/#pagesizes) property as true.

```html
pageSettings: {pageSize: 7, pageSizes: true},
```

<!-- markdownlint-disable MD033 -->
<img src="/treegrid/images/pagesizes.png" alt="Page size dropdown">
<!-- markdownlint-enable MD033 -->

## How to render Pager at the Top of the TreeGrid

By default, Pager will be rendered at the bottom of the TreeGrid. You can also render the Pager at the top of the TreeGrid by using the `dataBound` event.

{% tab template="treegrid/paging/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' :dataBound='ondataBound'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, TreeGridComponent,  Page } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

let initialGridLoad = true;

export default {
  data ()  {
    return {
      data: sampleData,
      pageSettings: { pageSize: 7, pageSizes: true },
      initialGridLoad : true
      };
  },
  provide: {
      treegrid: [ Page ]
    },
     methods: {
    ondataBound: function() {
      if (this.initialGridLoad) {
          this.initialGridLoad = false;
          let pager = document.getElementsByClassName('e-gridpager e-control e-pager e-lib');
          let topElement;
         if ( this.$refs.treegrid.toolbar) {
             topElement = document.getElementsByClassName('e-toolbar');
        } else {
          topElement = document.getElementsByClassName('e-gridheader e-lib e-droppable');
        }
          topElement[0].before(pager[0]);
      }
    }
}
}
</script>

```

{% endtab %}

> During the paging action, the pager component triggers the below three events.
> * The `created` event triggers when Pager is created.
> * The `click` event triggers when the numeric items in the pager is clicked.
> * The `dropDownChanged` event triggers when pageSize DropDownList value is selected.