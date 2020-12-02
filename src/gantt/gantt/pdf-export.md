---
title: "PDF Export"
component: "Gantt"
description: "Learn how to export Gantt data to PDF document in the Essential JS 2 Gantt control."
---

# PDF Export

PDF export allows exporting Gantt data to PDF document. You need to use the [`pdfExport`](../api/gantt/#pdfexport) method for exporting. To enable PDF export in the Gantt, set the [`allowPdfExport`](../api/gantt/#allowpdfexport) to true.

To export data to PDF document, inject the `PdfExport` module in Gantt.

>Note: Currently, we do not have support for exporting manually scheduled tasks.

{% tab template="gantt/pdf-export" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowPdfExport='true' :height="height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, PdfExport, Selection } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations/src/toolbar/toolbar';
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
        toolbar: ['PdfExport'],
        toolbarClick: (args) => {
               if (args.item.id === 'GanttContainer_pdfexport') {
                    var ganttChart = document.getElementById('app').ej2_instances[0];
                    ganttChart.pdfExport();
                }
            },
      };
  },
  provide: {
      gantt: [Toolbar, PdfExport]
  }
};
</script>

```

{% endtab %}

## Multiple exporting

PDF export provides an option for exporting multiple Gantt to same file. In this exported document, each Gantt will be exported to a new page of the document in same file.

{% tab template="gantt/pdf-multiple-export" %}

```html

<template>
     <div>
     <p><b>First Gantt:</b></p>
        <ejs-gantt ref='gantt1' id="GanttContainer1" :dataSource="fData" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowPdfExport='true' :height="height1" :treeColumnIndex="1" :projectStartDate="projectStartDate" :projectEndDate="projectEndDate"></ejs-gantt>
    <p><b>Second Gantt:</b></p>
        <ejs-gantt ref='gantt2' id="GanttContainer2" :dataSource="sData" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick"  :allowPdfExport='true' :height="height2" :treeColumnIndex="1"></ejs-gantt>  
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, PdfExport, Selection } from "@syncfusion/ej2-vue-gantt";
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
        toolbar: ['PdfExport'],
        projectStartDate: new Date('03/31/2019'),
        projectEndDate: new Date('04/14/2019'),
        toolbarClick: (args) => {
                if (args.item.id === 'GanttContainer1_pdfexport') {
                    var firstGantt = document.getElementById('GanttContainer1').ej2_instances[0];
                    var firstGanttExport =  firstGantt.pdfExport({},true);
                    firstGanttExport.then((fData) => {
                        var secondGantt = document.getElementById('GanttContainer2').ej2_instances[0];
                        secondGantt.pdfExport({},false,fData);
                    });
                }
        },
        };
  },
  provide: {
    gantt: [Toolbar, PdfExport]
  }
};
</script>

```

{% endtab %}

## To customize PDF export

PDF export provides an option to customize the mapping of Gantt to exported PDF document.

### File name for exported document

You can assign a file name for the exported document by defining the `fileName` property in `pdfExportProperties`.

{% tab template="gantt/pdf-export" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowPdfExport='true' :height="height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, PdfExport, Selection } from "@syncfusion/ej2-vue-gantt";
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
        toolbar: ['PdfExport'],
        toolbarClick: (args) => {
                if (args.item.id === 'GanttContainer_pdfexport') {
                    var exportProperties: PdfExportProperties = {
                      fileName:"new.pdf"
                    };
                    var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttChart.pdfExport(exportProperties);
                }
            },
      };
  },
  provide: {
      gantt: [Toolbar, PdfExport]
  }
};
</script>

```

{% endtab %}

### How to change page orientation

Page orientation can be changed to `Portrait` (Default Landscape) for the exported document using the property `pdfExportProperties.pageOrientation`.

{% tab template="gantt/pdf-export" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowPdfExport='true' :height="height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, PdfExport, Selection } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations/src/toolbar/toolbar';
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
        toolbar: ['PdfExport'],
        toolbarClick: (args) => {
                if (args.item.id === 'GanttContainer_pdfexport') {
                    var exportProperties: PdfExportProperties = {
                      pageOrientation: 'Portrait'
                    };
                    var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttChart.pdfExport(exportProperties);
                }
            },
      };
  },
  provide: {
      gantt: [Toolbar, PdfExport]
  }
};
</script>

```

{% endtab %}

### How to change page size

Page size can be customized for the exported document using the property `pdfExportProperties.pageSize`.
The supported page sizes are:

* Letter
* Note
* Legal
* A0
* A1
* A2
* A3
* A5
* A6
* A7
* A8
* A9
* B0
* B1
* B2
* B3
* B4
* B5
* Archa
* Archb
* Archc
* Archd
* Arche
* Flsa
* HalfLetter
* Letter11x17
* Ledger

{% tab template="gantt/pdf-export" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowPdfExport='true' :height="height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { Gantt, Toolbar, PdfExport, Selection, PdfExportProperties } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations/src/toolbar/toolbar';
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
        toolbar: ['PdfExport'],
        toolbarClick: (args) => {
                if (args.item.id === 'GanttContainer_pdfexport') {
                    var exportProperties: PdfExportProperties = {
                      pageSize: 'A0'
                    };
                    var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttChart.pdfExport(exportProperties);
                }
            },
      };
  },
  provide: {
      gantt: [Toolbar, PdfExport]
  }
};
</script>

```

{% endtab %}

### Export current view data

PDF export provides an option to export the current view data into PDF. To export current view data alone, define the `exportType` to `CurrentViewData`.

{% tab template="gantt/pdf-export" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowPdfExport='true' :height="height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { Gantt, Toolbar, PdfExport, Selection, Filter, PdfExportProperties } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations/src/toolbar/toolbar';
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
        toolbar: ['PdfExport'],
        toolbarClick: (args) => {
                if (args.item.id === 'GanttContainer_pdfexport') {
                    var exportProperties: PdfExportProperties = {
                      exportType: 'CurrentViewData'
                    };
                    var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttChart.pdfExport(exportProperties);
                }
            },
      };
  },
  provide: {
      gantt: [Toolbar, PdfExport]
  }
};
</script>

```

{% endtab %}

### Enable footer

By default, we render the default footer for a PDF file, this can be enabled or disabled by using the `enableFooter` property.

{% tab template="gantt/pdf-export" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowPdfExport='true' :height="height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { Gantt, Toolbar, PdfExport, Selection, PdfExportProperties } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations/src/toolbar/toolbar';
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
        toolbar: ['PdfExport'],
        toolbarClick: (args) => {
                if (args.item.id === 'GanttContainer_pdfexport') {
                    var exportProperties: PdfExportProperties = {
                      enableFooter: false
                    };
                    var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttChart.pdfExport(exportProperties);
                }
            },
      };
  },
  provide: {
      gantt: [Toolbar, PdfExport]
  }
};
</script>

```

{% endtab %}

### Export hidden columns

PDF export provides an option to export hidden columns of Gantt by defining the `includeHiddenColumn` to `true`.

{% tab template="gantt/pdf-export" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :columns="columns" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowPdfExport='true' :height="height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { Gantt, Toolbar, PdfExport, Selection, PdfExportProperties } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations/src/toolbar/toolbar';
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
        columns: [
            { field: 'TaskID', headerText:  'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText:  'Task Name', width: '150', visible: false },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration',headerText: 'Duration', width: '150'},
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
        toolbar: ['PdfExport'],
        toolbarClick: (args) => {
                if (args.item.id === 'GanttContainer_pdfexport') {
                    var exportProperties: PdfExportProperties = {
                      includeHiddenColumn: true
                    };
                    var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttChart.pdfExport(exportProperties);
                }
            },
      };
  },
  provide: {
      gantt: [Toolbar, PdfExport]
  }
};
</script>

```

{% endtab %}

### Export predecessor lines

By using `showPredecessorLines`, you can hide or show predecessor lines in the exported PDF document.

{% tab template="gantt/pdf-export" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :columns="columns" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowPdfExport='true' :height="height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { Gantt, Toolbar, PdfExport, Selection, PdfExportProperties } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations/src/toolbar/toolbar';
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
        columns: [
            { field: 'TaskID', headerText:  'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText:  'Task Name', width: '150' },
            { field: 'StartDate', headerText: 'Start Date', width: '150', visible: false },
            { field: 'Duration',headerText: 'Duration', width: '150'},
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
        toolbar: ['PdfExport'],
        toolbarClick: (args) => {
                if (args.item.id === 'GanttContainer_pdfexport') {
                    var exportProperties: PdfExportProperties = {
                      showPredecessorLines: true
                    };
                    var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttChart.pdfExport(exportProperties);
                }
            },
      };
  },
  provide: {
      gantt: [Toolbar, PdfExport]
  }
};
</script>

```

{% endtab %}

### Show or hide columns on exported PDF

You can show a hidden column or hide a visible column while exporting the Gantt using the [`toolbarClick`](../api/gantt#toolbarclick) and [`beforePdfExport`](../api/gantt#beforepdfexport) events.

You can show or hide columns by setting the `column.visible` property to `true` or `false` respectively.

In the following example, there is a hidden column `Duration` in the Gantt. While exporting, we have changed `Duration` to visible column and `StartDate` to hidden column.

{% tab template="gantt/pdf-export" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :columns="columns" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowPdfExport='true' :beforePdfExport="beforePdfExport" :height="height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, PdfExport, Selection } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations/src/toolbar/toolbar';
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
        columns: [
            { field: 'TaskID', headerText:  'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText:  'Task Name', width: '150' },
            { field: 'StartDate', headerText: 'Start Date', width: '150'},
            { field: 'Duration',headerText: 'Duration', width: '150', visible: false },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
        toolbar: ['PdfExport'],
        toolbarClick: (args) => {
                if (args.item.id === 'GanttContainer_pdfexport') {
                    var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
                     ganttChart.pdfExport();
                }
            },
        beforePdfExport: EmitType<Object> = (args: Object) => {
         var obj = (document.getElementById('GanttContainer')).ej2_instances[0]
         obj.treeGrid.columns[3].visible = true;
         obj.treeGrid.columns[2].visible = false;
};
      };
  },
  provide: {
      gantt: [Toolbar, PdfExport]
  }
};
</script>

```

{% endtab %}

### Conditional cell formatting

TreeGrid cells in the exported PDF can be customized or formatted using the [`pdfQueryCellInfo`](../api/gantt#pdfquerycellinfo) event. In this event, you can format the treegrid cells of exported PDF document based on the column cell value.

In the following sample, the background color is set for `Progress` column in the exported document by using the `args.style` and `backgroundColor` properties.

{% tab template="gantt/pdf-export" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :columns="columns" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowPdfExport='true' :pdfQueryCellInfo="pdfQueryCellInfo"  :height="height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { Gantt, Toolbar, PdfExport, Selection, PdfQueryTimelineCellInfoEventArgs } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations/src/toolbar/toolbar';
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
        columns: [
            { field: 'TaskID', headerText:  'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText:  'Task Name', width: '150' },
            { field: 'StartDate', headerText: 'Start Date', width: '150'},
            { field: 'Duration',headerText: 'Duration', width: '150', visible: false },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
        toolbar: ['PdfExport'],
        toolbarClick: (args) => {
                if (args.item.id === 'GanttContainer_pdfexport') {
                    var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
                     ganttChart.pdfExport();
                }
            },
        pdfQueryCellInfo: (args) => {
    if(args.column.field == 'Progress'){
        if(args.value < 50) {
            args.style = {backgroundColor: '#F08080'};
        } else {
            args.style = {backgroundColor: '#A569BD'};
        }
    }
};
      };
  },
  provide: {
      gantt: [Toolbar, PdfExport]
  }
};
</script>

```

{% endtab %}

### Timeline cell formatting

Timeline cells in the exported PDF document can be customized or formatted using the [`pdfQueryTimelineCellInfo`](../api/treegrid#pdfquerytimelinecellinfo) event.

In the following sample, the header background color is set for timeline cells in the exported document by using the `args.headerBackgroundColor` property.

{% tab template="gantt/pdf-export" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields"
:columns="columns" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowPdfExport='true' :pdfQueryTimelineCellInfo="pdfQueryTimelineCellInfo" :height="height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { Gantt, Toolbar, PdfExport, Selection, PdfQueryTimelineCellInfoEventArgs } from "@syncfusion/ej2-vue-gantt";
import { PdfColor } from '@syncfusion/ej2-pdf-export';
import { ClickEventArgs } from '@syncfusion/ej2-navigations/src/toolbar/toolbar';
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
        columns: [
            { field: 'TaskID', headerText:  'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText:  'Task Name', width: '150' },
            { field: 'StartDate', headerText: 'Start Date', width: '150'},
            { field: 'Duration',headerText: 'Duration', width: '150', visible: false },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
        toolbar: ['PdfExport'],
        toolbarClick: (args) => {
                if (args.item.id === 'GanttContainer_pdfexport') {
                    var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
                     ganttChart.treeGrid.grid.columns[2].visible = false;
                     ganttChart.pdfExport();
                }
            },
        pdfQueryTimelineCellInfo: (args) => {
          args.timelineCell.backgroundColor = new PdfColor(240, 248, 255);
        };
      };
  },
  provide: {
      gantt: [Toolbar, PdfExport]
  }
};
</script>

```

{% endtab %}

### Taskbar formatting

Taskbars in the exported PDF document can be customized or formatted using the [`pdfQueryTaskbarInfo`](../api/treegrid#pdfquerytaskbarinfo) event.

In the following sample, the taskbar background color is customized in the chart side of the exported document by using the `args.taskbar` property.

{% tab template="gantt/pdf-export" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields"
:columns="columns" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowPdfExport='true' :pdfQueryTaskbarInfo="pdfQueryTaskbarInfo" :height="height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Toolbar, PdfExport, Selection } from "@syncfusion/ej2-vue-gantt";
import { PdfColor } from '@syncfusion/ej2-pdf-export';
import { ClickEventArgs } from '@syncfusion/ej2-navigations/src/toolbar/toolbar';
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
        columns: [
            { field: 'TaskID', headerText:  'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText:  'Task Name', width: '150', visible: false },
            { field: 'StartDate', headerText: 'Start Date', width: '150'},
            { field: 'Duration',headerText: 'Duration', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ],
        toolbar: ['PdfExport'],
        toolbarClick: (args) => {
                if (args.item.id === 'GanttContainer_pdfexport') {
                    var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
                     ganttChart.treeGrid.grid.columns[2].visible = false;
                     ganttChart.pdfExport();
                }
            },
        pdfQueryTaskbarInfo: (args) => {
          if(args.data.Progress < 50 && !args.data.hasChildRecords) {
           args.taskbar.progressColor = new PdfColor(205, 92, 92);
           args.taskbar.taskColor =  args.taskbar.taskBorderColor = new PdfColor(240, 128, 128);
    }
};
      };
  },
  provide: {
      gantt: [Toolbar, PdfExport]
  }
};
</script>

```

{% endtab %}

### Customized Theme

PDF export provides an option to customize the Gantt style in the exported PDF documents.

To customize the Gantt style in exported PDF, define the 'ganttStyle' in `pdfExportProperties`.  

{% tab template="gantt/pdf-export" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields="taskFields" :toolbar="toolbar" :toolbarClick="toolbarClick" :allowPdfExport='true' :height="height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { Gantt, Toolbar, PdfExport, Selection, PdfExportProperties } from "@syncfusion/ej2-vue-gantt";
import { ClickEventArgs } from '@syncfusion/ej2-navigations/src/toolbar/toolbar';
import { PdfColor } from '@syncfusion/ej2-pdf-export';
import { PdfPaddings } from '@syncfusion/ej2-gantt/src/export/pdf-base/pdf-borders';
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
        toolbar: ['PdfExport'],
        toolbarClick: (args) => {
                if (args.item.id === 'GanttContainer_pdfexport') {
                    let exportProperties: PdfExportProperties = {
                      fontFamily: 1,
                      columnHeader: {
                         backgroundColor: new PdfColor(179, 219, 255)
                      },
                      taskbar: {
                         taskColor: new PdfColor(240, 128, 128),
                         taskBorderColor: new PdfColor(240, 128, 128),
                         progressColor: new PdfColor(205, 92, 92),
                      },
                      connectorLineColor: new PdfColor(128, 0, 0),
                      footer: {
                        backgroundColor: new PdfColor(205, 92, 92)
                      },
                      timeline: {
                        backgroundColor: new PdfColor(179, 219, 255),
                        padding: new PdfPaddings(5, 2, 0, 0),
                     },
                     label: {
                        fontColor: new PdfColor(128, 0, 0),
                    },
                    cell: {
                      backgroundColor: new PdfColor(240, 248, 255),
                      fontColor: new PdfColor(0, 0, 0),
                      borderColor:new PdfColor(179, 219, 255),
                    },
                };
                    var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
                    ganttChart.pdfExport(exportProperties);
                }
            }
      };
  },
  provide: {
      gantt: [Toolbar, PdfExport]
  }
};
</script>

```

{% endtab %}