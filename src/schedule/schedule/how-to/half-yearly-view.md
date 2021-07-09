---
title: "Scheduler Year view customization"
component: "Scheduler"
description: "This section explains how to customize the Year view using different properties in scheduler"
---

# Half-yearly view

The year view of our scheduler displays all the 365 days and their related appointments of a particular year. You can customize the year view by using the following properties.

* [`firstMonthOfYear`](../../api/schedule#firstmonthofyear)
* [`monthsCount`](../../api/schedule#monthscount)
* [`monthHeaderTemplate`](../../api/schedule#monthheadertemplate)

In the following code example, you can see how to render only the last six months of a year in the scheduler. To start with the month of  June, `firstMonthYear` is set to 6 and `monthsCount` is set to 6 to render only 6 months.

{% tab template="schedule/year-customizations", iframeHeight="588px" %}

```html
<template>
  <div>
    <div id="app">
      <div id="container">
        <ejs-schedule
          id="Schedule"
          height="650px"
          :eventSettings="eventSettings"
          :currentView="currentView"
          :firstMonthOfYear="firstMonthOfYear"
          :monthsCount="monthsCount"
          :group="group"
          :monthHeaderTemplate="monthHeaderTemplate"
          :resourceHeaderTemplate="resourceHeaderTemplate"
        >
          <e-views>
            <e-view option="Year"></e-view>
            <e-view
              option="TimelineYear"
              displayName="Horizontal TimelineYear"
              isSelected="true"
            ></e-view>
            <e-view
              option="TimelineYear"
              displayName="Vertical TimelineYear"
              orientation="Vertical"
            ></e-view>
          </e-views>
          <e-resources>
            <e-resource
              field="OwnerId"
              title="Owner"
              name="Owners"
              :dataSource="ownerDataSource"
              textField="OwnerText"
              idField="Id"
              colorField="OwnerColor"
            ></e-resource>
          </e-resources>
        </ejs-schedule>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import { resourceData } from "./datasource.js";
import {
  SchedulePlugin,
  Year,
  TimelineYear,
  Resize,
  DragAndDrop
} from "@syncfusion/ej2-vue-schedule";

Vue.use(SchedulePlugin);

var monthHeaderTemplate = Vue.component("demo", {
  template: "<div>{{monthHeaderTemplate(data.date)}}</div>",
  data() {
    return {
      data: {},
      monthHeaderTemplate: function(date) {
        return (
          date.toLocaleString("en-us", { month: "long" }) +
          " " +
          date.getFullYear()
        );
      }
    };
  }
});
var resourceHeaderTemplateVue = Vue.component("headerTemplate", {
  template: `<div class='template-wrap'><div class="resource-details"><div class="resource-name">{{data.resourceData.OwnerText}}</div></div></div>`,
  data() {
    return {
      data: {}
    };
  }
});
export default {
  data() {
    return {
      width: "100%",
      height: "550px",
      currentView: "TimelineWeek",
      selectedDate: new Date(2021, 7, 4),
      firstMonthOfYear: 6,
      monthsCount: 6,
      group: {
        resources: ["Owners"]
      },
      monthHeaderTemplate: function(e) {
        return { template: monthHeaderTemplate };
      },
      allowMultiple: true,
      ownerDataSource: [
        { OwnerText: "Nancy", Id: 1, OwnerColor: "#ffaa00" },
        { OwnerText: "Steven", Id: 2, OwnerColor: "#f8a398" },
        { OwnerText: "Robert", Id: 3, OwnerColor: "#7499e1" },
        { OwnerText: "Smith", Id: 4, OwnerColor: "#5978ee" },
        { OwnerText: "Micheal", Id: 5, OwnerColor: "#df5286" }
      ],
      resourceHeaderTemplate: function(e) {
        return {
          template: resourceHeaderTemplateVue
        };
      },
      eventSettings: { dataSource: resourceData }
    };
  },
  provide: {
    schedule: [Year, TimelineYear, Resize, DragAndDrop]
  }
};
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

.e-schedule .e-vertical-view .e-resource-cells {
  height: 62px;
}

.e-schedule .template-wrap {
  display: flex;
  text-align: left;
}

.e-schedule .template-wrap .resource-details {
  padding-left: 10px;
}

.e-schedule .template-wrap .resource-details .resource-name {
  font-size: 16px;
  font-weight: 500;
  margin-top: 5px;
}

.e-schedule.e-device .template-wrap .resource-details .resource-name {
  font-size: inherit;
  font-weight: inherit;
}

.e-schedule.e-device .e-resource-tree-popup .e-fullrow {
  height: 50px;
}
</style>

```

{% endtab %}