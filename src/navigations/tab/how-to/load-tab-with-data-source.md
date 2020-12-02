---
title: "Load tab with DataSource"
component: "Tab"
description: "This example demonstrates how to bind any data object to tab Items in the Essential JS 2 Tab control."
---

# Load tab with DataSource

You can bind any data object to Tab items, by mapping it to a [`header`](../../api/tab/tabItem#header) and [`content`](../../api/tab/tabItem#content)
property.

In the below demo, Data is fetched from an `OData` service using `DataManager`. The result data is formatted as a JSON object with `header`
and `content` fields, which is set to items property of Tab.

{% tab template="tab/how-to/datasource", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-tab ref="TabInstance">

    </ejs-tab>
  </div>
</template>
<script>
import Vue from 'vue';
import { TabPlugin } from '@syncfusion/ej2-vue-navigations';
import { DataManager, Query, ODataAdaptor, ReturnOption } from '@syncfusion/ej2-data';
Vue.use(TabPlugin);
export default {
  name: 'app',
  data () {

}, mounted(){

  new DataManager({ url: 'https://js.syncfusion.com/ejServices/Wcf/Northwind.svc/Employees', adaptor: new ODataAdaptor}).executeQuery(new Query().range(4, 7)).then((e) => {

        var result = e.result;
        var obj = this.$refs.TabInstance.ej2Instances
        var itemsData =[];
        var  mapping =  { header: 'FirstName', content: 'Notes' };
        for(var i= 0; i < result.length; i++) {
        itemsData.push({ header: {text: result[i][mapping.header]}, content: result[i][mapping.content] });
       }
      obj.items = itemsData;
      obj.refresh();

});
}
}
</script>

<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
</style>
```

{% endtab %}
