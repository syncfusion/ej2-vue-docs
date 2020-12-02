---
title: "Hyperlink"
component: "Pivot Table"
description: "User allows to show hyperlink option to the link data for individual cells."
---

# Hyperlink

The pivot table allows you to show hyperlink option to the link data for individual cells that display in the pivot table. Also, the hyperlink can be enabled separately for row header, column header, value, and summary cells using the `hyperlinkSettings`. It can be configured through code behind, during initial rendering. The settings available to show hyperlink to the cells are:

* `showHyperlink`: It allows to set the visibility of hyperlink in all cells.
* `showRowHeaderHyperlink`: It allows to set the visibility of hyperlink in row headers.
* `showColumnHeaderHyperlink`: It allows to set the visibility of hyperlink in column headers.
* `showValueCellHyperlink`: It allows to set the visibility of hyperlink in value cells.
* `showSummaryCellHyperlink`: It allows to set the visibility of hyperlink in summary cells.
* `headerText`: It allows to set the visibility of hyperlink based on header text.
* `conditionalSettings`: It allows to set the visibility of hyperlink based on specific condition.

> By default, the hyperlink options are disabled for all cells in the pivot table.

## Hyperlink for all cells

The pivot table has an option to show hyperlink option to all the cells that are currently displaying. To show hyperlink option, you need to set `showHyperlink` to **true**.

{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview :height="height" :dataSourceSettings="dataSourceSettings" :hyperlinkSettings="hyperlinkSettings"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin } from "@syncfusion/ej2-vue-pivotview";
import { pivotData } from './datasource.js';

Vue.use(PivotViewPlugin);

export default {
  data () {
    return {
      dataSourceSettings: {
        dataSource: pivotData,
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
      },
      height: 350,
      hyperlinkSettings: {
          showHyperlink: true,
          cssClass: 'e-custom-class'
      }
    }
  }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";
.e-custom-class {
  color: #008cff;
  text-decoration: underline;
}

.e-custom-class:hover {
  color: red;
  text-decoration: none;
}
</style>
```

{% endraw %}

{% endtab %}

## Hyperlink for row headers

The pivot table has an option to show hyperlink option to row header cells that are currently displaying. To show hyperlink option for row headers alone, you need to set `showRowHeaderHyperlink` to **true**.

{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview :height="height" :dataSourceSettings="dataSourceSettings" :hyperlinkSettings="hyperlinkSettings"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin } from "@syncfusion/ej2-vue-pivotview";
import { pivotData } from './datasource.js';

Vue.use(PivotViewPlugin);

export default {
  data () {
    return {
      dataSourceSettings: {
        dataSource: pivotData,
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
      },
      height: 350,
      hyperlinkSettings: {
          showRowHeaderHyperlink: true,
          cssClass: 'e-custom-class'
      }
    }
  }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";
.e-custom-class {
  color: #008cff;
  text-decoration: underline;
}

.e-custom-class:hover {
  color: red;
  text-decoration: none;
}
</style>
```

{% endraw %}

{% endtab %}

## Hyperlink for column headers

The pivot table has an option to show hyperlink option to columns header cells that are currently displaying. To show hyperlink option for column headers alone, you need to set `showColumnHeaderHyperlink` to **true**.

{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview :height="height" :dataSourceSettings="dataSourceSettings" :hyperlinkSettings="hyperlinkSettings"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin } from "@syncfusion/ej2-vue-pivotview";
import { pivotData } from './datasource.js';

Vue.use(PivotViewPlugin);

export default {
  data () {
    return {
      dataSourceSettings: {
        dataSource: pivotData,
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
      },
      height: 350,
      hyperlinkSettings: {
          showColumnHeaderHyperlink: true,
          cssClass: 'e-custom-class'
      }
    }
  }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";
.e-custom-class {
  color: #008cff;
  text-decoration: underline;
}

.e-custom-class:hover {
  color: red;
  text-decoration: none;
}
</style>
```

{% endraw %}

{% endtab %}

## Hyperlink for value cells

The pivot table has an option to show hyperlink option to value cells that are currently displaying. To show hyperlink option for values alone, you need to set `showValueCellHyperlink` to **true**.

{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview :height="height" :dataSourceSettings="dataSourceSettings" :hyperlinkSettings="hyperlinkSettings"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin } from "@syncfusion/ej2-vue-pivotview";
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
      hyperlinkSettings: {
          showValueCellHyperlink: true,
          cssClass: 'e-custom-class'
      }
    }
  }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";
.e-custom-class {
  color: #008cff;
  text-decoration: underline;
}

.e-custom-class:hover {
  color: red;
  text-decoration: none;
}
</style>
```

{% endraw %}

{% endtab %}

## Hyperlink for summary cells

The pivot table has an option to show hyperlink option to summary value cells that are currently displaying. To show hyperlink option for summary values alone, you need to set `showSummaryCellHyperlink` to **true**.

{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview :height="height" :dataSourceSettings="dataSourceSettings" :hyperlinkSettings="hyperlinkSettings"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin } from "@syncfusion/ej2-vue-pivotview";
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
      hyperlinkSettings: {
          showSummaryCellHyperlink: true,
          cssClass: 'e-custom-class'
      }
    }
  }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";
.e-custom-class {
  color: #008cff;
  text-decoration: underline;
}

.e-custom-class:hover {
  color: red;
  text-decoration: none;
}
</style>
```

{% endraw %}

{% endtab %}

## Condition based hyperlink

The pivot table has an option to show hyperlink option to the cells based on specific conditions. It can be configured using the `conditionalSettings` option through code behind, during initial rendering. The settings required to sort are:

* `measure`: Specifies the value field name to get visibility of hyperlink option for specific measure.
* `conditions`: Specifies the operator type such as equals, greater than, less than, etc.
* `value1`: Specifies the start value.
* `value2`: Specifies the end value.

{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview :height="height" :dataSourceSettings="dataSourceSettings" :hyperlinkSettings="hyperlinkSettings"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin } from "@syncfusion/ej2-vue-pivotview";
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
      hyperlinkSettings: {
        cssClass: 'e-custom-class',
        conditionalSettings: [{
            measure: 'Sold',
            conditions: 'Between',
            value1: 150,
            value2: 200
        },{
            label: 'Germany',
            conditions: 'GreaterThan',
            value1: 500
        }]
      }
    }
  }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";
.e-custom-class {
  color: #008cff;
  text-decoration: underline;
}

.e-custom-class:hover {
  color: red;
  text-decoration: none;
}
</style>
```

{% endraw %}

{% endtab %}

## Header based hyperlink

The pivot table has an option to show hyperlink option to the cells based on specific row or column. It can be configured using the `headerText` option through code behind, during initial rendering.

{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview :height="height" :dataSourceSettings="dataSourceSettings" :hyperlinkSettings="hyperlinkSettings"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin } from "@syncfusion/ej2-vue-pivotview";
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
      hyperlinkSettings: {
        headerText: 'FY 2015.Q1.Units Sold',
        cssClass: 'e-custom-class'
      }
    }
  }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";
.e-custom-class {
  color: #008cff;
  text-decoration: underline;
}

.e-custom-class:hover {
  color: red;
  text-decoration: none;
}
</style>
```

{% endraw %}

{% endtab %}

## Event

The event [`hyperlinkCellClick`](https://ej2.syncfusion.com/vue/documentation/api/pivotview#hyperlinkcellclick) fires on every hyperlink cell click.

It has following parameters - `Cancel` and `CurrentCell`. The parameter `CurrentCell` is used to customize the host cell element by any means. Meanwhile, when the parameter `Cancel` is set to **true**, applied customization will not be updated to the host cell element.

{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview :height="height" :dataSourceSettings="dataSourceSettings" :hyperlinkSettings="hyperlinkSettings" :hyperlinkCellClick="hyperlinkCellClick"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin } from "@syncfusion/ej2-vue-pivotview";
import { pivotData } from './datasource.js';

Vue.use(PivotViewPlugin);

export default {
  data () {
    return {
      dataSourceSettings: {
        dataSource: pivotData,
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
      },
      height: 350,
      hyperlinkSettings: {
          showHyperlink: true,
          cssClass: 'e-custom-class'
      }
    }
  },
  methods: {
    hyperlinkCellClick: function(args) {
      args.cancel = false;
      args.currentCell.setAttribute("data-url", "https://ej2.syncfusion.com/");//here we have redirected to EJ2 Syncfusion on hyperlinkcell click
    }
  }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";
.e-custom-class {
  color: #008cff;
  text-decoration: underline;
}

.e-custom-class:hover {
  color: red;
  text-decoration: none;
}
</style>
```

{% endraw %}

{% endtab %}

## See Also

* [Apply condition based hyperlink for specific row or column](./how-to/apply-condition-based-hyper-link-for-specific-row-or-column)