---
title: "Row auto height in VueJS Scheduler"
component: "Scheduler"
description: "This section shows the way to auto-adjust the height of the work-cells of Scheduler based on the number of appointments present in those time ranges."
---

# Row Auto Height

By default, the height of the Scheduler rows in Timeline views are static and therefore, when the same time range holds multiple overlapping appointments, a `+n more` text indicator will be displayed. With this feature enabled, you can now view all the overlapping appointments present in those specific time range by auto-adjusting the row height based on the presence of the appointments count, instead of displaying the `+n more` text indicators.

To enable auto row height adjustments on Scheduler Timeline views and Month view, set `true` to the `rowAutoHeight` property whose default value is `false`.

> This auto row height adjustment is applicable only on all the Timeline views as well as on the calendar Month view.

Now, let's see how it works on those applicable views with examples.

## Calendar month view

By default, the rows of the calendar Month view can hold only the limited appointments count based on its row height, and the rest of the overlapping appointments are indicated with a `+n more` text indicator. The following example shows how the month view row auto-adjusts based on the number of appointments count, when this `RowAutoHeight` feature is enabled.

{% tab template="schedule/working-days", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule height='550px' width='100%' :selectedDate='selectedDate' :eventSettings='eventSettings' :rowAutoHeight='rowAutoHeight'>
                    <e-views>
                        <e-view option='Month'></e-view>
                    </e-views>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { scheduleData } from './datasource.js';
    import { SchedulePlugin, Month } from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                selectedDate: new Date(2018, 1, 15),
                currentView: 'Month',
                rowAutoHeight: true,
                eventSettings: { dataSource: scheduleData }
            }
        },
        provide: {
            schedule: [Month]
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

## Timeline views

When the feature `RowAutoHeight` is enabled in Timeline views, the row height gets auto-adjusted based on the number of overlapping events occupied on the same time range, which is demonstrated in the following example.

{% tab template="schedule/working-days", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule height='550px' width='100%' :selectedDate='selectedDate' :eventSettings='eventSettings' :rowAutoHeight='rowAutoHeight'>
                    <e-views>
                        <e-view option='TimelineDay'></e-view>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineWorkWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                        <e-view option='Agenda'></e-view>
                    </e-views>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { scheduleData } from './datasource.js';
    import { SchedulePlugin, TimelineViews, TimelineMonth, Agenda
    } from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                selectedDate: new Date(2018, 1, 15),
                currentView: 'TimelineWeek',
                rowAutoHeight: true,
                eventSettings: { dataSource: scheduleData }
            }
        },
        provide: {
            schedule: [TimelineViews, TimelineMonth, Agenda]
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

## Timeline views with multiple resources

The following example shows how the auto row adjustment feature works on timeline views with multiple resources.

{% tab template="schedule/working-days", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule height='550px' width='100%' :selectedDate='selectedDate' :eventSettings='eventSettings' :rowAutoHeight='rowAutoHeight' :group='group'>
                    <e-views>
                        <e-view option='TimelineDay'></e-view>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineWorkWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                        <e-view option='Agenda'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='RoomId' title='Room Type' name='MeetingRoom' allowMultiple=true :dataSource='meetingRoomDataSource' textField='text' idField='id' colorField='color'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { roomData } from './datasource.js';
    import { SchedulePlugin, TimelineViews, TimelineMonth, Agenda
    } from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                selectedDate: new Date(2018, 7, 1),
                currentView: 'TimelineWeek',
                rowAutoHeight: true,
                eventSettings: {
                    dataSource: roomData,
                    fields: {
                        id: 'Id',
                        subject: { name: 'Subject', title: 'Summary' },
                        location: { name: 'Location', title: 'Location' },
                        description: { name: 'Description', title: 'Comments' },
                        startTime: { name: 'StartTime', title: 'From' },
                        endTime: { name: 'EndTime', title: 'To' }
                    }
                },
                group: {
                    enableCompactView: false,
                    resources: ['MeetingRoom']
                },
                meetingRoomDataSource: [
                    { text: 'Room A', id: 1, color: '#98AFC7' },
                    { text: 'Room B', id: 2, color: '#99c68e' },
                    { text: 'Room C', id: 3, color: '#C2B280' },
                    { text: 'Room D', id: 4, color: '#3090C7' },
                    { text: 'Room E', id: 5, color: '#95b9' },
                    { text: 'Room F', id: 6, color: '#95b9c7' },
                    { text: 'Room G', id: 7, color: '#deb887' },
                    { text: 'Room H', id: 8, color: '#3090C7' },
                    { text: 'Room I', id: 9, color: '#98AFC7' },
                    { text: 'Room J', id: 10, color: '#778899' }
                ]
            }
        },
        provide: {
            schedule: [TimelineViews, TimelineMonth, Agenda]
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

## Appointments occupying entire cell

By default, with the feature `rowAutoHeight`, there will be a space in the bottom of the cell when appointment is rendered. To avoid this space, we can set true to the property `ignoreWhitespace` with in `eventSettings` whereas its default property value is false. In the following code example, the whitespace below the appointments has been ignored.

{% tab template="schedule/ignore-whitespace", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :currentView='currentView' :group='group' :rowAutoHeight='rowAutoHeight'>
                    <e-views>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field= 'RoomId' title= 'Room' name= 'Rooms' :dataSource='roomDataSource' textField='RoomText' idField='Id' colorField='RoomColor'>
                        </e-resource>
                        <e-resource field='OwnerId' title='Owner' name='Owners' :allowMultiple='allowMultiple' :dataSource='ownerDataSource'
                        textField='OwnerText' idField='Id' groupIDField= 'OwnerGroupId' colorField='OwnerColor'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { resourceData } from './datasource.js';
    import { SchedulePlugin, TimelineViews, TimelineMonth } from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                width: '100%',
                height: '550px',
                currentView: 'TimelineWeek',
                rowAutoHeight: true,
                selectedDate: new Date(2021, 7, 4),
                group: {
                    resources: ['Rooms', 'Owners']
                },
                roomDataSource: [
                    { RoomText: 'ROOM 1', Id: 1, RoomColor: '#cb6bb2' },
                    { RoomText: 'ROOM 2', Id: 2, RoomColor: '#56ca85' }
                ],
                allowMultiple: true,
                ownerDataSource: [
                    { OwnerText: 'Nancy', Id: 1, OwnerGroupId: 1, OwnerColor: '#ffaa00' },
                    { OwnerText: 'Steven', Id: 2, OwnerGroupId: 2, OwnerColor: '#f8a398' },
                    { OwnerText: 'Michael', Id: 3, OwnerGroupId: 1, OwnerColor: '#7499e1' }
                ],
                eventSettings: { dataSource: resourceData, ignoreWhitespace: true },
            }
        },
        provide: {
            schedule: [TimelineViews, TimelineMonth]
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

**Note**: The property `ignoreWhitespace` will be applicable only when `rowAutoHeight` feature is enabled in the Scheduler

> You can refer to our [Vue Scheduler](https://www.syncfusion.com/vue-ui-components/vue-scheduler) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Scheduler example](https://ej2.syncfusion.com/vue/demos/#/material/schedule/overview.html) to knows how to present and manipulate data.