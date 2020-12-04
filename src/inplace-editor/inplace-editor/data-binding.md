---
title: "Data Binding"
component: "In-place Editor"
description: "Learn how to bind local and remote data for dependent components of the Essential JS 2 Vue In-place Editor component."
---

# Data Binding

The Essential JS 2 components load the data either from local data sources or remote data services using the `dataSource` property and it supports the data type of an array or `DataManager`. Also supports different kind of data services such as OData, OData V4, Web API, and data formats such as XML, JSON, JSONP with the help of `DataManager` adaptors.

## Local

To bind local data to the Essential JS 2 components, you can assign a JavaScript array of object or string to the `dataSource` property. The local data source can also be provided as an instance of the `DataManager`.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html
<template>
<div class="app">
    <table class="table-section">
       <tr>
       <td>Select customer name: </td>
       <td>
       <ejs-inplaceeditor ref="dropObj" id="dropdownEle" mode="Inline" type="DropDownList"  :model="dropdownModel" value="Maria Anders">
       </ejs-inplaceeditor>
       </td>
       </tr>
    </table>
    </div>
</template>

<script>
import Vue from 'vue';
import { InPlaceEditorPlugin, MultiSelect, ActionEventArgs } from "@syncfusion/ej2-vue-inplace-editor";

Vue.use(InPlaceEditorPlugin);

export default {
  name: 'app',
      data () {
        let dropdownData =  [
          { Id: '1', Name: 'Maria Anders' },
          { Id: '2', Name: 'Ana Trujillo' },
          { Id: '3', Name: 'Antonio Moreno' },
          { Id: '4', Name: 'Thomas Hardy' },
          { Id: '5', Name: 'Chiristina Berglund' },
          { Id: '6', Name: 'Hanna Moos' }
        ];
        return {
              dropdownModel: {
            dataSource: dropdownData,
            placeholder: 'Select a customer',
             fields: { text: 'Name' },
        },
        };
    },
    mounted: function() {
   this.dropObj = this.$refs.dropObj.ej2Instances;
    },
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-lists/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-splitbuttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inplace-editor/styles/material.css";

.table-section {
    margin: 0 auto;
    margin-top: 45px;
}

tr td:first-child {
    text-align: right;
    padding-right: 20px;
}
</style>

```

{% endtab %}

## Remote

To bind remote data to the Essential JS 2 Vue components, assign service data as an instance of `DataManager` to the `dataSource` property. To interact with remote data source, provide the endpoint URL.

### OData V4

The OData V4 is an improved version of OData protocols, and the [DataManager](../data/getting-started/) can also retrieve and consume OData V4 services. To fetch data from the server by using `DataManager` with the adaptor property configure as [ODataV4Adaptor](../data/adaptors/#odatav4-adaptor).

In the following sample, In-place Editor renders a `DropDownList` component and its `dataSource` property configured for fetching a data from the server by using `ODataV4Adaptor` with `DataManager`.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html
<template>
<div id="app">
    <table class="table-section">
       <tr>
       <td>Select customer name:</td>
       <td>
       <ejs-inplaceeditor ref="dropObj" id="dropdownEle" mode="Inline" type="DropDownList" value='Maria Anders' :model="dropdownModel">
       </ejs-inplaceeditor>
       </td>
       </tr>
    </table>
  </div>
</template>

<script>
import Vue from 'vue';
import { InPlaceEditorPlugin } from "@syncfusion/ej2-vue-inplace-editor";
Vue.use(InPlaceEditorPlugin);
import { DataManager,Query,ODataV4Adaptor } from "@syncfusion/ej2-data";

export default {
  data (){
    return {
        dropdownModel: {
            dataSource: new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
        }),
        placeholder:"Select a customer",
        query: new Query().from('Customers').select(['ContactName', 'CustomerID']).take(6),
        fields: { text: 'ContactName', value: 'CustomerID' }
        }
    }
  }
}

</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-lists/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-splitbuttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inplace-editor/styles/material.css";

.table-section {
    margin: 0 auto;
    margin-top: 45px;
}

tr td:first-child {
    text-align: right;
    padding-right: 20px;
}
</style>

```

{% endtab %}

### Web API

Data can fetch from the server by using [DataManager](../data/getting-started/) with the adaptor property configure as [WebApiAdaptor](../data/adaptors/#web-api-adaptor).

In the following sample, In-place Editor render a `DropDownList` component and its `dataSource` property configured for fetching a data from the server by using `WebApiAdaptor` with `DataManager`.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html
<template>
<div id="app">
    <table class="table-section">
       <tr>
            <td>select customer name:</td>
        <td>
            <ejs-inplaceeditor ref="dropObj" id="dropdownEle" mode="Inline" type="DropDownList" value='Maria Anders' :model="dropdownModel">
            </ejs-inplaceeditor>
        </td>
        </tr>
    </table>
  </div>
</template>

<script>
import Vue from 'vue';
import { InPlaceEditorPlugin } from "@syncfusion/ej2-vue-inplace-editor";
import { DataManager, WebApiAdaptor, Query } from '@syncfusion/ej2-data';

Vue.use(InPlaceEditorPlugin);

export default {
  data (){
        return {
            dm: new DataManager({
                    url: 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Customers/',
                    adaptor: new WebApiAdaptor
                }).executeQuery(new Query().take(8)).then((e) => {
                    this.dropdownModel.dataSource = e.result.d;
            }),
            dropdownModel: {  
                dataSource: [{}],
                placeholder:"Select a customer",
                query: new Query().from('Customers').select(['ContactName', 'CustomerID']).take(6),
                fields: { text: 'ContactName', value: 'CustomerID' }
            }
        }
    },
    mounted: function() {
        this.dropObj = this.$refs.dropObj.ej2Instances;
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-lists/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-splitbuttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inplace-editor/styles/material.css";

.table-section {
    margin: 0 auto;
    margin-top: 45px;
}

tr td:first-child {
    text-align: right;
    padding-right: 20px;
}
</style>
```

{% endtab %}