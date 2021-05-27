---
title: "Exporting"
component: "Scheduler"
description: "Learn how to export Scheduler events to an excel file/ICS file."
---

# Exporting

The Scheduler supports exporting all its appointments both to an Excel or ICS extension file at client-side. It offers different client-side methods to export its appointments in an Excel or ICal format file. Let's look onto the ways on how to implement the exporting functionality in Scheduler.

## Excel Exporting

The Scheduler allows you to export all its events into an Excel format file by using the [`exportToExcel`] client-side method. By default, it exports all the default fields of Scheduler mapped through `eventSettings` property.

> Before you start with excel exporting functionality, you need to import and inject the `ExcelExport` module from the '@syncfusion/ej2-schedule' package using the `Inject` method of Scheduler.

{% tab template="schedule/excel-export", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' ref="ScheduleObj" :cssClass="cssClass" height="550px" :selectedDate='selectedDate' :eventSettings='eventSettings'
                    :currentView="currentView" :actionBegin="onActionBegin">
                    <e-views>
                        <e-view option="Week"></e-view>
                    </e-views>
                </ejs-schedule>
            </div>
        </div>
</template>
<script>
import Vue from "vue";
import { SchedulePlugin, Week, View, Resize, DragAndDrop, ExcelExport
} from "@syncfusion/ej2-vue-schedule";
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);
export default {
        data: function () {
            return {
                cssClass: 'excel-export',
                eventSettings: { dataSource: scheduleData },
                selectedDate: new Date(2019, 0, 10),
                currentView: 'Week'
            }
        },
        provide: {
            schedule: [Week, Resize, DragAndDrop, ExcelExport]
        },
        methods: {
            onActionBegin: function (args) {
                if (args.requestType === 'toolbarItemRendering') {
                    let exportItem = {
                        align: 'Right', showTextOn: 'Both', prefixIcon: 'e-icon-schedule-excel-export',
                        text: 'Excel Export', cssClass: 'e-excel-export', click: this.onExportClick.bind(this)
                    };
                    args.items.push(exportItem);
                }
            },

            onExportClick: function () {
                let scheduleObj = this.$refs.ScheduleObj;
                scheduleObj.exportToExcel();
            }
        }
    }
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-schedule/styles/material.css";

    .excel-export.e-schedule .e-schedule-toolbar .e-icon-schedule-excel-export::before {
        content: '\e242';
    }

    .excel-export.e-schedule .e-schedule-toolbar .e-toolbar-item.e-today{
        display: none !important;
    }

</style>
```

{% endtab %}

### Exporting with custom fields

By default, Scheduler exports all the default event fields that are mapped to it through the `eventSettings` property. To limit the number of fields on the exported excel file, it provides an option to export only the custom fields of the event data. To export such custom fields alone, define the required `fields` through the `ExportOptions` interface and pass it as argument to the `exportToExcel` method as shown in the following example. For example: `['Id', 'Subject', 'StartTime', 'EndTime', 'Location']`.

{% tab template="schedule/excel-export", iframeHeight="588px"  %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' ref="ScheduleObj" :cssClass="cssClass" height="550px" :selectedDate='selectedDate' :eventSettings='eventSettings'
                    :currentView="currentView" :actionBegin="onActionBegin">
                    <e-views>
                        <e-view option="Week"></e-view>
                    </e-views>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { SchedulePlugin, Week, View, Resize, DragAndDrop, ExcelExport
} from "@syncfusion/ej2-vue-schedule";
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);
export default {
        data: function () {
            return {
                cssClass: 'excel-export',
                eventSettings: { dataSource: scheduleData },
                selectedDate: new Date(2019, 0, 10),
                currentView: 'Week'
            }
        },
        provide: {
            schedule: [Week, Resize, DragAndDrop, ExcelExport]
        },
        methods: {
            onActionBegin: function (args) {
                if (args.requestType === 'toolbarItemRendering') {
                    let exportItem = {
                        align: 'Right', showTextOn: 'Both', prefixIcon: 'e-icon-schedule-excel-export',
                        text: 'Excel Export', cssClass: 'e-excel-export', click: this.onExportClick.bind(this)
                    };
                    args.items.push(exportItem);
                }
            },

            onExportClick: function () {
                let scheduleObj = this.$refs.ScheduleObj;
                let exportValues = {
                    fields: ['Id', 'Subject', 'StartTime', 'EndTime', 'Location']
                };
                scheduleObj.exportToExcel(exportValues);
            }
        }
    }
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-schedule/styles/material.css";

    .excel-export.e-schedule .e-schedule-toolbar .e-icon-schedule-excel-export::before {
        content: '\e242';
    }

    .excel-export.e-schedule .e-schedule-toolbar .e-toolbar-item.e-today{
        display: none !important;
    }

</style>
```

{% endtab %}

### Exporting individual occurrences of a recurring series

By default, the Scheduler exports recurring events as a single data by exporting only its parent record into the excel file. If you want to export each individual occurrences of a recurring series appointment as separate records in an Excel file, define the `includeOccurrences` option as `true` through the `ExportOptions` interface and pass it as argument to the `exportToExcel` method. By default, the `includeOccurrences` option is set to `false`.

{% tab template="schedule/excel-export", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' ref="ScheduleObj" :cssClass="cssClass" height="550px" :selectedDate='selectedDate' :eventSettings='eventSettings'
                    :currentView="currentView" :actionBegin="onActionBegin">
                    <e-views>
                        <e-view option="Week"></e-view>
                    </e-views>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { SchedulePlugin, Week, View, Resize, DragAndDrop, ExcelExport
} from "@syncfusion/ej2-vue-schedule";
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);
export default {
        data: function () {
            return {
                cssClass: 'excel-export',
                eventSettings: { dataSource: scheduleData },
                selectedDate: new Date(2019, 0, 10),
                currentView: 'Week'
            }
        },
        provide: {
            schedule: [Week, Resize, DragAndDrop, ExcelExport]
        },
        methods: {
            onActionBegin: function (args) {
                if (args.requestType === 'toolbarItemRendering') {
                    let exportItem = {
                        align: 'Right', showTextOn: 'Both', prefixIcon: 'e-icon-schedule-excel-export',
                        text: 'Excel Export', cssClass: 'e-excel-export', click: this.onExportClick.bind(this)
                    };
                    args.items.push(exportItem);
                }
            },

            onExportClick: function () {
                let scheduleObj = this.$refs.ScheduleObj;
                let exportValues = { includeOccurrences: true };
                scheduleObj.exportToExcel(exportValues);
            }
        }
    }
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-schedule/styles/material.css";

    .excel-export.e-schedule .e-schedule-toolbar .e-icon-schedule-excel-export::before {
        content: '\e242';
    }

    .excel-export.e-schedule .e-schedule-toolbar .e-toolbar-item.e-today{
        display: none !important;
    }

</style>
```

{% endtab %}

### Exporting custom event data

By default, the whole event collection bound to the Scheduler gets exported as an excel file. To export only specific events of Scheduler or some custom event collection, you need to pass those custom data collection as a parameter to the `exportToExcel` method as shown in this following example, through the `customData` option of `ExportOptions` interface.

> By default, the event data are taken from Scheduler dataSource.

{% tab template="schedule/excel-export", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' ref="ScheduleObj" :cssClass="cssClass" height="550px" :selectedDate='selectedDate' :eventSettings='eventSettings'
                    :currentView="currentView" :actionBegin="onActionBegin">
                    <e-views>
                        <e-view option="Week"></e-view>
                    </e-views>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { SchedulePlugin, Week, View, Resize, DragAndDrop, ExcelExport
} from "@syncfusion/ej2-vue-schedule";
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);
export default {
        data: function () {
            return {
                cssClass: 'excel-export',
                eventSettings: { dataSource: scheduleData },
                selectedDate: new Date(2019, 0, 10),
                currentView: 'Week'
            }
        },
        provide: {
            schedule: [Week, Resize, DragAndDrop, ExcelExport]
        },
        methods: {
            onActionBegin: function (args) {
                if (args.requestType === 'toolbarItemRendering') {
                    let exportItem = {
                        align: 'Right', showTextOn: 'Both', prefixIcon: 'e-icon-schedule-excel-export',
                        text: 'Excel Export', cssClass: 'e-excel-export', click: this.onExportClick.bind(this)
                    };
                    args.items.push(exportItem);
                }
            },

            onExportClick: function () {
                let scheduleObj = this.$refs.ScheduleObj;
                let exportValues = {
                    customData: [{
                        Id: 1,
                        Subject: 'Explosion of Betelgeuse Star',
                        Location: 'Space Centre USA',
                        StartTime: new Date(2019, 0, 6, 9, 30),
                        EndTime: new Date(2019, 0, 6, 11, 0),
                        CategoryColor: '#1aaa55'
                    }, {
                        Id: 2,
                        Subject: 'Thule Air Crash Report',
                        Location: 'Newyork City',
                        StartTime: new Date(2019, 0, 7, 12, 0),
                        EndTime: new Date(2019, 0, 7, 14, 0),
                        CategoryColor: '#357cd2'
                    }]
                };
                scheduleObj.exportToExcel(exportValues);
            }
        }
    }
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-schedule/styles/material.css";

    .excel-export.e-schedule .e-schedule-toolbar .e-icon-schedule-excel-export::before {
        content: '\e242';
    }

    .excel-export.e-schedule .e-schedule-toolbar .e-toolbar-item.e-today{
        display: none !important;
    }

</style>
```

{% endtab %}

### Export with custom file name

By default, the Scheduler allows you to download the exported Excel file with a name `Schedule.xlsx`. It also provides an option to export the excel file with a custom file name, by defining the desired `fileName` through the `ExportOptions` interface and passing it as an argument to the `exportToExcel` method.

{% tab template="schedule/excel-export", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' ref="ScheduleObj" :cssClass="cssClass" height="550px" :selectedDate='selectedDate' :eventSettings='eventSettings'
                    :currentView="currentView" :actionBegin="onActionBegin">
                    <e-views>
                        <e-view option="Week"></e-view>
                    </e-views>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { SchedulePlugin, Week, View, Resize, DragAndDrop, ExcelExport
} from "@syncfusion/ej2-vue-schedule";
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);
export default {
        data: function () {
            return {
                cssClass: 'excel-export',
                eventSettings: { dataSource: scheduleData },
                selectedDate: new Date(2019, 0, 10),
                currentView: 'Week'
            }
        },
        provide: {
            schedule: [Week, Resize, DragAndDrop, ExcelExport]
        },
        methods: {
            onActionBegin: function (args) {
                if (args.requestType === 'toolbarItemRendering') {
                    let exportItem = {
                        align: 'Right', showTextOn: 'Both', prefixIcon: 'e-icon-schedule-excel-export',
                        text: 'Excel Export', cssClass: 'e-excel-export', click: this.onExportClick.bind(this)
                    };
                    args.items.push(exportItem);
                }
            },

            onExportClick: function () {
                let scheduleObj = this.$refs.ScheduleObj;
                let exportValues = { fileName: "SchedulerData" };
                scheduleObj.exportToExcel(exportValues);
            }
        }
    }
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-schedule/styles/material.css";

    .excel-export.e-schedule .e-schedule-toolbar .e-icon-schedule-excel-export::before {
        content: '\e242';
    }

    .excel-export.e-schedule .e-schedule-toolbar .e-toolbar-item.e-today{
        display: none !important;
    }

</style>
```

{% endtab %}

### Excel file formats

By default, the Scheduler exports event data to an excel file in the `.xlsx` format. You can also export the Scheduler data in either of the file type such as `.xlsx` or `csv` formats, by defining the `exportType` option as either `csv` or `xlsx` through the `ExportOptions` interface. By default, the `exportType` is set to `xlsx`.

{% tab template="schedule/excel-export", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' ref="ScheduleObj" :cssClass="cssClass" height="550px" :selectedDate='selectedDate' :eventSettings='eventSettings'
                    :currentView="currentView" :actionBegin="onActionBegin">
                    <e-views>
                        <e-view option="Week"></e-view>
                    </e-views>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { SchedulePlugin, Week, View, Resize, DragAndDrop, ExcelExport
} from "@syncfusion/ej2-vue-schedule";
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);
export default {
        data: function () {
            return {
                cssClass: 'excel-export',
                eventSettings: { dataSource: scheduleData },
                selectedDate: new Date(2019, 0, 10),
                currentView: 'Week'
            }
        },
        provide: {
            schedule: [Week, Resize, DragAndDrop, ExcelExport]
        },
        methods: {
            onActionBegin: function (args) {
                if (args.requestType === 'toolbarItemRendering') {
                    let exportItem = {
                        align: 'Right', showTextOn: 'Both', prefixIcon: 'e-icon-schedule-excel-export',
                        text: 'Excel Export', cssClass: 'e-excel-export', click: this.onExportClick.bind(this)
                    };
                    args.items.push(exportItem);
                }
            },

            onExportClick: function () {
                let scheduleObj = this.$refs.ScheduleObj;
                let exportValues = { exportType: "csv" };
                scheduleObj.exportToExcel(exportValues);
            }
        }
    }
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-schedule/styles/material.css";

    .excel-export.e-schedule .e-schedule-toolbar .e-icon-schedule-excel-export::before {
        content: '\e242';
    }

    .excel-export.e-schedule .e-schedule-toolbar .e-toolbar-item.e-today{
        display: none !important;
    }

</style>
```

{% endtab %}

## Exporting calendar events as ICS file

You can export the Scheduler events to a calendar (.ics) file format, and open it on any of the other default calendars such as Google or Outlook. To export the events of Scheduler to an ICS file, you need to first import the `ICalendarExport` module from `@syncfusion/ej2-schedule` package and then inject it using the `Schedule.Inject(ICalendarExport)` method.

The following code example shows how the Scheduler events are exported to a calendar (.ics) file by making use of the `exportToICalendar` public method.

{% tab template="schedule/calendar-export", iframeHeight="588px" %}

```html
<template>
  <div>
        <div id='app'>
            <div id='container'>
                <ejs-button id='ics-export' v-on:click.native="onClick">Export</ejs-button>
                <ejs-schedule id="Schedule" ref="ScheduleObj" height="520px" :selectedDate='selectedDate'
                    :eventSettings='eventSettings' :currentView='currentView'>
                    <e-views>
                        <e-view option="Day"></e-view>
                        <e-view option="Week"></e-view>
                        <e-view option="WorkWeek"></e-view>
                        <e-view option="Month"></e-view>
                        <e-view option="Agenda"></e-view>
                    </e-views>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>
<script>
    import Vue from "vue";
    import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda, Resize, DragAndDrop, ICalendarExport, ICalendarImport } from "@syncfusion/ej2-vue-schedule";
    import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
    import { scheduleData } from './datasource.js';

    Vue.use(ButtonPlugin);
    Vue.use(SchedulePlugin);

    export default {
        data: function () {
            return {
                eventSettings: { dataSource: scheduleData },
                selectedDate: new Date(2018, 1, 15),
                currentView: 'Week',
                cssClass:'calendar-import',
                multiple: false,
                allowedExtensions: '.ics',
                buttons: {
                    browse: 'Choose file',
                },
                showFileList: false,
            }
        },
        provide: {
            schedule: [Day, Week, WorkWeek, Month, Agenda, Resize, DragAndDrop, ICalendarExport, ICalendarImport]
        },
        methods: {
            onClick: function () {
                let scheduleObj = document.getElementById('Schedule').ej2_instances[0];
                scheduleObj.exportToICalendar();
            }
        }
    }
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-schedule/styles/material.css";

    .calendar-import.e-upload {
        border: 0;
        padding-left: 0 !important;
    }

    .calendar-import.e-upload .e-file-select-wrap {
        padding: 0
    }

    .calendar-import.e-upload .e-file-select-wrap .e-file-drop {
        display: none;
    }
</style>
```

{% endtab %}

### Exporting calendar with custom file name

By default, the calendar is exported with a file name `Calendar.ics`. To change this file name on export, pass the custom string value as `fileName` to the method argument so as to get the file downloaded with this provided name.

The following example downloads the iCal file with a name `ScheduleEvents.ics`.

{% tab template="schedule/calendar-export", iframeHeight="588px" %}

```html
<template>
  <div>
        <div id='app'>
            <div id='container'>
                <ejs-button id='ics-export' v-on:click.native="onClick">Export</ejs-button>
                <ejs-schedule id="Schedule" ref="ScheduleObj" height="520px" :selectedDate='selectedDate'
                    :eventSettings='eventSettings' :currentView='currentView'>
                    <e-views>
                        <e-view option="Day"></e-view>
                        <e-view option="Week"></e-view>
                        <e-view option="WorkWeek"></e-view>
                        <e-view option="Month"></e-view>
                        <e-view option="Agenda"></e-view>
                    </e-views>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>
<script>
    import Vue from "vue";
    import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda, Resize, DragAndDrop, ICalendarExport, ICalendarImport } from "@syncfusion/ej2-vue-schedule";
    import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
    import { scheduleData } from './datasource.js';

    Vue.use(ButtonPlugin);
    Vue.use(SchedulePlugin);

    export default {
        data: function () {
            return {
                eventSettings: { dataSource: scheduleData },
                selectedDate: new Date(2018, 1, 15),
                currentView: 'Week',
                cssClass:'calendar-import',
                multiple: false,
                allowedExtensions: '.ics',
                buttons: {
                    browse: 'Choose file',
                },
                showFileList: false,
            }
        },
        provide: {
            schedule: [Day, Week, WorkWeek, Month, Agenda, Resize, DragAndDrop, ICalendarExport, ICalendarImport]
        },
        methods: {
            onClick: function () {
                let scheduleObj = document.getElementById('Schedule').ej2_instances[0];
                scheduleObj.exportToICalendar('ScheduleEvents');
            }
        }
    }
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-schedule/styles/material.css";

    .calendar-import.e-upload {
        border: 0;
        padding-left: 0 !important;
    }

    .calendar-import.e-upload .e-file-select-wrap {
        padding: 0
    }

    .calendar-import.e-upload .e-file-select-wrap .e-file-drop {
        display: none;
    }
</style>
```

{% endtab %}

## Import events from other calendars

The events from external calendars (ICS files) can be imported into Scheduler by using the `importICalendar` method. This method accepts the `blob object` of an .ics file to be imported, as a mandatory argument.

> To import an ICS file containing events into Scheduler, you need to first import the `ICalendarImport` module from `@syncfusion/ej2-schedule` package and then inject it using the `Schedule.Inject(ICalendarImport)` method.

The following example shows how to import an ICS file into Scheduler, using the `importICalendar` method.

{% tab template="schedule/calendar-import", iframeHeight="588px" %}

```html
<template>
  <div>
        <div id='app'>
            <div id='container'>
                <ejs-uploader id='ics-import' :cssClass='cssClass' name="ics-import" :buttons="buttons"
                :showFileList='showFileList' :multiple='multiple' :allowedExtensions='extensions'
                :selected='onSelect'/>
                <ejs-schedule id="Schedule" ref="ScheduleObj" height="520px" :selectedDate='selectedDate'
                    :eventSettings='eventSettings' :currentView='currentView'>
                    <e-views>
                        <e-view option="Day"></e-view>
                        <e-view option="Week"></e-view>
                        <e-view option="WorkWeek"></e-view>
                        <e-view option="Month"></e-view>
                        <e-view option="Agenda"></e-view>
                    </e-views>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>
<script>
    import Vue from "vue";
    import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda, Resize, DragAndDrop, ICalendarExport, ICalendarImport } from "@syncfusion/ej2-vue-schedule";
    import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
    import { scheduleData } from './datasource.js';

    Vue.use(UploaderPlugin);
    Vue.use(SchedulePlugin);

    export default {
        data: function () {
            return {
                eventSettings: { dataSource: scheduleData },
                selectedDate: new Date(2018, 1, 15),
                currentView: 'Week',
                cssClass:'calendar-import',
                multiple: false,
                extensions: '.ics',
                buttons: {
                    browse: 'Choose file',
                },
                showFileList: false,
            }
        },
        provide: {
            schedule: [Day, Week, WorkWeek, Month, Agenda, Resize, DragAndDrop, ICalendarExport, ICalendarImport]
        },
        methods: {
            onSelect: function (args) {
                let scheduleObj = document.getElementById('Schedule').ej2_instances[0];
                scheduleObj.importICalendar(args.event.target.files[0]);
            }
        }
    }
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-schedule/styles/material.css";

    .calendar-import.e-upload {
        border: 0;
        padding-left: 0 !important;
    }

    .calendar-import.e-upload .e-file-select-wrap {
        padding: 0
    }

    .calendar-import.e-upload .e-file-select-wrap .e-file-drop {
        display: none;
    }
</style>
```

{% endtab %}

## How to print the Scheduler element

The Scheduler allows you to print the Scheduler element by using the `print` client-side method. The print method works in two ways. You can find it below.

* Using print method without options.
* Using a print method with options.

> To print the Schedule, you need to import the `Print` module from the `@syncfusion/ej2-vue-schedule` package and then inject it using `provide: {schedule: [Print]}`.

### Using print method without options

You can print the Schedule element with the current view by using the `print` method without passing the options. The following example shows how to print the Scheduler using the `print` method without passing options.

{% tab template="schedule/print", iframeHeight="588px" %}

```html
<template>
  <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id="Schedule" ref="ScheduleObj" height="520px" :selectedDate='selectedDate'
                    :eventSettings='eventSettings' :actionBegin="onActionBegin">
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>
<script>
    import Vue from "vue";
    import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda, Print } from "@syncfusion/ej2-vue-schedule";
    import { scheduleData } from './datasource.js';

    Vue.use(SchedulePlugin);

    export default {
        data: function () {
            return {
                eventSettings: { dataSource: scheduleData },
                selectedDate: new Date(2018, 1, 15),
                cssClass:'schedule-print',
            }
        },
        provide: {
            schedule: [Day, Week, WorkWeek, Month, Agenda, Print]
        },
        methods: {
            onActionBegin: function (args) {
                if (args.requestType === 'toolbarItemRendering') {
                    let exportItem = {
                        align: 'Right', showTextOn: 'Both', prefixIcon: 'e-icon-schedule-print',
                        text: 'Print', cssClass: 'e-print', click: this.onPrintIconClick.bind(this)
                    };
                    args.items.push(exportItem);
                }
            },

            onPrintIconClick: function () {
                let scheduleObj = this.$refs.ScheduleObj;
                scheduleObj.print();
            }
        }
    }
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-schedule/styles/material.css";

.e-schedule .e-schedule-toolbar .e-icon-schedule-print::before {
  content: '\e813';
}
</style>
```

{% endtab %}

### Using a print method with options

You can print the Schedule element based on your needs using the `print` method by passing the print options used in this example with its values. The following example shows how to print the Scheduler using the `print` method by passing the options.

{% tab template="schedule/print", iframeHeight="588px" %}

```html
<template>
  <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id="Schedule" ref="ScheduleObj" height="520px" :selectedDate='selectedDate'
                    :eventSettings='eventSettings' :actionBegin="onActionBegin">
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>
<script>
    import Vue from "vue";
    import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda, Print } from "@syncfusion/ej2-vue-schedule";
    import { scheduleData } from './datasource.js';

    Vue.use(SchedulePlugin);

    export default {
        data: function () {
            return {
                eventSettings: { dataSource: scheduleData },
                selectedDate: new Date(2018, 1, 15),
                cssClass:'schedule-print',
            }
        },
        provide: {
            schedule: [Day, Week, WorkWeek, Month, Agenda, Print]
        },
        methods: {
            onActionBegin: function (args) {
                if (args.requestType === 'toolbarItemRendering') {
                    let exportItem = {
                        align: 'Right', showTextOn: 'Both', prefixIcon: 'e-icon-schedule-print',
                        text: 'Print', cssClass: 'e-print', click: this.onPrintIconClick.bind(this)
                    };
                    args.items.push(exportItem);
                }
            },

            onPrintIconClick: function () {
                let scheduleObj = this.$refs.ScheduleObj;
                let printModel = {
                    agendaDaysCount: 14,
                    cssClass: 'e-print-schedule',
                    currentView: scheduleObj.currentView,
                    dateFormat: 'dd-MMM-yyyy',
                    enableRtl: false,
                    endHour: '18:00',
                    firstDayOfWeek: 1,
                    firstMonthOfYear: 0,
                    group: {},
                    height: 'auto',
                    locale: scheduleObj.locale,
                    maxDate: scheduleObj.selectedDate,
                    minDate: scheduleObj.getCurrentViewDates()[0],
                    readonly: true,
                    resources: [],
                    rowAutoHeight: false,
                    selectedDate: new Date(),
                    showHeaderBar: false,
                    showTimeIndicator: false,
                    showWeekNumber: false,
                    showWeekend: false,
                    startHour: '06:00',
                    timeFormat: 'HH',
                    timeScale: { enable: true },
                    width: 'auto',
                    workDays: [1, 2, 3, 4, 5],
                    workHours: { highlight: true, start: '10:00', end: '20:00' }
                };
                scheduleObj.print(printModel);
            }
        }
    }
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-schedule/styles/material.css";

.e-schedule .e-schedule-toolbar .e-icon-schedule-print::before {
  content: '\e813';
}
</style>
```

{% endtab %}