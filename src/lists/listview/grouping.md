---
title: "ListView Grouping"
component: "ListView"
description: "Vue listView component supports grouping feature that helps group the logically related items under a category."
---

# Grouping

The ListView supports to wrap the nested element into a group based on the category.
The category of each list item can be mapped with groupBy field in the data table, that also supports single-level navigation.

In the following sample, The cars are grouped based on its category by using the groupBy field.

{% tab template="listview/grouping", isDefaultActive=true %}

```html
<template>
  <div class="control-section">
     <div id = 'group-list'>
    <!-- Group ListView element -->
    <ejs-listview id='sample-list-group' :dataSource='cars' :fields='fields'></ejs-listview>
    </div>
  </div>
</template>
<style>
#sample-list-group {
    border: 1px solid #dddddd;
    border-radius: 3px;
    margin: auto;
}
#group-list {
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
      cars: [
    {
        'text': 'Audi A4',
        'id': '9bdb',
        'category': 'Audi'
    },
    {
        'text': 'Audi A5',
        'id': '4589',
        'category': 'Audi'
    },
    {
        'text': 'BMW 501',
        'id': 'f849',
        'category': 'BMW'
    },
    {
        'text': 'BMW 502',
        'id': '7aff',
        'category': 'BMW'
    }
],
fields: { groupBy: 'category', tooltip: 'text' }
    };
  }
}
</script>
```

{% endtab %}

## Customization

The grouping header can be customized by using the groupTemplate property for both inline and fixed group header.
The complete customization description and explanation with an example is given in the following link.

[Group Template](./customizing-templates#group-template).