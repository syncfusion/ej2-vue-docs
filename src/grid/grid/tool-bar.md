---
title: "ToolBar"
component: "Grid"
description: "Learn how to use the toolbar and add custom toolbar items in the Essential JS 2 DataGrid control."
---

# Toolbar

The Grid provides ToolBar support to handle grid actions. The [`toolbar`](../api/grid/#toolbar)
property accepts either the collection of built-in toolbar items and
`ItemModel` objects for custom toolbar items or
HTML element ID for toolbar template.

To use Toolbar, you need to inject `Toolbar` module in the `provide` section.

## Built-in Toolbar Items

Built-in Toolbar Items execute standard actions of the Grid and it can be added by defining
[`toolbar`](../api/grid/#toolbar)
as a collection of built-in items. It renders the button with icon and text.

The following table shows Built-in toolbar items and its action.

| Built-in Toolbar Items | Actions |
|------------------------|---------|
| Add | Add a new record.|
| Edit | Edit the selected record.|
| Update | Update edited record.|
| Delete | Delete the selected record.|
| Cancel | Cancel the edit state.|
| Search | Search the records by given key.|
| Print | Print the Grid.|
| ColumnChooser | Choose the column's visibility.|
| PdfExport | Exports grid to PDF document.|
| ExcelExport | Exports grid to Excel document.|
| CsvExport | Exports grid to CSV document.|

{% tab template="grid/toolbar/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' height='270px' :toolbar='toolbar'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Toolbar } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      toolbar: ['Print', 'Search']
    };
  },
  provide: {
      grid: [Toolbar]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> * The [`toolbar`](../api/grid/#toolbar) has options to define both built-in and custom toolbar items.

## Custom Toolbar Items

Custom toolbar items can be added by defining [`toolbar`](../api/grid/#toolbar) as a collection of
`ItemModel`
Actions for this customized toolbar items are defined in the [`toolbarClick`](../api/grid/#toolbarclick) event.

By default, Custom toolbar items are in position `Left`. You can change the position by using the `align` property. In the below sample, we have applied position `Right` for the `Collapse All` toolbar item.

{% tab template="grid/toolbar/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' height='200px' :allowGrouping='true' :groupSettings='groupOptions' :toolbar='toolbar' :toolbarClick='clickHandler'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Toolbar, Group } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      toolbar: [{ text: 'Expand All', tooltipText: 'Expand All', prefixIcon: 'e-expand', id: 'expandall' },{ text: 'Collapse All', tooltipText: 'collection All', prefixIcon: 'e-collapse', id: 'collapseall' , align:'Right'}],
      groupOptions: { columns: ['CustomerID'] }
    };
  },
  methods: {
      clickHandler: function(args) {
        if (args.item.id === 'expandall') {
            this.$refs.grid.ej2Instances.groupModule.expandAll();
        }

        if (args.item.id === "collapseall"){
            this.$refs.grid.ej2Instances.groupModule.collapseAll();
        }
    }
  },
  provide: {
      grid: [Toolbar, Group]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> * The [`toolbar`](../api/grid/#toolbar) has options to define both built-in and custom toolbar items.
> * If a toolbar item does not match with built-in items, it will be treated as custom toolbar item.

## Built-in and custom items in toolbar

Grid have an option to use both built-in and custom toolbar items at same time.

In the below example, `Add`, `Edit`, `Delete`, `Update`, `Cancel` are built-in toolbar items and `Click` is custom toolbar item.

{% tab template="grid/toolbar/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' height='200px' :editSettings='editSettings' :toolbar='toolbar' :toolbarClick='clickHandler'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel','Print', 'Search', { text: 'Click', tooltipText: 'Click', prefixIcon: 'e-expand', id: 'Click' }]
    };
  },
  methods: {
      clickHandler: function(args) {
        if (args.item.id === 'Click') {
            alert("Custom Toolbar Click...");
        }
    }
  },
  provide: {
      grid: [Toolbar, Edit]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";

 .e-expand::before {
      content: '\e5b8';
    }
</style>
```

{% endtab %}

## Custom Toolbar

Custom Toolbar is used to customize the whole toolbar. It can be added by defining
`toolbarTemplate`. Actions for this toolbar template items are defined in the
`clicked` event in toolbar.

{% tab template="grid/toolbar/custom" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' height='200px' :toolbarTemplate='toolbar'>
                <e-columns>
                    <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                    <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                    <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                    <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
                </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Toolbar } from "@syncfusion/ej2-vue-grids";
import { ToolbarPlugin } from '@syncfusion/ej2-vue-navigations';
import { data } from './datasource.js';

Vue.use(GridPlugin);
Vue.use(ToolbarPlugin);

export default {
  data() {
    return {
      data: data,
      toolbar: function() {
            return { template: Vue.component('custom-toolbar', {
                template: `<ejs-toolbar :clicked='clickHandler'>
                        <e-items>
                            <e-item id='collapse' prefixIcon='e-collapse'></e-item>
                        </e-items>
                    </ejs-toolbar>`,
                data: function() { return {};},
                methods: {
                    clickHandler(args) {
                        let target = args.originalEvent.target.closest('button'); //find clicked button
                        if (target.id === 'collapse') {
                            //collapse all expanded grouped row
                            this.$refs.grid.ej2Insatnces.groupModule.collapseAll();
                        }
                    }
                }
            })
        };
      }
    };
  },
  provide: {
      grid: [Toolbar]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Enable/Disable Toolbar Items

You can enable/disable toolbar items by using the `enableItems` method.

{% tab template="grid/toolbar/default" %}

```html
<template>
    <div id="app">
        <ejs-button id='enable' cssClass='e-flat' @click.native='enable'>Enable</ejs-button>
        <ejs-button id='disable' cssClass='e-flat' @click.native='disable'>Disable</ejs-button>
        <ejs-grid id='Grid' ref='grid' :dataSource='data' height='200px' :allowGrouping='true' :groupSettings='groupOptions' :toolbar='toolbar' :toolbarClick='clickHandler'>
                <e-columns>
                    <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                    <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                    <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                    <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
                </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Toolbar, Group } from "@syncfusion/ej2-vue-grids";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { data } from './datasource.js';

Vue.use(GridPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      data: data,
      toolbar: ['Expand', 'Collapse'],
      groupOptions: { columns: ['CustomerID'] }
    };
  },
  methods: {
      clickHandler: function(args) {
        if (args.item.id === 'Grid_Collapse') { // Grid_Collapse is control id + '_' + toolbar value.
            this.$refs.grid.ej2Instances.groupModule.collapseAll();
        }

        if (args.item.id === "Grid_Expand"){
            this.$refs.grid.ej2Instances.groupModule.expandAll();
        }
    },
    enable: function() {
        this.$refs.grid.ej2Instances.toolbarModule.enableItems(['Grid_Collapse','Grid_Expand'],true);//Enable toolbar items.
    },
    disable: function() {
        this.$refs.grid.ej2Instances.toolbarModule.enableItems(['Grid_Collapse','Grid_Expand'],false);//Disable toolbar items.
    }
  },
  provide: {
      grid: [Toolbar]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## See Also

* [Toolbar Component](../../toolbar/getting-started/)
