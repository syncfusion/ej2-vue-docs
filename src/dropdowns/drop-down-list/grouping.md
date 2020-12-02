---
title: "Drop-down list Grouping"
component: "DropDownList"
description: "This section for Syncfusion vue drop-down list component explains the grouping of suggestions based on different categories with individual header."
---

# Grouping

The DropDownList supports wrapping nested elements into a group based on different categories. The category
of each list item can be mapped through the [groupBy](../api/drop-down-list/#fields) field in
the data table. The group header is displayed both as inline and fixed headers. The fixed group header content
is updated dynamically on scrolling the popup list with its category value.

How to group and filter the DropDownList Items, you can check on this video:

`youtube:3KqDc3YnmNE`

In the following sample, vegetables are grouped according on its category using `groupBy` field.

{% tab template="drop-down-list/grouping", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:20px auto 0; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' popupHeight='200px' placeholder='Select a vegetable' :fields='fields' :dataSource='dataSource'></ejs-dropdownlist>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
export default {
  data () {
      var vegetableData =  [
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
        ];
    return {
        dataSource : vegetableData,
        fields : { groupBy: 'Category', text: 'Vegetable', value: 'Id' }
    }
  }
}

</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>
```

{% endtab %}

## Customization

The grouping header is also provided with customization option. This allows custom designing
using the `groupTemplate` property for both inline and fixed headers.

## See Also

* [Group Template support to DropDownList](./templates#group-template).
* [How to disable the fixed group header](./how-to/group-header/)