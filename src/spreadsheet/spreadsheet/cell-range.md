---
title: "Cell Range"
component: "Spreadsheet"
description: "Learn the various operations that you can perform in range of cells of the Angular Spreadsheet."
---

# Cell Range

A group of cells in a sheet is known as cell range.

## Wrap text

Wrap text allows you to display large content as multiple lines in a single cell. By default, the wrap text support is enabled. Use the [`allowWrap`](../api/spreadsheet/#allowwrap) property to enable or disable the wrap text support in spreadsheet.

Wrap text can be applied or removed to a cell or range of cells in the following ways,

* Using the `wrap` property in `cell`, you can enable or disable wrap text to a cell at initial load.
* Select or deselect wrap button from ribbon toolbar to apply or remove the wrap text to the selected range.
* Using the [`wrap`](../api/spreadsheet/#wrap) method, you can apply or remove the wrap text once the component is loaded.

The following code example shows the wrap text functionality in spreadsheet.

{% tab template="spreadsheet/wrap-text", iframeHeight="450px" , isDefaultActive=true %}

```html
<template>
   <ejs-spreadsheet ref="spreadsheet" :created="created" :showFormulaBar="false">
  <e-sheets>
    <e-sheet name="Movie List">
      <e-ranges>
        <e-range :dataSource="dataSource"></e-range>
      </e-ranges>
      <e-columns>
        <e-column index=1 :width="100"></e-column>
        <e-column :width="140"></e-column>
        <e-column :width="90"></e-column>
        <e-column :width="150"></e-column>
        <e-column :width="120"></e-column>
        <e-column :width="90"></e-column>
        <e-column :width="180"></e-column>
      </e-columns>
      <e-rows>
        <e-row :height="30"></e-row>
        <e-row>
          <e-cells>
            <e-cell :index=7 wrap="true"></e-cell>
          </e-cells>
        </e-row>
        <e-row>
          <e-cells>
            <e-cell :index=7 wrap="true"></e-cell>
          </e-cells>
        </e-row>
        <e-row>
          <e-cells>
            <e-cell :index=7 wrap="true"></e-cell>
          </e-cells>
        </e-row>
        <e-row>
          <e-cells>
            <e-cell :index=7 wrap="true"></e-cell>
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
    }
  },
  methods: {
  created: function () {
      var spreadsheet = this.$refs.spreadsheet;
      spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A1:H1');
      spreadsheet.cellFormat({ verticalAlign: 'middle' }, 'A1:H5');
      spreadsheet.cellFormat({ textAlign: 'center' }, 'A2:B5');
      spreadsheet.cellFormat({ textAlign: 'center' }, 'D2:D5');
      // To wrap the cells from E2 to E5 range
      spreadsheet.wrap('E2:E5');
      // To unwrap the H3 cell
      spreadsheet.wrap('H3', false);
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

### Limitation of Wrap text

The following features have some limitations in wrap text:

* Sorting with wrap text applied data.
* Merge with wrap text.

## Merge cells

Merge cells allows users to span two or more cells in the same row or column into a single cell. When cells with multiple values are merged, top-left most cell data will be the data for the merged cell. By default, the merge cells option is enabled. Use [`allowMerge`](../api/spreadsheet/#allowmerge) property to enable or disable the merge cells option in spreadsheet.

You can merge the range of cells in the following ways,

* Set the `rowSpan` and `colSpan` property in `cell` to merge the number of cells at initial load.
* Select the range of cells and apply merge by selecting the desired option from ribbon toolbar.
* Use [`merge`](../api/spreadsheet/#merge) method to merge the range of cells, once the component is loaded.

The available merge options in spreadsheet are,

| Type | Action |
|-------|---------|
| Merge All | Combines all the cells in a range in to a single cell (default). |
| Merge Horizontally | Combines cells in a range as row-wise. |
| Merge Vertically | Combines cells in a range as column-wise. |
| UnMerge | Splits the merged cells into multiple cells. |

The following code example shows the merge cells operation in spreadsheet.

{% tab template="spreadsheet/merge-cells", iframeHeight="450px" , isDefaultActive=true %}

```html
<template>
   <ejs-spreadsheet ref="spreadsheet" :created="created" :showFormulaBar="false">
  <e-sheets>
    <e-sheet name="Merge Cells">
      <e-ranges>
        <e-range :dataSource="dataSource"></e-range>
      </e-ranges>
      <e-columns>
        <e-column :width=90></e-column>
        <e-column :width=150></e-column>
        <e-column :width=100></e-column>
        <e-column :width=100></e-column>
        <e-column :width=100></e-column>
        <e-column :width=100></e-column>
        <e-column :width=100></e-column>
        <e-column :width=100></e-column>
        <e-column :width=100></e-column>
        <e-column :width=100></e-column>
        <e-column :width=120></e-column>
        <e-column :width=120></e-column>
        <e-column :width=120></e-column>
        <e-column :width=120></e-column>
        <e-column :width=120></e-column>
        <e-column :width=120></e-column>
        <e-column :width=100></e-column>
        <e-column :width=100></e-column>
        <e-column :width=100></e-column>
        <e-column :width=100></e-column>
      </e-columns>
      <e-rows>
        <e-row :height=35></e-row>
        <e-row :height=35>
          <e-cells>
            <e-cell :index=1 :rowSpan=2></e-cell>
            <e-cell :colSpan=2></e-cell>
            <e-cell :index=6 :colSpan=3></e-cell>
            <e-cell :index=10 :rowSpan=2 :colSpan=3></e-cell>
            <e-cell :index=13 :colSpan=2></e-cell>
            <e-cell :index=17 :colSpan=2></e-cell>
          </e-cells>
        </e-row>
        <e-row :height=35>
          <e-cells>
            <e-cell :index=3 :colSpan=3></e-cell>
            <e-cell :index=6 :colSpan=4></e-cell>
            <e-cell :index=13 :colSpan=3></e-cell>
            <e-cell :index=17 :colSpan=2></e-cell>
          </e-cells>
        </e-row>
        <e-row :height=35>
          <e-cells>
            <e-cell :index=2 :colSpan=3></e-cell>
            <e-cell :index=5 :colSpan=2></e-cell>
            <e-cell :index=7 :colSpan=3></e-cell>
            <e-cell :index=15 :colSpan=2></e-cell>
            <e-cell :index=17 :colSpan=2></e-cell>
          </e-cells>
        </e-row>
        <e-row :height=35>
          <e-cells>
            <e-cell :index=2 :colSpan=3></e-cell>
            <e-cell :index=6 :colSpan=4></e-cell>
            <e-cell :index=16 :colSpan=2></e-cell>
          </e-cells>
        </e-row>
        <e-row :height=35>
          <e-cells>
            <e-cell :index=2 :colSpan=4></e-cell>
            <e-cell :index=7 :colSpan=3></e-cell>
            <e-cell :index=15 :colSpan=2></e-cell>
            <e-cell :index=17 :colSpan=2></e-cell>
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
    }
  },
  methods: {
  created: function () {
      var spreadsheet = this.$refs.spreadsheet;
      spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A1:S1');
      spreadsheet.numberFormat('h:mm AM/PM', 'C1:S1');
      spreadsheet.cellFormat({ verticalAlign: 'middle' }, 'A1:S11');
        // Merging the `K4:M4` cells using method
        spreadsheet.merge('K4:M4');
      // Merging the 5th and 6th row cells across 11th, 12th and 13th column
      spreadsheet.merge('K5:M6', 'Vertically');
      // Merging the 18th and 19th column cells across 2nd, 3rd and 4th row
      spreadsheet.merge('N4:O6', 'Horizontally');
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

### Limitation of Merge

The following features have some limitations in Merge:

* Merge with filter.
* Merge with wrap text.

## Data Validation

Data Validation is used to restrict the user from entering the invalid data. You can use the [`allowDataValidation`](../api/spreadsheet/#allowDataValidation) property to enable or disable data validation.

> * The default value for `allowDataValidation` property is `true`.

### Apply Validation

You can apply data validation to restrict the type of data or the values that users enter into a cell.

You can apply data validation by using one of the following ways,

* Select the Data tab in the Ribbon toolbar, and then choose the Data Validation item.
* Use the [`addDataValidation()`](../api/spreadsheet/#addDataValidation) method programmatically.

### Clear Validation

Clear validation feature is used to remove data validations from the specified ranges or the whole worksheet.

You can clear data validation rule by one of the following ways,

* Select the Data tab in the Ribbon toolbar, and then choose the Clear Validation item.
* Use the [`removeDataValidation()`](../api/spreadsheet/#removeDataValidation) method programmatically.

### Highlight Invalid Data

Highlight invalid data feature is used to highlight the previously entered invalid values.

You can highlight an invalid data by using one of the following ways,

* Select the Data tab in the Ribbon toolbar, and then choose the Highlight Invalid Data item.
* Use the [`addInvalidHighlight()`](../api/spreadsheet/#addInvalidHighlight) method programmatically.

### Clear Highlighted Invalid Data

Clear highlight feature is used to remove the highlight from invalid cells.

You can clear the highlighted invalid data by using the following ways,

* Select the Data tab in the Ribbon toolbar, and then choose the Clear Highlight item.
* Use the [`removeInvalidHighlight()`](../api/spreadsheet/#removeInvalidHighlight) method programmatically.

{% tab template="spreadsheet/number-format", iframeHeight="450px" , isDefaultActive=true %}

```html
<template>
 <ejs-spreadsheet ref="spreadsheet" :created="created">
                <e-sheets>
                  <e-sheet name ="PriceDetails">
                    <e-columns>
                      <e-column :width=88></e-column>
                      <e-column :width=88></e-column>
                      <e-column :width=106></e-column>
                      <e-column :width=98></e-column>
                      <e-column :width=88></e-column>
                      <e-column :width=86></e-column>
                      <e-column :width=107></e-column>
                      <e-column :width=81></e-column>
                    </e-columns>
                    <e-rows>
                      <e-row>
                        <e-cells>
                          <e-cell value="Seller Name" style="style"></e-cell>
                          <e-cell value="Customer Id" style="style"></e-cell>
                          <e-cell value="Customer Name" style="style"></e-cell>
                          <e-cell value="Product Name" style="style"></e-cell>
                          <e-cell value="Product Price" style="style"></e-cell>
                          <e-cell value="Sales Date" style="style"></e-cell>
                          <e-cell value="Billing Time" style="style"></e-cell>
                          <e-cell value="Total Price" style="style"></e-cell>
                        </e-cells>
                      </e-row>
                      <e-row>
                       <e-cells>
                          <e-cell value="John"></e-cell>
                          <e-cell value="1" validation="validation"></e-cell>
                          <e-cell value="Nash"></e-cell>
                          <e-cell value="Digger" validation="listValidation"></e-cell>
                          <e-cell value="50000" validation="listValidation1"></e-cell>
                          <e-cell value="04/11/2019"></e-cell>
                          <e-cell value="11:34:32 AM"></e-cell>
                          <e-cell value="1,45,000.00"></e-cell>
                        </e-cells>
                      </e-row>
                      <e-row>
                       <e-cells>
                          <e-cell value="Mike"></e-cell>
                          <e-cell value="2" validation="validation"></e-cell>
                          <e-cell value="Jim"></e-cell>
                          <e-cell value="Cherrypicker" validation="validation1"></e-cell>
                          <e-cell value="45000" validation="listValidation2"></e-cell>
                          <e-cell value="04/11/2019"></e-cell>
                          <e-cell value="10:15:00 AM"></e-cell>
                          <e-cell value="1,40,040.00"></e-cell>
                        </e-cells>
                      </e-row>
                      <e-row>
                       <e-cells>
                          <e-cell value="shane"></e-cell>
                          <e-cell value="3" validation="validation"></e-cell>
                          <e-cell value="Sean"></e-cell>
                          <e-cell value="Kango" validation="listValidation3"></e-cell>
                          <e-cell value="450" validation="listValidation4"></e-cell>
                          <e-cell value="06/25/2019"></e-cell>
                          <e-cell value="01:30:11 PM"></e-cell>
                          <e-cell value="545.00"></e-cell>
                        </e-cells>
                      </e-row>
                      <e-row>
                       <e-cells>
                          <e-cell value="John"></e-cell>
                          <e-cell value="1" validation="validation"></e-cell>
                          <e-cell value="Nash"></e-cell>
                          <e-cell value="JCB" validation="listValidation5"></e-cell>
                          <e-cell value="90000" validation="listValidation6"></e-cell>
                          <e-cell value="09/22/2019"></e-cell>
                          <e-cell value="12:30:02 PM"></e-cell>
                          <e-cell value="1,00,095.00"></e-cell>
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
Vue.use(SpreadsheetPlugin);
export default {
   data: () => {
    return {
      style: { fontWeight : "bold", textAlign: "center" },
      validation: { type: 'WholeNumber', operator: 'NotEqualTo', value1: '1'},
      listValidation: { type: 'List', value1: 'Digger, Digger, Cherrypicker' },
      listValidation1: { type: 'List', value1: '50000,50000,45000' },
      validation1: { type: 'List', value1: 'Cherrypicker, JCB, Wheelbarrow' },
      listValidation2:{ type: 'List', value1: '45000,90000,40' },
      listValidation3:{ type: 'List', value1: 'Kango, Ropes' },
      listValidation4:{ type: 'List', value1: '450, 95' },
      listValidation5:{ type: 'List', value1: 'JCB, Ropes, scaffolding' },
      listValidation6:{ type: 'List', value1: '90000, 95, 10000' }
    }
  },
  methods: {
   created: function () {
      var spreadsheet = this.$refs.spreadsheet;
       //Add Data validation to range.
      spreadsheet.addDataValidation({ type: 'TextLength' , operator: 'LessThanOrEqualTo' , value1: '4' }, 'A2:A5');
      spreadsheet.addDataValidation({ type: 'WholeNumber', operator: 'NotEqualTo', value1: '1' }, 'B2:B5');
      spreadsheet.addDataValidation({ type: 'Date', operator: 'NotEqualTo', value1: '04/11/2019'}, 'F2:F5');
      spreadsheet.addDataValidation({ type: 'Time', operator: 'Between', value1: '10:00:00 AM', value2: '11:00:00 AM' }, 'G2:G5');
      spreadsheet.addDataValidation({ type: 'Decimal', operator: 'LessThan', value1: '100000.00'}, 'H2:H5');
      //Highlight Invalid Data.
      spreadsheet.addInvalidHighlight('A1:H5');
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

### Limitation of Data validation

The following features have some limitations in Data Validation:

* Entire row data validation.
* Insert row between the data validation.
* Copy/paste with data validation.
* Delete cells between data validation applied range.

## See Also

* [Rows and columns](./rows-and-columns)
* [Formatting](./formatting)
* [Hyperlink](./link)
* [Sorting](./sort)
* [Filtering](./filter)