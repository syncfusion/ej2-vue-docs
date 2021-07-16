---
title: "Context Menu | VueJS Scheduler"
component: "Scheduler"
description: "This section explains how to integrate the context menu manually to a Scheduler and use it with required options."
---

# Context menu

You can display context menu on work cells and appointments of Scheduler by making use of the `ContextMenu` control manually from the application end. In the following code example, context menu control is being added from sample end and set its target as `Scheduler`.

On Scheduler cells, you can display the menu items such as `New Event`, `New Recurring Event` and `Today` option. For appointments, you can display its related options such as `Edit Event` and `Delete Event`. The default event window can be opened for appointment creation and editing using the `openEditor` method of Scheduler.

The deletion of appointments can be done by using the `deleteEvent` public method. Also, the `selectedDate` property can be used to navigate between different dates.

> You can also display custom menu options on Scheduler cells and appointments. Context menu will open on tap-hold in responsive mode.

{% tab template="schedule/context-menu", iframeHeight="588px" %}

```html
<template>
    <div id='app'>
        <div id='container'>
             <div class='content-wrapper'>
                <ejs-schedule id='Schedule' ref='scheduleObj' height='550px' :selectedDate='selectedDate' :eventSettings='eventSettings'></ejs-schedule>
            </div>
            <div>
                <ejs-contextmenu id='contextmenu' ref='menuObj' cssClass='schedule-context-menu' target='.e-schedule' :items='menuItems' :beforeOpen='onContextMenuBeforeOpen' :select='onMenuItemSelect' ></ejs-contextmenu>
            </div>
        </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { scheduleData } from './datasource.js';
    import { extend, closest, isNullOrUndefined, Browser, remove, removeClass } from '@syncfusion/ej2-base';
    import { DataManager, Query } from '@syncfusion/ej2-data';
    import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-vue-schedule';
    import { ContextMenuPlugin } from '@syncfusion/ej2-vue-navigations';
    Vue.use(SchedulePlugin);
    Vue.use(ContextMenuPlugin);

    export default {
        data: function () {
            return {
                eventSettings: { dataSource: extend([], scheduleData, null, true) },
                selectedDate: new Date(2018, 1, 15),
                menuItems: [
                    {
                        text: 'New Event',
                        iconCss: 'e-icons new',
                        id: 'Add'
                    }, {
                        text: 'New Recurring Event',
                        iconCss: 'e-icons recurrence',
                        id: 'AddRecurrence'
                    }, {
                        text: 'Today',
                        iconCss: 'e-icons today',
                        id: 'Today'
                    }, {
                        text: 'Edit Event',
                        iconCss: 'e-icons edit',
                        id: 'Save'
                    }, {
                        text: 'Edit Event',
                        id: 'EditRecurrenceEvent',
                        iconCss: 'e-icons edit',
                        items: [{
                            text: 'Edit Occurrence',
                            id: 'EditOccurrence'
                        }, {
                            text: 'Edit Series',
                            id: 'EditSeries'
                        }]
                    }, {
                        text: 'Delete Event',
                        iconCss: 'e-icons delete',
                        id: 'Delete'
                    }, {
                        text: 'Delete Event',
                        id: 'DeleteRecurrenceEvent',
                        iconCss: 'e-icons delete',
                        items: [{
                            text: 'Delete Occurrence',
                            id: 'DeleteOccurrence'
                        }, {
                            text: 'Delete Series',
                            id: 'DeleteSeries'
                        }]
                    }
                ],
                selectedTarget: null
            }
        },
        provide: {
            schedule: [Day, Week, WorkWeek, Month, Agenda]
        },
        methods: {
            onContextMenuBeforeOpen: function(args) {
                let newEventElement = document.querySelector('.e-new-event');
                if (newEventElement) {
                    remove(newEventElement);
                    removeClass([document.querySelector('.e-selected-cell')], 'e-selected-cell');
                }
                let targetElement = args.event.target;
                if (closest(targetElement, '.e-contextmenu')) {
                    return;
                }
                let menuObj = this.$refs.menuObj;
                let scheduleObj = this.$refs.scheduleObj;
                this.selectedTarget = closest(targetElement, '.e-appointment,.e-work-cells,' +
                        '.e-vertical-view .e-date-header-wrap .e-all-day-cells,.e-vertical-view .e-date-header-wrap .e-header-cells');
                if (isNullOrUndefined(this.selectedTarget)) {
                    args.cancel = true;
                    return;
                }
                if (this.selectedTarget.classList.contains('e-appointment')) {
                    let eventObj= scheduleObj.getEventDetails(this.selectedTarget);
                    if (eventObj.RecurrenceRule) {
                        menuObj.showItems(['EditRecurrenceEvent', 'DeleteRecurrenceEvent'], true);
                        menuObj.hideItems(['Add', 'AddRecurrence', 'Today', 'Save', 'Delete'], true);
                    } else {
                        menuObj.showItems(['Save', 'Delete'], true);
                        menuObj.hideItems(['Add', 'AddRecurrence', 'Today', 'EditRecurrenceEvent', 'DeleteRecurrenceEvent'], true);
                    }
                    return;
                }
                menuObj.hideItems(['Save', 'Delete', 'EditRecurrenceEvent', 'DeleteRecurrenceEvent'], true);
                menuObj.showItems(['Add', 'AddRecurrence', 'Today'], true);
            },
            onMenuItemSelect: function(args) {
                let scheduleObj = this.$refs.scheduleObj.ej2Instances;
                let selectedMenuItem = args.item.id;
                let eventObj;
                if (this.selectedTarget.classList.contains('e-appointment')) {
                    eventObj = scheduleObj.getEventDetails(this.selectedTarget);
                }
                switch (selectedMenuItem) {
                    case 'Today':
                        scheduleObj.selectedDate = new Date();
                        break;
                    case 'Add':
                    case 'AddRecurrence':
                        let selectedCells = scheduleObj.getSelectedElements();
                        let activeCellsData = scheduleObj.getCellDetails(selectedCells.length > 0 ? selectedCells : this.selectedTarget);
                        if (selectedMenuItem === 'Add') {
                            scheduleObj.openEditor(activeCellsData, 'Add');
                        } else {
                            scheduleObj.openEditor(activeCellsData, 'Add', null, 1);
                        }
                        break;
                    case 'Save':
                    case 'EditOccurrence':
                    case 'EditSeries':
                        if (selectedMenuItem === 'EditSeries') {
                            eventObj = new DataManager(scheduleObj.eventsData).
                                executeLocal(new Query().where(scheduleObj.eventFields.id, 'equal', eventObj[scheduleObj.eventFields.recurrenceID]))[0];
                        }
                        scheduleObj.openEditor(eventObj, selectedMenuItem);
                        break;
                    case 'Delete':
                        scheduleObj.deleteEvent(eventObj);
                        break;
                    case 'DeleteOccurrence':
                    case 'DeleteSeries':
                        scheduleObj.deleteEvent(eventObj, selectedMenuItem);
                        break;
                }
            }
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

  .schedule-context-menu .e-menu-item .new::before {
        content: '\e7f9';
    }

    .schedule-context-menu .e-menu-item .edit::before {
        content: '\ea9a';
    }

    .schedule-context-menu .e-menu-item .recurrence::before {
        content: '\e308';
        font-weight: bold;
    }

    .schedule-context-menu .e-menu-item .today::before {
        content: '\e322';
    }

    .schedule-context-menu .e-menu-item .delete::before {
        content: '\e94a';
    }

    .e-bigger .schedule-context-menu ul .e-menu-item .e-menu-icon {
        font-size: 14px;
    }

    .schedule-context-menu ul .e-menu-item .e-menu-icon {
        font-size: 12px;
    }

    .schedule-context-menu .e-menu-parent.e-ul .e-menu-item {
        font-family: "Roboto", "Segoe UI", "GeezaPro", "DejaVu Serif", "sans-serif", "-apple-system", "BlinkMacSystemFont";
    }
</style>

```

{% endtab %}

> You can refer to our [Vue Scheduler](https://www.syncfusion.com/vue-ui-components/vue-scheduler) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Scheduler example](https://ej2.syncfusion.com/vue/demos/#/material/schedule/overview.html) to knows how to present and manipulate data.
