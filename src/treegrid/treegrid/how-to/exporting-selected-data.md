---
title: "Exporting the Selected Records"
component: "TreeGrid"
description: "Learn how to Export the Selected data."
---

# Exporting the Selected Records

You can export the selected records data by passing it to [`PdfExportProperties.dataSource`](../../api/grid/pdfExportProperties/) or [`ExcelExportProperties.dataSource`](../../api/grid/excelExportProperties/) property in the [`toolbarClick`](../../api/grid/#toolbarclick) event.

In the below exporting demo, we can get the selected records using [`getSelectedRecords`](../api/treegrid/#getselectedrecords) method and pass the selected data to [`pdfExport`](../api/treegrid/#pdfexport) or [`excelExport`](../api/treegrid/#excelExport) methods using respective export properties..

{% tab template="treegrid/how-to/default" %}

```html
<template>
  <div id="app">
        <ejs-treegrid :dataSource="data" :allowPaging='true' :treeColumnIndex="1" idMapping='TaskID' parentIdMapping='parentID' ref="treegrid" :toolbar="toolbarOptions"  :allowPdfExport='true' :allowExcelExport='true' :pageSettings='pageSettings' :toolbarClick='toolbarClick' :selectionSettings='selectionOption'>
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
      selectionOption: {type: 'Multiple'}
    };
  },
  methods: {
    toolbarClick(args){
         if (args['item'].id.indexOf("pdfexport") != -1) {
            let selectedRecords = this.$refs.treegrid.getSelectedRecords();
                  let exportProperties = {
                      dataSource: selectedRecords
                  };
                this.$refs.treegrid.pdfExport(exportProperties);
                }
              else if (args['item'].id.indexOf("excelexport") != -1) {
                  let selectedRecords = this.$refs.treegrid.getSelectedRecords();
                  let exportProperties = {
                      dataSource: selectedRecords
                  };
                this.$refs.treegrid.excelExport(exportProperties);
             }
         },
  },
  provide: {
    treegrid: [Page, Toolbar, PdfExport, ExcelExport]
  }
}
</script>

```

{% endtab %}
