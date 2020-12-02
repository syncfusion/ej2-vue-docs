# Prevent the Date Navigation

We can prevent navigation while clicking on the date header by simply removing `e-navigate` class from header cells which can be achieved in the `renderCell` event as shown in the following code example.

{% tab template="schedule/how-to", iframeHeight="588px"  %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :renderCell='onRenderCell'>
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
    import { extend, removeClass } from '@syncfusion/ej2-base';
    import { scheduleData } from './datasource.js';
    import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-vue-schedule';
    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                eventSettings: { dataSource: extend([], scheduleData, null, true)  },
                selectedDate: new Date(2018, 1, 15)
            }
        },
        provide: {
            schedule: [Day, Week, WorkWeek, Month, Agenda]
        },
        methods: {
            onRenderCell: function (args) {
                if(args.elementType === 'dateHeader' || args.elementType === 'monthCells') {
                    removeClass(args.element.childNodes, 'e-navigate');
                }
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