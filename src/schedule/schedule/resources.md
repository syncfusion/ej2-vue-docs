---
title: "Multiple Resources and Grouping | VueJS Scheduler"
component: "Scheduler"
description: "This article demonstrates how to assign a single or multiple resources to events and also shows how to group them in both hierarchical and vertical mode."
---

# Multiple resources and grouping

Resources and grouping support allows the Scheduler to be shared by multiple resources. Also, the appointments of each resources are displayed under relevant resources. Each resource in the Scheduler is arranged in a column/row wise order, with individual spacing to display all its respective appointments on a single page. It also supports the multiple levels of grouping of resources, thus enabling the categorization of resources in a hierarchical structure and shows it either in expandable groups (Timeline views) or else vertical hierarchy one after the other (Calendar views).

It is also possible to assign one or more resources to the same appointment, by allowing multiple selection of resource options available in the event editor window.

The HTML5 JavaScript Scheduler groups the resources based on different criteria. It includes grouping appointments based on resources, grouping resources based on dates, and timeline scheduling. Also, the data for resources bind with Scheduler either as a local JSON collection or URL, retrieving data from remote data services.

## Resource fields

The default options available within the `resources` collection are as follows,

| Field name | Type | Description |
|-------|---------| --------------- |
| `field` | String | A value that binds to the resource field of event object. |
| `title` | String | It holds the title of the resource field to be displayed on the event editor window. |
| `name` | String | A unique resource name used for differentiating various resource objects while grouping. |
| `allowMultiple` | Boolean | When set to `true`, allows multiple selection of resource names, thus creating multiple instances of same appointment for the selected resources. |
| `dataSource` | Object | Assigns the resource `dataSource`, where data can be passed either as an array of JavaScript objects, or else can create an instance of [`DataManager`](http://ej2.syncfusion.com/documentation/data/api-dataManager.html) in case of processing remote data and can be assigned to the `dataSource` property. With the remote data assigned to `dataSource`, check the available [adaptors](http://ej2.syncfusion.com/documentation/data/adaptors.html) to customize the data processing. |
| `query` | Query | Defines the external [`query`](http://ej2.syncfusion.com/documentation/data/api-query.html) that will be executed along with the data processing. |
| `idField` | String | Binds the resource ID field name from the resources `dataSource`. |
| `textField` | String | Binds the text field name from the resources `dataSource`. It usually holds the resource names. |
| `groupIDField` | String | Binds the group ID field name from the resource `dataSource`. It usually holds the value of resource IDs of parent level resources. |
| `colorField` | String | Binds the color field name from the resource `dataSource`. The color value mapped in this field will be applied to the events of resources. |
| `startHourField` | String | Binds the start hour field name from the resource `dataSource`. It allows to provide different work start hour for the resources. |
| `endHourField` | String | Binds the end hour field name from the resource `dataSource`. It allows to provide different work end hour for the resources. |
| `workDaysField` | String | Binds the work days field name from the resources `dataSource`. It allows to provide different working days collection for the resources. |
| `cssClassField` | String | Binds the custom CSS class field name from the resources `dataSource`. It maps the CSS class written for the specific resources and applies it to the events of those resources. |

## Resource data binding

The data for resources can bind with Scheduler either as a local JSON collection or a service URL, retrieving resource data from remote data services.

### Using local JSON data

The following code example depicts how to bind the local JSON data to the `dataSource` of `resources` collection.

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :currentView='currentView'>
                    <e-views>
                        <e-view option='Week'></e-view>
                        <e-view option='Month'></e-view>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                        <e-view option='Agenda'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='OwnerId' title='Owner' name='Owners'  :dataSource='resourceDataSource' textField='OwnerText' idField='Id' colorField='OwnerColor'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { resourceData } from './datasource.js';
    import { SchedulePlugin, Week, Month, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);

    export default {
        data () {
            return {
                width: '100%',
                height: '550px',
                currentView: 'Week',
                views: ['Week', 'Month', 'TimelineWeek','TimelineMonth', 'Agenda'],
                selectedDate: new Date(2018, 3, 1),
                resourceDataSource: [
                    { OwnerText: 'Nancy', Id: 1, OwnerColor: '#ffaa00' },
                    { OwnerText: 'Steven', Id: 2, OwnerColor: '#f8a398' },
                    { OwnerText: 'Michael', Id: 3, OwnerColor: '#7499e1' }
                ],
                eventSettings: { dataSource: resourceData }
            }
        },
        provide: {
            schedule: [Week, Month, Agenda, TimelineViews, TimelineMonth]
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

### Using remote service URL

The following code example depicts how to bind the remote data for resources `dataSource`.

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :currentView='currentView'>
                    <e-views>
                        <e-view option='Week'></e-view>
                        <e-view option='Month'></e-view>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                        <e-view option='Agenda'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='OwnerId' title='Owner' name='Owners'  :dataSource='resourceDataSource' textField='OwnerText' idField='Id' colorField='OwnerColor'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { DataManager, UrlAdaptor } from '@syncfusion/ej2-data';
    import { SchedulePlugin, Week, Month, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-vue-schedule';
    import { resourceData } from './datasource.js';

    Vue.use(SchedulePlugin);

    let resource = new DataManager({
       url: 'Home/GetResourceData',
       adaptor: new UrlAdaptor,
       crossDomain: true
    });

    export default {
        data () {
            return {
                width: '100%',
                height: '550px',
                currentView: 'Week',
                views: ['Week', 'Month', 'TimelineWeek','TimelineMonth', 'Agenda'],
                selectedDate: new Date(2018, 3, 1),
                resourceDataSource: resource,
                eventSettings: { dataSource: resourceData }
            }
        },
        provide: {
            schedule: [Week, Month, Agenda, TimelineViews, TimelineMonth]
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

## Scheduler with multiple resources

It is possible to display the Scheduler in default mode without visually showcasing all the resources in it, but allowing to assign the required resources to the appointments through the event editor resource options.

The appointments belonging to the different resources will be displayed altogether on the default Scheduler, which will be differentiated based on the resource color assigned in the **resources** (depicting to which resource that particular appointment belongs) collection.

**Example:** To display default Scheduler with multiple resource options in the event editor, ignore the group option and simply define the `resources` property with all its internal options.

{% tab template="schedule/multiple-resources", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :currentView='currentView'>
                    <e-views>
                        <e-view option='Week'></e-view>
                        <e-view option='Month'></e-view>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                        <e-view option='Agenda'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='OwnerId' title='Owner' name='Owners' :allowMultiple='allowMultiple' :dataSource='resourceDataSource' textField='OwnerText' idField='Id' colorField='OwnerColor'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { resourceData } from './datasource.js';
    import { SchedulePlugin, Week, Month, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);

    export default {
        data () {
            return {
                width: '100%',
                height: '550px',
                currentView: 'Week',
                views: ['Week', 'Month', 'TimelineWeek','TimelineMonth', 'Agenda'],
                selectedDate: new Date(2018, 3, 1),
                allowMultiple: true,
                resourceDataSource: [
                    { OwnerText: 'Nancy', Id: 1, OwnerColor: '#ffaa00' },
                    { OwnerText: 'Steven', Id: 2, OwnerColor: '#f8a398' },
                    { OwnerText: 'Michael', Id: 3, OwnerColor: '#7499e1' }
                ],
                eventSettings: { dataSource: resourceData }
            }
        },
        provide: {
            schedule: [Week, Month, Agenda, TimelineViews, TimelineMonth]
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

> Setting `allowMultiple` to `true` in the above code example allows you to select multiple resources from the event editor and also creates multiple copies of the same appointment in the Scheduler for each resources while rendering.

## Resource grouping

Resource grouping support allows the Scheduler to group the resources in a hierarchical structure both as an expandable groups (Timeline views) and as vertical hierarchy displaying resources one after the other (Resources view).

Scheduler supports both single and multiple levels of resource grouping that can be customized both in timeline and vertical Scheduler views.

### Vertical resource view

The following code example displays how the multiple resources are grouped and its events are portrayed in the default calendar views.

{% tab template="schedule/resource-grouping", iframeHeight="588px" %}

```html
<template>
    <div id='app'>
        <div id='container'>
            <ejs-schedule id='Schedule' width='100%' height='550px'
            :eventSettings='eventSettings' :currentView='currentView' :selectedDate='selectedDate' :group='group'>
                <e-views>
                    <e-view option='Week'></e-view>
                    <e-view option='Month'></e-view>
                    <e-view option='Agenda'></e-view>
                </e-views>
                <e-resources>
                    <e-resource field='ProjectId' title='Choose Project' name='Projects' :dataSource='projectResourceDataSource' textField='text'
                    idField='id' colorField='color'>
                    </e-resource>
                    <e-resource field='CategoryId' title='Category' name='Categories' :dataSource='categoryResourceDataSource' :allowMultiple='allowMultiple'
                    textField='text' idField='id' colorField='color'>
                    </e-resource>
                </e-resources>
            </ejs-schedule>
        </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { resourceProjectData } from './datasource.js';
    import { SchedulePlugin, Week, Month, Agenda } from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                currentView: 'Week',
                selectedDate: new Date(2018, 3, 4),
                group: {
                    byGroupID: false,
                    resources: ['Projects', 'Categories']
                },
                projectResourceDataSource: [
                    { text: 'PROJECT 1', id: 1, color: '#cb6bb2' },
                    { text: 'PROJECT 2', id: 2, color: '#56ca85' },
                    { text: 'PROJECT 3', id: 3, color: '#df5286' }
                ],
                categoryResourceDataSource: [
                    { text: 'Development', id: 1, color: '#df5286' },
                    { text: 'Testing', id: 2, color: '#7fa900' }
                ],
                eventSettings: { dataSource: resourceProjectData },
                allowMultiple: true
            }
        },
        provide: {
            schedule: [Week, Month, Agenda]
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

### Timeline resource view

The following code example depicts how to group the multiple resources on Timeline Scheduler views and its relevant events are displayed accordingly under those resources.

{% tab template="schedule/resource-grouping", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :currentView='currentView' :group='group'>
                    <e-views>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                        <e-view option='Agenda'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field= 'RoomId' title= 'Room' name= 'Rooms' :dataSource='roomDataSource' textField='RoomText' idField='Id' colorField='RoomColor'>
                        </e-resource>
                        <e-resource field='OwnerId' title='Owner' name='Owners' :allowMultiple='allowMultiple' :dataSource='ownerDataSource'
                        textField='OwnerText' idField='Id' groupIDField= 'OwnerGroupId' colorField='OwnerColor'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { resourceData } from './datasource.js';
    import { SchedulePlugin, TimelineViews, TimelineMonth, Agenda } from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                width: '100%',
                height: '550px',
                currentView: 'TimelineWeek',
                selectedDate: new Date(2018, 3, 4),
                group: {
                    resources: ['Rooms', 'Owners']
                },
                roomDataSource: [
                    { RoomText: 'ROOM 1', Id: 1, RoomColor: '#cb6bb2' },
                    { RoomText: 'ROOM 2', Id: 2, RoomColor: '#56ca85' }
                ],
                allowMultiple: true,
                ownerDataSource: [
                    { OwnerText: 'Nancy', Id: 1, OwnerGroupId: 1, OwnerColor: '#ffaa00' },
                    { OwnerText: 'Steven', Id: 2, OwnerGroupId: 2, OwnerColor: '#f8a398' },
                    { OwnerText: 'Michael', Id: 3, OwnerGroupId: 1, OwnerColor: '#7499e1' }
                ],
                eventSettings: { dataSource: resourceData },
            }
        },
        provide: {
            schedule: [TimelineViews, TimelineMonth, Agenda]
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

### Grouping single-level resources

This kind of grouping allows the Scheduler to display all the resources at a single level simultaneously. The appointments mapped under resources will be displayed with the colors as per the `colorField` defined on the resources collection.

**Example:** To display the Scheduler with single level resource grouping,

{% tab template="schedule/single-level-resource", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :group='group'>
                    <e-views>
                        <e-view option='Week'></e-view>
                        <e-view option='Month'></e-view>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                        <e-view option='Agenda'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='OwnerId' title='Owner' name='Owners' :allowMultiple='allowMultiple' :dataSource='ownerDataSource'
                        textField='OwnerText' idField='Id' colorField='OwnerColor'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { resourceData } from './datasource.js';
    import { SchedulePlugin, Week, Month, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                width: '100%',
                height: '550px',
                currentView: 'TimelineWeek',
                selectedDate: new Date(2018, 3, 4),
                group: {
                    resources: ['Owners']
                },
                allowMultiple: true,
                ownerDataSource: [
                    { OwnerText: 'Nancy', Id: 1, OwnerColor: '#ffaa00' },
                    { OwnerText: 'Steven', Id: 2, OwnerColor: '#f8a398' },
                    { OwnerText: 'Michael', Id: 3, OwnerColor: '#7499e1' }
                ],
                eventSettings: { dataSource: resourceData },
            }
        },
        provide: {
            schedule: [Week, Month, Agenda, TimelineViews, TimelineMonth]
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

> The `name` field defined in the **resources** collection namely `Owners` will be mapped within the `group` property, in order to enable the grouping option with those resource levels on the Scheduler.

### Grouping multi-level resources

It is possible to group the resources of Scheduler in multiple levels, by mapping the child resources to each parent resource. In the following example, there are 2 levels of resources, on which the second level resources are defined with `groupID` mapping to the first level resource's ID so as to establish the parent-child relationship between them.

**Example:** To display the Scheduler with multiple level resource grouping options,

{% tab template="schedule/resource-grouping", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :group='group'>
                    <e-views>
                        <e-view option='Week'></e-view>
                        <e-view option='Month'></e-view>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                        <e-view option='Agenda'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='RoomId' title='Room' name='Rooms' :dataSource='roomDataSource' textField='RoomText' idField='Id' colorField='RoomColor'>
                        </e-resource>
                        <e-resource field='OwnerId' title='Owner' name='Owners' :allowMultiple='allowMultiple' :dataSource='ownerDataSource'
                        textField='OwnerText' idField='Id' groupIDField= 'OwnerGroupId' colorField='OwnerColor'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { resourceData } from './datasource.js';
    import { SchedulePlugin, Week, Month, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                width: '100%',
                height: '550px',
                selectedDate: new Date(2018, 3, 4),
                group: {
                    resources: ['Rooms', 'Owners']
                },
                roomDataSource: [
                    { RoomText: 'ROOM 1', Id: 1, RoomColor: '#cb6bb2' },
                    { RoomText: 'ROOM 2', Id: 2, RoomColor: '#56ca85' }
                ],
                allowMultiple: true,
                ownerDataSource: [
                    { OwnerText: 'Nancy', Id: 1, OwnerGroupId: 1, OwnerColor: '#ffaa00' },
                    { OwnerText: 'Steven', Id: 2, OwnerGroupId: 2, OwnerColor: '#f8a398' },
                    { OwnerText: 'Michael', Id: 3, OwnerGroupId: 1, OwnerColor: '#7499e1' }
                ],
                eventSettings: { dataSource: resourceData },
            }
        },
        provide: {
            schedule: [Week, Month, Agenda, TimelineViews, TimelineMonth]
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

### One-to-One grouping

In multi-level grouping, Scheduler usually groups the resources on the child level based on the `GroupID` that maps with the `Id` field of parent level resources (as `byGroupID` set to true by default). There are also option which allows you to group all the child resource(s) against each of its parent resource(s). To enable this kind of grouping, set `false` to the `byGroupID` option within the `group` property. In the following code example, there are two levels of resources, on which all the 3 resources at the child level is mapped one to one with each resource on the first level.

{% tab template="schedule/resource-grouping", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :group='group'>
                    <e-views>
                        <e-view option='Week'></e-view>
                        <e-view option='Month'></e-view>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                        <e-view option='Agenda'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field= 'RoomId' title= 'Room' name= 'Rooms' :dataSource='roomDataSource' textField='RoomText' idField='Id' colorField='RoomColor'>
                        </e-resource>
                        <e-resource field='OwnerId' title='Owner' name='Owners' :allowMultiple='allowMultiple' :dataSource='ownerDataSource'
                        textField='OwnerText' idField='Id' groupIDField= 'OwnerGroupId' colorField='OwnerColor'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { resourceData } from './datasource.js';
    import { SchedulePlugin, Week, Month, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                width: '100%',
                height: '550px',
                selectedDate: new Date(2018, 3, 4),
                currentView: 'Week',
                group: {
                    byGroupID: false,
                    resources: ['Rooms', 'Owners']
                },
                roomDataSource: [
                    { RoomText: 'ROOM 1', Id: 1, RoomColor: '#cb6bb2' },
                    { RoomText: 'ROOM 2', Id: 2, RoomColor: '#56ca85' }
                ],
                allowMultiple: true,
                ownerDataSource: [
                    { OwnerText: 'Nancy', Id: 1, OwnerGroupId: 1, OwnerColor: '#ffaa00' },
                    { OwnerText: 'Steven', Id: 2, OwnerGroupId: 2, OwnerColor: '#f8a398' },
                    { OwnerText: 'Michael', Id: 3, OwnerGroupId: 1, OwnerColor: '#7499e1' }
                ],
                eventSettings: { dataSource: resourceData },
            }
        },
        provide: {
            schedule: [Week, Month, Agenda, TimelineViews, TimelineMonth]
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

### Grouping resources by date

It groups the number of resources under each date and is applicable only on the calendar views such as Day, Week, Work Week, Month, Agenda and Month-Agenda. To enable such grouping, set `byDate` option to `true` within the `group` property.

**Example:** To display the Scheduler with resources grouped by date,

{% tab template="schedule/single-level-resource", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :group='group'>
                    <e-views>
                        <e-view option='Week'></e-view>
                        <e-view option='Month'></e-view>
                        <e-view option='Agenda'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='OwnerId' title='Owner' name='Owners' :allowMultiple='allowMultiple' :dataSource='ownerDataSource'
                        textField='text' idField='id' colorField='color'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { resourceData } from './datasource.js';
    import { SchedulePlugin, Week, Month, Agenda} from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                width: '100%',
                height: '550px',
                selectedDate: new Date(2018, 3, 4),
                group: {
                    byDate: true,
                    resources: ['Owners']
                },
                allowMultiple: true,
                ownerDataSource: [
                   { text: 'Alice', id: 1, color: '#1aaa55' },
                   { text: 'Smith', id: 2, color: '#7fa900' }
                ],
                eventSettings: { dataSource: resourceData },
            }
        },
        provide: {
            schedule: [Week, Month, Agenda]
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

> This kind of grouping by date is not applicable on any of the timeline views.

### Grouping with empty resource datasource

When using grouping, it is mandatory to provide at least one resource data in dataSource collection this is the default behavior of our scheduler. If the resource does not have a dataSource, scheduler rendered like below image.

![Grouping with empty resource](./images/empty-datasource.png)

To handle this case you can make the default schedule by emptying the group property.

{% tab template="schedule/single-level-resource", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                 <ejs-schedule id='Schedule' height="650px" :cssClass='cssClass' :selectedDate='selectedDate' :eventSettings='eventSettings'
                    :group='group' :dataBinding="dataBinding" readonly='true'>
                    <e-views>
                        <e-view option="Week"></e-view>
                        <e-view option="Month"></e-view>
                        <e-view option="Agenda"></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='AirlineId' title='Airline Name' name='Airlines' :allowMultiple='allowMultiple' :dataSource='resourceDataSource'
                            textField='AirlineName' idField='AirlineId' colorField='AirlineColor'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { resourceData } from './datasource.js';
    import { SchedulePlugin, Week, Month, Agenda, View, Resize, DragAndDrop } from "@syncfusion/ej2-vue-schedule";

    Vue.use(SchedulePlugin);
    export default {
        data: function () {
            return {
                cssClass: 'schedule-group',
                eventSettings: {
                    dataSource: [],
                    fields: {
                        subject: { title: 'Travel Summary', name: 'Subject' },
                        location: { title: 'Source', name: 'Location' },
                        description: { title: 'Comments', name: 'Description' },
                        startTime: { title: 'Departure Time', name: 'StartTime' },
                        endTime: { title: 'Arrival Time', name: 'EndTime' }
                    }
                },
                selectedDate: new Date(2018, 3, 1),
                allowMultiple: true,
                resourceDataSource: [],
                group: { resources: ['Airlines'] }
            }
        },
        provide: {
            schedule: [Week, Month, Agenda, Resize, DragAndDrop]
        },
        methods: {
            dataBinding: function () {
                let scheduleObj = document.getElementById('Schedule').ej2_instances[0];
                //check the resource count
                if ((scheduleObj.resourceCollection[0].dataSource as any).length === 0 && scheduleObj.group.resources.length > 0) {
                // Render default scheduler to handle above case.
                    scheduleObj.group.resources = [];
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
</style>

```

{% endtab %}

## Customizing parent resource cells

In timeline view work cells of parent resource can be customized by checking the `elementType` as `resourceGroupCells` in the event `renderCell`. In the following code example, background color of the work hours has been changed.

{% tab template="schedule/resource-grouping", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='container'>
            <ejs-schedule ref='scheduleObj' id='Schedule' width='100%' height='550px' :eventSettings='eventSettings'
            :selectedDate='selectedDate' :currentView='currentView' :group='group' :renderCell='onRenderCell'>
                <e-views>
                    <e-view option='TimelineDay'></e-view>
                    <e-view option='TimelineWeek'></e-view>
                    <e-view option='TimelineMonth'></e-view>
                </e-views>
                <e-resources>
                    <e-resource field='RoomId' title='Room' name='Rooms' :dataSource='roomDataSource' textField='RoomText' idField='Id' groupIDField= 'RoomGroupId' colorField='RoomColor'>
                    </e-resource>
                    <e-resource field='OwnerId' title='Owner' name='Owners' :allowMultiple='allowMultiple' :dataSource='ownerDataSource'
                    textField='OwnerText' idField='Id' groupIDField= 'OwnerGroupId' colorField='OwnerColor'>
                    </e-resource>
                </e-resources>
            </ejs-schedule>
        </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { resourceData } from './datasource.js';
    import { SchedulePlugin, TimelineViews, TimelineMonth } from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);

    export default {
        data () {
            return {
                selectedDate: new Date(2018, 3, 4),
                currentView: 'TimelineWeek',
                group: {
                    resources: ['Rooms', 'Owners']
                },
                roomDataSource: [
                    { RoomText: 'ROOM 1', Id: 1, RoomGroupId: 1, RoomColor: '#cb6bb2' },
                    { RoomText: 'ROOM 2', Id: 2, RoomGroupId: 2, RoomColor: '#56ca85' }
                ],
                allowMultiple: true,
                ownerDataSource: [
                    { OwnerText: 'Nancy', Id: 1, OwnerGroupId: 1, OwnerColor: '#ffaa00' },
                    { OwnerText: 'Steven', Id: 2, OwnerGroupId: 2, OwnerColor: '#f8a398' },
                    { OwnerText: 'Michael', Id: 3, OwnerGroupId: 1, OwnerColor: '#7499e1' }
                ],
                eventSettings: { dataSource: resourceData }
            }
        },
        provide: {
            schedule: [TimelineViews, TimelineMonth]
        },
        methods: {
            onRenderCell(args) {
                if (args.elementType == 'resourceGroupCells' && args.element.className.indexOf('e-work-hours') > 0) {
                    args.element.style.background = "#FAFAE3";
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
</style>
```

{% endtab %}

## Working with shared events

Multiple resources can share the same events, thus allowing the CRUD action made on it to reflect on all other shared instances simultaneously. To enable such option, set `allowGroupEdit` option to `true` within the `group` property. With this property enabled, a single appointment
object will be maintained within the appointment collection, even if it is shared by more than one resource – whereas the resource fields of such appointment object will be in array which hold the IDs of the multiple resources.

> Any actions such as create, edit or delete held on any one of the shared event instances, will be reflected on all other related instances visible on the UI.

**Example:** To edit all the resource events simultaneously,

{% tab template="schedule/resource-grouping", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :selectedDate='selectedDate' :eventSettings='eventSettings' :currentView='currentView' :group='group'>
                    <e-views>
                        <e-view option='Week'></e-view>
                        <e-view option='Month'></e-view>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                        <e-view option='Agenda'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='ConferenceId' title='Conference' name='Conferences' :allowMultiple='allowMultiple' :dataSource='resourceDataSource'
                        textField='Text' idField='Id' colorField='Color'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { SchedulePlugin, Week, Month, Agenda, TimelineViews, TimelineMonth, Resize} from '@syncfusion/ej2-vue-schedule';
    import { resourceConferenceData } from './datasource.js';

    Vue.use(SchedulePlugin);

    export default {
        data () {
            return {
                selectedDate: new Date(2018, 5, 2),
                currentView: 'Week',
                group: {
                    allowGroupEdit: true,
                    resources: ['Conferences']
                },
                resourceDataSource: [
                    { Text: 'Margaret', Id: 1, Color: '#1aaa55' },
                    { Text: 'Robert', Id: 2, Color: '#357cd2' },
                    { Text: 'Laura', Id: 3, Color: '#7fa900' }
                ],
                allowMultiple: true,
                eventSettings: { dataSource: resourceConferenceData }
            }
        },
        provide: {
            schedule: [Week, Month, Agenda, TimelineViews, TimelineMonth, Resize]
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

## Simple resource header customization

It is possible to customize the resource header cells using built-in template option and change the look and appearance of it in both the vertical and timeline view modes. All the resource related fields and other information can be accessed within the resource header template option.

**Example:** To customize the resource header and display it along with designation field, refer the below code example.

{% tab template="schedule/resource-header", iframeHeight="588px" %}

```html
<template>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :group='group' :resourceHeaderTemplate='resourceHeaderTemplate'>
                    <e-views>
                        <e-view option='Week'></e-view>
                        <e-view option='Month'></e-view>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                        <e-view option='Agenda'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='DoctorId' title='Doctor Name' name='Doctors' :dataSource='ownerDataSource'
                        textField='text' idField='id' colorField='color'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
</template>

<script>
    import Vue from 'vue';
    import { doctorData} from './datasource.js';
    import { SchedulePlugin, Week, Month, Agenda, TimelineViews, TimelineMonth} from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);

    var resourceHeaderTemplateVue = Vue.component('headerTemplate', {
        template: `<div class='template-wrap'><div class="resource-details"><div class="resource-name">{{data.resourceData.text}}</div><div class="resource-designation">{{data.resourceData.designation}}</div></div></div>`,
        data() {
            return {
                data: {}
            };
        }
    });

    export default {
        data () {
            return {
                selectedDate: new Date(2018, 3, 4),
                group: {
                    resources: ['Doctors']
                },
                ownerDataSource: [
                    { text: 'Will Smith', id: 1, color: '#ea7a57', designation: 'Cardioligst' },
                    { text: 'Alice', id: 2, color: '#7fa900', designation: 'Neurologist' },
                    { text: 'Robson', id: 3, color: '#7fa900', designation: 'Orthopedic Surgeon'  }
                ],
                resourceHeaderTemplate: function(e){
                    return {
                        template: resourceHeaderTemplateVue
                    };
                },
                eventSettings: { dataSource: doctorData },
            }
        },
        provide: {
            schedule: [Week, Month, Agenda, TimelineViews, TimelineMonth]
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

    .e-schedule.e-device .template-wrap .resource-details .resource-designation {
        display: none;
    }
</style>

```

{% endtab %}

> To customize the resource header in compact mode properly make use of the class `e-device` as in the code example.

![Resource header template in compact mode](./images/header-template.png)

## Customizing resource header with multiple columns

It is possible to customize the resource headers to display with multiple columns such as Room, Type and Capacity. The following code example depicts the way to achieve it and is applicable only on timeline views.

{% tab template="schedule/resource-header-column-customization", iframeHeight="588px" %}

```html
<template>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :group='group' :resourceHeaderTemplate='resourceHeaderTemplate' :renderCell='onRenderCell'>
                    <e-views>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='RoomId' title='RoomType' name='MeetingRoom'  :dataSource='ownerDataSource'
                        textField='text' idField='id' colorField='color'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
</template>

<script>
    import Vue from 'vue';
    import { roomData} from './datasource.js';
    import { SchedulePlugin, TimelineViews, TimelineMonth} from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);

    var resourceHeaderTemplateVue = Vue.component('headerTemplate', {
        template: `<div class='template-wrap'>
                <div class="room-name">{{data.resourceData.text}}</div>
                <div class="room-type">{{data.resourceData.type}}</div>
                <div class="room-capacity">{{data.resourceData.capacity}}</div>
                </div>`,
        data() {
            return {
                data: {}
            };
        }
    });

    export default {
        data () {
            return {
                selectedDate: new Date(2018, 7, 1),
                group: {
                    resources: ['MeetingRoom']
                },
                ownerDataSource: [
                    { text: 'Jammy', id: 1, color: '#ea7a57', capacity: 20, type: 'Conference' },
                    { text: 'Tweety', id: 2, color: '#7fa900', capacity: 7, type: 'Cabin' },
                    { text: 'Nestle', id: 3, color: '#5978ee', capacity: 5, type: 'Cabin' },
                    { text: 'Phoenix', id: 4, color: '#fec200', capacity: 15, type: 'Conference' },
                    { text: 'Mission', id: 5, color: '#df5286', capacity: 25, type: 'Conference' },
                    { text: 'Hangout', id: 6, color: '#00bdae', capacity: 10, type: 'Cabin' },
                    { text: 'Rick Roll', id: 7, color: '#865fcf', capacity: 20, type: 'Conference' },
                    { text: 'Rainbow', id: 8, color: '#1aaa55', capacity: 8, type: 'Cabin' },
                    { text: 'Swarm', id: 9, color: '#df5286', capacity: 30, type: 'Conference' },
                    { text: 'Photogenic', id: 10, color: '#710193', capacity: 25, type: 'Conference' }  
                ],
                resourceHeaderTemplate: function(e){
                     return {
                        template: resourceHeaderTemplateVue
                    };
                },
                eventSettings: { dataSource: roomData },
            }
        },
        methods: {
            onRenderCell: function(args){
                if (args.elementType === 'emptyCells' && args.element.classList.contains('e-resource-left-td')) {
                    let target = args.element.querySelector('.e-resource-text');
                    target.innerHTML = '<div class="name">Rooms</div><div class="type">Type</div><div class="capacity">Capacity</div>';
                }
            }
        },
        provide: {
            schedule: [TimelineViews, TimelineMonth]
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

    .e-schedule .e-timeline-view .e-resource-left-td .e-resource-text {
        display: flex;
        font-weight: 500;
        padding: 0;
    }

    .e-schedule .e-timeline-view .e-resource-left-td .e-resource-text>div {
        border-right: 1px solid rgba(0, 0, 0, 0.12);
        border-top: 1px solid rgba(0, 0, 0, 0.12);
        flex: 0 0 33.3%;
        font-weight: 500;
        height: 36px;
        line-height: 34px;
        padding-left: 5px;
    }

    .e-schedule .e-timeline-view .e-resource-left-td .e-resource-text>div:last-child {
        border-right: 0;
    }

    .e-schedule .template-wrap {
        display: flex;
        height: 100%;
        text-align: left;
    }

    .e-schedule .template-wrap>div {
        border-right: 1px solid rgba(0, 0, 0, 0.12);
        flex: 0 0 33.3%;
        font-weight: 500;
        line-height: 58px;
        overflow: hidden;
        padding-left: 5px;
        text-overflow: ellipsis;
    }

    .e-schedule .template-wrap>div:last-child {
        border-right: 0;
    }

    .e-schedule .e-timeline-view .e-resource-cells,
    .e-schedule .e-timeline-month-view .e-resource-cells {
        padding-left: 0;
    }

    .e-schedule .e-timeline-view .e-date-header-wrap table col,
    .e-schedule .e-timeline-view .e-content-wrap table col {
        width: 100px;
    }

    @media (max-width: 550px) {
        .e-schedule .e-timeline-view .e-resource-left-td {
            width: 100px;
        }
        .e-schedule .e-timeline-view .e-resource-left-td .e-resource-text>div,
        .e-schedule .template-wrap>div {
            flex: 0 0 100%;
        }
        .e-schedule .template-wrap>div:first-child {
            border-right: 0;
        }
        .e-schedule .e-timeline-view .e-resource-left-td .e-resource-text>div:first-child {
            border-right: 0;
        }
        .e-schedule .room-type,
        .e-schedule .room-capacity {
            display: none;
        }
    }
</style>

```

{% endtab %}

## Displaying tooltip for resource headers

It is possible to display tooltips over the resource headers showing the resource information. By default, there won't be any tooltips displayed on the resource headers, and to enable it, you need to assign the customized template design to the `headerTooltipTemplate` option within the `group` property.

{% tab template="schedule/header-tooltip", iframeHeight="588px" %}

```html
<template>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :group='group'>
                    <e-views>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='OwnerId' title='Owner' name='Owners' :dataSource='ownerDataSource' :allowMultiple='allowMultiple'
                        textField='OwnerText' idField='Id' groupIDField='OwnerGroupId' colorField='OwnerColor'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
</template>

<script>
    import Vue from 'vue';
    import { SchedulePlugin, Week, Month, TimelineViews, TimelineMonth } from '@syncfusion/ej2-vue-schedule';
    import { resourceData } from './datasource.js';

    Vue.use(SchedulePlugin);

    var headerTooltipTemplateVue = Vue.component('headerTooltipTemplate', {
        template: `<div class='template-wrap'><div class="resource-text">Name:{{data.resourceData.OwnerText}}</div></div>`,
        data() {
            return {
                data: {}
            };
        }
    });

    export default {
        data () {
            return {
                selectedDate: new Date(2018, 3, 4),
                group: {
                  resources: ['Rooms', 'Owners'],
                  headerTooltipTemplate: function(e){
                      return {
                          template: headerTooltipTemplateVue
                      };
                  }
                },
                allowMultiple: true,
                ownerDataSource: [
                    { OwnerText: 'Nancy', Id: 1, OwnerGroupId: 1, OwnerColor: '#ffaa00' },
                    { OwnerText: 'Steven', Id: 2, OwnerGroupId: 2, OwnerColor: '#f8a398' },
                    { OwnerText: 'Michael', Id: 3, OwnerGroupId: 1, OwnerColor: '#7499e1' }  
                ],
                eventSettings: { dataSource: resourceData },
            }
        },
        provide: {
            schedule: [TimelineViews, TimelineMonth]
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

  .e-schedule .e-vertical-view .e-resource-cells {
        height: 45px;
    }

    .e-schedule .e-agenda-view .template-wrap .resource-text {
        text-align: center;
    }

    .e-schedule .template-wrap .resource-text {
        font-size: 15px;
        padding: 4px 4px 4px;
        height: 25px;
        text-overflow: ellipsis;
        white-space: nowrap;
        overflow: hidden;
    }
</style>

```

{% endtab %}

## Choosing among resource colors for appointments

By default, the colors defined on the top level resources collection will be applied for the events. In case, if you want to apply specific resource color to events irrespective of its top-level parent resource color, it can be achieved by defining `resourceColorField` option within the `eventSettings` property.

In the following example, the colors mentioned in the second level will get applied over the events.

{% tab template="schedule/resource-color", iframeHeight="588px" %}

```html
<template>
    <div>
    <div id='container' class='col-lg-12'>
        <div class='content-wrapper'>
            <div class='col-lg-12 property-section'>
                <table id='property' title='Event Trace'>
                    <tbody>
                        <tr>
                            <td>
                                <ejs-radiobutton label="Rooms" name="default" value="Rooms" :checked='true'
                                    :change='onChange'></ejs-radiobutton>
                            </td>
                            <td>
                                <ejs-radiobutton label='Owners' name="default" value="Owners" :checked='false'
                                    :change='onChange'></ejs-radiobutton>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <div>
                <ejs-schedule ref='scheduleObj' id='Schedule' width='100%' height='500px' :eventSettings='eventSettings'
                    :selectedDate='selectedDate' :group='group'>
                    <e-views>
                        <e-view option='Week'></e-view>
                        <e-view option='Month'></e-view>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                        <e-view option='Agenda'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='RoomId' title='Room' name='Rooms' :dataSource='roomDataSource'
                            textField='RoomText' idField='Id' groupIDField='RoomGroupId' colorField='RoomColor'>
                        </e-resource>
                        <e-resource field='OwnerId' title='Owner' name='Owners' :allowMultiple='allowMultiple'
                            :dataSource='ownerDataSource' textField='OwnerText' idField='Id' groupIDField='OwnerGroupId'
                            colorField='OwnerColor'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>

        </div>
    </div>
</div>
</template>
<script>
    import Vue from 'vue';
    import { resourceData } from './datasource.js';
    import { SchedulePlugin, Month, Week, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-vue-schedule';
    import { RadioButtonPlugin} from '@syncfusion/ej2-vue-buttons';

    Vue.use(SchedulePlugin);
    Vue.use(RadioButtonPlugin);
    export default {
        data () {
            return {
                selectedDate: new Date(2018, 3, 4),
                group: {
                    resources: ['Rooms', 'Owners']
                },
                roomDataSource: [
                    { RoomText: 'ROOM 1', Id: 1, RoomGroupId: 1, RoomColor: '#cb6bb2' },
                    { RoomText: 'ROOM 2', Id: 2, RoomGroupId: 2, RoomColor: '#56ca85' }
                ],
                allowMultiple: true,
                ownerDataSource: [
                    { OwnerText: 'Nancy', Id: 1, OwnerGroupId: 1, OwnerColor: '#ffaa00' },
                    { OwnerText: 'Steven', Id: 2, OwnerGroupId: 2, OwnerColor: '#f8a398' },
                    { OwnerText: 'Michael', Id: 3, OwnerGroupId: 1, OwnerColor: '#7499e1' }
                ],
                eventSettings: { dataSource: resourceData, resourceColorField: 'Rooms' }
            }
        },
        provide: {
            schedule: [Month, Week, Agenda, TimelineViews, TimelineMonth]
        },
        methods: {
            onChange(args) {
                this.$refs.scheduleObj.ej2Instances.eventSettings.resourceColorField = args.value;
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
</style>

```

{% endtab %}

> The value of the `resourceColorField` field should be mapped with the `name` value given within the `resources` property.

## Dynamically add and remove resources

It is possible to add or remove the resources dynamically to and from the Scheduler respectively. In the following example, when the checkboxes are checked and unchecked, the respective resources gets added up or removed from the Scheduler layout. To add new resource dynamically, `addResource` method is used which accepts the arguments such as resource object, resource name (within which level, the resource object to be added) and index (position where the resource needs to be added).

To remove the resources dynamically, `removeResource` method is used which accepts the index (position from where the resource to be removed) and resource name (within which level, the resource object presents) as parameters.

{% tab template="schedule/dynamic-resource", iframeHeight="588px"  %}

```html
<template>
    <div>
        <div id='app'>
            <div class='col-lg-3'>
                <table id='property' title='Show / Hide Resource' style='width: 100%;padding-right:25px'>
                    <tbody>
                        <tr style='height: 50px'>
                                <td style='width: 100%'>
                                    <ejs-checkbox cssClass='personal' label='My Calender' value='1' :checked='true' :disabled='true' :change='onChange'></ejs-checkbox>
                                </td>
                            </tr>
                            <tr style='height: 50px'>
                                <td style='width: 100%'>
                                    <ejs-checkbox cssClass='company' label='Company' value='2' :checked='false' :change='onChange'></ejs-checkbox>
                                </td>
                            </tr>
                            <tr style='height: 50px'>
                                <td style='width: 100%'>
                                    <ejs-checkbox cssClass='birthday' label='Birthday' value='3' :checked='false' :change='onChange'></ejs-checkbox>
                                </td>
                            </tr>
                            <tr style='height: 50px'>
                                <td style='width: 100%'>
                                    <ejs-checkbox cssClass='holiday' label='Holiday' value='4' :checked='false' :change='onChange'></ejs-checkbox>
                                </td>
                            </tr>
                        </tbody>
                </table>
            </div>
            <div id='container'>
                <ejs-schedule id='Schedule' ref='ScheduleObj' width='100%' height='550px' :calendarCollections='calendarCollection' :group='group' :selectedDate='selectedDate'
                :eventSettings='eventSettings'>
                    <e-resources>
                        <e-resource field='CalendarId' title='Calendars' :dataSource='resourceDataSource' :allowMultiple='allowMultiple'
                         name='Calendars' textField='CalendarText' idField='CalendarId' colorField='CalendarColor'>
                        </e-resource>
                    </e-resources>
                    <e-views>
                        <e-view option='Month'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                    </e-views>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { holidayData, birthdayData, companyData, personalData } from './datasource.js';
    import { SchedulePlugin, Month, TimelineMonth } from '@syncfusion/ej2-vue-schedule';
    import { CheckBoxPlugin } from '@syncfusion/ej2-vue-buttons';

    Vue.use(SchedulePlugin);
    Vue.use(CheckBoxPlugin);

    var calendarCollections = [
        { CalendarText: 'My Calendar', CalendarId: 1, CalendarColor: '#c43081' },
        { CalendarText: 'Company', CalendarId: 2, CalendarColor: '#ff7f50' },
        { CalendarText: 'Birthday', CalendarId: 3, CalendarColor: '#AF27CD' },
        { CalendarText: 'Holiday', CalendarId: 4, CalendarColor: '#808000' }
    ];

    export default {
        data () {
            return {
                selectedDate: new Date(2018, 3, 1),
                group: { resources: ['Calendars'] },
                resourceDataSource: [calendarCollections[0]],
                calendarCollection: calendarCollections,
                allowMultiple: true,
                eventSettings: { dataSource: this.generateCalendarData() }
            }
        },
        provide: {
            schedule: [Month, TimelineMonth]
        },
        methods: {
            generateCalendarData: function () {
                var collections = [];
                var dataCollections = [personalData, companyData, birthdayData, holidayData];
                for (var i = 0; i < dataCollections.length; i++) {
                    collections = collections.concat(dataCollections[i]);
                }
                return collections;
            },
            onChange: function (args) {
                let scheduleObj = this.$refs.ScheduleObj;
                let value = parseInt((args.event.target).getAttribute('value'), 10);
                let resourceData = calendarCollections.filter(function (calendar) { return calendar.CalendarId === value; });
                if (args.checked) {
                    scheduleObj.addResource(resourceData[0], 'Calendars', value - 1);
                    scheduleObj.dataBind();
                } else {
                    scheduleObj.removeResource(value, 'Calendars');
                    scheduleObj.dataBind();
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

  #app {
    display: flex;
  }
</style>

```

{% endtab %}

## Setting different working days and hours for resources

Each resource in the Scheduler can have different working hours as well as different working days set to it. There are default options available within the `resources` collection, to customize the default working hours and days of the Scheduler.

### Set different work days

Different working days can be set for the resources of Scheduler using the `workDaysField` property which maps the working days field from the resource dataSource. This field accepts the collection of day indexes (from 0 to 6) of a week. By default, it is set to [1, 2, 3, 4, 5] and in the following example, each resource has been set with different values and therefore each of them will render only those working days. This option is applicable only on the calendar views and is not applicable on timeline views.

{% tab template="schedule/multiple-resources", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :currentView='currentView' :group='group'>
                    <e-views>
                        <e-view option='Week'></e-view>
                        <e-view option='WorkWeek'></e-view>
                        <e-view option='Month'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='ConferenceId' title='Conference' name='Conferences' :allowMultiple='allowMultiple' :dataSource='ownerDataSource'
                        textField='text' idField='id' colorField='color' workDaysField='workDays'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { doctorData } from './datasource.js';
    import { SchedulePlugin, Week, WorkWeek, Month} from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);

    export default {
        data () {
            return {
                selectedDate: new Date(2018, 3, 4),
                currentView: 'WorkWeek',
                group: {
                    resources: ['Conferences']
                },
                allowMultiple: true,
                ownerDataSource: [
                    { text: 'Will Smith', id: 1, color: '#ea7a57', workDays: [1, 2, 4, 5] },
                    { text: 'Alice', id: 2, color: 'rgb(53, 124, 210)', workDays: [1, 3, 5] },
                    { text: 'Robson', id: 3, color: '#7fa900' , workDays: [2,6]}
                ],
                eventSettings: { dataSource: doctorData },
            }
        },
        provide: {
            schedule: [Week, WorkWeek, Month]
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

### Set different work hours

Working hours indicates the work hour duration of a day, which is highlighted visually with active color over the work cells. Each resource on the Scheduler can be defined with its own set of working hours as depicted in the following example.

* `startHourField` - Denotes the start time of the working/business hour in a day.
* `endHourField` - Denotes the end time limit of the working/business hour in a day.

{% tab template="schedule/multiple-resources", iframeHeight="588px" %}

```html
<template>
    <div>
        <div id='app'>
            <div id='container'>
                <ejs-schedule id='Schedule' width='100%' height='550px' :eventSettings='eventSettings' :selectedDate='selectedDate' :group='group'>
                    <e-views>
                        <e-view option='Week'></e-view>
                        <e-view option='Month'></e-view>
                        <e-view option='TimelineWeek'></e-view>
                        <e-view option='TimelineMonth'></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='ConferenceId' title='Conference' name='Conferences' :allowMultiple='allowMultiple' :dataSource='ownerDataSource'
                        textField='text' idField='id' colorField='color' startHourField='startHour'
                        endHourField='endHour'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import { doctorData } from './datasource.js';
    import { SchedulePlugin, Week, Month, TimelineViews, TimelineMonth} from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);

    export default {
        data () {
            return {
                selectedDate: new Date(2018, 3, 4),
                group: {
                    resources: ['Conferences']
                },
                allowMultiple: true,
                ownerDataSource: [
                    { text: 'Will Smith', id: 1, color: '#ea7a57', startHour: '08:00', endHour: '15:00' },
                    { text: 'Alice', id: 2, color: '#357cd2', startHour: '10:00', endHour: '18:00'},
                    { text: 'Robson', id: 3, color: '#7fa900', startHour: '06:00', endHour: '13:00' }
                ],
                eventSettings: { dataSource: doctorData },
            }
        },
        provide: {
            schedule: [Week, Month, TimelineViews, TimelineMonth]
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

In this example, a resource named `Will Smith` is depicted with working hours ranging from 8.00 AM to 3.00 PM and is visually illustrated with active colors, whereas the other two resources have different working hours set.

## Compact view in mobile

Although the Scheduler views are designed keeping in mind the responsiveness of the control in mobile devices, however when using Scheduler with multiple resources - it is difficult to view all the resources and its relevant events at once on the mobile. Therefore, we have introduced a new compact mode specially for displaying multiple resources of Scheduler on mobile devices. By default, this mode is enabled while using Scheduler with multiple resources on mobile devices. If in case, you need to disable this compact mode, set `false` to the `enableCompactView` option within the `group` property. Disabling this option will display the exact desktop mode of Scheduler view on mobile devices.

With this compact view enabled on mobile, you can view only single resource at a time and to switch to other resources, there is a treeview at the left listing out all other available resources - clicking on which will display that particular resource and its related appointments.

![Resources in compact mode](./images/resource-mobile.png)

Clicking on the menu icon before the resource text will show the resources available in the Scheduler as following.

![Resources menu option in compact mode](./images/resource-menu.png)

## Adaptive UI in desktop

By default, the Scheduler layout adapts automatically in the desktop and mobile devices with appropriate UI changes. In case, if the user wants to display the Adaptive scheduler in desktop mode with adaptive enhancements, then the property `enableAdaptiveUI` can be set to true. Enabling this option will display the exact mobile mode of Scheduler view on desktop devices.

Some of the default changes made for compact Scheduler to render in desktop devices are as follows,
* View options displayed in the Navigation drawer.
* Plus icon is added to the header for new event creation.
* Today icon is added to the header instead of the Today button.
* With Multiple resources – only one resource has been shown to enhance the view experience of resource events details clearly. To switch to other resources, there is a TreeView on the left that lists all other available resources, clicking on which will display that particular resource and its related events.

{% tab template="schedule/resource-grouping", iframeHeight="588px" %}

```html
<template>
    <div id='app'>
        <div id='container'>
            <ejs-schedule id="schedule" ref="ScheduleObj" width='100%' height='650px'
                    :selectedDate="selectedDate" :eventSettings="eventSettings" currentView="Month" :enableAdaptiveUI="enableAdaptiveUI" :group="group">
                    <e-views>
                        <e-view option="Day"></e-view>
                        <e-view option="Week"></e-view>
                        <e-view option="Month"></e-view>
                    </e-views>
                    <e-resources>
                        <e-resource field='ProjectId' title='Choose Project' name='Projects' :dataSource='projectResourceDataSource' textField='text'
                            idField='id' colorField='color'>
                        </e-resource>
                        <e-resource field='TaskId' title='Employee' name='Employees' :dataSource='employeeDataSource' :allowMultiple='allowMultiple'
                            textField='text' idField='id' groupIDField='groupId' colorField='color'>
                        </e-resource>
                    </e-resources>
                </ejs-schedule>
        </div>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { resourceData, timelineResourceData } from './datasource.js';
    import { SchedulePlugin, Day, Week, Month, DragAndDrop, Resize } from '@syncfusion/ej2-vue-schedule';

    Vue.use(SchedulePlugin);
    export default {
        data () {
            return {
                eventSettings: {
                    dataSource: this.generateData()
                },
                selectedDate: new Date(2018, 3, 4),
                enableAdaptiveUI: true,
                allowMultiple : true,
                group: {
                    resources: ['Projects', 'Employees']
                },
                projectResourceDataSource: [
                    { text: 'PROJECT 1', id: 1, color: '#cb6bb2' },
                    { text: 'PROJECT 2', id: 2, color: '#56ca85' },
                    { text: 'PROJECT 3', id: 3, color: '#df5286' }
                ],
                employeeDataSource: [
                    { text: 'Nancy', id: 1, groupId: 1, color: '#df5286' },
                    { text: 'Steven', id: 2, groupId: 1, color: '#7fa900' },
                    { text: 'Robert', id: 3, groupId: 2, color: '#ea7a57' },
                    { text: 'Smith', id: 4, groupId: 2, color: '#5978ee' },
                    { text: 'Micheal', id: 5, groupId: 3, color: '#df5286' },
                    { text: 'Root', id: 6, groupId: 3, color: '#00bdae' }
                ],
            }
        },
        provide: {
            schedule: [Day, Week, Month, DragAndDrop, Resize]
        },
        methods: {
            generateData: function () {
                var collections = [];
                var dataCollections = [resourceData, timelineResourceData];
                for (var i = 0; i < dataCollections.length; i++) {
                    collections = collections.concat(dataCollections[i]);
                }
                return collections;
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
</style>

```

{% endtab %}

> You can refer to our [Vue Scheduler](https://www.syncfusion.com/vue-ui-components/vue-scheduler) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Scheduler example](https://ej2.syncfusion.com/vue/demos/#/material/schedule/overview.html) to knows how to present and manipulate data.
