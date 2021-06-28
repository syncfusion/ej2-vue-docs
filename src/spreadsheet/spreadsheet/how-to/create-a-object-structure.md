---
title: "Create a JSON structure"
component: "Spreadsheet"
description: "Learn how to create a JSON structure for the spreadsheet"
---

# Create a JSON structure

This topic guides you to construct a JSON structure that can be passed to the [`openFromJson`](../api/spreadsheet/#openfromjson) method to render the spreadsheet. The JSON structure is an object with the key as `Workbook` and the [`properties`](../api/spreadsheet#properties) of the spreadsheet as value.

```js
{ Workbook: {} }
```

The following properties are the root level properties of the `Workbook` object.

| Property | Type | Description |
|-------|-------|-------|
| activeSheetIndex | number | Specifies active sheet index in the workbook. |
| sheets | `Sheet[]` | Contains a list of sheet properties. |
| definedNames | `DefineName[]` | Specifies the name for a range and uses it in the formula for calculation. |

The following table defines each property of the `Sheet`.

| Property | Type | Description |
|-------|-------|-------|
| name | string | Specifies the name of the sheet. |
| selectedRange | string | Specifies selected range in the sheet. |
| activeCell | string | Specifies active cell within `selectedRange` in the sheet. |
| topLeftCell | string | Specified cell will be positioned at the upper-left corner of the sheet. |
| showHeaders | boolean | Specifies to show or hide column and row headers in the sheet. |
| showGridLines | boolean | Specifies to show or hide gridlines in the sheet. |
| isProtected | boolean | Specifies to protect the cells in the sheet. |
| state | [`SheetState`](./worksheet/#sheet-visibility) | Specifies the sheet visibility state. There must be at least one visible sheet in Spreadsheet. |
| columns | `Column[]` | Contains a list of column properties |
| rows | `Row[]` | Contains a list of row properties |
| protectSettings | [`ProtectSettings`](./protect-sheet/#protect-sheet) | Configures protect and its options. |
| conditionalFormats | `ConditionalFormat[]` | Specifies the conditional formatting for the sheet. |

The following table defines each property of the `Column`.

| Property | Type | Description |
|-------|-------|-------|
| width | number | Specifies the width of the column. |
| customWidth | boolean | Specifies custom width of the column. |
| hidden | boolean | To hide or show the column in the sheet. |

The following table defines each property of the `Row`.

| Property | Type | Description |
|-------|-------|-------|
| height | number | Specifies the height of the row. |
| customHeight | boolean | Specifies the custom height of the row. |
| hidden | boolean | To hide or show the row in the sheet. |
| cells | `Cell[]` | Contains a list of cell properties |

The following table defines each property of the `Cell`.

| Property | Type | Description |
|-------|-------|-------|
| value | string | Defines the value of the cell which can be text or number. |
| formula | string | Defines the formula or expression of the cell. |
| format | string | Specifies the number format code to display the value in specified number format. |
| hyperlink | string | Specifies the hyperlink of the cell. |
| wrap | boolean | Wraps the cell text to the next line, if the text width exceeds the column width. |
| isLocked | boolean | Specifies the cell whether it is locked or not, for allowing edit range in the spreadsheet protect option. |
| colSpan | number | Specifies the column-wise cell merge count. |
| rowSpan | number | Specifies the row-wise cell merge count. |
| style | `CellStyle` | Specifies the cell style options. |
| validation | `Validation` | Specifies the validation of the cell. |
| image | `Image[]` | Specifies the image of the cell. |

The following table defines each property of the `CellStyle`.

| Property | Type | Description |
|-------|-------|-------|
| fontFamily | `FontFamily` | Specifies font family of the cell. |
| verticalAlign | `VerticalAlign` | Specifies vertical align of the cell. |
| textAlign | `TextAlign` | Specifies text align style of the cell. |
| textIndent | string | Specifies text indent style of the cell. |
| color | string | Specifies font color of the cell. |
| backgroundColor | string | Specifies the background color of the cell. |
| fontWeight | `FontWeight` | Specifies font weight of the cell. |
| fontStyle | `FontStyle` | Specifies font style of the cell. |
| fontSize | string | Specifies font size of the cell. |
| textDecoration | `TextDecoration` | Specifies text decoration of the cell. |
| border | string | Specifies border of the cell. |
| borderTop | string | Specifies top border of the cell. |
| borderBottom | string | Specifies bottom border of the cell. |
| borderLeft | string | Specifies left border of the cell. |
| borderRight | string | Specifies right border of the cell. |

```js
type FontFamily = 'Arial' | 'Arial Black' | 'Axettac Demo' | 'Batang' | 'Book Antiqua' | 'Calibri' | 'Courier' | 'Courier New' | 'Din Condensed' | 'Georgia' | 'Helvetica' | 'Helvetica New' | 'Roboto' | 'Tahoma' | 'Times New Roman' | 'Verdana';
type VerticalAlign = 'bottom' | 'middle' | 'top';
type TextAlign = 'left' | 'center' | 'right';
type FontWeight = 'bold' | 'normal';
type FontStyle = 'italic' | 'normal';
type TextDecoration = 'underline' | 'line-through' | 'underline line-through' | 'none';
```

The following table defines each property of the `Validation`.

| Property | Type | Description |
|-------|-------|-------|
| type | `ValidationType` | Specifies Validation Type. |
| operator | `ValidationOperator` | Specifies Validation Operator. |
| value1 | string | Specifies Validation Minimum Value. |
| value2 | string | Specifies Validation Maximum Value. |
| ignoreBlank | boolean | Specifies IgnoreBlank option in Data Validation. |
| inCellDropDown | boolean | Specifies InCellDropDown option in Data Validation. |
| isHighlighted | boolean | Specifies to allow Highlight Invalid Data. |
|  |  |  |

```js
type ValidationType = 'WholeNumber' | 'Decimal' | 'Date' | 'TextLength' | 'List' | 'Time';
type ValidationOperator = 'Between' | 'NotBetween' | 'EqualTo' | 'NotEqualTo' | 'LessThan' | 'GreaterThan' | 'GreaterThanOrEqualTo' | 'LessThanOrEqualTo';
```

The following table defines each property of the `Image`.

| Property | Type | Description |
|-------|-------|-------|
| src | string | Specifies the image source. |
| id | string | Specifies image element id. |
| height | number | Specifies the height of the image. |
| width | number | Specifies the width of the image. |
| top | number | Specifies the top position of the image. |
| left | number | Specifies the left position of the image. |

The following table defines each property of the `Format`.

| Property | Type | Description |
|-------|-------|-------|
| format | string | Specifies the number format code to display the value in specified number format. |
| style | `CellStyle` | Specifies the cell style options. |

The following table defines each property of the `DefinedName`.

| Property | Type | Description |
|-------|-------|-------|
| name | string | Specifies a name for the defined name, which can be used in the formula. |
| scope | string | Specifies scope for the defined name. |
| comment | string | Specifies comment for the defined name. |
| refersTo | string | Specifies reference for the defined name. |

In the following code, the JSON structure is passed to the `openFromJson` method to render the spreadsheet in the `created` event.

```html
<template>
   <ejs-spreadsheet ref="spreadsheet" :created="created"></ejs-spreadsheet>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";
import { jsonData }  from './data.json';
Vue.use(SpreadsheetPlugin);
export default {
   data: () => {
    return {

    }
  },
  methods: {
    created: function () {
        var spreadsheet = this.$refs.spreadsheet;
        spreadsheet.openFromJson({ file: jsonData });
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

Sample link : [`create-a-object-structure`](https://codesandbox.io/s/vue-template-forked-rzkpc)