---
title: "Drop-down list How to disable fixed group"
component: "DropDownList"
description: "This section explains on how to disable the fixed group header in the Syncfusion Vue drop-down list component."
---

# Disable the Fixed group header in DropDownList

The following example demonstrate about how to disable the Fixed group header in DropDownList through CSS by using `visibility` attribute.

{% tab template="drop-down-list/how-to/header", isDefaultActive=true %}

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
.e-ddl .e-dropdownbase .e-fixed-head {
  visibility: hidden;
}
</style>
```

{% endtab %}