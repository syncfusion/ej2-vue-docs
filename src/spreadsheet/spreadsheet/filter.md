---
title: "Filtering"
component: "Spreadsheet"
description: "This section helps you to view specific rows in the spreadsheet by hiding the other rows."
---

# Filtering

Filtering helps you to view specific rows in the spreadsheet by hiding the other rows. You can use the [`allowFiltering`](../api/spreadsheet/#allowfiltering) property to enable or disable filtering functionality.

> * The default value for `allowFiltering` property is `true`.

By default, the `Filter` module is injected internally into Spreadsheet to perform filtering.

## Apply filter on UI

In the active sheet, select a range of cells to filter by value of the cell. The filtering can be done by any of the following ways:

* Select the filter item in the Ribbon toolbar.
* Right-click the sheet, select the filter item in the context menu.
* Use the [`applyFilter()`](../api/spreadsheet/#applyfilter) method programmatically.
* Use `Ctrl + Shift + L` keyboard shortcut to apply the filter.

> * Use `Alt + Up/Down` keyboard shortcut to open the filter dialog.

## Filter by criteria

The [`applyFilter()`](../api/spreadsheet/#applyfilter) method will apply the filter UI, based on the predicate and range given in the arguments.

> * The [`beforeFilter`](../api/spreadsheet/#beforefilter) event will be triggered before filtering the specified range.
> * The [`filterComplete`](../api/spreadsheet/#filtercomplete) event will be triggered after the filter action is completed successfully.

The following code example shows `filter` functionality in the Spreadsheet control.

{% tab template="spreadsheet/filter", iframeHeight="450px" , isDefaultActive=true %}

```html
<template>
   <ejs-spreadsheet ref="spreadsheet" :allowFiltering='true' :dataBound="dataBound">
   <e-sheets>
          <e-sheet>
            <e-ranges>
              <e-range :dataSource="dataSource"></e-range>
            </e-ranges>
            <e-columns>
              <e-column :width="width1"></e-column>
              <e-column :width="width2"></e-column>
              <e-column :width="width3"></e-column>
              <e-column :width="width2"></e-column>
              <e-column :width="width2"></e-column>
              <e-column :width="width3"></e-column>
              <e-column :width="width1"></e-column>
              <e-column :width="width1"></e-column>
              <e-column :width="width4"></e-column>
              <e-column :width="width1"></e-column>
              <e-column :width="width2"></e-column>
              <e-column :width="width5"></e-column>
            </e-columns>
          </e-sheet>
        </e-sheets></ejs-spreadsheet>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";
import { tradeData } from './data.js';
Vue.use(SpreadsheetPlugin);
export default {
   data: () => {
    return {
      dataSource: tradeData,
      width1: 100,
      width2: 130,
      width3: 96,
      width4: 110,
      width5: 150,
    }
  },
  methods: {
  dataBound: function () {
      var spreadsheet = this.$refs.spreadsheet;
        if (spreadsheet.ej2Instances.activeSheetIndex === 0) {
            var departments = ['Sweden', 'Canada', 'UK'];
            var predicateList = []
            departments.forEach((department) => { predicateList.push({ field: 'D', predicate: 'or', operator: 'equal', value: department }); })
            spreadsheet.applyFilter(predicateList);
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
</style>
```

{% endtab %}

## Filter by cell value

To apply a filter for a cell value, right-click the cell and choose filter -> `Filter By Selected Cell's Value` option from the menu. It applies the filter based on the value of the selected cell in the current sheet.

## Clear filter

After applying filter to a certain column, you may want to clear it to make all filtered rows visible again. It can be done in the following ways,

* Choose `Clear` option in ribbon toolbar under `Filter and Sort`. It clears the filters applied in the spreadsheet for all fields.

* Use the [`clearFilter()`](../api/spreadsheet/#clearfilter) method programmatically, to clear the applied filters in spreadsheet for all fields.

## Clear filter on a field

After filtering, you can clear/reset the filter for a field alone. It can be done in the following ways,

* Click filter icon in the column’s header and then choose `Clear Filter` option from the filter dialog.
* You can right-click on a filtered column cell and choose `Clear Filter from <Column Name>.` option from the context menu.
* Use the [`clearFilter(field)`](../api/spreadsheet/#clearfilter) method programmatically, to clear the filter in a particular column.

## Reapply filter

When you want to reapply the filter after some changes happened in the rows. It can be done in the following ways,

* You can choose `Reapply` option in ribbon toolbar under `Filter and Sort` to reapply the filtered columns again.
* You can right-click on a filtered cell and choose `Reapply` option from the context menu. It reapplies the filters again in the Spreadsheet for all the fields.

## Known error validations

The following errors have been handled for filtering,
* *Out of range validation:* When the selected range is not a used range of the active sheet, it is considered as invalid and the out of range alert with the message `Select a cell or range inside the used range and try again` will be displayed. No filter will be performed if the range is invalid.

## Limitations

The following features have some limitations in Filter:

* Insert/delete row/column between the filter applied cells.
* Merge cells with filter.
* Copy/cut paste the filter applied cells.

## See Also

* [Sorting](./sort)
* [Hyperlink](./link)
* [Undo Redo](./undo-redo)