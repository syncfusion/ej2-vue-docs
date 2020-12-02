# Set Default Value for Event Fields

Event window default fields name like Title, Location, etc.. can be customized and default value can be set to Subject field using `default` property which will be added if an appointment is created with empty subject.

{% tab template="schedule/how-to", iframeHeight="588px" %}

```html
<template>
    <div>
        <div class='col-md-9 control-section'>
            <div class='content-wrapper'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate'>
                    <e-views>
                        <e-view option='Day'></e-view>
                        <e-view option='Week'></e-view>
                        <e-view option='WorkWeek'></e-view>
                        <e-view option='Month'></e-view>
                        <e-view option='Agenda'></e-view>
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
    import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-vue-schedule';
    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                eventSettings: {
                    dataSource: extend([], scheduleData, null, true),
                    fields: {
                        subject: { title: 'Event Name', name: 'Subject', default: 'Add Name' },
                        location: { title: 'Event Location', name: 'Location', default: 'USA'},
                        description: { title: 'Summary', name: 'Description' },
                        startTime: { title: 'From', name: 'StartTime' },
                        endTime: { title: 'To', name: 'EndTime' }
                    }
                },
                selectedDate: new Date(2018, 1, 15)
            }
        },
        provide: {
            schedule: [Day, Week, WorkWeek, Month, Agenda]
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