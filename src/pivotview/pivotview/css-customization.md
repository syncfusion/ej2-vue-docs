---
title: "CSS Customization"
component: "Pivot Table"
description: "CSS Customization allows user to hide axis for the pivot by overriding the styles."
---

# CSS Customization

## Hiding Axis

The visibility of row, column, value and filter axis in Field List and Grouping Bar can be changed using custom CSS setting. To do so, please refer the code sample below:

{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview id="PivotTable" :height="height" :dataSourceSettings="dataSourceSettings" :showGroupingBar="showGroupingBar" :showFieldList="showFieldList"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin, GroupingBar, FieldList } from "@syncfusion/ej2-vue-pivotview";
import { pivotData } from './datasource.js';

Vue.use(PivotViewPlugin);

export default {
  data () {
    return {
      dataSourceSettings: {
        dataSource: pivotData,
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Year', items: ['FY 2015'] }, { name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
      },
      height: 350,
      showGroupingBar: true,
      showFieldList: true
    }
  },
  provide: {
    pivotview: [GroupingBar,FieldList]
  }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";

/* csslint ignore:start */
#PivotTable .e-group-columns {
  display: none;
}
#PivotTable .e-group-filters {
  height: 71px !important;
}

#PivotTable_PivotFieldList_Wrapper .e-field-list-columns{
  display: none;
}
#PivotTable_PivotFieldList_Wrapper .e-field-list-values{
  margin-top: 0px;
  height: 338px;
}
.e-pivotfieldlist-wrapper .e-values {
  height: 310px !important;
}

/* Hiding row axis in grouping bar */
/* #PivotView .e-group-rows {
    display: none;
} */

/* Hiding row axis in field list */
/* .e-pivotfieldlist-wrapper .e-field-list-rows {
    display: none;
} */

/* Hiding value axis in grouping bar */
/* #PivotView .e-group-values {
    display: none;
} */
/* Hiding value axis in field list */
/* .e-pivotfieldlist-wrapper .e-field-list-values {
    display: none;
} */
/* Hiding filter axis in grouping bar */
/* #PivotView .e-group-filters {
    display: none;
} */
/* Hiding filter axis in field list */
/* .e-pivotfieldlist-wrapper .e-field-list-filters {
    display: none;
} */
/* csslint ignore:end */
</style>
```

{% endraw %}

{% endtab %}

## Text Alignment

The alignment of text inside row headers, column headers, value cells and summary cells can be changed using custom CSS setting. To do so, please refer the code sample below:

{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview id="pivotview" :height="height" :dataSourceSettings="dataSourceSettings" :showGroupingBar="showGroupingBar" :showFieldList="showFieldList"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin, GroupingBar, FieldList } from "@syncfusion/ej2-vue-pivotview";
import { pivotData } from './datasource.js';

Vue.use(PivotViewPlugin);

export default {
  data () {
    return {
      dataSourceSettings: {
        dataSource: pivotData,
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Year', items: ['FY 2015'] }, { name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
      },
      height: 350,
      showGroupingBar: true,
      showFieldList: true
    }
  },
  provide: {
    pivotview: [GroupingBar,FieldList]
  }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";

/* csslint ignore:start */
.e-pivotview .e-valuescontent {
  text-align: center !important;
}
/* csslint ignore:end */
</style>
```

{% endraw %}

{% endtab %}

## Customize header, value and summary cell style

The elements in pivot table like header cell, value cell and summary cell style can be customized using built-in CSS names. To do so, please refer the code sample below:

{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview id="PivotTable" :height="height" :dataSourceSettings="dataSourceSettings" :showGroupingBar="showGroupingBar" :showFieldList="showFieldList"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin, GroupingBar, FieldList } from "@syncfusion/ej2-vue-pivotview";
import { pivotData } from './datasource.js';

Vue.use(PivotViewPlugin);

export default {
  data () {
    return {
      dataSourceSettings: {
        dataSource: pivotData,
        drilledMembers: [{ name: 'Year', items: ['FY 2015'] }, { name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
      },
      height: 350,
      showGroupingBar: true,
      showFieldList: true
    }
  },
  provide: {
    pivotview: [GroupingBar,FieldList]
  }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";

/* csslint ignore:start */
.e-pivotview .e-headercell {
  background-color: thistle !important;
}
.e-pivotview .e-rowsheader {
  background-color: skyblue !important;
}
.e-pivotview .e-valuescontent:not(.e-gtot) {
  background-color: pink !important;
}
.e-pivotview .e-gtot {
  background-color: greenYellow !important;
}

/* csslint ignore:end */
</style>
```

{% endraw %}

{% endtab %}