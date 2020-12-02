# Open Editor Window Manually

Scheduler allows the user to manually open the event editor on specific time or on certain events using `openEditor` method. To open the editor on specific range of time, user need to pass the cell details as first argument and **Add** as second argument whereas to open it on event pass that event detail and **Save** as arguments. In the following code example, on clicking the respective button will open the respective editor window manually.

{% tab template="schedule/open-editor", iframeHeight="616px"  %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <tr>
                    <td>
                        <div>
                            <ejs-button  v-on:click.native='onSubmit'>Click to open Editor</ejs-button>
                        </div>
                    </td>
                    <td>
                        <div>
                            <ejs-button v-on:click.native='onEventSubmit'>Click to open Event Editor</ejs-button>
                        </div>
                    </td>
                </tr>
                <br><br>
                <ejs-schedule id='Schedule' width='100%' height='500px' :eventSettings='eventSettings' :selectedDate='selectedDate'>
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
    import { scheduleData } from './datasource.js';
    import { SchedulePlugin, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-vue-schedule';
    import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
    Vue.use(ButtonPlugin);
    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                eventSettings: { dataSource: extend([], scheduleData, null, true)  },
                selectedDate: new Date(2018, 1, 15)
            }
        },
        provide: {
            schedule: [Day, Week, WorkWeek, Month]
        },
        methods: {
            onEventSubmit: function () {
                let scheduleObj = document.getElementById('Schedule').ej2_instances[0];
                let eventData ={
                    Id: 4,
                    Subject: 'Meteor Showers in 2018',
                    StartTime: new Date(2018, 1, 14, 13, 0),
                    EndTime: new Date(2018, 1, 14, 14, 30)
                };
                scheduleObj.openEditor(eventData,'Save');
            },
            onSubmit: function () {
                let scheduleObj = document.getElementById('Schedule').ej2_instances[0];
                let cellData ={
                      startTime: new Date(2018, 1, 15, 10, 0),
                      endTime: new Date(2018, 1, 15, 11, 0),
                };
                scheduleObj.openEditor(cellData,'Add');
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