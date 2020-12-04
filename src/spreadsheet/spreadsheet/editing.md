---
title: "Editing"
component: "Spreadsheet"
description: "This section explains you about the editing feature in the Angular spreadsheet."
---

# Editing

You can edit the contents of a cell directly in the cell or by typing in the formula bar. By default, the editing feature is enabled in the spreadsheet. Use the [`allowEditing`](../api/spreadsheet/#allowediting) property to enable or disable the editing feature.

## Edit cell

You can start editing by one of the following ways,

* Double click a cell to start the edit mode.
* Press `F2` key to edit the active cell.
* Use formula bar to perform editing.
* Use `BACKSPACE` or `SPACE` key to clear the cell content and start the edit mode.
* Using the [`startEdit`](../api/spreadsheet/#startedit) method.

## Save cell

If the cell is in editable state, you can save the edited cell by one of the following ways,

* Perform mouse click on any other cell rather than the current editing cell.
* Press `Enter` or `Tab` keys to save the edited cell content.
* Using the [`endEdit`](../api/spreadsheet/#endedit) method.

## Cancel editing

To cancel the editing without saving the changes, you can use one of the following ways,

* Press `ESCAPE` key, this will remove the editable state and update the unchanged cell content.
* Using the [`closeEdit`](../api/spreadsheet/#closeedit) method.

The following code example shows the editing operation in spreadsheet.

{% tab template="spreadsheet/editing", iframeHeight="450px" , isDefaultActive=true %}

```html
<template>
  <ejs-spreadsheet ref="spreadsheet" :created="created" :showFormulaBar="false" :cellEdit="cellEdit" :beforeCellSave="beforeCellSave">
  <e-sheets>
            <e-sheet selectedRange="E11">
                    <e-ranges>
                      <e-range :dataSource="dataSource"></e-range>
                    </e-ranges>
                    <e-columns>
                      <e-column :width=120></e-column>
                      <e-column :width=180></e-column>
                      <e-column :width=100></e-column>
                      <e-column :width=120></e-column>
                      <e-column :width=120></e-column>
                    </e-columns>
                    <e-rows>
                      <e-row index="10">
                      <e-cells>
                      <e-cell index="3" value="Total Amount:" style="fontStyle"></e-cell>
                      <e-cell formula="=SUM(E2:E10)"></e-cell>
                      </e-cells>
                      </e-row>
                    </e-rows>
                  </e-sheet>
                </e-sheets>
</ejs-spreadsheet>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";
import { data } from './data.js';
Vue.use(SpreadsheetPlugin);
export default {
   data: () => {
    return {
      dataSource: data,
       fontStyle: { fontWeight: 'bold' }
    }
  },
  methods: {
  created: function () {
      var spreadsheet = this.$refs.spreadsheet;
     spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A1:E1');
        spreadsheet.cellFormat({ textAlign: 'center' }, 'A2:A10');
        spreadsheet.cellFormat({ textAlign: 'center' }, 'C2:C10');
        spreadsheet.numberFormat('$#,##0.00', 'D2:D10');
        spreadsheet.numberFormat('$#,##0.00', 'E2:E11');
      },
      cellEdit: function (args) {
       // Preventing the editing in 5th(Amount) column.
        if (args.address.includes('E')) { args.cancel = true; }
      },
    beforeCellSave: function (args) {
      var spreadsheet = this.$refs.spreadsheet;
         // Prevent saving the edited changes in 4th(Rate) column.
        if (args.address.includes('D')) {
            args.cancel = true;
            // Manually removes the editable state without saving the changes. Use `endEdit` method if you want to save the changes.
            spreadsheet.closeEdit();
        }
      }
       },
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-spreadsheet/styles/material.css";
 @import '../node_modules/@syncfusion/ej2-base/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-grids/styles/material.css';
 @import "../node_modules/@syncfusion/ej2-spreadsheet/styles/material.css";
</style>
```

{% endtab %}

## See Also

* [Cell range](./cell-range)
* [Formatting](./formatting)
* [Hyperlink](./link)
* [Undo and Redo](./undo-redo)
* [Unlock the particular cells in the protected sheet](./protect-sheet#unlock-the-particular-cells-in-the-protected-sheet)
