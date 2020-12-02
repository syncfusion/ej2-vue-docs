---
title: "Combo box Filtering"
component: "ComboBox"
description: "This section for Syncfusion vue combobox component explains the built-in filtering support with a rich set of filtering configurations."
---

# Filtering

The ComboBox has built-in support to filter data items when `allowFiltering` is enabled. The filter
operation starts as soon as you start typing characters in the component.

To display filtered items in the popup, filter the required data and return it to the ComboBox
via [updateData](/api/drop-down-list/filteringEventArgs/#updatedata) method by using
the [filtering](../api/combo-box/#filtering) event.

To filter the Vue ComboBox items, you can check on this video:

`youtube:AMTe9vmvYYE`

The following sample illustrates how to query the data source and pass the data to the ComboBox
through the `updateData` method in `filtering` event.

{% tab template="combobox/filtering/default", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' sortOrder='Ascending' popupHeight="250px" :allowFiltering='allowFiltering' :filtering='filtering' :dataSource='searchData' :fields='fields' placeholder="Select a country"></ejs-combobox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ComboBoxPlugin);
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
</style>
```

{% endtab %}

## Limit the minimum filter character

When filtering the list items, you can set the limit for character count to raise remote request and fetch
filtered data on the ComboBox. This can be done by manual validation within the filter event handler.

In the following example, the remote request does not fetch the search data until the search key contains three characters.

{% tab template="combobox/filtering/min-char", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' sortOrder='Ascending' popupHeight="250px" :allowFiltering='allowFiltering' :filtering='filtering' :dataSource='searchData' :fields='fields' placeholder="Select a customer"></ejs-combobox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ComboBoxPlugin);
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
</style>
```

{% endtab %}

## Change the filter type

While filtering, you can change the filter type to `contains`,
`startsWith`, or `endsWith` for string type within the filter event handler.

In the following examples, data filtering is done with `endsWith` type.

{% tab template="combobox/filtering/type", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' sortOrder='Ascending' popupHeight="250px" :allowFiltering='allowFiltering' :filtering='filtering' :dataSource='searchData' :query='query' :fields='fields' placeholder="Select a customer"></ejs-combobox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ComboBoxPlugin);
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
</style>
```

{% endtab %}

## Case sensitive filtering

Data items can be filtered either with or without case sensitivity using the DataManager. This can be done
by passing the fourth optional parameter of the `where` clause.

The following example shows how to perform case-sensitive filter.

{% tab template="combobox/filtering/case", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' sortOrder='Ascending' popupHeight="250px" :allowFiltering='allowFiltering' :filtering='filtering' :dataSource='searchData' :query='query' :fields='fields' placeholder="Select a customer"></ejs-combobox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ComboBoxPlugin);
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
                //enable the case sensitive filtering by passing false to 4th parameter.
                query = (e.text !== '') ? query.where('ContactName', 'contains', e.text, false) : query;
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

ComboBox supports diacritics filtering which will ignore the [diacritics](https://en.wikipedia.org/wiki/Diacritic) and
makes it easier to filter the results in international characters lists
when the [ignoreAccent](../api/combo-box/#ignoreaccent) is enabled.

In the following sample,data with diacritics are bound as dataSource for ComboBox.

{% tab template="combobox/filtering/diacritics", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' :dataSource='diacriticsData' :ignoreAccent="ignoreAccent" :allowFiltering='allowFiltering' placeholder="e.g: aero"></ejs-combobox>
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
</style>
```

{% endtab %}

## See Also

* [How to achieve autofill while filtering](./how-to#autofill-supported-with-combobox)
* [How to group the data using header](./grouping/)