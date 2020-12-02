# Customize the icons for pivot table

You can customize the pivot button icons in the pivot table by overriding the class **.pivot-button** with a custom property content as mentioned below.

```html

#PivotView_PivotFieldList .e-icons.e-toggle-field-list::before {
    content: '\e337';
}

```

In the below sample, pivot table is rendered with a customized pivot button icons.

{% tab template="pivot-grid/common", isDefaultActive=true %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview id="pivotview" :dataSourceSettings="dataSourceSettings" :height="height" :showFieldList="showFieldList"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin, FieldList } from "@syncfusion/ej2-vue-pivotview";
import { pivotData } from './datasource.js';

Vue.use(PivotViewPlugin);

export default {
  data () {
    return {
      dataSourceSettings: {
        dataSource: pivotData,
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: [],
        calculatedFieldSettings: [{ name: 'Total', formula: '"Sum(Amount)"+"Sum(Sold)"' }]
      },
      showFieldList: true,
      height: 350
    }
  },
  provide: {
    pivotview: [FieldList]
  }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";

/* csslint ignore:start */
#PivotView_PivotFieldList_Wrapper .e-pivot-button .e-icons.e-dropdown-icon::before,
#PivotView .e-pivot-button .e-icons.e-dropdown-icon::before {
    content: "\e941";
}

#PivotView_PivotFieldList_Wrapper .e-pivot-button .e-icons.e-pv-filtered::before,
#PivotView .e-pivot-button .e-icons.e-pv-filtered::before {
    content: "\e974";
}

#PivotView_PivotFieldList_Wrapper .e-pivot-button .e-icons.e-pv-filter::before,
#PivotView .e-pivot-button .e-icons.e-pv-filter::before {
    content: '\e202';
}

#PivotView_PivotFieldList .e-icons.e-toggle-field-list::before {
    content: '\e337';
}

#PivotView_PivotFieldList_Wrapper .e-pivot-button .e-icons.e-sort::before,
#PivotView .e-pivot-button .e-icons.e-sort::before {
    content: '\e306';
}

#PivotView_PivotFieldList_Wrapper .e-pivot-button .e-icons.e-remove::before,
#PivotView .e-pivot-button .e-icons.e-remove::before {
    content: '\e201';
}

/* csslint ignore:end */
</style>
```

{% endraw %}

{% endtab %}
