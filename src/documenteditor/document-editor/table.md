---
title: "Tables"
component: "DocumentEditor"
description: "Learn how to insert, select, or delete table, row(s), and column(s) in JavaScript document editor."
---

# Tables

Tables are an efficient way to present information. Document editor can display and edit the tables. You can select and edit tables through keyboard, mouse, or touch interactions. Document editor exposes a rich set of APIs to perform these operations programmatically.

## Create a table

You can create and insert a table at cursor position by specifying the required number of rows and columns.

Refer to the following sample code.

```typescript
 this.$refs.documenteditor.ej2Instances.editor.insertTable(3,3);
```

The maximum size of row and column is limited to 32767 and 63 respectively.

## Insert rows

You can add a row (or several rows) above or below the row at cursor position by using the `insertRow` method. This method accepts the following parameters:

Parameter | Type | Description
----------|------|-------------
above(optional) | boolean | This is optional and if omitted, it takes the value as false and inserts below the row at cursor position.
count(optional) | number | This is optional and if omitted, it takes the value as 1.

Refer to the following sample code.

```typescript
//Inserts a row below the row at cursor position
this.$refs.documenteditor.ej2Instances.editor.insertRow();
//Inserts a row above the row at cursor position
this.$refs.documenteditor.ej2Instances.editor.insertRow(false);
//Inserts three rows below the row at cursor position
this.$refs.documenteditor.ej2Instances.editor.insertRow(true, 3)
```

## Insert columns

You can add a column (or several columns) to the left or right of the column at cursor position by using the `insertColumn` method. This method accepts the following parameters:

Parameter | Type | Description
----------|------|-------------
left(optional) | boolean| This is optional and if omitted, it takes the value as false and inserts to the right of column at cursor position.
count(optional) | number |  This is optional and if omitted, it takes the value as 1.

Refer to the following sample code.

```typescript
//Insert a column to the right of the column at cursor position.
this.$refs.documenteditor.ej2Instances.editor.insertColumn();
//Insert a column to the left of the column at cursor position.
this.$refs.documenteditor.ej2Instances.editor.insertColumn(false);
//Insert two columns to the left of the column at cursor position.
this.$refs.documenteditor.ej2Instances.editor.insertColumn(false, 2);
```

### Select an entire table

If the cursor position is inside a table, you can select the entire table by using the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.selection.selectTable();
```

### Select row

You can select the entire row at cursor position by using the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.selection.selectRow();
```

If current selection spans across cells of different rows, all these rows will be selected.

### Select column

You can select the entire column at cursor position by using the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.selection.selectColumn();
```

If current selection spans across cells of different columns, all these columns will be selected.

### Select cell

You can select the cell at cursor position by using the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.selection.selectCell();
```

## Delete table

Document editor allows you to delete the entire table. You can use the `deleteTable()` method of editor instance, if selection is in table. Refer to the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.editor.deleteTable();
```

## Delete row

Document editor allows you to delete the selected number of rows. You can use the `deleteRow()` method of editor instance to delete the selected number of rows, if selection is in table. Refer to the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.editor.deleteRow();
```

## Delete column

Document editor allows you to delete the selected number of columns. You can use the `deleteColumn ()` method of editor instance to delete the selected number of columns, if selection is in table. Refer to the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.editor.deleteColumn();
```

## Merge cells

You can merge cells vertically, horizontally, or combination of both to a single cell. To vertically merge the cells, the columns within selection should be even in left and right directions. To horizontally merge the cells, the rows within selection should be even in top and bottom direction.
Refer to the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.editor.mergeCells()
```

## How to work with tables

The following sample demonstrates how to delete the table row or columns, merge cells and how to bind the API with button.

```html
<template>
    <div id="app" style="height:330px">
    <div>
        <ejs-toolbar v-bind:clicked='toolbarClickHandler'>
            <e-items>
                <e-item prefixIcon="e-de-icon-Table" tooltipText="Insert Table" id="table"></e-item>
                <e-item type="Separator"></e-item>
                <e-item prefixIcon="e-de-icon-InsertAbove" tooltipText="Insert new row above" id="insert_above"></e-item>
                <e-item prefixIcon="e-de-icon-InsertBelow" tooltipText="Insert new row below" id="insert_below"></e-item>
                <e-item type="Separator"></e-item>
                <e-item prefixIcon="e-de-icon-InsertLeft" tooltipText="Insert new column to the left" id="insert_left"></e-item>
                <e-item prefixIcon="e-de-icon-InsertRight" tooltipText="Insert new column to the right" id="insert_right"></e-item>
                <e-item type="Separator"></e-item>
                <e-item prefixIcon="e-de-icon-DeleteTable" tooltipText="Delete Entire table" id="delete_table"></e-item>
                <e-item prefixIcon="e-de-icon-DeleteRows" tooltipText="Delete the selected row" id="delete_row"></e-item>
                <e-item prefixIcon="e-de-icon-DeleteColumns" tooltipText="Delete the selected column" id="delete_column"></e-item>
                <e-item type="Separator"></e-item>
                <e-item prefixIcon="e-de-icon-Cell" tooltipText="Merge the selected cells" id="merge_cell"></e-item>
                <e-item type="Separator"></e-item>
                <e-item text="Dialog" tooltipText="Open insert table dialog" id="table_dialog"></e-item>
            </e-items>
        </ejs-toolbar>
    </div>
    <ejs-documenteditor ref="documenteditor" :isReadOnly='false' :enableEditor='true' :enableEditorHistory='true' :enableTableDialog='true' :enableSfdtExport='true' :enableContextMenu='true' style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin,  Editor, Selection, EditorHistory, TableDialog, ContextMenu, SfdtExport } from '@syncfusion/ej2-vue-documenteditor';
import { ToolbarPlugin } from "@syncfusion/ej2-vue-navigations";

Vue.use(DocumentEditorPlugin);
Vue.use(ToolbarPlugin);

export default {
    data: function () {
        return {
        };
    },
    provide: {
        DocumentEditor: [Editor, Selection, EditorHistory, TableDialog, ContextMenu, SfdtExport]
    },
    methods: {
        toolbarClickHandler :function(args){
          switch (arg.item.id) {
            case 'table':
              //Insert table API to add table
              this.$refs.documenteditor.ej2Instances.editor.insertTable(3, 2);
              break;
            case 'insert_above':
              //Insert the specified number of rows to the table above to the row at cursor position
              this.$refs.documenteditor.ej2Instances.editor.insertRow(true, 2);
              break;
            case 'insert_below':
              //Insert the specified number of rows to the table below to the row at cursor position
              this.$refs.documenteditor.ej2Instances.editor.insertRow();
              break;
            case 'insert_left':
              //Insert the specified number of columns to the table left to the column at cursor position
              this.$refs.documenteditor.ej2Instances.editor.insertColumn(true, 2);
              break;
            case 'insert_right':
              //Insert the specified number of columns to the table right to the column at cursor position
              this.$refs.documenteditor.ej2Instances.editor.insertColumn();
              break;
            case 'delete_table':
              //Delete the entire table
              this.$refs.documenteditor.ej2Instances.editor.deleteTable();
              break;
            case 'delete_row':
              //Delete the selected number of rows
              this.$refs.documenteditor.ej2Instances.editor.deleteRow();
              break;
            case 'delete_column':
              //Delete the selected number of columns
              this.$refs.documenteditor.ej2Instances.editor.deleteColumn();
              break;
            case 'merge_cell':
              //Merge the selected cells into one (both vertically and horizontally)
              this.$refs.documenteditor.ej2Instances.editor.mergeCells();
              break;
            case 'table_dialog':
              //Opens insert table dialog
              this.$refs.documenteditor.showDialog('Table');
              break;
          }
      }
    },
    mounted() {
      this.$refs.documenteditor.ej2Instances.editor.insertTable(2, 2);
    }
}
</script>
<style>
 @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

## See Also

* [Feature modules](../document-editor/feature-module/)
* [Insert table dialog](../document-editor/dialog#table-dialog/)