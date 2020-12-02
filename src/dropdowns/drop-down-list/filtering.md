---
title: "Drop-down list Filtering"
component: "DropDownList"
description: "This section explains the built-in filtering support with a rich set of filtering configurations in Syncfusion vue drop-down list component."
---

# Filtering

The DropDownList has built-in support to filter data items when `allowFiltering` is enabled. The filter
operation starts as soon as you start typing characters in the search box.

To display filtered items in the popup, filter the required data and return it to the DropDownList
via [updateData](/drop-down-list/api-filteringEventArgs.html#updatedata) method by using the [filtering](../api/drop-down-list/#filtering) event.

How to group and filter the DropDownList Items, you can check on this video:

`youtube:3KqDc3YnmNE`

The following sample illustrates how to query the data source and pass the data to the DropDownList
through the `updateData` method in `filtering` event.

{% tab template="drop-down-list/filtering/default", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:20px auto 0; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' placeholder='Select a country' :allowFiltering='allowFiltering' :filtering='filtering' :dataSource='dataSource' :fields='fields'></ejs-dropdownlist>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
import { DataManager,Query,ODataV4Adaptor,Predicate } from "@syncfusion/ej2-data";

export default {
  data () {
      var searchData = [
            { Index: "s1", Country: "Alaska" }, { Index: "s2", Country: "California" },
            { Index: "s3", Country: "Florida" }, { Index: "s4", Country: "Georgia" }
        ];
    return {
        dataSource : searchData,
        fields : { text: "Country", value: "Index" },
        allowFiltering: true,
    }
  },
  methods: {
        filtering: function(e) {
           var searchData = [
                { Index: "s1", Country: "Alaska" }, { Index: "s2", Country: "California" },
                { Index: "s3", Country: "Florida" }, { Index: "s4", Country: "Georgia" }
            ];
           var query = new Query();
            //frame the query based on search string with filter type.
            query = (e.text != "") ? query.where("Country", "startswith", e.text, true) : query;
            //pass the filter data source, filter query to updateData method.
            e.updateData(searchData, query);
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

## Limit the minimum filter character

When filtering the list items, you can set the limit for character count to raise remote request and fetch
filtered data on the DropDownList. This can be done by manual validation within the filter event handler.

In the following example, the remote request does not fetch the search data until the search key contains three characters

{% tab template="drop-down-list/filtering/min-filter-char", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:20px auto 0; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' placeholder='Select a name' sortOrder="Ascending" :query='query' :allowFiltering='allowFiltering' :filtering='filtering' :dataSource='dataSource' :fields='fields'></ejs-dropdownlist>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
import { DataManager,Query,ODataV4Adaptor,Predicate } from "@syncfusion/ej2-data";

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
           if(e.text == '') e.updateData(searchData);
            else{
            // restrict the remote request until search key contains 3 characters.
                if (e.text.length < 3) { return; }
                var query = new Query().select(['ContactName', 'CustomerID']);
                query = (e.text !== '') ? query.where('ContactName', 'startswith', e.text, true) : query;
                e.updateData(searchData, query);
            }
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

## Change the filter type

While filtering, you can change the filter type to `contains`,
`startsWith`, or `endsWith` for string type within the filter event handler

In the following examples, data filtering is done with `endsWith` type.

{% tab template="drop-down-list/filtering/filter-type", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:20px auto 0; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' placeholder='Select a name' popupHeight='250px' sortOrder="Ascending" :query='query' :allowFiltering='allowFiltering' :filtering='filtering' :dataSource='dataSource' :fields='fields'></ejs-dropdownlist>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
import { DataManager,Query,ODataV4Adaptor,Predicate } from "@syncfusion/ej2-data";

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
           // load overall data when search key empty.
            if(e.text == '') e.updateData(searchData);
            else{
                let query: Query = new Query().select(['ContactName', 'CustomerID']);
                // change the type of filtering
                query = (e.text !== '') ? query.where('ContactName', 'endswith', e.text, true) : query;
                e.updateData(searchData, query);
            }
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

## Case sensitive filtering

Data items can be filtered either with or without case sensitivity using the DataManager. This can be done
by passing the fourth optional parameter of the `where` clause

The following example shows how to perform case-sensitive filter

{% tab template="drop-down-list/filtering/case-sensitive-filter", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:20px auto 0; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' placeholder='Select a name' popupHeight='250px' sortOrder="Ascending" :query='query' :allowFiltering='allowFiltering' :filtering='filtering' :dataSource='dataSource' :fields='fields'></ejs-dropdownlist>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
import { DataManager,Query,ODataV4Adaptor,Predicate } from "@syncfusion/ej2-data";

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
            // load overall data when search key empty.
            if(e.text == '') e.updateData(searchData);
            else{
                let query: Query = new Query().select(['ContactName', 'CustomerID']);
                //enable the case sensitive filtering by passing false to 4th parameter.
                query = (e.text !== '') ? query.where('ContactName', 'startswith', e.text, false) : query;
                e.updateData(searchData, query);
            }
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

## Diacritics Filtering

The DropDownList supports diacritics filtering which will ignore the [diacritics](https://en.wikipedia.org/wiki/Diacritic) and makes it
easier to filter the results in international characters lists when the
[ignoreAccent](../api/drop-down-list/#ignoreaccent) is enabled

In the following sample,data with diacritics are bound as dataSource for DropDownList.

{% tab template="drop-down-list/filtering/diacritics-filter", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:20px auto 0; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' placeholder='Select a value' filterBarPlaceholder='e.g: aero' :ignoreAccent='ignoreAccent' :allowFiltering='allowFiltering' :dataSource='dataSource'></ejs-dropdownlist>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
import { DataManager,Query,ODataV4Adaptor,Predicate } from "@syncfusion/ej2-data";

export default {
  data () {
    return {
        dataSource : [
            'Aeróbics',
            'Aeróbics en Agua',
            'Aerografía',
            'Aeromodelaje',
            'Águilas',
            'Ajedrez',
            'Ala Delta',
            'Álbumes de Música',
            'Alusivos',
            'Análisis de Escritura a Mano'
        ],
        allowFiltering : true,
        ignoreAccent : true
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

## See Also

* [How to limit the search result while filtering](./how-to/search-on-filtering/)
* [How to highlight the matched characters in filtering](./how-to/highlight-filtering/)
* [How to modify the result data using remote data source](./how-to/modify-data/)