---
title: "Clipboard"
component: "Spreadsheet"
description: "This section explains you about the Clipboard feature (cut, copy, paste) in the Essential JS 2 spreadsheet."
---

# Clipboard

The Spreadsheet provides support for the clipboard operations (cut, copy, and paste). Clipboard operations can be enabled or disabled by setting the [`enableClipboard`](../api/spreadsheet/#enableclipboard) property in Spreadsheet.

> By default, the `enableClipboard` property is true.

## Cut

It is used to cut the data from selected range of cells, rows or columns in a spreadsheet and make it available in the clipboard.

**User Interface**:

Cut can be done in one of the following ways.

* Using Cut button in the Ribbon’s HOME tab to perform cut operation.
* Using Cut option in the Context Menu.
* Using `Ctrl + X` | `Command + X` keyboard shortcut.
* Using the [`cut`](../api/spreadsheet/#cut) method.

## Copy

It is used to copy the data from selected range of cells, rows or columns in a spreadsheet and make it available in the clipboard.

**User Interface**:

Copy can be done in one of the following ways.

* Using Copy button in the Ribbon’s HOME tab to perform copy operation.
* Using Copy option in the Context Menu.
* Using `Ctrl + C` | `Command + C` keyboard shortcut.
* Using the [`copy`](../api/spreadsheet/#copy) method.

## Paste

It is used to paste the clipboard data to the selected range, rows or columns. You have the following options in Paste,

* `Paste Special` - You can paste the values with formatting.
* `Paste` - You can paste only the values without formatting.

It also performs for external clipboard operation. If you perform cut and paste, clipboard data will be cleared, whereas in copy and paste the clipboard contents will be maintained. If you perform paste inside the copied range, the clipboard data will be cleared.

**User Interface**:

Paste can be done in one of the following ways.

* Using Paste button in the Ribbon’s HOME tab to perform paste operation.
* Using Paste option in the Context Menu.
* Using `Ctrl + V` | `Command + V` keyboard shortcut.
* Using the [`paste`](../api/spreadsheet/#paste) method.

> If you use the Keyboard shortcut key for cut (`Ctrl + X`) | copy (`Ctrl + C`) from other sources, you should use `Ctrl + V` shortcut while pasting into the spreadsheet.

{% tab template="spreadsheet/undo-redo", iframeHeight="450px" %}

```html
<template>
  <div>
    <ejs-button id='xlsx' v-on:click.native="cut">Cut</ejs-button>
    <ejs-button id='xls' v-on:click.native="copy">Copy</ejs-button>
    <ejs-button id='csv' v-on:click.native="paste">Paste</ejs-button>
    <ejs-spreadsheet ref="spreadsheet">
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
  created: function () {
       var spreadsheet = this.$refs.spreadsheet;
    spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A1:H1');
      },
      cut: function (event) {
        var spreadsheet = this.$refs.spreadsheet;
        spreadsheet.cut();
    },
    copy: function (event) {
        var spreadsheet = this.$refs.spreadsheet;
        spreadsheet.copy();
    },
    paste: function (event) {
        var spreadsheet = this.$refs.spreadsheet;
        spreadsheet.paste();
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

</style>
```

{% endtab %}

## Limitations

* External clipboard is not fully supported while copying data from another source and pasting into a spreadsheet, it only works with basic supports (Values, Number, cell, and Text formatting).
* If you copy =SUM(A2,B2) and paste, the formula reference will change depending on the pasted cell address but we don't have support for nested formula(formula reference will be same).
* Clipboard is not supported with conditional formatting (values only pasting).
* We have limitation while copying the whole sheet data and pasting it into another sheet.