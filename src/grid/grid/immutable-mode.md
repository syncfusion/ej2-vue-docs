---
title: "Immutable"
component: "Grid"
description: "Learn how to use immutable data in the Essential JS 2 DataGrid control. Also learn about the limitations of this feature."
---

# Immutable Mode

The immutable mode optimizes the Grid re-rendering performance by using the object reference and [`deep compare`](https://dmitripavlutin.com/how-to-compare-objects-in-javascript/#4-deep-equality) concept. When performing the Grid actions, it will only re-render the modified or newly added rows and prevent the re-rendering of the unchanged rows.

To enable this feature, you have to set the [`enableImmutableMode`](../api/grid/#enableImmutableMode) property as **true**.

>* This feature uses the primary key value for data comparison. So, you need to provide the [`isPrimaryKey`](../api/grid/column/#isprimarykey) column.

{% tab template="grid/immutable-mode" %}

```html
<template>
    <div id="app">
        <table>
      <tbody>
        <tr>
          <td>
            <span id="immutableDelete"></span>
          </td>
        </tr>
        <tr>
          <td>
            <span id="normalDelete"></span>
          </td>
        </tr>
        <tr>
          <td>
            <div>
              <ejs-button cssClass="e-info" v-on:click.native="addTopEvent"
                >Add 5 rows at top</ejs-button
              >
              <ejs-button cssClass="e-info" v-on:click.native="addBottomEvent"
                >Add 5 rows at bottom</ejs-button
              >
              <ejs-button cssClass="e-info" v-on:click.native="deleteEvent"
                >Delete 5 rows</ejs-button
              >
              <ejs-button cssClass="e-info" v-on:click.native="sortEvent"
                >Sort Order ID</ejs-button
              >
              <ejs-button cssClass="e-info" v-on:click.native="pageEvent"
                >Paging</ejs-button
              >
            </div>
          </td>
        </tr>
        <tr>
          <td>
            <span><b>Immutable Grid</b></span>
            <ejs-grid
              ref="immutablegrid"
              :dataSource="data"
              height="250"
              :enableImmutableMode="true"
              :allowPaging="true"
              :pageSettings="pageSettings"
              :beforeDataBound="immutableBeforeDataBound"
              :dataBound="immutableDataBound"
            >
              <e-columns>
                <e-column
                  field="OrderID"
                  headerText="Order ID"
                  width="120"
                  isPrimaryKey="true"
                  textAlign="Right"
                ></e-column>
                <e-column
                  field="ProductName"
                  headerText="Product Name"
                  width="160"
                ></e-column>
                <e-column
                  field="ProductID"
                  headerText="Product ID"
                  width="120"
                  textAlign="Right"
                ></e-column>
                <e-column
                  field="CustomerID"
                  headerText="Customer ID"
                  width="120"
                ></e-column>
                <e-column
                  field="CustomerName"
                  headerText="Customer Name"
                  width="160"
                ></e-column>
              </e-columns>
            </ejs-grid>
          </td>
        </tr>
        <tr>
          <td>
            <span><b>Normal Grid</b></span>
            <ejs-grid
              ref="nomalgrid"
              :dataSource="data"
              height="250"
              :allowPaging="true"
              :pageSettings="pageSettings"
              :beforeDataBound="beforeDataBound"
              :dataBound="dataBound"
            >
              <e-columns>
                <e-column
                  field="OrderID"
                  headerText="Order ID"
                  width="120"
                  isPrimaryKey="true"
                  textAlign="Right"
                ></e-column>
                <e-column
                  field="ProductName"
                  headerText="Product Name"
                  width="160"
                ></e-column>
                <e-column
                  field="ProductID"
                  headerText="Product ID"
                  width="120"
                  textAlign="Right"
                ></e-column>
                <e-column
                  field="CustomerID"
                  headerText="Customer ID"
                  width="120"
                ></e-column>
                <e-column
                  field="CustomerName"
                  headerText="Customer Name"
                  width="160"
                ></e-column>
              </e-columns>
            </ejs-grid>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import Vue from "vue";
import { GridPlugin, Page } from "@syncfusion/ej2-vue-grids";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { data } from "./datasource.js";

Vue.use(GridPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      data: data,
      pageSettings: { pageSize: 50 },
      immutableStart: 0,
      normalStart: 0,
      primaryKey: 0,
      immutableInit: true,
      init: true
    };
  },
  provide: {
    grid: [Page],
  },
  methods: {
    addTopEvent: function () {
      let immutableInstance = this.$refs.immutablegrid;
      let instance = this.$refs.nomalgrid;
      let addedRecords = [
        { OrderID: ++this.primaryKey,
          ProductName: "Chai",
          ProductID: "Sasquatch Ale",
          CustomerID: "QUEDE",
          CustomerName: "Yoshi Tannamuri",
        },
        {
          OrderID: ++this.primaryKey,
          ProductName: "Georg Pipps",
          ProductID: "Valkoinen suklaa",
          CustomerID: "RATTC",
          CustomerName: "Martín Sommer",
        },
        {
          OrderID: ++this.primaryKey,
          ProductName: "Yoshi Tannamuri",
          ProductID: "Gula Malacca",
          CustomerID: "COMMI",
          CustomerName: "Ann Devon",
        },
        {
          OrderID: ++this.primaryKey,
          ProductName: "Palle Ibsen",
          ProductID: "Rogede sild",
          CustomerID: "RATTC",
          CustomerName: "Paula Wilson",
        },
        {
          OrderID: ++this.primaryKey,
          ProductName: "Francisco Chang",
          ProductID: "Mascarpone Fabioli",
          CustomerID: "ROMEY",
          CustomerName: "Jose Pavarotti",
        },
      ];
      let aData = addedRecords.concat(immutableInstance.dataSource);
      instance.setProperties({ dataSource: aData });
      immutableInstance.setProperties({ dataSource: aData });
    },
    addBottomEvent: function () {
      let immutableInstance = this.$refs.immutablegrid;
      let instance = this.$refs.nomalgrid;
      let addedRecords = [
        {
          OrderID: ++this.primaryKey,
          ProductName: "Chai",
          ProductID: "Sasquatch Ale",
          CustomerID: "QUEDE",
          CustomerName: "Yoshi Tannamuri",
        },
        {
          OrderID: ++this.primaryKey,
          ProductName: "Georg Pipps",
          ProductID: "Valkoinen suklaa",
          CustomerID: "RATTC",
          CustomerName: "Martín Sommer",
        },
        {
          OrderID: ++this.primaryKey,
          ProductName: "Yoshi Tannamuri",
          ProductID: "Gula Malacca",
          CustomerID: "COMMI",
          CustomerName: "Ann Devon",
        },
        {
          OrderID: ++this.primaryKey,
          ProductName: "Palle Ibsen",
          ProductID: "Rogede sild",
          CustomerID: "RATTC",
          CustomerName: "Paula Wilson",
        },
        {
          OrderID: ++this.primaryKey,
          ProductName: "Francisco Chang",
          ProductID: "Mascarpone Fabioli",
          CustomerID: "ROMEY",
          CustomerName: "Jose Pavarotti",
        },
      ];
      let aData = immutableInstance.dataSource.concat(addedRecords);
      instance.setProperties({ dataSource: aData });
      immutableInstance.setProperties({ dataSource: aData });
    },
    deleteEvent: function () {
      let immutableInstance = this.$refs.immutablegrid;
      let instance = this.$refs.nomalgrid;
      immutableInstance.dataSource.splice(0, 5);
      instance.setProperties({ dataSource: immutableInstance.dataSource });
      immutableInstance.setProperties({
        dataSource: immutableInstance.dataSource,
      });
    },
    sortEvent: function () {
      let immutableInstance = this.$refs.immutablegrid;
      let instance = this.$refs.nomalgrid;
      let aData = immutableInstance.dataSource.reverse();
      instance.setProperties({ dataSource: aData });
      immutableInstance.setProperties({ dataSource: aData });
    },
    pageEvent: function () {
      let immutableInstance = this.$refs.immutablegrid;
      let instance = this.$refs.nomalgrid;
      let totalPage =
        immutableInstance.dataSource.length /
        immutableInstance.pageSettings.pageSize;
      let page = Math.floor(Math.random() * totalPage) + 1;
      instance.setProperties({ pageSettings: { currentPage: page } });
      immutableInstance.setProperties({ pageSettings: { currentPage: page } });
    },
    immutableBeforeDataBound: function () {
      this.immutableStart = new Date().getTime();
    },
    immutableDataBound: function () {
      let val = this.immutableInit ? '' : new Date().getTime() - this.immutableStart;
      document.getElementById("immutableDelete").innerHTML =
        "Immutable rendering Time: " + "<b>" + val + "</b>" + "<b>ms</b>";
      this.immutableStart = 0; this.immutableInit = false;
    },
    beforeDataBound: function () {
      this.normalStart = new Date().getTime();
    },
    dataBound: function () {
      let val = this.init ? '' : new Date().getTime() - this.normalStart;
      document.getElementById("normalDelete").innerHTML =
        "Normal rendering Time: " + "<b>" + val + "</b>" + "<b>ms</b>";
      this.normalStart = 0; this.init = false;
    },
  },
};
</script>
<style>
.e-grid {
  pointer-events: none;
}
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Limitations

The following features are not supported in the immutable mode:

* Frozen rows and columns
* Row Template
* Detail Template
* Hierarchy Grid
* Column reorder
* Virtualization
* Infinite scroll
* Grouping
