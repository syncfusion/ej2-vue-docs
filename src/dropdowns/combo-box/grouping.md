---
title: "Combo box Grouping"
component: "ComboBox"
description: "This section Syncfusion vue combo box component demonstrates the grouping of suggestions based on different categories with individual header."
---

# Grouping

The ComboBox supports wrapping nested elements into a group based on different categories. The category
of each list item can be mapped through the
[groupBy](../api/combo-box/#fields) &nbsp;field in
the data table. The group header is displayed both as inline and fixed headers. The fixed group header content
is updated dynamically on scrolling the popup list with its category value.

To group the Vue ComboBox items, you can check on this video:

`youtube:AMTe9vmvYYE`

In the following sample, the vegetables are grouped according on its category using `groupBy` field.

{% tab template="combobox/grouping", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' :dataSource='vegetableData' :fields='fields' popupHeight="200px" placeholder="select a vegetable"></ejs-combobox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ComboBoxPlugin);

export default {
  data (){
    return {
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

The grouping header is also provided with customization option. This allows custom designing using
the [`groupTemplate`](../api/combo-box/#grouptemplate) property for both inline and fixed headers.

## See Also

* [Group Template support to ComboBox](./templates#group-template).