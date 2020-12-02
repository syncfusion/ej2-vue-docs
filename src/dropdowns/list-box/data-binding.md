---
title: "ListBox data binding and initialization through HTML tags"
component: "ListBox"
description: "Vue ListBox supports databinding with local and remote data source."
---

# Data Binding

The ListBox loads the data either from local data sources or remote data services using the [`dataSource`](../api/list-box/#datasource) property. It supports
the data type of `array` or `DataManager`.

| Fields | Type | Description |
|------|------|-------------|
| [`text`](../api/list-box/fieldSettingsModel/#text) |  `string` | Specifies the display text of each list item. |
| [`value`](../api/list-box/fieldSettingsModel/#value) |  `string` | Specifies the hidden data value mapped to each list item that should contain a unique value. |
| [`groupBy`](../api/list-box/fieldSettingsModel/#groupby) |  `string` | Specifies the category under which the list item has to be grouped. |
| [`iconCss`](../api/list-box/fieldSettingsModel/#iconcss) |  `string` | Specifies the iconCss class that needs to be mapped. |
| [`htmlAttributes`](../api/list-box/fieldSettingsModel/#htmlattributes) |  `string` | Allows additional attributes to configure the elements in various ways to meet the criteria. |

> When binding complex data to the ListBox, fields should be mapped correctly. Otherwise, the selected item remains undefined.

## Local Data

Local data can be represented by the following ways as described below.

### Array of string

The ListBox has support to load array of primitive data such as strings or numbers. Here, both value and text field acts as same.

{% tab template="list-box/getting-started/getting-started", isDefaultActive=true %}

```html

<template>
  <div id="app">
    <div id='container' style="margin:10px auto 0; width:250px;">
        <ejs-listbox :dataSource='data' ></ejs-listbox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(ListBoxPlugin);
export default {
  data (){
    return {
       data: ["Hennessey Venom", "Bugatti Chiron", "Bugatti Veyron Super Sport", "SSC Ultimate Aero", "Koenigsegg CCR", "McLaren F1", "Aston Martin One- 77", "Jaguar XJ220", "McLaren P1", "Ferrari LaFerrari"];
    }
  }
}

</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>

```

{% endtab %}

### Array of object

The ListBox can generate its list items through an array of object data. For this,
the appropriate columns should be mapped to the [`fields`](../api/list-box/#fields) property.

In the following example, `id` and `sports` column from complex data have been mapped to the `value` field and `text` field, respectively.

{% tab template="list-box/getting-started/getting-started", isDefaultActive=true %}

```html

<template>
  <div id="app">
    <div id='container' style="margin:10px auto 0; width:250px;">
        <ejs-listbox :dataSource='data' ></ejs-listbox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(ListBoxPlugin);
export default {
  data (){
    return {
       data: [
            { id: 'game1', sports: 'Badminton' },
            { id: 'game2', sports: 'Cricket'},
            { id: 'game3', sports: 'Football'},
            { id: 'game4', sports: 'Golf'},
            { id: 'game5', sports: 'Tennis'},
            { id: 'game6', sports: 'Basket Ball'},
            { id: 'game7', sports: 'Base Ball'},
            { id: 'game8', sports: 'Hockey'},
            { id: 'game9', sports: 'Volley Ball'}
        ];
    fields:{ text:"sports" }
    }
  }
}

</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>

```

{% endtab %}

### Array of complex object

The ListBox can generate its list items through an array of complex data. For this,
the appropriate columns should be mapped to the [`fields`](../api/list-box/#fields) property.

In the following example, `Sports.Name` column from complex data have been mapped to the `text` field.

{% tab template="list-box/getting-started/getting-started", isDefaultActive=true %}

```html

<template>
  <div id="app">
    <div id='container' style="margin:10px auto 0; width:250px;">
        <ejs-listbox :dataSource='data' :fields="fields" ></ejs-listbox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(ListBoxPlugin);
export default {
  data (){
    return {
       data: [
    { Id: 'game1', Sports: { Name: 'Badminton'} },
    { Id: 'game2', Sports: { Name: 'Cricket'} },
    { Id: 'game3', Sports: { Name: 'Football'} },
    { Id: 'game4', Sports: { Name: 'Golf'} },
    { Id: 'game5', Sports: { Name: 'Tennis'} },
    { Id: 'game6', Sports: { Name: 'Basket Ball'} },
    { Id: 'game7', Sports: { Name: 'Base Ball'} },
    { Id: 'game8', Sports: { Name: 'Hockey'} },
    { Id: 'game9', Sports: { Name: 'Volley Ball'} }
];
fields:{ text:"Sports.Name" }
    }
  }
}

</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>

```

{% endtab %}

## Remote Data

The ListBox supports retrieval of data from remote data services with the help of [`DataManager`](https://ej2.syncfusion.com/documentation/data/getting-started/) component. The [`Query`](../api/list-box/#query) property is used to fetch
data from the database and bind it to the ListBox.

The following sample displays the first 10 products from `Products` table of the `Northwind` Data Service.

{% tab template="list-box/getting-started/getting-started", isDefaultActive=true %}

```html

<template>
  <div id="app">
    <div id='container' style="margin:10px auto 0; width:250px;">
        <ejs-listbox :dataSource='data' :query="query" :fields="fields" ></ejs-listbox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

Vue.use(ListBoxPlugin);
export default {
  data (){
    return {
    data : new DataManager({
        url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
        adaptor: new ODataV4Adaptor
      }),
      query : new Query().from('Products').select('ProductID,ProductName').take(10),
      fields : { text: 'ProductName', value: 'ProductID' }
    }
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>

```

{% endtab %}