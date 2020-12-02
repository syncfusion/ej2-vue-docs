---
title: "Show Spinner on Grid when Exporting"
component: "Grid"
description: "Learn how to Show spinner while exporting the grid."
---

# Show Spinner on Grid when Exporting

You can show/ hide spinner component while exporting the grid using `showSpinner`/ `hideSpinner` methods. You can use `toolbarClick` event to show spinner before exporting and hide a spinner in the `pdfExportComplete` or `excelExportComplete` event after the exporting.

In the `toolbarClick` event, based on the parameter `args.item.id` as `Grid_pdfexport` or `Grid_excelexport` we can call the `showSpinner` method from grid instance.

In the `pdfExportComplete` or `excelExportComplete` event, We can call the `hideSpinner` method.

In the below demo, we have rendered the default spinner component when exporting the grid.

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
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      toolbarOptions: ['PdfExport', 'ExcelExport']
    };
  },
  methods: {
    toolbarClick(args) {
        if (args.item.id === 'Grid_pdfexport') {
            this.$refs.grid.showSpinner();
            this.$refs.grid.pdfExport();
        }
        else if (args.item.id === 'Grid_excelexport') {
            this.$refs.grid.showSpinner();
            this.$refs.grid.excelExport();
        }
    }
    pdfExportComplete(args) {
        this.$refs.grid.hideSpinner();
    }
    excelExportComplete(args) {
        this.$refs.grid.hideSpinner();
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