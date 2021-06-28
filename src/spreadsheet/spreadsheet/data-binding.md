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

{% tab template="spreadsheet/remote-data-binding", iframeHeight="450px" %}

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

### Binding with OData services

`OData` is a standardized protocol for creating and consuming data. You can retrieve data from OData service using the DataManager. Refer to the following code example for remote Data binding using OData service.

{% tab template="spreadsheet/remote-data-binding", iframeHeight="450px" %}

```html
<template>
    <ejs-spreadsheet ref="spreadsheet">
            <e-sheets>
                <e-sheet name="Order Details" :columns="columns" :created="created">
                    <e-ranges>
                        <e-range :dataSource="dataSource"></e-range>
                    </e-ranges>
                </e-sheet>
            </e-sheets>
        </ejs-spreadsheet>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";
import { DataManager, ODataAdaptor } from "@syncfusion/ej2-data";
Vue.use(SpreadsheetPlugin);
export default {
   data: () => {
    return {
     dataSource: new DataManager({
                    // Remote service url
                    url: 'https://ej2services.syncfusion.com/production/web-services/api/Orders',
                    adaptor: new ODataAdaptor(),
                    crossDomain: true
                }),
        columns: [{ width: 80 }, { width: 80 }, { width: 80 }, { width: 80 }, { width: 80 }, { width: 80 }, { width: 280 }, { width: 180 }, { width: 80 }, { width: 180 }, { width: 180 }],
    }
  },
  methods: {
    created: function () {
        //Applies cell and number formatting to specified range of the active sheet
        this.$refs.spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center', verticalAlign: 'middle' },'A1:K1');
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

### Web API

You can use WebApiAdaptor to bind spreadsheet with Web API created using OData endpoint.

{% tab template="spreadsheet/remote-data-binding", iframeHeight="450px" %}

```html
<template>
    <ejs-spreadsheet ref="spreadsheet">
            <e-sheets>
                <e-sheet name="Order Details" :columns="columns" :created="created">
                    <e-ranges>
                        <e-range :dataSource="dataSource"></e-range>
                    </e-ranges>
                </e-sheet>
            </e-sheets>
        </ejs-spreadsheet>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";
import { DataManager, WebApiAdaptor } from "@syncfusion/ej2-data";
Vue.use(SpreadsheetPlugin);
export default {
   data: () => {
    return {
     dataSource: new DataManager({
                    // Remote service url
                    url: 'https://ej2services.syncfusion.com/production/web-services/api/Orders',
                    adaptor: new WebApiAdaptor(),
                    crossDomain: true
                }),
        columns: [{ width: 80 }, { width: 80 }, { width: 80 }, { width: 80 }, { width: 80 }, { width: 80 }, { width: 280 }, { width: 180 }, { width: 80 }, { width: 180 }, { width: 180 }],
    }
  },
  methods: {
    created: function () {
        //Applies cell and number formatting to specified range of the active sheet
        this.$refs.spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center', verticalAlign: 'middle' },'A1:K1');
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

## Cell data binding

The Spreadsheet control can bind the data to individual cell in a sheet . To achive this you can use the
`value` property.

Refer to the following code example for cell data binding.

{% tab template="spreadsheet/cell-data-binding", iframeHeight="450px"  %}

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

## Dynamic data binding and Datasource change event

You can dynamically change the datasource of the spreadsheet by changing the `dataSource` property of the `range` object of the `sheet`. The `dataSourceChanged` event handler will be triggered when editing, inserting, and deleting a row in the datasource range. This event will be triggered with a parameter named `action` which indicates the `edit`, `add` and `delete` actions for the respective ones.

The following table defines the arguments of the `dataSourceChanged` event.

| Property | Type | Description |
|-----|-----|-------|
| action | string | Indicates the type of action such as `edit`, `add`, and `delete` performed in the datasource range. |
| data | object[] | Modified data for `edit` action; New data for `add` action; Deleted data for `delete` action. |
| rangeIndex | number | Specifies the range index of the datasource. |
| sheetIndex | number | Specifies the sheet index of the datasource. |

> For `add` action, the value for all the fields will be `null` in the data. In the case that you do not want the primary key field to be null which needs to be updated in the backend service, you can use `edit` action after updating the primary key field to update in the backend service. <br><br>
> For inserting a row at the end of the datasource range, you should insert a row below at the end of the range to trigger the `dataSourceChanged` event with action `add`.

{% tab template="spreadsheet/dynamic-data-binding", iframeHeight="750px" %}

```html
<template>
    <div>
    <div>
      <ejs-button id="changeDataBtn" class="e-btn" v-on:click.native="dataSourceBtnClick" style="margin-bottom: 10px" >Change Datasource</ejs-button>
      <ejs-spreadsheet ref="spreadsheet" :dataSourceChanged="dataSourceChanged">
        <e-sheets>
          <e-sheet name="Car Sales Report">
            <e-ranges>
              <e-range :dataSource="dataSource"></e-range>
            </e-ranges>
            <e-columns>
              <e-column :width="width1"></e-column>
              <e-column :width="width2"></e-column>
              <e-column :width="width2"></e-column>
              <e-column :width="width1"></e-column>
              <e-column :width="width2"></e-column>
              <e-column :width="width3"></e-column>
            </e-columns>
          </e-sheet>
        </e-sheets>
      </ejs-spreadsheet>
    </div>
     <div>
                        <h4><b>Event Trace</b></h4>
                        <div id="evt" style="border: 1px solid #dcdcdc;padding: 10px;">
                                <div style="height:173px;overflow: auto;min-width: 250px;">
                                        <span id="EventLog" style="word-break: normal;"></span>
                                </div>
                                <ejs-button id="clearBtn" class='e-btn'>Clear</ejs-button>
                        </div>
                </div>
  </div>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";
import { tradeData, defaultData } from './data.js';
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
Vue.use(ButtonPlugin);
Vue.use(SpreadsheetPlugin);
export default {
   data: () => {
    return {
      width1: 110,
      width2: 115,
      width3: 100
      dataSource: tradeData
    }
  },
   methods: {
    dataSourceChanged: function (args) {
      this.appendElement("Data source changed with" + "<b>&nbsp;" + args.action + "</b> action<hr>"
      );
    },

    dataSourceBtnClick: function () {
         this.$refs.spreadsheet.ej2Instances.sheets[0].ranges[0].dataSource = defaultData;
    },

    clearBtnClick: function () {
      document.getElementById("EventLog").innerHTML = "";
    },

    appendElement: function (html) {
      var span = document.createElement("span");
      span.innerHTML = html;
      var log = document.getElementById("EventLog");
      log.insertBefore(span, log.firstChild);
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

## Note

You can refer to our [Vue Spreadsheet](https://www.syncfusion.com/vue-ui-components/vue-spreadsheet) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Spreadsheet example](https://ej2.syncfusion.com/vue/demos/#/material/spreadsheet/default.html) to knows how to present and manipulate data.

## See Also

* [Filtering](./filter)
* [Sorting](./sort)
* [Hyperlink](./link)
* [`Collaborative Editing`](use-cases/collaborative-editing)