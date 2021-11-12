---
title: "Scheduler Header customization"
component: "Scheduler"
description: "This section explains how to customize the header bar of Scheduler and to add custom items into it."
---

# Header customization

The header part of Scheduler can be customized easily with the built-in options available.

## Show or Hide header bar

By default, the header bar holds the date and view navigation options, through which the user can switch between the dates and various views. This header bar can be hidden from the UI by setting `false` to the `showHeaderBar` property. It's default value is `true`.

{% tab template="schedule/header-bar", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :selectedDate='selectedData' :eventSettings='eventSettings' :showHeaderBar='showHeaderBar'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);
export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      showHeaderBar: false,
      eventSettings: { dataSource: scheduleData  },
      selectedData: new Date(2018, 1, 15),
      views: ['Day', 'Week', 'WorkWeek'],
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek]
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

## Customizing header bar

Apart from the default date navigation and view options available on the header bar, you can add custom items into the Scheduler header bar by making use of the `actionBegin` event. Here, an employee image is added to the header bar, clicking on which will open the popup showing that person's short profile information.

{% tab template="schedule/header-bar", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule id='Schedule' :height='height' :selectedDate='selectedData' :eventSettings='eventSettings' :views='views' :actionBegin='onActionBegin' :actionComplete='onActionComplete'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { createElement, compile } from '@syncfusion/ej2-base';
import { Popup } from '@syncfusion/ej2-popups';
import { ItemModel } from '@syncfusion/ej2-navigations';
import { SchedulePlugin, Month } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);

var headerTemplateVue = Vue.component('header-template', {
    template: `<div class="profile-container"><div class="profile-image"></div><div class="content-wrap">
        '<div class="name">Nancy</div><div class="destination">Product Manager</div><div class="status"><div class="status-icon"></div>Online</div></div></div>`,
    data() {
        return {
            data: {}
        };
    }
});

export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      eventSettings: { dataSource: scheduleData  },
      selectedData: new Date(2018, 1, 15),
      views: ['Month'],
      currentView: 'Month',
      headerTemplate: function () {
        return { template: headerTemplateVue }
      },
    }
  },
  methods: {
      onActionBegin: function(args) {
        if (args.requestType === 'toolbarItemRendering') {
            let userIconItem = {
                align: 'Right', prefixIcon: 'user-icon', text: 'Nancy', cssClass: 'e-schedule-user-icon'
            };
            args.items.push(userIconItem);
        }
      },
      onActionComplete: function(args) {
        let scheduleElement = document.getElementById('Schedule');
        if (args.requestType === 'toolBarItemRendered') {
            let userIconEle = scheduleElement.querySelector('.e-schedule-user-icon');
            userIconEle.onclick = () => {
                this.profilePopup.relateTo = userIconEle;
                this.profilePopup.dataBind();
                if (this.profilePopup.element.classList.contains('e-popup-close')) {
                    this.profilePopup.show();
                } else {
                    this.profilePopup.hide();
                }
            };
        }
        let userContentEle = createElement('div', {
            className: 'e-profile-wrapper'
        });
        scheduleElement.parentElement.appendChild(userContentEle);
        let userIconEle = scheduleElement.querySelector('.e-schedule-user-icon');
        let getDOMString = compile(this.headerTemplate);
        let output = getDOMString({});
        this.profilePopup = new Popup(userContentEle, {
            content: output[0],
            relateTo: userIconEle,
            position: { X: 'left', Y: 'bottom' },
            collision: { X: 'flip', Y: 'flip' },
            targetType: 'relative',
            viewPortElement: scheduleElement,
            width: 210,
            height: 80
        });
        this.profilePopup.hide();
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

.e-schedule .e-schedule-toolbar .user-icon,
.e-profile-wrapper .profile-image {
  background-image: url('https://ej2.syncfusion.com/demos/src/schedule/images/nancy.png');
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
  border-radius: 50%;
}

/* csslint ignore:start */
.e-schedule .e-schedule-toolbar .user-icon {
  height: 24px;
  min-width: 24px !important;
  width: 24px !important;
}
/* csslint ignore:end */

.e-schedule .e-schedule-toolbar .e-toolbar-items .e-schedule-user-icon .e-tbar-btn:hover {
  background-color: inherit;
}

.e-schedule .e-schedule-toolbar .e-toolbar-items .e-schedule-user-icon .e-tbar-btn-text {
  display: none;
}

/* csslint ignore:start */
.e-schedule .e-schedule-toolbar .e-toolbar-pop .e-schedule-user-icon .e-tbar-btn-text {
  padding-left: 8px !important;
}
/* csslint ignore:end */

.e-profile-wrapper {
  width: 210px;
  height: 80px;
  background-color: #fafafa;
  box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.2);
  overflow: hidden;
}

.e-profile-wrapper .profile-container {
  display: flex;
  padding: 10px;
}

.e-profile-wrapper .profile-image {
  box-shadow: inset 0 0 1px #e0e0e0, inset 0 0 14px rgba(0, 0, 0, 0.2);
  width: 60px;
  height: 60px;
}

.e-profile-wrapper .content-wrap {
  padding-left: 10px;
}

.e-profile-wrapper .name {
  font-size: 14px;
  line-height: 20px;
  font-weight: 500;
  margin-top: 2px;
}

.e-profile-wrapper .destination {
  font-size: 12px;
}

.e-profile-wrapper .status-icon {
  height: 6px;
  width: 6px;
  background: green;
  border-radius: 100%;
  float: left;
  margin-right: 4px;
  margin-top: 4px;
 }

 .e-profile-wrapper .status {
  font-size: 11px;
 }
</style>
```

{% endtab %}

## How to display the view options within the header bar popup

By default, the header bar holds the view navigation options, through which the user can switch between various views. You can move this view options to the header bar popup by setting `true` to the `enableAdaptiveUI` property.

{% tab template="schedule/header-bar", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :selectedDate='selectedData' :eventSettings='eventSettings' :enableAdaptiveUI='enableAdaptiveUI'></ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);
export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      enableAdaptiveUI: true,
      eventSettings: { dataSource: scheduleData  },
      selectedData: new Date(2018, 1, 15),
      views: ['Day', 'Week', 'WorkWeek', 'Month', 'Agenda,'],
    }
  },
  provide: {
    schedule: [Day, Week, WorkWeek, Month, Agenda]
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

> Refer [here](./resources/#adaptive-ui-in-desktop) to know more about adaptive UI in resources scheduler.

## Date header customization

The Scheduler UI that displays the date text on all views are considered as the date header cells. You can customize the date header cells of Scheduler either using `dateHeaderTemplate` or `renderCell` event.

### Using date header template

The `dateHeaderTemplate` option is used to customize the date header cells of day, week and work-week views.

{% tab template="schedule/date-header", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule height='550px' width='100%' :selectedDate='selectedDate' :eventSettings='eventSettings' :dateHeaderTemplate='dateHeaderTemplate' :cssClass='cssClass'>
            <e-views>
                <e-view option='Day'></e-view>
                <e-view option='Week'></e-view>
                <e-view option='Agenda'></e-view>
                <e-view option='TimelineWorkWeek'></e-view>
                <e-view option='TimelineMonth'></e-view>
            </e-views>
        </ejs-schedule>
    </div>
  </div>
</template>
<script>
    import Vue from 'vue';
    import { Internationalization } from '@syncfusion/ej2-base';
    import { scheduleData } from './datasource.js';
    import { SchedulePlugin, Day, Week, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-vue-schedule';
    Vue.use(SchedulePlugin);

    var instance = new Internationalization();
    var dateHeaderTemplateVue = Vue.component('demo', {
        template: '<div class="date-text" v-html="getDateHeaderText(data.date)"></div>'+
        '<div v-html="getWeather(data.date)"></div>',
        data() {
            return {
                data: {}
            };
        },
        methods: {
            getDateHeaderText: function (Date) {
                return instance.formatDate(Date, { skeleton: 'Ed' });
            },
            getWeather: function (Date) {
                switch (Date.getDay()) {
                    case 0:
                        return '<div class="weather-text">25°C</div>';
                    case 1:
                        return '<div class="weather-text">18°C</div>';
                    case 2:
                        return '<div class="weather-text">10°C</div>';
                    case 3:
                        return '<div class="weather-text">16°C</div>';
                    case 4:
                        return '<div class="weather-text">8°C</div>';
                    case 5:
                        return '<div class="weather-text">27°C</div>';
                    case 6:
                        return '<div class="weather-text">17°C</div>';
                    default:
                        return null;
                }
            }
        }
    });
    export default {
        data () {
            return {
                eventSettings: { dataSource: scheduleData },
                cssClass: 'schedule-date-header-template',
                selectedDate: new Date(2018, 1, 15),
                dateHeaderTemplate: function (e) {
                    return { template: dateHeaderTemplateVue }
                }
            }
        },
        provide: {
            schedule: [Day, Week, Agenda, TimelineViews, TimelineMonth]
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

### Using renderCell event

In month view, the date header template is not applicable and therefore the same customization can be added beside the date text in month cells by making use of the `renderCell` event.

{% tab template="schedule/render-cell", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule id='Schedule' :height='height' :selectedDate='selectedData' :eventSettings='eventSettings' :views='views' :renderCell='onRenderCell'>
        </ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { createElement } from '@syncfusion/ej2-base';
import { SchedulePlugin, Month } from '@syncfusion/ej2-vue-schedule';
import { scheduleData } from './datasource.js';

Vue.use(SchedulePlugin);

export default {
  data (){
    return {
      height: '550px',
      width: '100%',
      eventSettings: { dataSource: scheduleData  },
      selectedData: new Date(2018, 1, 15),
      views: ['Month'],
      currentView: 'Month'
    }
  },
  methods: {
      onRenderCell: function(args) {
        if (args.elementType === 'monthCells') {
            let ele = document.createElement('div');
            ele.innerHTML = this.getWeather(args.date);
            (args.element).appendChild(ele.firstChild);
        }
      },
      getWeather: function(value) {
        switch (value.getDay()) {
            case 0:
                return '<div class="weather-text">25°C</div>';
            case 1:
                return '<div class="weather-text">18°C</div>';
            case 2:
                return '<div class="weather-text">10°C</div>';
            case 3:
                return '<div class="weather-text">16°C</div>';
            case 4:
                return '<div class="weather-text">8°C</div>';
            case 5:
                return '<div class="weather-text">27°C</div>';
            case 6:
                return '<div class="weather-text">17°C</div>';
            default:
                return null;
        }
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
  .weather-text {
    float: right;
    margin: -20px 12px 0 0;
    width: 20px;
    height: 20px;
  }
</style>
```

{% endtab %}

## Customizing header indent cells

It is possible to customize the header indent cells using the `headerIndentTemplate` option and change the look and appearance in both the vertical and timeline views. In vertical views, You can customize the header indent cells at the hierarchy level and you can customize the resource header left indent cell in timeline views using the template option.

**Example:** To customize the header left indent cell to display resources text, refer to the below code example.

{% tab template="schedule/header-indent", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
      <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :group='group'>
        <e-views>
          <e-view option='Day'></e-view>
          <e-view option='Week'></e-view>
          <e-view option='TimelineWeek'></e-view>
          <e-view option='TimelineMonth'></e-view>
        </e-views>
        <e-resources>
          <e-resource field='OwnerId' title='Owner' name='Owners' :allowMultiple='allowMultiple' :dataSource='ownerDataSource'
            textField='OwnerText' idField='Id' colorField='OwnerColor'>
          </e-resource>
        </e-resources>
      </ejs-schedule>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { SchedulePlugin, Week, Day, TimelineViews, TimelineMonth } from '@syncfusion/ej2-vue-schedule';
import { resourceData } from './datasource.js';

Vue.use(SchedulePlugin);

var headerIndentTemplate = Vue.component('headerTemplate', {
        template: `<div class='e-resource-text'>
          <div class="text">Resources</div>`,
        data() {
            return {
                data: {}
            };
        }
});

export default {
        data () {
            return {
                width: '100%',
                height: '550px',
                currentView: 'Week',
                selectedDate: new Date(2018, 3, 1),
                group: {
                    resources: ['Owners']
                },
                allowMultiple: true,
                headerIndentTemplate: function(e){
                    return {
                        template: headerIndentTemplate
                    };
                },
                ownerDataSource: [
                    { OwnerText: 'Nancy', Id: 1, OwnerColor: '#ffaa00' },
                    { OwnerText: 'Steven', Id: 2, OwnerColor: '#f8a398' },
                    { OwnerText: 'Michael', Id: 3, OwnerColor: '#7499e1' }
                ],
                eventSettings: { dataSource: resourceData },
            }
        },
        provide: {
            schedule: [Day, Week, TimelineViews, TimelineMonth]
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

.e-schedule .e-timeline-view .e-resource-left-td {
  vertical-align: bottom;
}

.e-schedule .e-timeline-view .e-resource-left-td .e-resource-text,
.e-schedule .e-timeline-month-view .e-resource-left-td .e-resource-text {
  font-weight: 500;
  padding: 0;
}

.e-schedule .e-timeline-view .e-resource-left-td .e-resource-text > div {
  border-right: 1px solid rgba(0, 0, 0, 0.12);
  border-top: 1px solid rgba(0, 0, 0, 0.12);
  flex: 0 0 33.3%;
  font-weight: 500;
  height: 36px;
  line-height: 34px;
  padding-left: 50px;
}

.e-schedule .e-timeline-month-view .e-resource-left-td .e-resource-text > div {
  border-right: 1px solid rgba(0, 0, 0, 0.12);
  flex: 0 0 33.3%;
  font-weight: 500;
  height: 36px;
  line-height: 34px;
  padding-left: 50px;
}

/* csslint ignore:start */
.e-schedule .e-vertical-view .e-left-indent-wrap table tbody td.e-resource-cells {
  border-bottom-color: rgba(0, 0, 0, 0.12);
}

.e-schedule .e-vertical-view .e-left-indent-wrap table tbody td.e-resource-cells .e-resource-text {
  font-weight: 500;
}

.e-schedule .e-vertical-view .e-left-indent-wrap table tbody td.e-header-cells .e-resource-text,
.e-schedule .e-vertical-view .e-left-indent-wrap table tbody td.e-all-day-cells .e-resource-text {
  display: none;
}
/* csslint ignore:end */
</style>

```

{% endtab %}

> You can refer to our [Vue Scheduler](https://www.syncfusion.com/vue-ui-components/vue-scheduler) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Scheduler example](https://ej2.syncfusion.com/vue/demos/#/material/schedule/overview.html) to knows how to present and manipulate data.