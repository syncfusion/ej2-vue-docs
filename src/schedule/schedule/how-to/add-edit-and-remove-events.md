# Perform CRUD Actions Dynamically

CRUD actions can be manually performed on appointments using `addEvent`, `saveEvent` and `deleteEvent` methods as shown below.

## Normal event

{% tab template="schedule/app-crud", iframeHeight="588px"  %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <tr>
                    <td>
                        <div>
                            <ejs-button v-on:click.native='onAdd'>Add</ejs-button>
                        </div>
                    </td>
                    <td>
                        <div>
                            <ejs-button v-on:click.native='onSave'>Edit</ejs-button>
                        </div>
                    </td>
                    <td>
                        <div>
                            <ejs-button v-on:click.native='onDelete'>Delete</ejs-button>
                        </div>
                    </td>
                </tr><br>
                <ejs-schedule id='Schedule' width='100%' height='485px' :eventSettings='eventSettings' :selectedDate='selectedDate'>
                    <e-views>
                        <e-view option='Day'></e-view>
                        <e-view option='Week'></e-view>
                        <e-view option='WorkWeek'></e-view>
                        <e-view option='Month'></e-view>
                    </e-views>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { extend } from '@syncfusion/ej2-base';
    import { SchedulePlugin, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-vue-schedule';
    import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
    Vue.use(ButtonPlugin);
    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                eventSettings: {
                    dataSource:  [{
                            Id: 3,
                            Subject: 'Testing',
                            StartTime: new Date(2018, 1, 11, 9, 0),
                            EndTime: new Date(2018, 1, 11, 10, 0),
                            IsAllDay: false
                        },{
                            Id: 4,
                            Subject: 'Vacation',
                            StartTime: new Date(2018, 1, 13, 9, 0),
                            EndTime: new Date(2018, 1, 13, 10, 0),
                            IsAllDay: false
                    }]
                },
                selectedDate: new Date(2018, 1, 15)
            }
        },
        provide: {
            schedule: [Day, Week, WorkWeek, Month]
        },
        methods: {
            onSave: function () {
                let scheduleObj = document.getElementById('Schedule').ej2_instances[0];
                let eventData = {
                    Id: 3,
                    Subject: 'Testing-edited',
                    StartTime: new Date(2018, 1, 11, 10, 0),
                    EndTime: new Date(2018, 1, 11, 11, 0),
                    IsAllDay: false
                };
                scheduleObj.saveEvent(eventData);
            },
            onAdd: function () {
                let scheduleObj = document.getElementById('Schedule').ej2_instances[0];
                let Data = [{
                    Id: 1,
                    Subject: 'Conference',
                    StartTime: new Date(2018, 1, 12, 9, 0),
                    EndTime: new Date(2018, 1, 12, 10, 0),
                    IsAllDay: false
                },{
                    Id: 2,
                    Subject: 'Meeting',
                    StartTime: new Date(2018, 1, 15, 10, 0),
                    EndTime: new Date(2018, 1, 15, 11, 30),
                    IsAllDay: false
                }];
                scheduleObj.addEvent(Data);
            },
            onDelete: function () {
                let scheduleObj = document.getElementById('Schedule').ej2_instances[0];
                scheduleObj.deleteEvent(4);
            }
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
</style>

```

{% endtab %}

## Recurrence event

{% tab template="schedule/app-crud", iframeHeight="588px"  %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <tr>
                    <td>
                        <div>
                            <ejs-button v-on:click.native='onAdd'>Add</ejs-button>
                        </div>
                    </td>
                    <td>
                        <div>
                            <ejs-button v-on:click.native='onSave'>Edit</ejs-button>
                        </div>
                    </td>
                    <td>
                        <div>
                            <ejs-button v-on:click.native='onDelete'>Delete</ejs-button>
                        </div>
                    </td>
                </tr><br>
                <ejs-schedule id='Schedule' width='100%' height='485px' :eventSettings='eventSettings' :selectedDate='selectedDate'>
                    <e-views>
                        <e-view option='Day'></e-view>
                        <e-view option='Week'></e-view>
                        <e-view option='WorkWeek'></e-view>
                        <e-view option='Month'></e-view>
                    </e-views>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { extend } from '@syncfusion/ej2-base';
    import { SchedulePlugin, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-vue-schedule';
    import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
    Vue.use(ButtonPlugin);
    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                eventSettings: {
                    dataSource: [{
                        Id: 3,
                        Subject: 'Testing',
                        StartTime: new Date(2018, 1, 11, 9, 0),
                        EndTime: new Date(2018, 1, 11, 10, 0),
                        IsAllDay: false,
                        RecurrenceRule: 'FREQ=DAILY;INTERVAL=1;COUNT=3',
                    },{
                        Id: 4,
                        Subject: 'Vacation',
                        StartTime: new Date(2018, 1, 12, 11, 0),
                        EndTime: new Date(2018, 1, 12, 12, 0),
                        IsAllDay: false,
                        RecurrenceRule: 'FREQ=DAILY;INTERVAL=1;COUNT=2',
                    }]
                },
                selectedDate: new Date(2018, 1, 15),
            }
        },
        provide: {
            schedule: [Day, Week, WorkWeek, Month]
        },
        methods: {
            onSave: function () {
                let scheduleObj = document.getElementById('Schedule').ej2_instances[0];
                let eventData = {
                    Id: 3,
                    Subject: 'Testing-edited',
                    StartTime: new Date(2018, 1, 11, 10, 0),
                    EndTime: new Date(2018, 1, 11, 11, 0),
                    IsAllDay: false,
                    RecurrenceRule: 'FREQ=DAILY;INTERVAL=1;COUNT=3',
                };
                scheduleObj.saveEvent(eventData,'EditOccurrence');
            },
            onAdd: function () {
                let scheduleObj = document.getElementById('Schedule').ej2_instances[0];
                let Data = [{
                    Id: 1,
                    Subject: 'Conference',
                    StartTime: new Date(2018, 1, 15, 9, 0),
                    EndTime: new Date(2018, 1, 15, 10, 0),
                    IsAllDay: false,
                    RecurrenceRule: 'FREQ=DAILY;INTERVAL=1;COUNT=2',
                }];
                scheduleObj.addEvent(Data);
            },
            onDelete: function () {
                let scheduleObj = document.getElementById('Schedule').ej2_instances[0];
                let scheduleData = [{
                    Id: 4,
                    Subject: 'Vacation',
                    RecurrenceID: 4,
                    StartTime: new Date(2018, 1, 12, 11, 0),
                    EndTime: new Date(2018, 1, 12, 12, 0),
                    IsAllDay: false,
                    RecurrenceRule: 'FREQ=DAILY;INTERVAL=1;COUNT=2',
                }];
                scheduleObj.deleteEvent(scheduleData,'DeleteSeries');
            },
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
</style>

```

{% endtab %}