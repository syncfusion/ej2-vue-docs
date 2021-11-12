---
title: "Virtual Scrolling in Timeline Views"
component: "Scheduler"
description: "This section demonstrates how to load a large number of resources and events dynamically on Scheduler using Virtual Scrolling support."
---

# Virtual scrolling

To achieve better performance in the Scheduler when loading a large number of resources and events, we have added virtual scrolling support in the timeline views to load a large set of resources and events instantly as you scroll. You can dynamically load large number of resources and events in timeline view of the Scheduler by setting `true` to the `allowVirtualScrolling` property within the timeline view-specific settings. The virtual loading of events is possible in Agenda view, by setting `allowVirtualScrolling` property to `true` within the agenda view specific settings.

{% tab template="schedule/virtual-scrolling", iframeHeight="588px"  %}

```html
<template>
    <div id='app'>
        <div id='container'>
            <ejs-schedule id='Schedule' ref='ScheduleObj' width='100%' height='550px' :selectedDate='selectedDate' :eventSettings='eventSettings' :group='group'>
                <e-views>
                    <e-view option='TimelineMonth' :eventTemplate='timelineEventTemplate' :allowVirtualScrolling='virtualScroll'></e-view>
                </e-views>
                <e-resources>
                    <e-resource field='OwnerId' title='Owner' name='Owners' :allowMultiple='allowMultiple' :dataSource='ownerData' textField='Text' idField='Id' colorField='Color'>
                    </e-resource>
                </e-resources>
            </ejs-schedule>
        </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { generateResourceData, generateStaticEvents } from './datasource.js';
    import { SchedulePlugin, TimelineViews, TimelineMonth, Resize, DragAndDrop } from '@syncfusion/ej2-vue-schedule';
    Vue.use(SchedulePlugin);

    var timelineEventTemplateVue = Vue.component('timelineTemplate', {
        template: `<div class='template-wrap' style='{background: data.PrimaryColor}'>
            <div class="subject" style='{background: data.SecondaryColor};'>{{data.Subject}}</div></div>`,
        data() {
            return {
                data: {}
            };
        }
    });

    export default {
        data: function () {
            return {
                selectedDate: new Date(2018, 4, 1),
                timelineEventTemplate: function (e) {
                    return {
                        template: timelineEventTemplateVue
                    };
                },
                allowMultiple: true,
                virtualScroll: true,
                group: {
                    byGroupID: false,
                    resources: ['Owners']
                },
                ownerData: generateResourceData(1, 300, 'Resource'),
                eventSettings: { dataSource: generateStaticEvents(new Date(2018, 4, 1), 300, 12) }
            }
        },
        provide: {
            schedule: [TimelineViews, TimelineMonth, Resize, DragAndDrop]
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

  .e-schedule .template-wrap .subject {
        padding: 10px 25px;
    }

    .e-schedule .template-wrap {
        width: 100%;
    }

    .e-schedule .e-timeline-month-view .e-resource-left-td {
        width: 150px;
    }
</style>

```

{% endtab %}

> For now, the virtual loading of resources and events is available only for timeline views. In the future, we plan to port the same virtual loading on all other applicable Scheduler views.

## See Also

* [Virtual scrolling in Agenda view](./views/#agenda-view)

> You can refer to our [Vue Scheduler](https://www.syncfusion.com/vue-ui-components/vue-scheduler) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Scheduler example](https://ej2.syncfusion.com/vue/demos/#/material/schedule/overview.html) to knows how to present and manipulate data.