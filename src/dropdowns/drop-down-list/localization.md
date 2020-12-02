---
title: "Drop-down list Localization"
component: "DropDownList"
description: "This section explains the localization support of the Syncfusion vue drop-down list component."
---

# Localization

The Localization library allows you to localize static text content of the
[noRecordsTemplate](../api/drop-down-list/#norecordstemplate)
 and [actionFailureTemplate](../api/drop-down-list/#actionfailuretemplate)
&nbsp;properties according to the culture currently assigned to the DropDownList.

| Locale key | en-US (default)  |
|------------|------------------|
| noRecordsTemplate |  No records found |
| actionFailureTemplate | The request failed |

## Loading translations

To load translation object to your application, use load function of the **L10n** class.

In the following sample, French culture is set to the DropDownList and no data is loaded. Hence,
the `noRecordsTemplate` property displays its text in French culture initially, and if the sample is run offline,
the `actionFailureTemplate` property displays its text appropriately.

{% tab template="drop-down-list/locale", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:20px auto 0; width:250px;">
        <br>
        <ejs-dropdownlist id='dropdownlist' placeholder='Sélectionnez un client' locale="fr-BE" :fields='fields' :query='query' :dataSource='dataSource'></ejs-dropdownlist>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
import { DataManager,Query,ODataV4Adaptor,Predicate } from "@syncfusion/ej2-data";
import { L10n } from '@syncfusion/ej2-base';
export default {
  data () {
    var data = new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
        });
    var query = new Query().select(['ContactName', 'CustomerID']).take(0);
    L10n.load({
                'fr-BE': {
                    'dropdowns': {
                        'noRecordsTemplate': "Aucun enregistrement trouvé",
                        'actionFailureTemplate': "Modèle d'échec d'action"
                    }
                }
            });
    return {
        fields: { text: 'ContactName', value: 'CustomerID' },
        dataSource: data,
        query: query
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

* [Accessibility](./accessibility/)
* [How to bind the data to the combobox](./data-binding/)