---
title: "Show Spinner on Tree Grid when Exporting"
component: "TreeGrid"
description: "Learn how to Show spinner while exporting the Tree Grid."
---

# Show spinner on Tree Grid when Exporting

You can show/ hide spinner component while exporting the Tree Grid using [`showSpinner`](../api/treegrid/#showspinner)/ [`hideSpinner`](../api/treegrid/#hidespinner) methods. You can use  [`toolbarClick`](../api/treegrid/#toolbarclick) event to show spinner before exporting and hide a spinner in the [`pdfExportComplete`](../api/treegrid/#pdfexportcomplete) or [`excelExportComplete`](../api/treegrid/#excelexportcomplete) event after the exporting.

In the [`toolbarClick`](../../api/grid/#toolbarclick) event, based on the parameter **args.item.text** as **PDF Export** or **Excel Export** we can call the [`showSpinner`](../api/treegrid/#showspinner) method from Tree Grid instance.

In the [`pdfExportComplete`](../api/treegrid/#pdfexportcomplete) or [`excelExportComplete`](../api/treegrid/#excelexportcomplete) event, We can call the [`hideSpinner`](../api/treegrid/#hidespinner) method.

In the below demo, we have rendered the default spinner component when exporting the Tree Grid.

{% tab template="treegrid/how-to/default" %}

```html
<template>
  <div id="app">
        <ejs-treegrid :dataSource="data" :allowPaging='true' :treeColumnIndex="1" idMapping='TaskID' parentIdMapping='parentID' ref="treegrid" :toolbar="toolbarOptions"  :allowPdfExport='true' :allowExcelExport='true' :pageSettings='pageSettings' :toolbarClick='toolbarClick' :excelExportComplete='excelExportComplete' :pdfExportComplete='pdfExportComplete'>
        <e-columns>
          <e-column field="TaskID" headerText="Task ID" :isPrimaryKey='true' width="70" textAlign="Right"></e-column>
          <e-column field="TaskName" headerText="Task Name" width="100" ></e-column>
          <e-column field="StartDate" headerText="Start Date" format="yMd" editType= 'datepickeredit' width="100" textAlign="Right"></e-column>
          <e-column field="EndDate" headerText="End Date" width="100" format="yMd" editType='datepickeredit' textAlign="Right"></e-column>
          <e-column field="Duration" headerText="Duration" width="90" textAlign="Right"></e-column>
          <e-column field="Priority" headerText="Priority" width="90" textAlign="Left"></e-column>
        </e-columns>
       </ejs-treegrid>
  </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar, PdfExport, ExcelExport} from "@syncfusion/ej2-vue-treegrid";
import { projectData } from "./datasource.js";

Vue.use(TreeGridPlugin);
export default {
  data() {
    return {
      data: projectData,
      toolbarOptions: ['PdfExport', 'ExcelExport'],
      pageSettings: { pageSize: 5, pageCount:5 },
      queryClone: ""
    };
  },
  methods: {
    toolbarClick(args){
        if (args.item.text === 'PDF Export') {
            this.$refs.treegrid.showSpinner();
            this.$refs.treegrid.pdfExport();
        }
        else if (args.item.text === 'Excel Export') {
            this.$refs.treegrid.showSpinner();
            this.$refs.treegrid.excelExport();
        }
     },
    pdfExportComplete(args) {
        this.$refs.treegrid.hideSpinner();
     },
     excelExportComplete(args) {
        this.$refs.treegrid.hideSpinner();
     },
  },
  provide: {
    treegrid: [Page, Toolbar, PdfExport, ExcelExport]
  }
}
</script>

```

{% endtab %}
