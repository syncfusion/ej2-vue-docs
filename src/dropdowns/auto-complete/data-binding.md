---
title: "Autocomplete Data binding"
component: "AutoComplete"
description: "This section for Syncfusion vue autocomplete component shows how to bind with local data source and how to fetch data from remote data service."
---

# Data Binding

The AutoComplete loads the data either from local data sources or remote data services
using the [`dataSource`](../api/auto-complete/#datasource) property. It supports the data type of array or DataManager.
The AutoComplete also supports different kind of data services such as OData, OData V4,
Web API and data formats such as XML, JSON, JSONP with the help of DataManager Adaptors.

| Fields | Type | Description |
|------|------|-------------|
| value | number or string | Specifies the hidden data value mapped to each list item that should contain a unique value. |
| groupBy | string | Specifies the category under which the list item has to be grouped. |
| iconCss | string | Specifies the icon class of each list item |

> While binding complex data to AutoComplete, fields should be mapped correctly. Otherwise, the selected item remains undefined.

## Bind to local data

Local data can be represented in two ways, they are as follows:

### Array of string

The AutoComplete has support to load array of primitive data such as strings and numbers.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-autocomplete :dataSource='sportsData' :placeholder="waterMark" ></ejs-autocomplete>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';

Vue.use(AutoCompletePlugin);
export default {
  name: 'app',
   data () {
    return {
      waterMark : 'Find a game',
      allowCustom: true,
      sportsData: ['Badminton', 'Basketball', 'Cricket',
                'Football', 'Golf', 'Gymnastics',
                'Hockey', 'Rugby', 'Snooker', 'Tennis'
            ]
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    left: 35%;
    position: absolute;
    top: 35%;
    width: 30%;
  }
</style>
```

{% endtab %}

### Array of object

The AutoComplete can generate its list items through an array of complex data. For this,
the appropriate columns should be mapped to the `fields` property.

In the following example, Game column from complex data have been mapped to the value field.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-autocomplete :dataSource='sportsData' :fields='fields' :placeholder="waterMark" ></ejs-autocomplete>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';

Vue.use(AutoCompletePlugin);
export default {
  name: 'app',
   data () {
    return {
      waterMark : 'Find a game',
      sportsData: [
          { Id: 'Game1', Game: 'Badminton' },
    { Id: 'Game2', Game: 'Basketball' },
    { Id: 'Game3', Game: 'Cricket' },
    { Id: 'Game4', Game: 'Football' },
    { Id: 'Game5', Game: 'Golf' },
    { Id: 'Game6', Game: 'Hockey' },
    { Id: 'Game7', Game: 'Rugby' },
    { Id: 'Game8', Game: 'Snooker' }
    ],
    fields: { value: 'Game' }
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    left: 35%;
    position: absolute;
    top: 35%;
    width: 30%;
  }
</style>
```

{% endtab %}

## Array of complex object

The AutoComplete can generate its list items through an array of complex data. For this,
the appropriate columns should be mapped to the `fields` property.
In the following example, `Country.Name` column from complex data have been mapped to the
value field.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-autocomplete :dataSource='countriesData' :fields='fields' :placeholder="waterMark" ></ejs-autocomplete>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';

Vue.use(AutoCompletePlugin);
export default {
  name: 'app',
   data () {
    return {
      waterMark : 'Find a country',
      countriesData: [
          { Country: { Name: 'Australia' }, Code: { Id: 'AU' }},
        { Country: { Name: 'Bermuda' },Code: { Id: 'BM' }},
        { Country:{ Name: 'Canada'}, Code:{ Id: 'CA'} },
        { Country:{Name: 'Cameroon'}, Code:{ Id: 'CM'} },
        { Country:{Name: 'Denmark'}, Code:{ Id: 'DK' }},
        { Country:{Name: 'France'}, Code: { Id:'FR'} },
        { Country:{Name: 'Finland'}, Code:  { Id:'FI'} },
        { Country:{Name: 'Germany'}, Code: { Id:'DE'} },
        { Country:{Name: 'Greenland'}, Code:{ Id: 'GL' }},
        { Country:{Name: 'Hong Kong'}, Code: { Id:'HK'} },
        { Country:{Name: 'India'}, Code:{ Id: 'IN'} },
        { Country:{ Name: 'Italy'}, Code: { Id:'IT'} },
        { Country:{ Name: 'Japan'}, Code: { Id: 'JP'} },
        { Country:{Name: 'Mexico'}, Code: { Id: 'MX' }},
        { Country:{Name: 'Norway'}, Code: { Id: 'NO'} },
        { Country:{Name: 'Poland'}, Code: { Id: 'PL' }},
        { Country:{Name: 'Switzerland'}, Code: { Id: 'CH'} },
        { Country:{Name: 'United Kingdom'},Code: { Id: 'GB'} },
        { Country:{Name: 'United States'}, Code: { Id: 'US'} }
            ],
            fields: { value: 'Country.Name' }
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    left: 35%;
    position: absolute;
    top: 10%;
    width: 30%;
  }
</style>
```

{% endtab %}

## Bind to remote data

The AutoComplete supports retrieval of data from remote data services with the
help of `DataManager` component. The Query property is used to fetch data from the
database and bind it to the AutoComplete.
The following sample displays the first 6 contacts from the Customers table of the `Northwind` data service.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-autocomplete :dataSource='data' :fields='fields' sortOrder='sortOrder' :query='query' :placeholder="waterMark" ></ejs-autocomplete>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

Vue.use(AutoCompletePlugin);

var remoteData = new DataManager({
    url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
    adaptor: new ODataV4Adaptor,
    crossDomain: true
});

export default {
  name: 'app',
   data () {
    return {
      waterMark : 'Find a customer',
      data: remoteData,
      fields: { value: 'ContactName' },
      query: new Query().select(['ContactName', 'CustomerID']),
      sortOrder: 'Ascending'
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    left: 35%;
    position: absolute;
    top: 12%;
    width: 30%;
  }
</style>
```

{% endtab %}

## See Also

* [How to load data using template](./templates#item-template)
* [How to group the data using header](./grouping/)
* [How to filter the bound data](./filtering/)