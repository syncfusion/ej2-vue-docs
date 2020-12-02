---
title: "ListView Checklist"
component: "ListView"
description: "Vue listview supports check-list (list-view with checkbox) feature to select single or multiple list items."
---

# Checklist

The ListView supports checkbox in default and group-lists which is used to select multiple items. The checkbox can be enabled by the `showCheckBox`property.

The Checkbox will be useful in the scenario where we need to select multiple options.
For Example, In Shipping cart we can be able to select or unselect the desired items before checkout.
It will be useful in selecting multiple items that belongs to same category using the group list.

{% tab template="listview/checklist", isDefaultActive=true %}

```html
<template>
  <div class="control-section">
    <div id = 'flat-list'>
    <!-- ListView element -->
    <ejs-listview id='sample-list-flat' :dataSource='data' showCheckBox='true' headerTitle='To Do List' showHeader='true'></ejs-listview>
    </div>
  </div>
</template>
<style>
#sample-list-flat {
    border: 1px solid #dddddd;
    border-radius: 3px;
    margin: auto;
}
#flat-list {
    max-width: 350px;
    padding: 10px;
    margin: auto;
}
</style>
<script>
import Vue from "vue";
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";
Vue.use(ListViewPlugin);
export default {
  data: function() {
    return {
      data: [
        {text: 'Do Meditation', id: '1'},
        {text: 'Go Jogging', id: '2'},
        {text: 'Buy Groceries', id: '3'},
        {text: 'Pay Phone bill', id: '4'},
        {text: 'Play Football with your friends', id: '5'},
    ],
    };
  }
}
</script>
```

{% endtab %}

## Checkbox Position

In ListView the checkbox can be positioned into either `Left` or `Right` side of the list-item text.
This can be achieved by `checkBoxPositon` property. By default, checkbox will be positioned to `Left` of list-item text.

{% tab template="listview/checklist", isDefaultActive=true %}

```html
<template>
  <div class="control-section">
    <div id = 'flat-list'>
    <!-- ListView element -->
    <ejs-listview id='sample-list-flat' :dataSource='data' showCheckBox='true' checkBoxPosition='Right'></ejs-listview>
    </div>
  </div>
</template>
<style>
#sample-list-flat {
    border: 1px solid #dddddd;
    border-radius: 3px;
    margin: auto;
}
#flat-list {
    width: 50%;
    padding: 10px;
    margin: auto;
}
</style>
<script>
import Vue from "vue";
import { ListViewPlugin } from "@syncfusion/ej2-vue-lists";
Vue.use(ListViewPlugin);
export default {
  data: function() {
    return {
      data: [
        { text: 'Hennessey Venom', id: 'list-01' },
        { text: 'Bugatti Chiron', id: 'list-02' },
        { text: 'Bugatti Veyron Super Sport', id: 'list-03' },
        { text: 'SSC Ultimate Aero', id: 'list-04' },
        { text: 'Koenigsegg CCR', id: 'list-05' },
        { text: 'McLaren F1', id: 'list-06' },
        { text: 'Aston Martin One- 77', id: 'list-07' },
        { text: 'Jaguar XJ220', id: 'list-08' },
        { text: 'McLaren P1', id: 'list-09' },
        { text: 'Ferrari LaFerrari', id: 'list-10' },
      ],
    };
  }
}
</script>

```

{% endtab %}
