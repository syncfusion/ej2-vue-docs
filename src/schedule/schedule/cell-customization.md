---
title: "Customizing Scheduler Cells"
component: "Scheduler"
description: "This topic demonstrates how to customize the cells of Scheduler using template option, methods and events available in Scheduler."
---

# Cell Customization

The cells of the Scheduler can be easily customized either using the cell template or `RenderCell` event.

## Setting cell dimensions in all views

The height and width of the Scheduler cells can be customized either to increase or reduce its size through the `cssClass` property, which overrides the default CSS applied on cells.

{% tab template="schedule/cell-dimension", iframeHeight="588px"  %}

```html
<template>
    <div id='app'>
        <div id='container'>
            <ejs-schedule id='Schedule' width='100%' cssClass='schedule-cell-dimension' height='550px' :selectedDate='selectedDate' :eventSettings='eventSettings'>
                <e-views>
                    <e-view option='Day'></e-view>
                    <e-view option='Week'></e-view>
                    <e-view option='WorkWeek'></e-view>
                    <e-view option='Month'></e-view>
                </e-views>
            </ejs-schedule>
        </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { employeeEventData } from './datasource.js';
    import { SchedulePlugin, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-vue-schedule';
    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                eventSettings: { dataSource: employeeEventData },
                selectedDate: new Date(2018, 1, 15)
            }
        },
        provide: {
            schedule: [Day, Week, WorkWeek, Month]
        }
    }

</script>
<style>
@import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css';

.schedule-cell-dimension.e-schedule .e-vertical-view .e-date-header-wrap table col,
.schedule-cell-dimension.e-schedule .e-vertical-view .e-content-wrap table col {
    width: 200px;
}

.schedule-cell-dimension.e-schedule .e-vertical-view .e-time-cells-wrap table td,
.schedule-cell-dimension.e-schedule .e-vertical-view .e-work-cells {
    height: 100px;
}

.schedule-cell-dimension.e-schedule .e-month-view .e-work-cells,
.schedule-cell-dimension.e-schedule .e-month-view .e-date-header-wrap table col {
    width: 200px;
}

.schedule-cell-dimension.e-schedule .e-month-view .e-work-cells {
    height: 200px;
}

</style>

```

{% endtab %}

## Check for cell availability

You can check whether the given time range slots are available for event creation or already occupied by other events using the `isSlotAvailable` method. In the following code example, if a specific time slot already contains an appointment, then no more appointments can be added to that cell.

{% tab template="schedule/cell-dimension", iframeHeight="588px"  %}

```html
<template>
    <div id='app'>
        <div id='container'>
            <ejs-schedule ref='scheduleObj' width='100%' height='550px' :selectedDate='selectedDate' :eventSettings='eventSettings' :actionBegin='onActionBegin'>
                <e-views>
                    <e-view option='Week'></e-view>
                    <e-view option='WorkWeek'></e-view>
                </e-views>
            </ejs-schedule>
        </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { scheduleData } from './datasource.js';
    import { SchedulePlugin, Week, WorkWeek, View } from '@syncfusion/ej2-vue-schedule';
    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                eventSettings: { dataSource: scheduleData },
                selectedDate: new Date(2018, 1, 15)
            }
        },
        methods: {
            onActionBegin: function(args){
                if (args.requestType === 'eventCreate' && args.data.length > 0) {
                    let eventData = args.data[0];
                    let scheduleObj = this.$refs.scheduleObj.ej2Instances;
                    let eventField = scheduleObj.eventFields;
                    let startDate = eventData[eventField.startTime];
                    let endDate = eventData[eventField.endTime];
                    args.cancel = !scheduleObj.isSlotAvailable(startDate, endDate);
                }
            }
        },
        provide: {
            schedule: [Week, WorkWeek]
        }
    }
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";

</style>

```

{% endtab %}

## Customizing cells in all the views

It is possible to customize the appearance of the cells using both template options and `renderCell` event on all the views.

### Using template

The `cellTemplate` option accepts the template string and is used to customize the cell background with specific images or appropriate text on the given date values.

{% tab template="schedule/cell-dimension", iframeHeight="588px"  %}

```html
<template>
    <div id='app'>
        <div id='container'>
            <ejs-schedule ref='scheduleObj' width='100%' height='550px' :selectedDate='selectedDate' :cellTemplate='cellTemplate' cssClass='schedule-cell-template'>
                <e-views>
                    <e-view option='Day'></e-view>
                    <e-view option='Week'></e-view>
                    <e-view option='Month'></e-view>
                    <e-view option='TimelineWeek'></e-view>
                </e-views>
            </ejs-schedule>
        </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { SchedulePlugin, Day, Week, TimelineViews, Month, View } from '@syncfusion/ej2-vue-schedule';
    Vue.use(SchedulePlugin);

    var cellTemplateVue = Vue.component("cellTemplate", {
        template: `<div class="templatewrap"><div v-if="data.type==='workCells'"><div v-html=getWorkCellText(data.date)></div></div><div v-else-if="data.type==='monthCells'"><div v-html=getMonthCellText(data.date)></div></div></div>`,
        data() {
            return {
                data: {}
            };
        },
        methods: {
            getWorkCellText: function(date) {
                let weekEnds = [0, 6];
                if (weekEnds.indexOf(date.getDay()) >= 0) {
                    return "<img src='https://ej2.syncfusion.com/demos/src/schedule/images/newyear.svg' />";
                }
                return '';
            },
            getMonthCellText: function(date) {
                if (date.getMonth() === 10 && date.getDate() === 23) {
                    return '<img src= "https://ej2.syncfusion.com/demos/src/schedule/images/birthday.svg"/>';
                } else if (date.getMonth() === 11 && date.getDate() === 9) {
                    return '<img src= "https://ej2.syncfusion.com/demos/src/schedule/images/get-together.svg" />';
                } else if (date.getMonth() === 11 && date.getDate() === 13) {
                    return '<img src= "https://ej2.syncfusion.com/demos/src/schedule/images/birthday.svg" />';
                } else if (date.getMonth() === 11 && date.getDate() === 22) {
                    return '<img src= "https://ej2.syncfusion.com/demos/src/schedule/images/thanksgiving-day.svg" />';
                } else if (date.getMonth() === 11 && date.getDate() === 24) {
                    return '<img src="https://ej2.syncfusion.com/demos/src/schedule/images/christmas-eve.svg" />';
                } else if (date.getMonth() === 11 && date.getDate() === 25) {
                    return '<img src= "https://ej2.syncfusion.com/demos/src/schedule/images/christmas.svg" />';
                } else if (date.getMonth() === 0 && date.getDate() === 1) {
                    return '<img src= "https://ej2.syncfusion.com/demos/src/schedule/images/newyear.svg" />';
                } else if (date.getMonth() === 0 && date.getDate() === 14) {
                    return '<img src= "https://ej2.syncfusion.com/demos/src/schedule/images/birthday.svg" />';
                }
                return '';
            }
        }
    });

    export default {
        data () {
            return {
                selectedDate: new Date(2017, 11, 16),
                cellTemplate: function (e) {
                    return {
                        template: cellTemplateVue
                    };
                },
            }
        },
        provide: {
            schedule: [Day, Week, Month, TimelineViews]
        }
    }
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";

.templatewrap {
  text-align: center;
  /* In MONTH view the cell template is a SIBLING of event templates. So which is necessary to set the parent position relative and the child position absolute with 100% width */
  position: absolute;
  width: 100%;
}

.schedule-cell-template.e-schedule .e-month-view .e-work-cells {
  position: relative;
}

.templatewrap img {
  width: 20px;
  height: 20px;
}
</style>

```

{% endtab %}

### Using renderCell event

An alternative to `cellTemplate` is the `renderCell` event, which can also be used to customize the cells with appropriate images or formatted text values.

{% tab template="schedule/cell-dimension", iframeHeight="588px"  %}

```html
<template>
    <div id='app'>
        <div id='container'>
            <ejs-schedule ref='scheduleObj' width='100%' height='550px' :selectedDate='selectedDate' :currentView='currentView' :renderCell='onRenderCell'>
                <e-views>
                    <e-view option='Day'></e-view>
                    <e-view option='Week'></e-view>
                    <e-view option='Month'></e-view>
                </e-views>
            </ejs-schedule>
        </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { createElement } from '@syncfusion/ej2-base';
    import { SchedulePlugin, Day, Week, Month } from '@syncfusion/ej2-vue-schedule';
    import { scheduleData } from './datasource.js';
    Vue.use(SchedulePlugin);

    export default {
        data () {
            return {
                selectedDate: new Date(2018, 1, 14),
                eventSettings: { dataSource: scheduleData },
                currentView: 'Month'
            }
        },
        methods: {
            onRenderCell: (args) => {
                if (args.elementType == 'workCells' || args.elementType == 'monthCells') {
                    let weekEnds = [0, 6];
                    if (weekEnds.indexOf((args.date).getDay()) >= 0) {
                        let ele = createElement('div', {
                            innerHTML: "<img src='https://ej2.syncfusion.com/demos/src/schedule/images/newyear.svg' />",
                            className: 'templatewrap'
                        });
                        (args.element).appendChild(ele);
                    }
                }
            }
        },
        provide: {
            schedule: [Day, Week, Month]
        }
    }
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css";

.templatewrap {
  text-align: center;
  width: 100%;
}

.templatewrap img {
  width: 20px;
  height: 20px;
}
</style>
```

{% endtab %}

You can customize cells such as work cells, month cells, all-day cells, header cells, resource header cells using `renderCell` event by checking the `elementType` option within the event. You can check elementType with any of the following.

| Element type | Description |
|-------|---------|
| dateHeader | triggers on header cell rendering.|
| monthDay | triggers on header cell in month view rendering.|
| resourceHeader | triggers on resource header cell rendering.|
| alldayCells | triggers on all day cell rendering.|
| emptyCells | triggers on empty cell rendering on header bar.|
| resourceGroupCells | triggers on rendering of work cells for parent resource.|
| workCells | triggers on work cell rendering.|
| monthCells | triggers on month cell rendering.|
| majorSlot | triggers on major time slot cell rendering.|
| minorSlot | triggers on minor time slot cell rendering.|
| weekNumberCell | triggers on cell displaying week number.|

## Customizing cell header in month view

The month header of each date cell in the month view can be customized using the `cellHeaderTemplate` option which accepts the string or HTMLElement. The corresponding date can be accessed with the template.

{% tab template="schedule/cell-dimension", iframeHeight="588px"  %}

```html
<template>
    <div id='app'>
        <div id='container'>
            <ejs-schedule ref='scheduleObj' width='100%' height='550px' :cellHeaderTemplate='cellHeaderTemplate' cssClass='schedule-cell-header-template'>
                <e-views>
                    <e-view option='Month'></e-view>
                </e-views>
            </ejs-schedule>
        </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { Internationalization } from '@syncfusion/ej2-base';
    import { SchedulePlugin, Month } from '@syncfusion/ej2-vue-schedule';
    Vue.use(SchedulePlugin);

    var instance = new Internationalization();
    var cellHeaderTemplateVue = Vue.component("cellHeaderTemplate", {
        template: `<div v-html=getDateHeaderText(data.date)></div>`,
        data() {
            return {
                data: {}
            };
        },
        methods: {
            getDateHeaderText: function(date) {
                return instance.formatDate(date, { skeleton: "Ed" });
            }
        }
    });

    export default {
        data () {
            return {
                cellHeaderTemplate: function (e) {
                    return {
                        template: cellHeaderTemplateVue
                    };
                },
            }
        },
        provide: {
            schedule: [Month]
        }
    }
</script>
```

{% endtab %}

## Customizing the minimum and maximum date values

Providing the `minDate` and `maxDate` property with some date values, allows the Scheduler to set the minimum and maximum date range. The Scheduler date that lies beyond this minimum and maximum date range will be in a disabled state so that the date navigation will be blocked beyond the specified date range.

{% tab template="schedule/cell-dimension", iframeHeight="588px"  %}

```html
<template>
    <div id='app'>
        <ejs-schedule height='550px' :selectedDate='selectedDate' :minDate='minDate' :maxDate='maxDate' :currentView='currentView'>
        </ejs-schedule>
    </div>
</template>
<script>
  import Vue from 'vue';
  import { scheduleData } from './datasource.js';
  import { SchedulePlugin, Day, WorkWeek, Agenda, Month, Week } from '@syncfusion/ej2-vue-schedule';
  Vue.use(SchedulePlugin);
  export default {
    data () {
      return {
        selectedDate: new Date(2018, 1, 17),
        minDate: new Date(2017, 4, 17),
        maxDate: new Date(2018, 5, 17)
        eventSettings: { dataSource: scheduleData },
        currentView: 'Month',
      }
    },
    provide: {
      schedule: [Day, WorkWeek, Agenda, Month, Week]
    }
  }
</script>
```

{% endtab %}

>By default, the `minDate` property value is set to new Date(1900, 0, 1) and `maxDate` property value is set to new Date(2099, 11, 31). The user can also set the customized `minDate` and `maxDate` property values.

## How to disable multiple cell and row selection in Schedule

By default, the `allowMultiCellSelection` and `allowMultiRowSelection` properties of the Schedule are set to `true`. So, the Schedule allows user to select multiple cells and rows. If the user want to disable this multiple cell and row selection. The user can disable this feature by setting up `false` to these properties.