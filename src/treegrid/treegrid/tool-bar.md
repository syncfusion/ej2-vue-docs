---
title: "Paging"
component: "TreeGrid"
description: "Learn how to use the toolbar and add custom toolbar items in the Essential JS 2 TreeGrid control."
---

# ToolBar

The TreeGrid provides ToolBar support to handle treegrid actions. The [`toolbar`](../api/treegrid/#toolbar)
property accepts either the collection of built-in toolbar items and [`ItemModel`](../api/toolbar/#item)objects for custom toolbar items or
HTML element ID for toolbar template.

To use ToolBar, inject `Toolbar` module in the treegrid.

## Built-in toolbar items

The following table shows built-in toolbar items and its actions.

| Built-in Toolbar Items | Actions |
|------------------------|---------|
| ExpandAll | Expands all the rows.|
| CollapseAll | Collapses all the rows.|
| Add | Adds a new record.|
| Edit | Edits the selected record.|
| Update | Updates the edited record.|
| Delete | Deletes the selected record.|
| Cancel | Cancels the edit state.|
| Search | Searches the records by the given key.|
| Print | Prints the treegrid.|
| ExcelExport | Exports the treegrid to Excel.|
| PdfExport | Exports the treegrid to PDF.|
| WordExport | Exports the treegrid to Word.|

{% tab template="treegrid/toolbar/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' height='265' childMapping='subtasks' :treeColumnIndex='1' :toolbar='toolbar'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='180'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Toolbar, Filter } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbar: ['Print', 'Search']
    };
  },
  provide: {
      treegrid: [ Toolbar, Filter ]
    }
}
</script>

```

{% endtab %}

> * The [`toolbar`](../api/treegrid/#toolbar) has options to define both built-in and custom toolbar items.

## Custom toolbar items

Custom toolbar items can be added by defining the [`toolbar`](../api/treegrid/#toolbar) as a collection of
[`ItemModels`](../api/toolbar/#item).
Actions for this customized toolbar items are defined in the [`toolbarClick`](../api/treegrid/#toolbarclick) event.

By default, Custom toolbar items are in position `Left`. You can change the position by using the [`align`](../api/toolbar/#item) property. In the below sample, we have applied position `Right` for the `Quick Filter` toolbar item.

{% tab template="treegrid/toolbar/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' height='220' childMapping='subtasks' :treeColumnIndex='1' :toolbar='toolbar' :allowFiltering='true' :toolbarClick='toolbarClick'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='180'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Toolbar, Filter } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";
import { ClickEventArgs } from '@syncfusion/ej2-vue-navigations';

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbar: [{text: 'Quick Filter', tooltipText: 'Quick Filter', id: 'toolbarfilter', align:'Right'}]
    };
  },
  methods: {
    toolbarClick: function (args: ClickEventArgs) {
      if (args.item.id === 'toolbarfilter') {
        this.$refs.treegrid.filterByColumn('taskName', 'startswith', 'Testing');
      }
    }
  },
  provide: {
      treegrid: [ Toolbar, Filter ]
  }
}
</script>

```

{% endtab %}

> * The [`toolbar`](../api/treegrid/#toolbar) has options to define both built-in and custom toolbar items.
> * If a toolbar item does not match the built-in items, it will be treated as a custom toolbar item.

## Built-in and custom items in toolbar

TreeGrid have an option to use both built-in and custom toolbar items at same time.

In the below example, `ExpandAll`, `CollapseAll` are built-in toolbar items and `Click` is custom toolbar item.

{% tab template="treegrid/toolbar/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' height='220' childMapping='subtasks' :treeColumnIndex='1' :toolbar='toolbar' :toolbarClick='toolbarClick' :editSettings='editSettings'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='180'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Toolbar, Edit } from "@syncfusion/ej2-vue-treegrid";
import { EmitType } from '@syncfusion/ej2-base';
import { sampleData } from "./datasource.js";
import { ClickEventArgs } from '@syncfusion/ej2-vue-navigations';

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbar: ['ExpandAll', 'CollapseAll', { text: 'Click', tooltipText: 'Click', prefixIcon: 'e-time', id: 'Click' }],
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
    };
  },
  methods: {
    toolbarClick: function (args: ClickEventArgs) {
      if (args.item.text === 'Click') {
        alert("Custom toolbar click...");
      }
    }
  },
  provide: {
      treegrid: [ Toolbar, Edit ]
  }
}
</script>

```

{% endtab %}

## Enable/disable toolbar items

You can enable/disable toolbar items by using the `enableItems` method.

{% tab template="treegrid/toolbar/default" %}

```html
<template>
<div id="app">
      <ejs-button id='enable' cssClass='e-flat' @click.native='enable'>Enable</ejs-button>
      <ejs-button id='disable' cssClass='e-flat' @click.native='disable'>Disable</ejs-button>
      <ejs-treegrid ref='treegrid' :dataSource='data' height='200' childMapping='subtasks' :treeColumnIndex='1' :toolbar='toolbar' :toolbarClick='toolbarClick' :allowFiltering='true'>
            <e-columns>
              <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
              <e-column field='taskName' headerText='Task Name' width='180'></e-column>
              <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
              <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
      </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Toolbar, Filter } from "@syncfusion/ej2-vue-treegrid";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { EmitType } from '@syncfusion/ej2-base';
import { sampleData } from "./datasource.js";
import { ClickEventArgs } from '@syncfusion/ej2-vue-navigations';

Vue.use(TreeGridPlugin);
Vue.use(ButtonPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbar: ['QuickFilter', 'ClearFilter'],
    };
  },
  methods: {
    toolbarClick: function (args: ClickEventArgs) {
      if (args.item.text === 'QuickFilter') {
        this.$refs.treegrid.filterByColumn('taskName', 'startswith', 'Testing');
      }
      if (args.item.text === 'ClearFilter') {
        this.$refs.treegrid.clearFiltering();
      }
    },
    enable: function() {
        this.$refs.treegrid.ej2Instances.toolbarModule.enableItems(['_gridcontrol_QuickFilter', '_gridcontrol_ClearFilter'], true);//Enable toolbar items.
    },
    disable: function() {
        this.$refs.treegrid.ej2Instances.toolbarModule.enableItems(['_gridcontrol_QuickFilter', '_gridcontrol_ClearFilter'], false);//Disable toolbar items.
    }
  },
  provide: {
      treegrid: [ Toolbar, Filter ]
  }
}
</script>

```

{% endtab %}