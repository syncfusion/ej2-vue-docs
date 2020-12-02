---
title: "Autocomplete Localization"
component: "AutoComplete"
description: "This section explains the localization support of the Syncfusion vue autocomplete component."
---

# Localization

The Localization library allows you to localize static text content of the
noRecordsTemplate and actionFailureTemplate properties according to the culture
currently assigned to the AutoComplete.

| Locale key | en-US (default) |
|-------------|-------------|
| noRecordsTemplate | No Records Found |
| actionFailureTemplate | The Request Failed |

## Loading translations

To load translation object to your application, use load function of the L10n class.
In the following sample, French culture is set to the AutoComplete and no data
is loaded.

Hence, the noRecordsTemplate property displays its text in French culture initially
and if the sample is run offline, the actionFailureTemplate property displays its text appropriately.

{% tab template="auto-complete/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-autocomplete :dataSource='data' :locale='locale' :fields='fields' sortOrder='sortOrder' :query='query' :placeholder="waterMark" ></ejs-autocomplete>
  </div>
</template>
<script>
import Vue from 'vue';
import { AutoCompletePlugin } from '@syncfusion/ej2-vue-dropdowns';
import { loadCldr,L10n } from '@syncfusion/ej2-base';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

Vue.use(AutoCompletePlugin);

var remoteData = new DataManager({
    url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
    adaptor: new ODataV4Adaptor,
    crossDomain: true
});

L10n.load({
    'fr-BE': {
        'dropdowns': {
            noRecordsTemplate: "Aucun enregistrement trouvé",
            actionFailureTemplate: "Modèle d'échec d'action"
        }
    },

});

export default {
  name: 'app',
   data () {
    return {
      waterMark : 'Trouver un client',
      query: new Query().select(['ContactName', 'CustomerID']),
      data: remoteData,
      locale: 'fr-BE',
      fields: { value: 'ContactName' },
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
    top: 15%;
    width: 30%;
  }
</style>
```

{% endtab %}

## See Also

* [Accessibility](./accessibility/)
* [How to bind the data to the autocomplete](./data-binding/)