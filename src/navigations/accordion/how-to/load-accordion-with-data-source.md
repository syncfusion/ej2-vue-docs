---
title: "Load accordion with DataSource"
component: "Accordion"
description: "This example demonstrates how to bind any data object to accordion items in the Essential JS 2 Accordion control."
---

# Load accordion with DataSource

You can bind any data object to Accordion items, by mapping it to [`header`](../../api/accordion/accordionItem#header) and [`content`](../../api/accordion/accordionItem#content)
property.

In the below demo, Data is fetched from an `OData` service using `DataManager`. The result data is formatted as a JSON object with `header`
and `content` fields, which is set to items property of Accordion.

{% tab template="accordion/how-to/accordion-datasource", isDefaultActive=true %}

```html
<template>
    <div id="app">

    <ejs-accordion ref="accordionInc">

    </ejs-accordion>
  </div>
</template>
<script>
import Vue from 'vue';
import { AccordionPlugin } from '@syncfusion/ej2-vue-navigations';
import { DataManager, Query, ODataAdaptor, ReturnOption } from '@syncfusion/ej2-data';
Vue.use(AccordionPlugin);
export default {
  name: 'app',
  data () {

}, mounted(){

  new DataManager({ url: 'https://js.syncfusion.com/ejServices/Wcf/Northwind.svc/Employees', adaptor: new ODataAdaptor})
    .executeQuery(new Query().range(4, 7)).then((e) => {

    var result = e.result;
        var obj = this.$refs.accordionInc.ej2Instances
         var itemsData =[];
        var  mapping =  { header: 'FirstName', content: 'Notes' };
      for(var i= 0; i < result.length; i++) {

        itemsData.push({ header: result[i][mapping.header], content: result[i][mapping.content] });
      }
     obj.items = itemsData;
      obj.refresh();

}
}
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
</style>
```

{% endtab %}
