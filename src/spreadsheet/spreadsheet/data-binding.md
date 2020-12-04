---
title: "Data Binding"
component: "Spreadsheet"
description: "Learn how to bind local and remote data in the Essential JS 2 Spreadsheet control."
---

# Data Binding

The Spreadsheet uses [`DataManager`](../data), which supports both RESTful JSON data services and local JavaScript object array binding to a range. The `dataSource` property can be assigned either with the instance of [`DataManager`](../data) or JavaScript object array collection.

> To bind data to a cell, use `cell data binding` support.

## Local data

To bind local data to the Spreadsheet, you can assign a JavaScript object array to the `dataSource` property.

Refer to the following code example for local data binding.

{% tab template="spreadsheet/local-data-binding", iframeHeight="450px" , isDefaultActive=true %}

```html
<template>
   <ejs-spreadsheet ref="spreadsheet">
   <e-sheets>
          <e-sheet>
            <e-ranges>
              <e-range :dataSource="dataSource"></e-range>
            </e-ranges>
          </e-sheet>
        </e-sheets></ejs-spreadsheet>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";
import { defaultData } from './data.js';
Vue.use(SpreadsheetPlugin);
export default {
   data: () => {
    return {
      dataSource: defaultData,
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-spreadsheet/styles/material.css";
 @import '../node_modules/@syncfusion/ej2-base/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-grids/styles/material.css';
 @import "../node_modules/@syncfusion/ej2-spreadsheet/styles/material.css";
</style>
```

{% endtab %}

> The local data source can also be provided as an instance of the [`DataManager`](../data). By default, [`DataManager`](../data) uses [`JsonAdaptor`](../data/adaptors/#json-adaptor) for local data-binding.

## Remote data

To bind remote data to the Spreadsheet control, assign service data as an instance of [`DataManager`](../data) to the `dataSource` property. To interact with remote data source, provide the service endpoint `url`.

Refer to the following code example for remote data binding.

{% tab template="spreadsheet/remote-data-binding", iframeHeight="450px" , isDefaultActive=true %}

```html
<template>
    <ejs-spreadsheet>
            <e-sheets>
                <e-sheet name="Shipment Details" :columns="columns">
                    <e-ranges>
                        <e-range :dataSource="dataSource" :query="query" :showFieldAsHeader="false" startCell="A2"></e-range>
                    </e-ranges>
                    <e-rows>
                        <e-row>
                            <e-cells>
                                <e-cell value="Order ID"></e-cell>
                                <e-cell value="Customer Name"></e-cell>
                                <e-cell value="Freight"></e-cell>
                                <e-cell value="Ship Name"></e-cell>
                                <e-cell value="Ship City"></e-cell>
                                <e-cell value="Ship Country"></e-cell>
                            </e-cells>
                        </e-row>
                    </e-rows>
                </e-sheet>
            </e-sheets>
        </ejs-spreadsheet>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";
import { DataManager, Query } from "@syncfusion/ej2-data";
import { defaultData } from './data.js';
Vue.use(SpreadsheetPlugin);
export default {
   data: () => {
    return {
     dataSource: new DataManager({
                    // Remote service url
                    url: 'https://js.syncfusion.com/demos/ejServices//wcf/Northwind.svc/Orders',
                    crossDomain: true
                }),
        query: new Query().select(['OrderID', 'CustomerID', 'Freight', 'ShipName', 'ShipCity', 'ShipCountry']).take(200),
        columns: [{ width: 100 }, { width: 130 }, { width: 100 }, { width: 220 }, { width: 150 }, { width: 180 }],
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-spreadsheet/styles/material.css";
 @import '../node_modules/@syncfusion/ej2-base/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-grids/styles/material.css';
 @import "../node_modules/@syncfusion/ej2-spreadsheet/styles/material.css";
</style>
```

{% endtab %}

> By default, `DataManager` uses **ODataAdaptor** for remote data-binding.

## Cell data binding

The Spreadsheet control can bind the data to individual cell in a sheet . To achive this you can use the
`value` property.

Refer to the following code example for cell data binding.

{% tab template="spreadsheet/cell-data-binding", iframeHeight="450px" , isDefaultActive=true %}

```html
<template>
     <ejs-spreadsheet >
            <e-sheets>
                <e-sheet name="Monthly Budget">
                    <e-rows>
                        <e-row>
                            <e-cells>
                                <e-cell value="Category"></e-cell>
                                <e-cell value="Planned cost"></e-cell>
                                <e-cell value="Actual cost"></e-cell>
                            </e-cells>
                        </e-row>
                        <e-row>
                            <e-cells>
                                <e-cell value="Food"></e-cell>
                                <e-cell value="$7000"></e-cell>
                                <e-cell value="$8120"></e-cell>
                            </e-cells>
                        </e-row>
                        <e-row>
                            <e-cells>
                                <e-cell value="Loan"></e-cell>
                                <e-cell value="$1500"></e-cell>
                                <e-cell value="$1500"></e-cell>
                            </e-cells>
                        </e-row>
                        <e-row>
                            <e-cells>
                                <e-cell value="Medical"></e-cell>
                                <e-cell value="$300"></e-cell>
                                <e-cell value="$0"></e-cell>
                            </e-cells>
                        </e-row>
                        <e-row>
                            <e-cells>
                                <e-cell value="Clothing"></e-cell>
                                <e-cell value="$400"></e-cell>
                                <e-cell value="$140"></e-cell>
                            </e-cells>
                        </e-row>
                        <e-row>
                            <e-cells>
                                <e-cell value="Education"></e-cell>
                                <e-cell value="$900"></e-cell>
                                <e-cell value="$750"></e-cell>
                            </e-cells>
                        </e-row>
                        <e-row>
                            <e-cells>
                                <e-cell value="Insurance"></e-cell>
                                <e-cell value="$30"></e-cell>
                                <e-cell value="$30"></e-cell>
                            </e-cells>
                        </e-row>
                    </e-rows>
                    <e-columns>
                        <e-column :width="width1"></e-column>
                        <e-column :width="width2"></e-column>
                        <e-column :width="width1"></e-column>
                    </e-columns>
                </e-sheet>
            </e-sheets>
        </ejs-spreadsheet>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";
import { defaultData } from './data.js';
Vue.use(SpreadsheetPlugin);
export default {
   data: () => {
    return {
        width1: 110,
        width2: 115,
        width3: 100
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-spreadsheet/styles/material.css";
 @import '../node_modules/@syncfusion/ej2-base/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-grids/styles/material.css';
 @import "../node_modules/@syncfusion/ej2-spreadsheet/styles/material.css";
</style>
```

{% endtab %}

> The cell data binding also supports formula, style, number format, and more.

## See Also

* [Filtering](./filter)
* [Sorting](./sort)
* [Hyperlink](./link)
* [`Collaborative Editing`](use-cases/collaborative-editing)