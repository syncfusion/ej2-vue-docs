---
title: "ListBox sorting and grouping"
component: "ListBox"
description: "Vue ListBox supports sorting of items in the alphabetical order and group items based on its category."
---

# sorting and grouping

## Sorting

The ListBox supports sorting of available items in the alphabetical order that can be either ascending or descending. This can achieved using
[`sortOrder`](../api/list-box/#sortorder) property. Sort order can be `None`, `Ascending` or `Descending`.

In the following example, the `SortOrder` is set as `Descending`.

{% tab template="list-box/getting-started/getting-started", isDefaultActive=true %}

```html

<template>
  <div id="app">
    <div id='container' style="margin:10px auto 0; width:250px;">
        <ejs-listbox :dataSource='groupA' sortOrder="Descending" :fields="fields" ></ejs-listbox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(ListBoxPlugin);
export default {
  data (){
    return {
groupA: [
    { "Name": "Australia", "Code": "AU" },
    { "Name": "Bermuda", "Code": "BM" },
    { "Name": "Canada", "Code": "CA" },
    { "Name": "Cameroon", "Code": "CM" },
    { "Name": "Denmark", "Code": "DK" },
    { "Name": "France", "Code": "FR" },
    { "Name": "Finland", "Code": "FI" },
    { "Name": "Germany", "Code": "DE" },
    { "Name": "Hong Kong", "Code": "HK" }
];

fields: { text:"Name"}
    }
  }
}

</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>

```

{% endtab %}

## Grouping

To get start quickly about how to `group` the Vue ListBox items, you can check on this video:

`youtube:ZCXxwuXvGrA`

The ListBox supports to wrap the nested element into a group based on its category. The category of each list item can be mapped with
[`groupBy`](../api/list-box/fieldSettingsModel/#groupby) field in the data table.

In the following example, vegetables are grouped based on its category.

{% tab template="list-box/getting-started/getting-started", isDefaultActive=true %}

```html

<template>
  <div id="app">
    <div id='container' style="margin:10px auto 0; width:250px;">
        <ejs-listbox :dataSource='data' :fields="fields" ></ejs-listbox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(ListBoxPlugin);
export default {
  data (){
    return {
data: [
    { "Vegetable": "Cabbage", "Category": "Leafy and Salad", "Id": "item1" },
    { "Vegetable": "Spinach", "Category": "Leafy and Salad", "Id": "item2" },
    { "Vegetable": "Wheat grass", "Category": "Leafy and Salad", "Id": "item3" },
    { "Vegetable": "Yarrow", "Category": "Leafy and Salad", "Id": "item4" },
    { "Vegetable": "Pumpkins", "Category": "Leafy and Salad", "Id": "item5" },
    { "Vegetable": "Chickpea", "Category": "Beans", "Id": "item6" },
    { "Vegetable": "Green bean", "Category": "Beans", "Id": "item7" },
    { "Vegetable": "Horse gram", "Category": "Beans", "Id": "item8" },
    { "Vegetable": "Garlic", "Category": "Bulb and Stem", "Id": "item9" },
    { "Vegetable": "Nopal", "Category": "Bulb and Stem", "Id": "item10" },
    { "Vegetable": "Onion", "Category": "Bulb and Stem", "Id": "item11" }
];

fields: { groupBy:"Category", text:"Vegetable", value:"Id" }
    }
  }
}

</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>

```

{% endtab %}