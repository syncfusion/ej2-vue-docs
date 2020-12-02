---
title: "Context Menu"
component: "Grid"
description: "Learn how to use the context menu and add custom context menu items in the Essential JS 2 DataGrid control."
---

# Context menu

The Grid has options to show the context menu when right clicked on it. To enable this feature,
you need to define either default or custom item in the
[`contextMenuItems`](../api/grid/#contextmenuitems).

To use the context menu, inject the **ContextMenu** module in the **provide** section.

The default items are in the following table.

Items| Description
----|----
`AutoFit`|  Auto fit the current column.
`AutoFitAll` | Auto fit all columns.
`Edit`|  Edit the current record.
`Delete` | Delete the current record.
`Save` | Save the edited record.
`Cancel` | Cancel the edited state.
`Copy` | Copy the selected records.
`PdfExport` | Export the grid data as Pdf document.
`ExcelExport` | Export the grid data as Excel document.
`CsvExport` | Export the grid data as CSV document.
`Group` | Group the current column.
`Ungroup` | Ungroup the current column.
`SortAscending` | Sort the current column in ascending order.
`SortDescending` | Sort the current column in descending order.
`FirstPage` | Go to the first page.
`PrevPage` | Go to the previous page.
`LastPage` | Go to the last page.
`NextPage` | Go to the next page.

{% tab template="grid/contextMenu/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' id="gridcomp" :allowPaging='true' :allowExcelExport='true' :allowPdfExport='true' height='215px' :allowSorting='true'
        :contextMenuItems="contextMenuItems" :editSettings='editing' :allowGrouping='true'>
        <e-columns>
            <e-column field='OrderID' headerText='Order ID' width='120' textAlign="Right" isPrimaryKey='true'></e-column>
            <e-column field='CustomerID' headerText='Customer Name'></e-column>
            <e-column field='Freight' headerText='Freight' format='C2' textAlign="Right" editType='numericedit'></e-column>
            <e-column field='ShipCity' headerText='Ship City' width='150'></e-column>
        </e-columns>
    </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, ContextMenu, Page, Resize, Sort, Group, Edit, PdfExport, ExcelExport  } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      contextMenuItems: ['AutoFit', 'AutoFitAll', 'SortAscending', 'SortDescending',
                'Copy', 'Edit', 'Delete', 'Save', 'Cancel',
                'PdfExport', 'ExcelExport', 'CsvExport', 'FirstPage', 'PrevPage',
                'LastPage', 'NextPage', 'Group', 'Ungroup'],
      editing: {allowEditing: true, allowDeleting: true}
    };
  },
  provide : {
      grid: [ContextMenu, Page, Resize, Sort, Group, Edit, PdfExport, ExcelExport]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

{% endtab %}

## Custom context menu items

The custom context menu items can be added by defining the
[`contextMenuItems`](../api/grid/#contextmenuitems) as a collection of
[`contextMenuItemModel`](../api/grid/contextMenuItemModel/).
Actions for this customized items can be defined in the
[`contextMenuClick`](../api/grid/#contextmenuclick) event.

{% tab template="grid/contextMenu/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' id='gridcomp' :dataSource='data' :allowSelection='true' :allowPaging='true' height='265px' :contextMenuItems='contextMenuItems' :contextMenuClick='contextMenuClick'>
            <e-columns>
                <e-column field='EmployeeID' :isPrimaryKey='true' headerText='Employee ID' textAlign='Right' width=120></e-column>
                <e-column field='FirstName' headerText='FirstName' width=150></e-column>
                <e-column field='LastName' headerText='Last Name' width=150></e-column>
                <e-column field='City' headerText='City' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, ContextMenu, Page } from "@syncfusion/ej2-vue-grids";
import { employeeData } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: employeeData,
      contextMenuItems: [{text: 'Copy with headers', target: '.e-content', id: 'copywithheader'}]
    };
  },
  methods: {
      contextMenuClick: function(args) {
        if(args.item.id === 'copywithheader') {
            this.$refs.grid.copy(true);
        }
    }
  },
  provide: {
      grid: [ContextMenu, Page]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

{% endtab %}

> You can hide or show an item in context menu for specific area inside of grid by defining the
[`target`](../api/grid/contextMenuItemModel/#target) property.
