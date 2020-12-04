---
title: "Undo Redo"
component: "Spreadsheet"
description: "This section helps you to revert the last action performed and revert the last undo action performed with Spreadsheet."
---

# Undo and Redo

`Undo` option helps you to undone the last action performed and `Redo` option helps you to do the same action which is reverted in the Spreadsheet. You can use the [`allowUndoRedo`](../api/spreadsheet/#allowundoredo) property to enable or disable undo redo functionality in spreadsheet.

> * The default value for `allowUndoRedo` property is `true`.

By default, the `UndoRedo` module is injected internally into Spreadsheet to perform undo redo.

## Undo

It reverses the last action you performed with Spreadsheet. Undo can be done by any of the following ways:

* Select the undo item from HOME tab in Ribbon toolbar.
* Use `Ctrl + Z` keyboard shortcut to perform the undo.
* Use the [`undo`](../api/spreadsheet/#undo) method programmatically.

## Redo

It reverses the last undo action you performed with Spreadsheet. Redo can be done by any of the following ways:

* Select the redo item from HOME tab in Ribbon toolbar.
* Use `Ctrl + Y` keyboard shortcut to perform the redo.
* Use the [`redo`](../api/spreadsheet/#redo) method programmatically.

## Update custom actions in UndoRedo collection

You can update your own custom actions in UndoRedo collection, by using the [`updateUndoRedoCollection`](../api/spreadsheet/#updateUndoRedoCollection) method. And also customize the undo redo operations of your custom action by using `actionComplete` event.

The following code example shows `How to update and customize your own actions for undo redo` functionality in the Spreadsheet control.

{% tab template="spreadsheet/undo-redo", iframeHeight="450px" , isDefaultActive=true %}

```html
<template>
  <div>
    <ejs-button id='customBtn' v-on:click.native="updateCollection">add/remove Class</ejs-button>
    <ejs-spreadsheet ref="spreadsheet" :actionComplete="actionComplete">
      <e-sheets>
          <e-sheet>
            <e-ranges>
              <e-range :dataSource="dataSource"></e-range>
            </e-ranges>
             <e-columns>
              <e-column :width="width1"></e-column>
              <e-column :width="width2"></e-column>
            </e-columns>
          </e-sheet>
        </e-sheets></ejs-spreadsheet>
        <div>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin, getRangeIndexes } from "@syncfusion/ej2-vue-spreadsheet";
import { addClass, removeClass } from '@syncfusion/ej2-base';
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { defaultData } from './data.js';
Vue.use(SpreadsheetPlugin);
Vue.use(ButtonPlugin);
export default {
   data: () => {
    return {
      dataSource: defaultData,
      width1: 130,
      width2: 96,
    }
  },
  methods: {
   actionComplete: function (args) {
        var actionEvents = args;
         var spreadsheet = this.$refs.spreadsheet;
        if (actionEvents.eventArgs.action == "customCSS") {
            var Element = spreadsheet.ej2Instances.getCell(actionEvents.eventArgs.rowIdx,actionEvents.eventArgs.colIdx);
            if (actionEvents.eventArgs.requestType == "undo") {
                removeClass([Element],'customClass'); // To remove the custom class in undo action
            }
            else {
                addClass([Element],'customClass');// To add the custom class in redo action
            }
        }
    },

    updateCollection: function() {
    var spreadsheet = this.$refs.spreadsheet;
    var cell = spreadsheet.ej2Instances.getActiveSheet().activeCell;
    var cellIdx = getRangeIndexes(cell);
    var Element = spreadsheet.ej2Instances.getCell(cellIdx[0], cellIdx[1]);
    if (!Element.classList.contains("customClass")) {
        addClass([Element], 'customClass'); // To add the custom class in active cell element
        spreadsheet.ej2Instances.updateUndoRedoCollection({ eventArgs: { class: 'customClass', rowIdx: cellIdx[0], colIdx: cellIdx[1], action: 'customCSS' } }); // To update the undo redo collection
    }
   }
  }
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

  .customClass.e-cell {
                      background-color: red;
                }
</style>
```

{% endtab %}

## See Also

* [Sorting](./sort)
* [Filtering](./filter)
* [Hyperlink](./link)