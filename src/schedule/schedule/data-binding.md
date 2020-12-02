---
title: "Binding data to VueJS Scheduler"
component: "Scheduler"
description: "This section includes the data binding topics explaining how to bind various data sources to Scheduler using DataManager adaptors."
---

# Data binding

The Scheduler uses `DataManager`, which supports both RESTful data service binding and JavaScript object array binding. The [`dataSource`](../api/schedule/eventSettings#datasource) property of Scheduler can be assigned either with the instance of `DataManager` or JavaScript object array collection, as it supports the following two kind of data binding methods:

* Local data
* Remote data

## Binding local data

To bind local JSON data to the Scheduler, you can simply assign a JavaScript object array to the [`dataSource`](../api/schedule/eventSettings#datasource) option of the scheduler within the `eventSettings` property. The JSON object dataSource can also be provided as an instance of `DataManager` and assigned to the Scheduler `dataSource` property.

{% tab template="schedule/data-bind", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :selectedDate='selectedData' :eventSettings='eventSettings'></ejs-schedule>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-vue-schedule';

Vue.use(SchedulePlugin);

let scheduleData = [{
    Id: 1,
    Subject: 'Explosion of Betelgeuse Star',
    StartTime: new Date(2018, 1, 15, 9, 30),
    EndTime: new Date(2018, 1, 15, 11, 0)
}, {
    Id: 2,
    Subject: 'Thule Air Crash Report',
    StartTime: new Date(2018, 1, 12, 12, 0),
    EndTime: new Date(2018, 1, 12, 14, 0)
}, {
    Id: 3,
    Subject: 'Blue Moon Eclipse',
    StartTime: new Date(2018, 1, 13, 9, 30),
    EndTime: new Date(2018, 1, 13, 11, 0)
}, {
    Id: 4,
    Subject: 'Meteor Showers in 2018',
    StartTime: new Date(2018, 1, 14, 13, 0),
    EndTime: new Date(2018, 1, 14, 14, 30)
}];

export default {
  data (){
    return {
      height: '550px',
      eventSettings: {
          dataSource: scheduleData
      },
      selectedData: new Date(2018, 1, 15),
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

> By default, `DataManager` uses `JsonAdaptor` for binding local data.

You can also bind different field names to the default event fields as well as include additional custom fields to the event object collection which can be referred [here](./appointments/#event-fields).

## Binding remote data

Any kind of remote data services can be bound to the Scheduler. To do so, create an instance of `DataManager` and provide the service URL to the `url` option of `DataManager` and then assign it to the [`dataSource`](../api/schedule/eventSettings#datasource) property within `eventSettings`.

### Using ODataV4Adaptor

[ODataV4](https://www.odata.org/documentation/) is a standardized protocol for creating and consuming data. Refer to the following code example to retrieve the data from ODataV4 service using the DataManager. To connect with ODataV4 service end points, it is necessary to make use of `ODataV4Adaptor` within `DataManager`.

{% tab template="schedule/data-bind", iframeHeight="588px" %}

```html
<template>
    <div id='app'>
      <div id='container'>
        <ejs-schedule height='550px' :selectedDate='selectedDate' :eventSettings='eventSettings'
        :readOnly='readOnly'></ejs-schedule>
      </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DataManager, ODataV4Adaptor, Query } from '@syncfusion/ej2-data';
    import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda, View } from '@syncfusion/ej2-vue-schedule';
    Vue.use(SchedulePlugin);

    let dataManager = new DataManager({
        url: 'https://ej2services.syncfusion.com/production/web-services/api/Schedule',
        adaptor: new ODataV4Adaptor(),
        crossDomain: true
    });
    export default {
        data() {
            return {
                selectedDate: new Date(2020, 9, 20),
                readOnly: true,
                eventSettings: { dataSource: dataManager }
            };
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

### Using custom adaptor

It is possible to create your own custom adaptor by extending the built-in available adaptors. The following example demonstrates the custom adaptor usage and how to add a custom field `EventID` for the appointments by overriding the built-in response processing using the `processResponse` method of the `ODataV4Adaptor`.

{% tab template="schedule/data-bind", iframeHeight="588px" %}

```html
<template>
    <div id='app'>
      <div id='container'>
        <ejs-schedule height='550px' :selectedDate='selectedDate' :eventSettings='eventSettings' :readOnly='readOnly'></ejs-schedule>
      </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DataManager, ODataV4Adaptor, Query } from '@syncfusion/ej2-data';
    import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda, View } from '@syncfusion/ej2-vue-schedule';
    Vue.use(SchedulePlugin);

    class CustomAdaptor extends ODataV4Adaptor {
        processResponse() {
            let i = 0;
            // calling base class processResponse function
            let original = super.processResponse.apply(this, arguments);
            // adding employee id
            original.forEach((item) => item['EventID'] = ++i);
            return  original;
        }
    }
    let dataManager = new DataManager({
       url: 'https://ej2services.syncfusion.com/production/web-services/api/Schedule',
       adaptor: new CustomAdaptor(),
       crossDomain: true
    });
    export default {
        data() {
            return {
                selectedDate: new Date(2020, 9, 20),
                readOnly: true,
                eventSettings: { dataSource: dataManager }
            };
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

## Loading data via AJAX post

You can bind the event data through external ajax request and assign it to the `dataSource`property of Scheduler. In the following code example, we have retrieved the data from server with the help of ajax request and assigned the resultant data to the `dataSource` property of Scheduler within the `onSuccess` event of Ajax.

`[src/app/App.vue]`

```html
<template>
    <div id='app'>
      <div id='container'>
        <ejs-schedule height='550px' :selectedDate='selectedDate'
        :eventSettings='eventSettings'></ejs-schedule>
      </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { Ajax } from '@syncfusion/ej2-base';
    import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda, View } from '@syncfusion/ej2-vue-schedule';
    Vue.use(SchedulePlugin);

    let dataManager = [];
    let ajax = new Ajax('Home/GetData', 'GET', false);
    ajax.onSuccess = function (value) {
        dataManager = value;
    };
    ajax.send();
    export default {
        data() {
            return {
                selectedDate: new Date(2017, 5, 11),
                eventSettings: { dataSource: dataManager }
            };
        },
        provide: {
            schedule: [Day, Week, WorkWeek, Month, Agenda]
        }
    }
</script>
```

> Definition for the controller method `GetData` can be referred [here](#scheduler-crud-actions).

## Passing additional parameters to the server

To send an additional custom parameter to the server-side post, you need to make use of the `addParams` method of `Query`. Now, assign this `Query` object with additional parameters to the [`query`](../api/schedule/eventSettings/#query) property of Scheduler.

{% tab template="schedule/data-bind", iframeHeight="588px" %}

```html
<template>
    <div id='app'>
      <div id='container'>
        <ejs-schedule height='550px' :selectedDate='selectedDate' :eventSettings='eventSettings'
        :readOnly='readOnly'></ejs-schedule>
      </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DataManager, ODataV4Adaptor, Query } from '@syncfusion/ej2-data';
    import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda, View } from '@syncfusion/ej2-vue-schedule';
    Vue.use(SchedulePlugin);

    let dataManager = new DataManager({
        url: 'https://js.syncfusion.com/demos/ejservices/api/Schedule/LoadData',
        adaptor: new ODataV4Adaptor(),
        crossDomain: true
    });
    let dataQuery = new Query().from('Events').addParams('readOnly', 'true');
    export default {
        data() {
            return {
                selectedDate: new Date(2017, 5, 11),
                readOnly: true,
                eventSettings: { dataSource: dataManager, query: dataQuery }
            };
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

> The parameters added using the [`query`](../api/schedule/eventSettings/#query) property will be sent along with the data request sent to the server on every scheduler actions.

## Handling failure actions

During the time of Scheduler interacting with server, there are chances that some server-side exceptions may occur. You can acquire those error messages or exception details in client-side using the [`actionFailure`](../api/schedule#actionfailure) event of Scheduler.

The argument passed to the [`actionFailure`](../api/schedule#actionfailure) event contains the error details returned from the server.

{% tab template="schedule/data-bind", iframeHeight="588px" %}

```html
<template>
    <div id='app'>
      <div id='container'>
        <ejs-schedule ref='scheduleObj' height='530px' :selectedDate='selectedDate' :eventSettings='eventSettings' :readOnly='readOnly' :actionFailure='onActionFailure'></ejs-schedule>
      </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DataManager } from '@syncfusion/ej2-data';
    import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda, View } from '@syncfusion/ej2-vue-schedule';
    Vue.use(SchedulePlugin);

    let dataManager = new DataManager({
        url: 'http://some.com/invalidUrl'
    });
    export default {
        data() {
            return {
                selectedDate: new Date(2017, 5, 11),
                readOnly: true,
                eventSettings: { dataSource: dataManager }
            };
        },
        methods: {
            onActionFailure: function () {
                let span = document.createElement('span');
                let scheduleObj = this.$refs.scheduleObj.ej2Instances;
                scheduleObj.element.parentNode.insertBefore(span, scheduleObj.element);
                span.style.color = '#FF0000'
                span.innerHTML = 'Server exception: 404 Not found';
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

> The [`actionFailure`](../api/schedule#actionfailure) event will be triggered not only on server returning errors, but also when there is an exception while processing any of the Scheduler CRUD actions.

## Scheduler CRUD actions

The CRUD (Create, Read, Update and Delete) actions can be performed easily on Scheduler appointments using the various adaptors available within the `DataManager`. Most preferably, we will be using `UrlAdaptor` for performing CRUD actions on scheduler appointments.

`[src/app/App.vue]`

```html
<template>
    <div id='app'>
      <div id='container'>
        <ejs-schedule height='550px' :selectedDate='selectedDate'
        :eventSettings='eventSettings'></ejs-schedule>
      </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda, View } from '@syncfusion/ej2-vue-schedule';
    import { DataManager, UrlAdaptor } from '@syncfusion/ej2-data';

    Vue.use(SchedulePlugin);

    let dataManager = new DataManager({
       url: 'Home/GetData', // 'controller/actions'
       crudUrl: 'Home/UpdateData',
       adaptor: new UrlAdaptor
    });
    export default {
        data() {
            return {
                selectedDate: new Date(2017, 5, 11),
                eventSettings: { dataSource: dataManager }
            };
        },
        provide: {
            schedule: [Day, Week, WorkWeek, Month, Agenda]
        }
    }
</script>
```

The server-side controller code to handle the CRUD operations are as follows.

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.Mvc;
using ScheduleSample.Models;

namespace ScheduleSample.Controllers
{
    public class HomeController : Controller
    {
        ScheduleDataDataContext db = new ScheduleDataDataContext();
        public ActionResult Index()
        {
            return View();
        }
        public JsonResult LoadData()  // Here we get the Start and End Date and based on that can filter the data and return to Scheduler
        {
            var data = db.ScheduleEventDatas.ToList();
            return Json(data, JsonRequestBehavior.AllowGet);
        }

        [HttpPost]
        public JsonResult UpdateData(EditParams param)
        {
            if (param.action == "insert" || (param.action == "batch" && param.added != null)) // this block of code will execute while inserting the appointments
            {
                var value = (param.action == "insert") ? param.value : param.added[0];
                int intMax = db.ScheduleEventDatas.ToList().Count > 0 ? db.ScheduleEventDatas.ToList().Max(p => p.Id) : 1;
                DateTime startTime = Convert.ToDateTime(value.StartTime);
                DateTime endTime = Convert.ToDateTime(value.EndTime);
                ScheduleEventData appointment = new ScheduleEventData()
                {
                    Id = intMax + 1,
                    StartTime = startTime.ToLocalTime(),
                    EndTime = endTime.ToLocalTime(),
                    Subject = value.Subject,
                    IsAllDay = value.IsAllDay,
                    StartTimezone = value.StartTimezone,
                    EndTimezone = value.EndTimezone,
                    RecurrenceRule = value.RecurrenceRule,
                    RecurrenceID = value.RecurrenceID,
                    RecurrenceException = value.RecurrenceException
                };
                db.ScheduleEventDatas.InsertOnSubmit(appointment);
                db.SubmitChanges();
            }
            if (param.action == "update" || (param.action == "batch" && param.changed != null)) // this block of code will execute while updating the appointment
            {
                var value = (param.action == "update") ? param.value : param.changed[0];
                var filterData = db.ScheduleEventDatas.Where(c => c.Id == Convert.ToInt32(value.Id));
                if (filterData.Count() > 0)
                {
                    DateTime startTime = Convert.ToDateTime(value.StartTime);
                    DateTime endTime = Convert.ToDateTime(value.EndTime);
                    ScheduleEventData appointment = db.ScheduleEventDatas.Single(A => A.Id == Convert.ToInt32(value.Id));
                    appointment.StartTime = startTime.ToLocalTime();
                    appointment.EndTime = endTime.ToLocalTime();
                    appointment.StartTimezone = value.StartTimezone;
                    appointment.EndTimezone = value.EndTimezone;
                    appointment.Subject = value.Subject;
                    appointment.IsAllDay = value.IsAllDay;
                    appointment.RecurrenceRule = value.RecurrenceRule;
                    appointment.RecurrenceID = value.RecurrenceID;
                    appointment.RecurrenceException = value.RecurrenceException;
                }
                db.SubmitChanges();
            }
            if (param.action == "remove" || (param.action == "batch" && param.deleted != null)) // this block of code will execute while removing the appointment
            {
                if (param.action == "remove")
                {
                    int key = Convert.ToInt32(param.key);
                    ScheduleEventData appointment = db.ScheduleEventDatas.Where(c => c.Id == key).FirstOrDefault();
                    if (appointment != null) db.ScheduleEventDatas.DeleteOnSubmit(appointment);
                }
                else
                {
                    foreach (var apps in param.deleted)
                    {
                        ScheduleEventData appointment = db.ScheduleEventDatas.Where(c => c.Id == apps.Id).FirstOrDefault();
                        if (apps != null) db.ScheduleEventDatas.DeleteOnSubmit(appointment);
                    }
                }
                db.SubmitChanges();
            }
            var data = db.ScheduleEventDatas.ToList();
            return Json(data, JsonRequestBehavior.AllowGet);
        }

        public class EditParams
        {
            public string key { get; set; }
            public string action { get; set; }
            public List<ScheduleEventData> added { get; set; }
            public List<ScheduleEventData> changed { get; set; }
            public List<ScheduleEventData> deleted { get; set; }
            public ScheduleEventData value { get; set; }
        }
    }
}
```

## Configuring Scheduler with Google API service

We have assigned our custom created Google Calendar url to the DataManager and assigned the same to the Scheduler `dataSource`. Since the events data retrieved from the Google Calendar will be in its own object format, therefore it needs to be resolved manually within the Scheduler’s `dataBinding` event. Within this event, the event fields needs to be mapped properly and then assigned to the result.

{% tab template="schedule/data-bind", iframeHeight="588px"  %}

```html
<template>
  <div id='app'>
    <div id='container'>
        <ejs-schedule :height='height' :selectedDate='selectedData' :readonly='readonly' :eventSettings='eventSettings' :dataBinding='onDataBinding'></ejs-schedule>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { DataManager, WebApiAdaptor } from '@syncfusion/ej2-data';
import { SchedulePlugin, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-vue-schedule';

Vue.use(SchedulePlugin);

var calendarId = '5105trob9dasha31vuqek6qgp0@group.calendar.google.com';
var publicKey = 'AIzaSyD76zjMDsL_jkenM5AAnNsORypS1Icuqxg';
var dataManager = new DataManager({
    url: 'https://www.googleapis.com/calendar/v3/calendars/' + calendarId + '/events?key=' + publicKey,
    adaptor: new WebApiAdaptor,
    crossDomain: true
});

export default {
  data (){
    return {
      height: '550px',
      eventSettings: {
          dataSource: dataManager
      },
      selectedData: new Date(2018, 10, 14),
      readonly: true,
    }
  },
  methods: {
      onDataBinding: function(e){
        var items = e.result.items;
        var scheduleData = [];
        if (items.length > 0) {
            for (var i = 0; i < items.length; i++) {
                var event = items[i];
                var when = event.start.dateTime;
                var start = event.start.dateTime;
                var end = event.end.dateTime;
                if (!when) {
                    when = event.start.date;
                    start = event.start.date;
                    end = event.end.date;
                }
                scheduleData.push({
                    Id: event.id,
                    Subject: event.summary,
                    StartTime: new Date(start),
                    EndTime: new Date(end),
                    IsAllDay: !event.start.dateTime
                });
            }
        }
        e.result = scheduleData;
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