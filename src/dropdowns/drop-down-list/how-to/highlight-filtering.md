---
title: "Drop-down list hightlight the character in filtering"
component: "DropDownList"
description: "This section explains on how to highlight the matched character in filtering Syncfusion Vue drop-down list component."
---

# Highlight the matched character in filtering

By using the `highlightSearch` method, you can highlight the matched character in DropDownList filtering.

The following example demonstrates about how to highlight the matched character in filtering.

{% tab template="drop-down-list/how-to/highlight", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:20px auto 0; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' placeholder='Select a customer' popupHeight='250px' sortOrder="Ascending" :query='query' :allowFiltering='allowFiltering' :filtering='filtering' :dataSource='dataSource' :fields='fields'></ejs-dropdownlist>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
import { DataManager,Query,ODataV4Adaptor,Predicate } from "@syncfusion/ej2-data";
import { DropDownList, FilteringEventArgs, highlightSearch } from '@syncfusion/ej2-dropdowns';

export default {
  data () {
    return {
        dataSource : new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
        }),
        query : new Query().select(['ContactName', 'CustomerID']).take(7),
        fields : { text: 'ContactName', value: 'CustomerID' },
        allowFiltering: true,
    }
  },
  methods: {
        filtering: function(e) {
            var searchData = new DataManager({
                url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
                adaptor: new ODataV4Adaptor,
                crossDomain: true
            });
            var text = e.text;
            var query = new Query().select(['ContactName', 'CustomerID']);
            //frame the query based on search string with filter type.
            query = (e.text !== '') ? query.where('ContactName', 'startswith', e.text, true) : query;
            //pass the filter data source, filter query to updateData method.
            e.updateData(searchData, query);
            setTimeout(() => {
                var popupElement = document.getElementById('dropdownlist_popup');
                // get the list from popup element
                var lists = popupElement.querySelector('ul');
                // pass the element, text, ignore case and filter type as argument to highlightSearch method.
                highlightSearch(lists, text, true, 'StartsWith');
            }, 300);
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
