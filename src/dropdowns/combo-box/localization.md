---
title: "Combo box Localization"
component: "ComboBox"
description: "This section explains the localization support of the Syncfusion vue combo box component."
---

# Localization

The Localization library allows you to localize static text content of the
[noRecordsTemplate](../api/combo-box/#norecordstemplate-string) and [actionFailureTemplate](../api/combo-box/#actionfailuretemplate-string)
&nbsp;property according to the culture currently assigned to the ComboBox.

| Locale key | en-US (default)  |
|------------|------------------|
| noRecordsTemplate |  No records found |
| actionFailureTemplate | The request failed |

## Loading translations

To load translation object to your application, use load function of the **L10n** class.

In the following sample, French culture is set to the ComboBox and no data is loaded.
Hence, the `noRecordsTemplate` property displays its text in French culture initially, and
if the sample is run offline, the `actionFailureTemplate` property displays its text appropriately.

{% tab template="combobox/locale", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' locale='fr-BE' :fields='fields' :dataSource='customerData' :query='query' placeholder="Sélectionnez un client"></ejs-combobox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ComboBoxPlugin);
//import DataManager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';
// import L10n class for load function
import { L10n } from '@syncfusion/ej2-base';

L10n.load({
            'fr-BE': {
                'dropdowns': {
                    'noRecordsTemplate': "Aucun enregistrement trouvé",
                    'actionFailureTemplate': "Modèle d'échec d'action"
                }
            }
        });
export default {
  data (){
    return {
        customerData: new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
        }),
        fields : { text: 'ContactName', value: 'CustomerID' },
        query : new Query().select(['ContactName', 'CustomerID']).take(0),
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