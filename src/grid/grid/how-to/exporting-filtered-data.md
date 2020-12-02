---
title: "Exporting Filtered Data Only"
component: "Grid"
description: "Learn how to Exporting Filtered Data Only."
---

# Exporting Filtered Data Only

You can export the filtered data by defining the resulted data in `exportProperties.dataSource` before export.

In the below Pdf exporting demo, We have gotten the filtered data by applying filter query to the grid data and then defines the resulted data in `exportProperties.dataSource` and pass it to `pdfExport` method.

{% tab template="grid/how-to/export-filtered-data" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :toolbar='toolbarOptions' :allowPaging='true' :allowFiltering='true' :allowPdfExport='true' :pageSettings='pageSettings'
        :toolbarClick='toolbarClick'>
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
import { GridPlugin,Toolbar,PdfExport,Filter,Page  } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
import { DataManager } from "@syncfusion/ej2-data";

Vue.use(GridPlugin);
export default {
      data: () => {
        return {
          data: data,
          toolbarOptions: ['PdfExport'],
          pageSettings: { pageSize: 5, pageCount:5 }

        };
      },
      methods: {
        toolbarClick: function (args) {
          if (args['item'].id.indexOf("pdfexport") != -1) {
           let pdfdata;
           let query = this.$refs.grid.ej2Instances.renderModule.data.generateQuery(); // get grid corresponding query  
         for(var i=0; i<query.queries.length; i++ ){
            if(query.queries[i].fn=='onPage'){
            query.queries.splice(i,1);      // remove page query to get all records
            break;
            }
          }
          let fdata = new DataManager({ json: data}).executeQuery(query).then((e) => {
          pdfdata = e.result;   // get all filtered records
          let exportProperties = {
           dataSource: pdfdata,
          };
          this.$refs.grid.pdfExport(exportProperties);
        }).catch((e) => true);
          }
        },
      },
      provide: {
        grid: [Toolbar, PdfExport, Filter, Page]
      },
    }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}
