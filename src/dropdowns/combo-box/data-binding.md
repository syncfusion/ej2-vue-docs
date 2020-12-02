---
title: "Combo box Data binding"
component: "ComboBox"
description: "This section for Syncfusion vue combo box component shows how to bind with local data source and how to fetch data from remote data service."
---

# Data Binding

The ComboBox loads the data either from local data sources or
remote data services using the
[dataSource](../api/combo-box/#datasource) property. It supports
the data type of `array` or `DataManager`.

The ComboBox also supports different kinds of data services such as OData, OData V4, and Web API,
and data formats such as XML, JSON, and JSONP with the help of `DataManager` adaptors.

| Fields | Type | Description |
|------|------|-------------|
| text |  `string` | Specifies the display text of each list item. |
| value |  `number or string` | Specifies the hidden data value which mapped to each list item that should be unique. |
| groupBy |  `string` | Specifies the category under which the list item needs to be grouped. |
| iconCss |  `string` | Specifies the icon class of each list item. |

> When binding complex data to the ComboBox, fields should be mapped correctly. Otherwise, the selected item remains undefined.

## Binding local data

Local data can be represented in two ways as described below.

### 1. Array of simple data

The ComboBox has support to load array of primitive data such as strings and numbers. Here, both value and text field act the same.

{% tab template="combobox/data-binding/simple", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' :dataSource='sportsData' placeholder="Select a game"></ejs-combobox>
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
      sportsData: ['Badminton', 'Cricket', 'Football', 'Golf', 'Tennis']
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

### 2. Array of JSON data

The ComboBox can generate its list items through an array of complex data. For this,
the appropriate columns should be mapped to the
[fields](../api/combo-box/#fields) property.

In the following example, `Id` column and `Game` column from complex data have been mapped to the `value` field and `text` field, respectively.

{% tab template="combobox/data-binding/json", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' :dataSource='sportsData' :fields='fields' placeholder="Select a game"></ejs-combobox>
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
      sportsData: [
        { Id: 'game1', Game: 'Badminton' },
        { Id: 'game2', Game: 'Football' },
        { Id: 'game3', Game: 'Tennis' }
    ],
     fields : { text: 'Game', value: 'Id' }
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

### 3. Array of Complex data

The ComboBox can generate its list items through an array of complex data. For this,
the appropriate columns should be mapped to the
[fields](../api/combo-box/#fields) property.

In the following example, `Code.Id` column and `Country.Name` column from complex data have been mapped
to the `value` field and `text` field, respectively.
{% tab template="combobox/data-binding/complex", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' :dataSource='countriesData' :fields='fields' placeholder="Select a Country"></ejs-combobox>
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
      countriesData: [
            { Country: { Name: 'Australia' }, Code: { Id: 'AU' }},
            { Country: { Name: 'Bermuda' },Code: { Id: 'BM' }},
            { Country:{ Name: 'Canada'}, Code:{ Id: 'CA'} },
            { Country:{Name: 'Cameroon'}, Code:{ Id: 'CM'} },
            { Country:{Name: 'Denmark'}, Code:{ Id: 'DK' }},
            { Country:{Name: 'France'}, Code: { Id:'FR'} }
        ],
     fields : { text: 'Country.Name', value: 'Code.Id' }
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

## Binding remote data

The ComboBox supports retrieval of data from remote data services with the help
of `DataManager` component. The [`Query`](../api/combo-box/#query) property
is used to fetch data from the database and bind it to the ComboBox.

The following sample displays the first 6 contacts from “Customers” table of the `Northwind` Data Service.

{% tab template="combobox/data-binding/remote", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' :dataSource='customerData' :query='query' :fields='fields' sortOrder='Ascending' placeholder="Select a Customer"></ejs-combobox>
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
      customerData : new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
        }),
     query : new Query().from('Customers').select(['ContactName', 'CustomerID']).take(6) ,
     fields : { text: 'ContactName', value: 'CustomerID' } ,
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

* [How to achieve cascading](./how-to/cascading/)
* [How to load data using template](./templates#item-template)
* [How to group the data using header](./grouping/)
* [How to filter the bound data](./filtering/)