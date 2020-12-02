# Customizing loading indicator

You can customize the appearance of the loading indicator in the pivot table by using the [`spinnerTemplate`](https://ej2.syncfusion.com/documentation/api/pivotview/#spinnertemplate) property. This property accepts an HTML string which can be used for appearance customization.

> You can also disable the loading indicator by setting [`spinnerTemplate`](https://ej2.syncfusion.com/documentation/api/pivotview/#spinnertemplate) to empty string.

{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview id="pivotview" :dataSourceSettings="dataSourceSettings" :spinnerTemplate="spinnerTemplate" :height="height"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin, IDataSet } from "@syncfusion/ej2-vue-pivotview";
import { DataManager, WebApiAdaptor, Query, ReturnOption } from '@syncfusion/ej2-data';

Vue.use(PivotViewPlugin);

let remoteData: IDataSet[];
new DataManager({
  url: "https://bi.syncfusion.com/northwindservice/api/orders",
  adaptor: new WebApiAdaptor(),
  crossDomain: true
}).executeQuery(new Query().take(8)).then((e: ReturnOption) => {
    let pivotGridObj = document.getElementById('pivotview').ej2_instances[0];
    pivotGridObj.dataSourceSettings.dataSource = e.result as IDataSet[];
  });

export default {
  data () {
    return {
      dataSourceSettings: {
        dataSource: [],
        expandAll: true,
        filters: [],
        columns: [{ name: 'ProductName', caption: 'Product Name' }],
        rows: [{ name: 'ShipCountry', caption: 'Ship Country' }, { name: 'ShipCity', caption: 'Ship City' }],
        formatSettings: [{ name: 'UnitPrice', format: 'C0' }],
        values: [{ name: 'Quantity' }, { name: 'UnitPrice', caption: 'Unit Price' }]
      },
      spinnerTemplate: '<i class="fa fa-cog fa-spin fa-3x fa-fw"></i>',
      height: 350
    }
  }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}
