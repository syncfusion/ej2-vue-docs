---
title: "Migration"
component: "TreeGrid"
description: "Documentation on exporting TreeGrid content to Excel document and customizing the exported document with headers and footers, and file name changes."
---

# Excel Export

The excel export allows exporting TreeGrid data to Excel document. You need to use the
[`excelExport`](../api/treegrid/#excelexport) method for exporting. To enable Excel export in the treegrid, set the [`allowExcelExport`](../api/treegrid/#allowexcelexport-boolean) as true.

To use excel export, You need to inject the `ExcelExport` module in treegrid.

{% tab template="treegrid/excel/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' height='220' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' :allowExcelExport='true' :toolbar='toolbarOptions' :toolbarClick='toolbarClick'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar, ExcelExport } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbarOptions: ['ExcelExport'],
      pageSettings: { pageSize: 7 }
    };
  },
  methods: {
      toolbarClick(args) {
        if (args['item'].text === 'Excel Export') {
            this.$refs.treegrid.excelExport();
        }
    }
  },
  provide: {
      treegrid: [ Page, Toolbar, ExcelExport ]
  }
}
</script>

```

{% endtab %}

## To customize excel export

The excel export provides an option to customize mapping of the treegrid to excel document.

### Export hidden columns

The excel export provides an option to export hidden columns of treegrid by defining `includeHiddenColumn` as `true`.

{% tab template="treegrid/excel/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' height='220' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' :allowExcelExport='true' :toolbar='toolbarOptions' :toolbarClick='toolbarClick'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' :visible='false' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar, ExcelExport } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbarOptions: ['ExcelExport'],
      pageSettings: { pageSize: 7 }
    };
  },
  methods: {
      toolbarClick(args) {
        if (args['item'].text === 'Excel Export') {
          let excelExportProperties = {
            includeHiddenColumn: true
          }
          this.$refs.treegrid.excelExport(excelExportProperties);
        }
    }
  },
  provide: {
      treegrid: [ Page, Toolbar, ExcelExport ]
  }
}
</script>

```

{% endtab %}

### Show or Hide columns on Exported Excel

You can show a hidden column or hide a visible column while printing the treegrid using [`toolbarClick`](../api/treegrid#toolbarclick) and [`excelExportComplete`](../api/treegrid/#excelExportComplete) events.

In the `toolbarClick` event, based on `args.item.text` as `Excel Export`. We can show or hide columns by setting `column.visible` property to `true` or `false` respectively.

In the excelExportComplete event, We have reversed the state back to the previous state.

In the below example, we have `Duration` as a hidden column in the treegrid. While exporting, we have changed `Duration` to visible column and `StartDate` as hidden column.

{% tab template="treegrid/excel/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' height='220' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' :allowExcelExport='true' :toolbar='toolbarOptions' :toolbarClick='toolbarClick' :excelExportComplete='excelExportComplete'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' :visible='false' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar, ExcelExport } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbarOptions: ['ExcelExport'],
      pageSettings: { pageSize: 7 }
    };
  },
  methods: {
      toolbarClick(args) {
        if (args['item'].text === 'Excel Export') {
          this.$refs.treegrid.ej2Instances.grid.getColumns()[2].visible = false;
          this.$refs.treegrid.ej2Instances.grid.getColumns()[3].visible = true;
          this.$refs.treegrid.excelExport();
        }
      }
      excelExportComplete() {
        this.$refs.treegrid.ej2Instances.grid.getColumns()[2].visible = true;
        this.$refs.treegrid.ej2Instances.grid.getColumns()[3].visible = false;
      }
  },
  provide: {
      treegrid: [ Page, Toolbar, ExcelExport ]
  }
}
</script>

```

{% endtab %}

### Conditional Cell Formatting

TreeGrid cells in the exported Excel can be customized or formatted using [`excelQueryCellInfo`](../api/treegrid/#excelQueryCellInfo) event. In this event, we can format the treegrid cells of exported PDF document based on the column cell value.

In the below sample, we have set the background color for `Duration` column in the exported excel by `args.cell` and `backgroundColor` property.

{% tab template="treegrid/excel/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' height='220' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' :allowExcelExport='true' :toolbar='toolbarOptions' :toolbarClick='toolbarClick' :queryCellInfo='queryCellInfo'
        :excelQueryCellInfo='excelQueryCellInfo'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar, ExcelExport } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbarOptions: ['ExcelExport'],
      pageSettings: { pageSize: 7 }
    };
  },
  methods: {
      toolbarClick(args) {
        if (args['item'].text === 'Excel Export') {
          this.$refs.treegrid.excelExport();
        }
      }
      excelQueryCellInfo(args) {
        if(args.column.field == 'duration'){
          if(args.value === 0 || args.value === "") {
            args.style = {backColor: '#336c12'};
          }
          else if(args.value < 3) {
            args.style = {backColor: '#7b2b1d'};
          }
        }
      }
      queryCellInfo(args) {
        if (args.data['duration'] == 0 && args.column.field === 'duration' ) {
            args.cell.style.background= '#336c12';
        } else if (args.data['duration'] < 3 && args.column.field === 'duration') {
            args.cell.style.background= '#7b2b1d';
        }
      }
  },
  provide: {
      treegrid: [ Page, Toolbar, ExcelExport ]
  }
}
</script>

```

{% endtab %}

### Theme

The excel export provides an option to include theme for exported excel document.

To apply theme in exported Excel, define the `theme` in `exportProperties`.

{% tab template="treegrid/excel/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' height='220' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' :allowExcelExport='true' :toolbar='toolbarOptions' :toolbarClick='toolbarClick'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar, ExcelExport } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbarOptions: ['ExcelExport'],
      pageSettings: { pageSize: 7 }
    };
  },
  methods: {
      toolbarClick(args) {
        if (args['item'].text === 'Excel Export') {
          let excelExportProperties = {
            theme:
              {
                header: { fontName: 'Segoe UI', fontColor: '#666666' },
                record: { fontName: 'Segoe UI', fontColor: '#666666' },
                caption: { fontName: 'Segoe UI', fontColor: '#666666' }
              }
          }
          this.$refs.treegrid.excelExport(excelExportProperties);
        }
    }
  },
  provide: {
      treegrid: [ Page, Toolbar, ExcelExport ]
  }
}
</script>

```

{% endtab %}

>By default, material theme is applied to exported excel document.

### To add header and footer

The excel export provides an option to include header and footer content for exported excel document.

{% tab template="treegrid/excel/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' height='220' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' :allowExcelExport='true' :toolbar='toolbarOptions' :toolbarClick='toolbarClick'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar, ExcelExport } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbarOptions: ['ExcelExport'],
      pageSettings: { pageSize: 7 }
    };
  },
  methods: {
      toolbarClick(args) {
        if (args['item'].text === 'Excel Export') {
          let excelExportProperties = {
            header: {
                headerRows: 7,
                rows: [
                    { cells: [{ colSpan: 4, value: "Northwind Traders", style: { fontColor: '#C67878', fontSize: 20, hAlign: 'Center', bold: true, } }] },
                    { cells: [{ colSpan: 4, value: "2501 Aerial Center Parkway", style: { fontColor: '#C67878', fontSize: 15, hAlign: 'Center', bold: true, } }] },
                    { cells: [{ colSpan: 4, value: "Suite 200 Morrisville, NC 27560 USA", style: { fontColor: '#C67878', fontSize: 15, hAlign: 'Center', bold: true, } }] },
                    { cells: [{ colSpan: 4, value: "Tel +1 888.936.8638 Fax +1 919.573.0306", style: { fontColor: '#C67878', fontSize: 15, hAlign: 'Center', bold: true, } }] },
                    { cells: [{ colSpan: 4, hyperlink: { target: 'https://www.northwind.com/', displayText: 'www.northwind.com' }, style: { hAlign: 'Center' } }] },
                    { cells: [{ colSpan: 4, hyperlink: { target: 'mailto:support@northwind.com' }, style: { hAlign: 'Center' } }] },
                ]
            },
            footer: {
                footerRows: 4,
                rows: [
                    { cells: [{ colSpan: 4, value: "Thank you for your business!", style: { hAlign: 'Center', bold: true } }] },
                    { cells: [{ colSpan: 4, value: "!Visit Again!", style: { hAlign: 'Center', bold: true } }] }
                ]
            },
          }
          this.$refs.treegrid.excelExport(excelExportProperties);
        }
    }
  },
  provide: {
      treegrid: [ Page, Toolbar, ExcelExport ]
  }
}
</script>

```

{% endtab %}

### File Name for Exported document

You can assign the file name for the exported document by defining `fileName` property in [`ExcelExportProperties`](../api/treegrid/#excelExportProperties).

{% tab template="treegrid/excel/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' height='220' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' :allowExcelExport='true' :toolbar='toolbarOptions' :toolbarClick='toolbarClick'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar, ExcelExport } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbarOptions: ['ExcelExport'],
      pageSettings: { pageSize: 7 }
    };
  },
  methods: {
      toolbarClick(args) {
        if (args['item'].text === 'Excel Export') {
          let excelExportProperties = {
            fileName:"new.xlsx"
          }
          this.$refs.treegrid.excelExport(excelExportProperties);
        }
    }
  },
  provide: {
      treegrid: [ Page, Toolbar, ExcelExport ]
  }
}
</script>

```

{% endtab %}

## Custom data source

The excel export provides an option to define datasource dynamically before exporting. To export data dynamically, define the `dataSource` in `exportProperties`.

{% tab template="treegrid/excel/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' height='220' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' :allowExcelExport='true' :toolbar='toolbarOptions' :toolbarClick='toolbarClick'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar, ExcelExport } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbarOptions: ['ExcelExport'],
      pageSettings: { pageSize: 7 }
    };
  },
  methods: {
      toolbarClick(args) {
        if (args['item'].text === 'Excel Export') {
          let excelExportProperties = {
            dataSource: sampleData
          }
          this.$refs.treegrid.excelExport(excelExportProperties);
        }
    }
  },
  provide: {
      treegrid: [ Page, Toolbar, ExcelExport ]
  }
}
</script>

```

{% endtab %}