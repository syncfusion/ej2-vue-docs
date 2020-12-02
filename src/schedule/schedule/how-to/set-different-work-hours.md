# Set Different Working Hours on Different Days

By default, the work hours of the Scheduler is highlighted based on the start and end values provided within the `workHours` property which remains same for all days. To highlight different work hours range for different days,`setWorkHours` method. You can pass date object/ multiple date objects collection as first argument and start and end time need to be added as work hours should be passed as second and third arguments respectively. In the following code example, on button click 11:00 AM to 08:00 PM of 15th and 17th February has been added in work hours.

{% tab template="schedule/open-editor", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <tr>
                    <td>
                        <div>
                            <ejs-button id='btn1' v-on:click.native='onChangeWorkHours'>Change the Work Hours</ejs-button>
                        </div>
                    </td>
                </tr>
                <ejs-schedule ref='scheduleObj' width='100%' height='500px' :eventSettings='eventSettings' :selectedDate='selectedDate' :workHours='workHours'>
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
    import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
    Vue.use(ButtonPlugin);
    import { SchedulePlugin, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-vue-schedule';
    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                eventSettings: { dataSource: extend([], scheduleData, null, true)  },
                workHours: {
                    highlight: true,
                    start: '09:00',
                    end: '11:00'
                },
                selectedDate: new Date(2018, 1, 15)
            }
        },
        provide: {
            schedule: [Day, Week, WorkWeek, Month]
        },
        methods: {
            onChangeWorkHours: function () {
                let dates = [new Date(2018, 1, 15), new Date(2018, 1, 17)];
                this.$refs.scheduleObj.setWorkHours(dates, '11:00','20:00');
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