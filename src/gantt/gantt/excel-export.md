---
title: "Excel Export"
component: "Gantt"
description: "Learn how to export Gantt data to Excel and CSV documents in the Essential JS 2 Gantt component."
---

# Excel Export

Gantt supports client-side exporting, which allows you to export its data to the Excel and CSV formats. Use the [`excelExport`](../api/gantt/#excelexport) and [`csvExport`](../api/gantt/#csvexport) methods for exporting. To enable Excel export in the Gantt, set the [`allowExcelExport`](../api/gantt/#allowexcelexport) to true.

To export data to Excel and CSV, inject the `ExcelExport` module in Gantt.

{% tab template="gantt/excel-export" %}

```html
<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowExcelExport='true' :height="height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, ExcelExport, Selection } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { ganttData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
        data: ganttData,
        height:'450px',
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        toolbar: ['ExcelExport', 'CsvExport'],
        toolbarClick: (args: ClickEventArgs) => {
                if (args.item.id === 'GanttContainer_excelexport') {
                    var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttObj.excelExport();
                } else if(args.item.id === 'GanttContainer_csvexport') {
                    var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttObj.csvExport();
                }
            },
      };
  },
  provide: {
      gantt: [Toolbar, ExcelExport]
  }
};
</script>
```

{% endtab %}

## Multiple Gantt exporting

In Gantt, the Excel export provides support to export multiple Gantt data in new sheet or same sheet.

### Same sheet

The Excel export provides support to export multiple Gantt data in the same sheet. To export in same sheet, define `multipleExport.type` as `AppendToSheet` in `ExcelExportProperties`. You can also provide blank rows between exported multiple Gantt data. These blank rows count can be defined using `multipleExport.blankRows`.

{% tab template="gantt/excel-export" %}

```html
<template>
     <div>
     <p><b>First Gantt:</b></p>
        <ejs-gantt ref='gantt1' id="GanttContainer1" :dataSource="fData" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowExcelExport='true' :height="height1" :treeColumnIndex="1" :projectStartDate="projectStartDate" :projectEndDate="projectEndDate"></ejs-gantt>
    <p><b>Second Gantt:</b></p>
        <ejs-gantt ref='gantt2' id="GanttContainer2" :dataSource="sData" :taskFields="taskFields" :allowExcelExport='true' :height="height2" :treeColumnIndex="1"></ejs-gantt>  
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, ExcelExport, Selection } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { ganttData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
        fData: [ganttData[0]],
        sData: [ganttData[1]],
        height1:'280px',
        height2:'250px',
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        toolbar: ['ExcelExport'],
        projectStartDate: new Date('03/31/2019'),
        projectEndDate: new Date('04/14/2019'),
        toolbarClick: (args: ClickEventArgs) => {
                if (args.item.id === 'GanttContainer1_excelexport') {
                    var appendExcelExportProperties: ExcelExportProperties = {
                        multipleExport: {type: 'AppendToSheet',blankRows: 2}
                    };
                    var FirstGantt = document.getElementById('GanttContainer1').ej2_instances[0];
                    var FirstGanttExport =  FirstGantt.excelExport(appendExcelExportProperties,true);
                    FirstGanttExport.then((fData) => {
                        var SecondGantt = document.getElementById('GanttContainer2').ej2_instances[0];
                        SecondGantt.excelExport(appendExcelExportProperties,false,fData);
                    });
                }
        },
        };
  },
  provide: {
    gantt: [Toolbar, ExcelExport]
  }
};
</script>
```

{% endtab %}

>By default, `multipleExport.blankRows` value is 5.

### New sheet

The Excel exporting provides support to export multiple Gantt in new sheet. To export in new sheet, define `multipleExport.type` as `NewSheet` in `ExcelExportProperties`.

{% tab template="gantt/excel-export" %}

```html
<template>
     <div>
     <p><b>First Gantt:</b></p>
        <ejs-gantt ref='gantt1' id="GanttContainer1" :dataSource="fData" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowExcelExport='true' :height="height1" :treeColumnIndex="1" :projectStartDate="projectStartDate" :projectEndDate="projectEndDate"></ejs-gantt>
    <p><b>Second Gantt:</b></p>
        <ejs-gantt ref='gantt2' id="GanttContainer2" :dataSource="sData" :taskFields="taskFields" :allowExcelExport='true' :height="height2" :treeColumnIndex="1"></ejs-gantt>  
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, ExcelExport, Selection } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { ganttData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
        fData: [ganttData[0]],
        sData: [ganttData[1]],
        height1:'280px',
        height2:'250px',
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        toolbar: ['ExcelExport'],
        projectStartDate: new Date('03/31/2019'),
        projectEndDate: new Date('04/14/2019'),
        toolbarClick: (args: ClickEventArgs) => {
                if (args.item.id === 'GanttContainer1_excelexport') {
                    var appendExcelExportProperties: ExcelExportProperties = {
                        multipleExport: {type: 'NewSheet'}
                    };
                    var FirstGantt = document.getElementById('GanttContainer1').ej2_instances[0];
                    var FirstGanttExport =  FirstGantt.excelExport(appendExcelExportProperties,true);
                    FirstGanttExport.then((fData) => {
                        var SecondGantt = document.getElementById('GanttContainer2').ej2_instances[0];
                        SecondGantt.excelExport(appendExcelExportProperties,false,fData);
                    });
                }
        },
        };
  },
  provide: {
    gantt: [Toolbar, ExcelExport]
  }
};
</script>
```

{% endtab %}

## Customize the Excel export

Gantt Excel export allows the users to customize the exported document based on requirement.

### Export hidden columns

In Gantt, the Excel export provides an option to export hidden columns by defining `includeHiddenColumn` as `true`.

{% tab template="gantt/excel-export" %}

```html
<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :columns="columns" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowExcelExport='true' :height="height" :treeColumnIndex="1"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, ExcelExport, Selection } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { ganttData } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
        data: ganttData,
        height:'450px',
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        columns: [
            { field: 'TaskID', headerText:  'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText:  'Task Name', width: '150' },
            { field: 'StartDate', headerText: 'Start Date', width: '150', visible: false },
            { field: 'Duration',headerText: 'Duration', width: '150'},
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
        toolbar: ['ExcelExport', 'CsvExport'],
        toolbarClick: (args: ClickEventArgs) => {
                if (args.item.id === 'GanttContainer_excelexport') {
                    var excelExportProperties:ExcelExportProperties = {
                        includeHiddenColumn: true
                    };
                    var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttObj.excelExport(excelExportProperties);
                } else if(args.item.id === 'GanttContainer_csvexport') {
                    var excelExportProperties:ExcelExportProperties = {
                        includeHiddenColumn: true
                    };
                    var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttObj.csvExport(excelExportProperties);
                }
            },
      };
  },
  provide: {
      gantt: [Toolbar, ExcelExport]
  }
};
</script>
```

{% endtab %}

### Show or hide columns on exported Excel

In Gantt, while exporting, you can show a hidden column or hide a visible column using the [`toolbarClick`](../api/gantt/#toolbarclick) and [`excelExportComplete`](../api/gantt/#excelexportcomplete) events.

In the `toolbarClick` event, using the `args.item.id` property, you can show or hide columns by setting the `column.visible` property to `true` or `false` respectively.

Similarly, in the excelExportComplete event, you can revert the columns visibility back to the previous state.

{% tab template="gantt/excel-export" %}

```html
<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :columns="columns"
        :toolbar="toolbar" :toolbarClick="toolbarClick" :excelExportComplete="excelExportComplete" :allowExcelExport='true'
        :height="height" :treeColumnIndex="1"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, ExcelExport, Selection } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { ganttData } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
        data: ganttData,
        height:'450px',
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        columns: [
            { field: 'TaskID', headerText:  'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText:  'Task Name', width: '150' },
            { field: 'StartDate', headerText: 'Start Date', width: '150', visible: false },
            { field: 'Duration',headerText: 'Duration', width: '150'},
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
        toolbar: ['ExcelExport', 'CsvExport'],
        toolbarClick: (args: ClickEventArgs) => {
                if (args.item.id === 'GanttContainer_excelexport') {
                    var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttObj.treeGrid.grid.columns[0].visible = true;
                    ganttObj.treeGrid.grid.columns[3].visible = false;
                    ganttObj.excelExport();
                } else if(args.item.id === 'GanttContainer_csvexport') {
                    var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttObj.treeGrid.grid.columns[0].visible = true;
                    ganttObj.treeGrid.grid.columns[3].visible = false;
                    ganttObj.csvExport();
                }
            },
        excelExportComplete: () => {
            var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
            ganttObj.treeGrid.grid.columns[0].visible = false;
            ganttObj.treeGrid.grid.columns[3].visible = true;
        },
      };
  },
  provide: {
      gantt: [Toolbar, ExcelExport]
  }
};
</script>
```

{% endtab %}

### Cell formatting during export

In Gantt, you can customize the TreeGrid cells in the exported document using the [`excelQueryCellInfo`](../api/gantt/#excelquerycellinfo) event. In this event, you can format the TreeGrid cells of exported Excel and CSV documents based on the required condition.

In the following sample, the background color has been customized for `TaskID` column in the exported Excel using the `args.style` and `backColor` properties.

{% tab template="gantt/excel-export" %}

```html
<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick" :excelQueryCellInfo="excelQueryCellInfo" :queryCellInfo="queryCellInfo" :queryTaskbarInfo = "queryTaskbarInfo" :allowExcelExport='true' :height="height" :treeColumnIndex="1" :columns = "columns" :labelSettings="labelSettings" :splitterSettings= "splitterSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, ExcelExport, Selection } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { ganttData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
        data: ganttData,
        height:'450px',
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        toolbar: ['ExcelExport'],
        columns: [
            { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100',visible:false  },
            { field: 'TaskName', headerText: 'Task Name', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '150' }
        ],
        labelSettings: {
            taskLabel: '${Progress}%'
        },
        splitterSettings: {
            columnIndex: 3
        },
        toolbarClick: (args: ClickEventArgs) => {
                if (args.item.id === 'GanttContainer_excelexport') {
                    var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttObj.excelExport();
                }
            },
        excelQueryCellInfo: (args: any) => {
            if(args.column.field == 'Progress'){
                if(args.value > 80) {
                    args.style = { backColor: '#A569BD' };
                }
                else if(args.value < 20) {
                    args.style = { backColor: '#F08080' };
                }
            }
        },
        queryTaskbarInfo: function(args) {
            if (args.data.Progress > 80) {
                args.progressBarBgColor = "#6C3483";
                args.taskbarBgColor = args.taskbarBorderColor = "#A569BD";
            } else if (args.data.Progress < 20) {
                args.progressBarBgColor = "#CD5C5C";
                args.taskbarBgColor = args.taskbarBorderColor = "#F08080";
            }
        },
        queryCellInfo: (args: any) => {
            if(args.column.field == 'Progress'){
                if(args.data.Progress > 80) {
                    args.cell.style.backgroundColor  = '#A569BD';
                }
                else if(args.data.Progress < 20) {
                    args.cell.style.backgroundColor  = '#F08080';
                }
            }  
        },
      };
  },
  provide: {
      gantt: [Toolbar, ExcelExport]
  }
};
</script>
```

{% endtab %}

### Theme

The Excel export also provides an option to include custom theme for exported Excel document.

To apply theme in exported Excel, define the `theme` in `ExcelExportProperties`.

{% tab template="gantt/excel-export" %}

```html
<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowExcelExport='true' :height = "height" :treeColumnIndex="1"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, ExcelExport, Selection } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { ganttData } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
        data: ganttData,
        height:'450px',
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        toolbar: ['ExcelExport'],
        toolbarClick: (args: ClickEventArgs) => {
                if (args.item.id === 'GanttContainer_excelexport') {
                    var excelExportProperties: ExcelExportProperties = {
                        theme:
                        {
                            header: { fontName: 'Segoe UI', fontColor: '#666666' },
                            record: { fontName: 'Segoe UI', fontColor: '#666666' }
                        }
                    };
                    var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttObj.excelExport(excelExportProperties);
                }
            },
      };
  },
  provide: {
      gantt: [Toolbar, ExcelExport]
  }
};
</script>
```

{% endtab %}

> By default, material theme is applied to the exported Excel document.

### Add header and footer

The Excel export also allows users to include header and footer contents to the exported Excel document.

{% tab template="gantt/excel-export" %}

```html
<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowExcelExport='true' :height="height" :treeColumnIndex="1"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, ExcelExport, Selection } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { ganttData } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
        data: ganttData,
        height:'450px',
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        toolbar: ['ExcelExport'],
        toolbarClick: (args: ClickEventArgs) => {
                if (args.item.id === 'GanttContainer_excelexport') {
                    var excelExportProperties: ExcelExportProperties = {
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
                    };
                    var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttObj.excelExport(excelExportProperties);
                }
            },
      };
  },
  provide: {
      gantt: [Toolbar, ExcelExport]
  }
};
</script>
```

{% endtab %}

### File name for exported document

You can set the required file name for the exported document by defining the `fileName` property in `ExcelExportProperties`.

{% tab template="gantt/excel-export" %}

```html
<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowExcelExport='true' :height="height" :treeColumnIndex="1"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, ExcelExport, Selection } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { ganttData } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
        data: ganttData,
        height:'450px',
        taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        toolbar: ['ExcelExport', 'CsvExport'],
        toolbarClick: (args: ClickEventArgs) => {
                if (args.item.id === 'GanttContainer_excelexport') {
                    var excelExportProperties: ExcelExportProperties = {
                        fileName:"Gantt.xlsx"
                    };
                    var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttObj.excelExport(excelExportProperties);
                } else if(args.item.id === 'GanttContainer_csvexport') {
                    var excelExportProperties: ExcelExportProperties = {
                        fileName:"Gantt.csv"
                    };
                    var ganttObj = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttObj.csvExport(excelExportProperties);
                }
            },
      };
  },
  provide: {
      gantt: [Toolbar, ExcelExport]
  }
};
</script>
```

{% endtab %}
