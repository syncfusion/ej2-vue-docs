---
title: "Multiselect Filtering"
component: "MultiSelect"
description: "This section for Syncfusion vue multiselect component shows how to bind with local data source and how to consume data from remote data service."
---

# Filtering

The MultiSelect has built-in support to filter data items when [`allowFiltering`](../api/multi-select/#allowfiltering) is enabled. The filter
operation starts as soon as you start typing characters in the MultiSelect input.

To display filtered items in the popup, filter the required data and return it to the MultiSelect
via `updateData` method by using the [filtering](../api/multi-select/#filtering) event.

To filter the Vue MultiSelect dropdown items, you can check on this video:

`youtube:nrmMCOHcxTg`

The following sample illustrates how to query the data source and pass the data to the MultiSelect
through the `updateData` method in `filtering` event.

{% tab template="multi-select/filtering/default", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-multiselect id='multiselect' popupHeight="250px" :allowFiltering='allowFiltering' :filtering='filtering' :dataSource='searchData' :fields='fields' placeholder="Select a country"></ejs-multiselect>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { MultiSelectPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(MultiSelectPlugin);
import { Query } from '@syncfusion/ej2-data';

export default {
  data (){
    return {
        searchData : [
            { Index: "s1", Country: "California" }, { Index: "s2", Country: "Florida" },
            { Index: "s3", Country: "Alaska" }, { Index: "s4", Country: "Georgia" }
        ],
        fields : { text: "Country", value: "Index" },
        allowFiltering : true
        }
  },
   methods: {
        filtering: function(args) {
           var searchData = [
                { Index: "s1", Country: "California" }, { Index: "s2", Country: "Florida" },
                { Index: "s3", Country: "Alaska" }, { Index: "s4", Country: "Georgia" }
            ];
           var query = new Query();
            //frame the query based on search string with filter type.
           query = (args.text != "") ? query.where("Country", "startswith", args.text, true) : query;
            //pass the filter data source, filter query to updateData method.
            args.updateData(searchData, query);
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
</style>
```

{% endtab %}

## Limit the minimum filter character

When filtering the list items, you can set the limit for character count to raise remote request and fetch
filtered data on the MultiSelect. This can be done by manual validation within the filter event handler.

In the following example, the remote request does not fetch the search data until the search key contains three characters.

{% tab template="multi-select/filtering/min-char", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-multiselect id='multiselect' sortOrder='Ascending' popupHeight="250px" :allowFiltering='allowFiltering' :filtering='filtering' :dataSource='searchData' :fields='fields' placeholder="Select a customer"></ejs-multiselect>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { MultiSelectPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(MultiSelectPlugin);
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

export default {
  data (){
    return {
        searchData : new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
        }),
        fields : { text: 'ContactName', value: 'CustomerID' },
        query : new Query().select(['ContactName', 'CustomerID']).take(6),
        allowFiltering : true
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
            if (e.text == '') e.updateData(searchData);
            else {
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
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
</style>
```

{% endtab %}

## Change the filter type

While filtering, you can change the filter type to `contains`,
`startsWith`, or `endsWith` for string type within the filter event handler.

In the following examples, data filtering is done with `endsWith` type.

{% tab template="multi-select/filtering/type", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-multiselect id='multiselect' sortOrder='Ascending' popupHeight="250px" :allowFiltering='allowFiltering' :filtering='filtering' :dataSource='searchData' :query='query' :fields='fields' placeholder="Select a customer"></ejs-multiselect>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { MultiSelectPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(MultiSelectPlugin);
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

export default {
  data (){
    return {
            searchData : new DataManager({
                url: 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Suppliers',
                crossDomain: true
            }),
            fields : { text: "ContactName", key: "SupplierID" },
            query : new Query().select(["SupplierID", "ContactName"]).take(6),
            allowFiltering : true
        }
  },
   methods: {
        filtering: function(e) {
           var searchData = new DataManager({
                url: 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Suppliers',
                crossDomain: true
            });
             if (e.text == '') e.updateData(searchData);
            else {
                var query = new Query().select(["SupplierID", "ContactName"]);
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
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
</style>
```

{% endtab %}

## Case sensitive filtering

Data items can be filtered either with or without case sensitivity using the DataManager. This can be done
by passing the fourth optional parameter of the `where` clause.

The following example shows how to perform case-sensitive filter.

{% tab template="multi-select/filtering/case", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-multiselect id='multiselect' sortOrder='Ascending' :allowFiltering='allowFiltering' :filtering='filtering' :dataSource='sportsData' :fields='fields' placeholder="Select a game"></ejs-multiselect>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { MultiSelectPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(MultiSelectPlugin);
import { Query } from '@syncfusion/ej2-data';

export default {
  data (){
    return {
            sportsData : [
                { id: 'game1', sports: 'Badminton' },
                { id: 'game2', sports: 'Tennis' },
                { id: 'game3', sports: 'Football' }
            ],
            fields : { text: 'sports', value: 'id' }
            allowFiltering : true,
        }
  },
   methods: {
        filtering: function(e) {
           var sportsData = [
                { id: 'game1', sports: 'Badminton' },
                { id: 'game2', sports: 'Tennis' },
                { id: 'game3', sports: 'Football' }
           ];
            if (e.text == '') e.updateData(sportsData);
            else {
                var query = new Query().select(["sports", "id"]);
                //enable the case sensitive filtering by passing false to 4th parameter.
                query = (e.text !== '') ? query.where('sports', 'startsWith', e.text, false) : query;
                e.updateData(sportsData, query);
            }
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
</style>
```

{% endtab %}

## Diacritics Filtering

MultiSelect supports diacritics filtering which will ignore the [diacritics](https://en.wikipedia.org/wiki/Diacritic) and
makes it easier to filter the results in international characters lists
when the [ignoreAccent](../api/multi-select/#ignoreaccent) is enabled.

In the following sample,data with diacritics are bound as dataSource for MultiSelect.

{% tab template="multi-select/filtering/diacritics", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:15px auto 0; width:250px;">
        <br>
        <ejs-multiselect id='multiselect' :dataSource='diacriticsData' :ignoreAccent="ignoreAccent" :allowFiltering='allowFiltering' placeholder="e.g: aero"></ejs-multiselect>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { MultiSelectPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(MultiSelectPlugin);

export default {
  data (){
    return {
      diacriticsData : [
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
        ignoreAccent : true,
        allowFiltering : true
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
</style>
```

{% endtab %}

## See Also

* [How to bind the data](./data-binding/)
* [How to group the data using header](./grouping/)
* [How to add custom value to the MultiSelect](./custom-value/)