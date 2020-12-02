---
title: "Context Menu"
component: "TreeGrid"
description: "Learn how to use the context menu and add custom context menu items in the Essential JS 2 TreeGrid control."
---

# Context menu

The TreeGrid has options to show the context menu when right clicked on it. To enable this feature, you need to define either default or custom item in the [`contextMenuItems`](../api/treegrid/#contextmenuitems).

To use the context menu, inject the `ContextMenu` module in the treegrid.

The default items are in the following table.

Items| Description
----|----
`AutoFit`|  Auto fit the current column.
`AutoFitAll` | Auto fit all columns.
`Edit`|  Edit the current record.
`Delete` | Delete the current record.
`Save` | Save the edited record.
`Cancel` | Cancel the edited state.
`PdfExport` | Export the treegrid data as Pdf document.
`ExcelExport` | Export the treegrid data as Excel document.
`CsvExport` | Export the treegrid data as CSV document.
`SortAscending` | Sort the current column in ascending order.
`SortDescending` | Sort the current column in descending order.
`FirstPage` | Go to the first page.
`PrevPage` | Go to the previous page.
`LastPage` | Go to the last page.
`NextPage` | Go to the next page.
`AddRow` | Add new row to the treegrid.

{% tab template="treegrid/contextMenu/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' :allowSorting='true' :allowResizing='true' :editSettings='editSettings' :allowPdfExport='true' :allowExcelExport='true' :contextMenuItems="contextMenuItems">
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
import { TreeGridPlugin, Resize, Sort, ContextMenu, Edit, Page, PdfExport, ExcelExport } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
      pageSettings: { pageSize: 7 },
      contextMenuItems: ['AutoFit', 'AutoFitAll', 'SortAscending', 'SortDescending',
        'Copy', 'Edit', 'Delete', 'Save', 'Cancel',
        'PdfExport', 'ExcelExport', 'CsvExport', 'FirstPage', 'PrevPage',
        'LastPage', 'NextPage', 'Group', 'Ungroup'],
    };
  },
  provide: {
      treegrid: [ Resize, Sort, ContextMenu, Edit, Page, PdfExport, ExcelExport ]
    }
}
</script>

```

{% endtab %}

## Custom context menu items

The custom context menu items can be added by defining the [`contextMenuItems`](../api/treegrid/#contextmenuitems) as a collection of
[`contextMenuItemModel`](https://ej2.syncfusion.com/vue/documentation/api/grid/contextMenuItemModel).
Actions for this customized items can be defined in the [`contextMenuClick`](../api/treegrid/#contextmenuclick) event.

In the below sample, we have shown context menu item for parent rows to expand or collapse child rows.

{% tab template="treegrid/contextMenu/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' :contextMenuItems="contextMenuItems" :contextMenuOpen='contextMenuOpen' :contextMenuClick='contextMenuClick'>
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
import { TreeGridPlugin, ContextMenu, Page, TreeGridComponent  } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";
import { BeforeOpenCloseEventArgs } from '@syncfusion/ej2-vue-inputs';
import { MenuEventArgs } from '@syncfusion/ej2-vue-navigations';
import { getValue, isNullOrUndefined } from '@syncfusion/ej2-base';

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      pageSettings: { pageSize: 7 },
      contextMenuItems: [
          {text: 'Collapse the Row', target: '.e-content', id: 'collapserow'},
          {text: 'Expand the Row', target: '.e-content', id: 'expandrow'}
      ],
    };
  },
  provide: {
      treegrid: [ ContextMenu, Page ]
  },
  methods:{
      contextMenuOpen:function (arg: BeforeOpenCloseEventArgs) {
        let elem: Element = arg.event.target as Element;
        let uid = (elem.closest('.e-row') as HTMLTableRowElement).getAttribute('data-uid');
        if (isNullOrUndefined(getValue('hasChildRecords', this.$refs.treegrid.ej2Instances.grid.getRowObjectFromUID(uid).data))) {
            arg.cancel = true;
        } else {
          let flag: boolean = getValue('expanded', this.$refs.treegrid.ej2Instances.grid.getRowObjectFromUID(uid).data);
          let val: string = flag ? 'none' : 'block';
          document.querySelectorAll('li#expandrow')[0].setAttribute('style', 'display: ' + val + ';');
          val = !flag ? 'none' : 'block';
          document.querySelectorAll('li#collapserow')[0].setAttribute('style', 'display: ' + val + ';');
        }
      },
      contextMenuClick:function (args: MenuEventArgs) {
        let selectedRows = this.$refs.treegrid.getSelectedRows() as any;
        let selectedRecords = this.$refs.treegrid.getSelectedRecords() as any;
        if (args.item.id === 'collapserow') {
          this.$refs.treegrid.collapseRow(selectedRows[0] as HTMLTableRowElement, selectedRecords[0]);
        } else {
          this.$refs.treegrid.expandRow(selectedRows[0] as HTMLTableRowElement, selectedRecords[0]);
        }
      }
  }
}
</script>

```

{% endtab %}

> You can hide or show an item in context menu for specific area inside of treegrid by defining the [`target`](..api/grid/contextMenuItemModel/#target) property.