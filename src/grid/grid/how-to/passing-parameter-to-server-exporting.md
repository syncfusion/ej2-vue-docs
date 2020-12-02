---
title: "Passing additional parameters to the server when Exporting"
component: "Grid"
description: "Learn how to pass additional parameters to server when Exporting."
---

# Passing additional parameters to the server when Exporting

You can pass the additional parameter in the `query` property by invoking `addParams` method. In the `toolbarClick` event, you can define params as key and value pair so it will receive at the server side when exporting.

In the below example, we have passed `recordcount` as `12` using `addParams` method.

{% tab template="grid/pdf/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' id='Grid' :dataSource='data' :toolbar='toolbarOptions' height='272px' :allowPdfExport='true' :allowExcelExport='true' :excelExportComplete='excelExportComplete' :pdfExportComplete='pdfExportComplete' :toolbarClick='toolbarClick'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                <e-column field='CustomerID' headerText='Customer ID' :visible='false' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Toolbar, PdfExport, ExcelExport } from "@syncfusion/ej2-vue-grids";
import { Query } from "@syncfusion/ej2-data";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      toolbarOptions: ['PdfExport', 'ExcelExport'],
      queryClone: ""
    };
  },
  methods: {
    toolbarClick(args) {
        if (args.item.id === 'Grid_pdfexport') {
            debugger
            this.queryClone = this.$refs.grid.query;
            this.$refs.grid.query = new Query().addParams("recordcount", "12")
            this.$refs.grid.pdfExport();
        }
        else if (args.item.id === 'Grid_excelexport') {
            this.queryClone = this.$refs.grid.query;
            this.$refs.grid.query = new Query().addParams("recordcount", "12")
            this.$refs.grid.excelExport();
        }
    }
    pdfExportComplete(args) {
        this.$refs.grid.query = this.queryClone();
    }
    excelExportComplete(args) {
        this.$refs.grid.query = this.queryClone();
    }
  },
  provide: {
    grid: [Toolbar, PdfExport, ExcelExport]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

{% endtab %}