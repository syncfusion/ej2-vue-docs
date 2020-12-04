---
title: "Sort a range by custom list"
component: "Spreadsheet"
description: "Learn how to sort a range of cells by custom list."
---

# Sort a range by custom list

You can also define the sorting of cell values based on your own customized personal list. In this article, custom list is achieved using `custom sort comparer`.

In the following demo, the `Trustworthiness` column is sorted based on the custom lists `Perfect`, `Sufficient`, and `Insufficient`.

{% tab template="spreadsheet/custom-sort", iframeHeight="450px" , isDefaultActive=true %}

```html
<template>
   <ejs-spreadsheet ref="spreadsheet" :allowSorting='true' :dataBound="dataBound" :sortComplete="sortComplete">
   <e-sheets>
          <e-sheet>
            <e-ranges>
              <e-range :dataSource="dataSource"></e-range>
            </e-ranges>
          </e-sheet>
        </e-sheets></ejs-spreadsheet>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";
import { DataManager, DataUtil } from '@syncfusion/ej2-data';
import { tradeData } from './data.js';
Vue.use(SpreadsheetPlugin);
export default {
   data: () => {
    return {
      dataSource: tradeData,
    }
  },
  methods: {
    dataBound: function () {
        var spreadsheet = this.$refs.spreadsheet;
        if (spreadsheet.ej2Instances.activeSheetIndex === 0) {
           spreadsheet.sort({sortDescriptors: { field: 'F',  sortComparer: this.mySortComparer }, containsHeader: true}, 'A1:H20');
        }
    },
    sortComplete: function (args) {
        var spreadsheet = this.$refs.spreadsheet;
        spreadsheet.selectRange(args.range);
        // code here.
    },

    mySortComparer: function (x, y) {
   // custom sort comparer to sort based on the custom list.
    var customList = ['Perfect', 'Sufficient', 'Insufficient'];
    var comparer = DataUtil.fnSort('Ascending');
    return comparer(x ? customList.indexOf(x.value) : x, y ? customList.indexOf(y.value) : y);
     };
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

## See Also

* [Filtering](./filter)
* [Sorting](./sort)
* [Hyperlink](./link)