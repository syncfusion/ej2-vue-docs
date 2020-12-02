---
title: "Exporting the Selected Records"
component: "Grid"
description: "Learn how to Export the Selected data."
---

# Exporting the Selected Records

You can export the selected records data by passing it to `exportProperties.dataSource` property in the `toolbarClick` event.

In the below exporting demo, We can get the selected records using `getSelectedRecords` method and pass the selected data to `PdfExport` or `excelExport` property.

{% tab template="grid/how-to/export-filtered-data" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :toolbar='toolbarOptions' :allowPaging='true' :allowFiltering='true' :allowPdfExport='true' :allowExcelExport='true' :pageSettings='pageSettings' :toolbarClick='toolbarClick' :selectionSettings='selectionOption'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Toolbar, PdfExport, Filter, Page, ExcelExport  } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
import { DataManager } from "@syncfusion/ej2-data";

Vue.use(GridPlugin);
export default {
      data: () => {
        return {
          data: data,
          toolbarOptions: ['PdfExport', 'ExcelExport'],
          pageSettings: { pageSize: 5, pageCount:5 },
          selectionOption: {type: 'Multiple'}

        };
      },
      methods: {
          toolbarClick(args: ClickEventArgs) {
              if (args['item'].id.indexOf("pdfexport") != -1) {
                  let selectedRecords = this.$refs.grid.getSelectedRecords();
                  let exportProperties = {
                      dataSource: selectedRecords
                    };
                      this.$refs.grid.pdfExport(exportProperties);
                }
              else if (args['item'].id.indexOf("excelexport") != -1) {
                  let selectedRecords = this.$refs.grid.getSelectedRecords();
                  let exportProperties = {
                      dataSource: selectedRecords
                      };
                        this.$refs.grid.excelExport(exportProperties);
                        }
                    },
                },
      provide: {
        grid: [Toolbar, PdfExport, Filter, Page, ExcelExport]
      },
    }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}