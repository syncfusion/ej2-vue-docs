---
title: "Autocomplete Grouping"
component: "AutoComplete"
description: "This section for Syncfusion vue autocomplete component demonstrates the grouping of suggestions based on different categories with individual header."
---

# Grouping

The AutoComplete supports wrapping nested elements into a group based on different
categories. The category of each list item can be mapped through the [`groupBy`](../api/auto-complete/#groupby) field in
the data table. The group header is displayed as both inline and fixed headers. The fixed
group header content is updated dynamically on scrolling the suggestion list with its
category value.

To group the Vue AutoComplete items, you can check on this video:

`youtube:7YycZgH89lk`

In the following sample, vegetables are grouped according on its category using groupBy field.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-autocomplete :dataSource='vegetableData' :fields='fields' :placeholder="waterMark" ></ejs-autocomplete>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';

Vue.use(AutoCompletePlugin);
export default {
  name: 'app',
   data () {
    return {
      waterMark : 'Find a vegetable',
      vegetableData: [
          { Vegetable: 'Cabbage', Category: 'Leafy and Salad', Id: 'item1' },
    { Vegetable: 'Spinach', Category: 'Leafy and Salad', Id: 'item2' },
    { Vegetable: 'Wheat grass', Category: 'Leafy and Salad', Id: 'item3' },
    { Vegetable: 'Yarrow', Category: 'Leafy and Salad', Id: 'item4' },
    { Vegetable: 'Pumpkins', Category: 'Leafy and Salad', Id: 'item5' },
    { Vegetable: 'Chickpea', Category: 'Beans', Id: 'item6' },
    { Vegetable: 'Green bean', Category: 'Beans', Id: 'item7' },
    { Vegetable: 'Horse gram', Category: 'Beans', Id: 'item8' },
    { Vegetable: 'Garlic', Category: 'Bulb and Stem', Id: 'item9' },
    { Vegetable: 'Nopal', Category: 'Bulb and Stem', Id: 'item10' },
    { Vegetable: 'Onion', Category: 'Bulb and Stem', Id: 'item11' }
    ],
    fields: { groupBy: 'Category', value: 'Vegetable' }
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    left: 35%;
    position: absolute;
    top: 10%;
    width: 30%;
  }
</style>
```

{% endtab %}

## See Also

* [Group Template support to AutoComplete](./templates#group-template).