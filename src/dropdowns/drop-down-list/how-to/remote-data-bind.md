---
title: "Drop-down list How to get total count"
component: "DropDownList"
description: "This section explains on how to get the total count of list items of the Syncfusion Vue drop-down list component."
---

# Get the total count of data when remote data bind with DropDownList

Before component rendering, you can get the total items count by using
[`actionComplete`](../../api/drop-down-list/#actioncomplete)
&nbsp;event with its result arguments.

After rendering this component, you can get the total items count by using
[`getItems`](../../api/drop-down-list/#getitems) method.

The following example demonstrate how to get the total items count.

{% tab template="drop-down-list/how-to/getItems", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' ref='dropdown' placeholder='Select a customer' :actionComplete='actionComplete' :dataSource='dataSource' :query='query' :fields='fields'></ejs-dropdownlist>
    </div>
    <div style='padding: 50px 0'>
      <button id='first' class="e-control e-btn" v-on:click="getItems"> Get items</button>
    </div>
    <p id='event'> </p>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
import { DataManager,Query,ODataV4Adaptor } from "@syncfusion/ej2-data";
export default {
  data (){
    return {
        query :  new Query().from('Customers').select(['ContactName', 'CustomerID']).take(6),
        dataSource : new DataManager({
          url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
          adaptor: new ODataV4Adaptor,
          crossDomain: true
          }),
        fields: { text: 'ContactName', value: 'CustomerID' }
    }
  },
   methods: {
        actionComplete: function (e) {
            // initially result contains 6 items
            console.log("Before modified the result: " + e.result.length);
            // remove first 2 items from result.
            e.result.splice(0, 2);
            // now displays the result count is 4.
            console.log("After modified the result: " + e.result.length);
        },
        getItems: function(e) {
            // get items count using getItems method
            console.log("Total items count: " + this.$refs.dropdown.getItems().length);
            var element = document.createElement('p');
            element.innerText = "Total items count: " + this.$refs.dropdown.getItems().length;
            document.getElementById('event').append(element);
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