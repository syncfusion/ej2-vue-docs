---
title: "State Persistence"
component: "Pivot Table"
description: "Describes about persistence in pivot table"
---

# State Persistence

State persistence allows user to maintain the current state of the component along with its report bounded in the browser local storage (cookie). Even if the browser is refreshed or if you move to the next page within the browser, components state will be persisted. State persistence stores the Pivot Table object in the local storage when [`enablePersistence`](https://ej2.syncfusion.com/vue/documentation/api/pivotview#enablepersistence) property in pivot table is set to **true**.

{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview :dataSourceSettings="dataSourceSettings" :height="height" :showGroupingBar="showGroupingBar" :enablePersistence="enablePersistence"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin, GroupingBar } from "@syncfusion/ej2-vue-pivotview";
import { pivotData } from './datasource.js';

Vue.use(PivotViewPlugin);

export default {
  data () {
    return {
      dataSourceSettings: {
        dataSource: pivotData,
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
      },
      height: 350,
      showGroupingBar: true,
      enablePersistence: true
    }
  },
  provide: {
        pivotview: [GroupingBar]
    }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

# Save and Load Pivot Layout

You can save the current layout of the pivot table by using [`getPersistData`](https://ej2.syncfusion.com/vue/documentation/api/pivotview#getpersistdata) in string format. The saved layout can be loaded to pivot table any time by passing the saved data as a parameter to [`loadPersistData`](https://ej2.syncfusion.com/vue/documentation/api/pivotview#loadpersistdata) method in the pivot table.

{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-button id="save-btn" :isPrimary="isPrimary" v-on:click.native="saveBtnClick">Save Layout</ejs-button>
        <ejs-button id="load-btn" :isPrimary="isPrimary" v-on:click.native="loadBtnClick">Load Layout</ejs-button>
        <ejs-pivotview id="pivotview" :dataSourceSettings="dataSourceSettings" :height="height" :showGroupingBar="showGroupingBar" :enablePersistence="enablePersistence"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin, PivotFieldListPlugin, FieldList, GroupingBar } from "@syncfusion/ej2-vue-pivotview";
import { ButtonPlugin, ChangeEventArgs} from "@syncfusion/ej2-vue-buttons";
import { pivotData } from './datasource.js';

Vue.use(PivotViewPlugin);
Vue.use(PivotFieldListPlugin);
Vue.use(ButtonPlugin);
let layout: string;
export default {
  data () {
    return {
      dataSourceSettings: {
        dataSource: pivotData,
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
      },
      height: 350,
      showGroupingBar: true,
      enablePersistence: true,
      isPrimary: true
    }
  },
  provide: {
       pivotview: [GroupingBar]
   }
  methods: {
    saveBtnClick: function(args) {
      let pivotGridObj = document.getElementById('pivotview').ej2_instances[0];
      this.layout = pivotGridObj.getPersistData();
    },
    loadBtnClick: function(args) {
      let pivotGridObj = document.getElementById('pivotview').ej2_instances[0];
      pivotGridObj.loadPersistData(this.layout);
    }
  }
}
</script>
<style>
    @import "@syncfusion/ej2-vue-pivotview/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}