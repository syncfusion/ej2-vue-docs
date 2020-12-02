---
title: "Tooltip"
component: "Gantt"
description: "Learn how to enable the tooltip for the task's in the Essential JS 2 Gantt component."
---

# Tooltip

The Gantt component has a support to display a tooltip for various UI elements like taskbar, timeline cells, and grid cells.

## Enable tooltip

In the Gantt component, you can enable or disable the mouse hover tooltip for the following UI elements using the [`tooltipSettings.showTooltip`](../api/gantt/tooltipSettings/#showtooltip) property:

* Taskbar
* Connector line
* Baseline
* Event marker

{% tab template="gantt/tooltip" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' :dataSource="data" id="GanttContainer" :taskFields = "taskFields" :height = "height" :eventMarkers="eventMarkers" :renderBaseline="renderBaseline" :treeColumnIndex='1' :baselineColor="baselineColor" :tooltipSettings="tooltipSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Selection, DayMarkers } from "@syncfusion/ej2-vue-gantt";
import { baselineData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
           data: [
        {
            TaskID: 1,
            TaskName: 'Project Initiation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            subtasks: [
                { TaskID: 2, TaskName: 'Identify Site location',BaselineStartDate: new Date('04/02/2019'),BaselineEndDate: new Date('04/02/2019'), StartDate: new Date('04/02/2019'), Duration: 0, Progress: 50 },
                { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'),BaselineStartDate: new Date('04/04/2019'),BaselineEndDate: new Date('04/09/2019'), Duration: 4, Progress: 50  },
                { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'),BaselineStartDate: new Date('04/08/2019'),BaselineEndDate: new Date('04/12/2019'), Duration: 4,Predecessor:"2FS", Progress: 50 },
            ]
        },
        {
            TaskID: 5,
            TaskName: 'Project Estimation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            subtasks: [
                { TaskID: 6, TaskName: 'Develop floor plan for estimation',BaselineStartDate: new Date('04/04/2019'),BaselineEndDate: new Date('04/08/2019'), StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 },
                { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'),BaselineStartDate: new Date('04/02/2019'),BaselineEndDate: new Date('04/04/2019'), Duration: 3, Progress: 50 },
                { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/02/2019'),BaselineStartDate: new Date('04/02/2019'),BaselineEndDate: new Date('04/08/2019'), Duration: 0,Predecessor:"6SS", Progress: 50 }
            ]
        },
    ],
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                baselineStartDate: "BaselineStartDate",
                baselineEndDate: "BaselineEndDate",
                progress: 'Progress',
                dependency: 'Predecessor',
                child: 'subtasks'
            },
            eventMarkers: [
            {
                day: '04/10/2019',
                label: 'Project approval and kick-off'
            }
            ],
            renderBaseline:true,
            baselineColor:'red',
            tooltipSettings:{
                showTooltip:true
                }
                height: '450px',
        };
  },
  provide: {
      gantt: [ Selection, DayMarkers ]
  }
};
</script>

```

{% endtab %}

> The default value of the [`tooltipSettings.showTooltip`](../api/gantt/tooltipSettings/#showtooltip) property is `true`.

## Timeline cells tooltip

In the Gantt component, you can enable or disable the mouse hover tooltip of timeline cells using the [`timelineSettings.showTooltip`](../api/gantt/timelineSettings/#showtooltip) property. The default value of this property is `true`. The following code example shows how to enable the timeline cells tooltip in Gantt.

{% tab template="gantt/tooltip" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' :dataSource="data" id="GanttContainer" :taskFields = "taskFields" :height = "height" :columns="columns" :timelineSettings="timelineSettings" ></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
import { editingData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: editingData,
            height: '450px',
            taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        timelineSettings: {
                showTooltip: true
            },
            columns: [
            { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '250' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ]
        };
  },
};
</script>

```

{% endtab %}

## Cell tooltip

You can enable or disable the Grid cell tooltip using the [`columns.clipMode`](../api/gantt/column/#clipmode) property.

{% tab template="gantt/tooltip" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' :dataSource="data" id="GanttContainer" :taskFields = "taskFields" :height = "height" :columns="columns"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
import { editingData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: editingData,
            height: '450px',
            taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        columns: [
            { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '150', clipMode: 'EllipsisWithTooltip' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '150',clipMode: 'Clip' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
        ]
        };
  },
};
</script>

```

{% endtab %}

### Clip mode

The clip mode provides options to display its overflow cell content and it can be defined by the [`columns.clipMode`](../api/gantt/column/#clipmode) property.

The following are three types of `clipMode`:

* `Clip`: Truncates the cell content when it overflows its area.
* `Ellipsis`: Displays ellipsis when content of the cell overflows its area.
* `EllipsisWithTooltip`: Displays ellipsis when content of the cell overflows its area; it displays the tooltip content when hover over ellipsis.

> NOTE
> By default, all the column's [`clipMode`](../api/gantt/column/#clipmode) property is defined as `EllipsisWithTooltip`.

## Tooltip template

### Taskbar tooltip

The default tooltip in the Gantt component can be customized using the [`tooltipSettings.taskbar`](../api/gantt/tooltipSettings/#taskbar) property.

{% tab template="gantt/tooltip" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' :dataSource="data" id="GanttContainer" :taskFields = "taskFields" :height = "height" :tooltipSettings="tooltipSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
import { editingData  } from './data-source.js';
import taskbarTemplate from './taskbartemplate.vue';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: editingData,
            height: '450px',
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                baselineStartDate:"BaselineStartDate",
                baselineEndDate:"BaselineEndDate",
                progress: 'Progress',
                dependency: 'Predecessor',
                child: 'subtasks'
            },
            tooltipSettings: {
                showTooltip: true,
                taskbar: function () {
                    return { template : Vue.component('taskbarTemplate',{
                        template: `<div>TaskID: {{data.TaskID}}</div>`,
                        data: function() {
                            return {
                                data: {}
                            }
                        },
                    })}
                }
            },
        };
  },
};
</script>

```

{% endtab %}

### Connector line tooltip

The default connector line tooltip in the Gantt component can be customized using the [`tooltipSettings.connectorLine`](../api/gantt/tooltipSettings/#connectorline) property. The following code example shows how to use the [`tooltipSettings.connectorLine`](../api/gantt/tooltipSettings/#connectorline) property.

{% tab template="gantt/tooltip" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' :dataSource="data" id="GanttContainer" :taskFields = "taskFields" :height = "height" :tooltipSettings="tooltipSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
import { editingData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: editingData,
            height: '450px',
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                progress: 'Progress',
                dependency: 'Predecessor',
                child: 'subtasks'
            },
            tooltipSettings: {
                showTooltip: true,
                connectorLine: function () {
                        return { template : Vue.component('connectorLineTemplate',{
                            template: `<div>Offset : {{data.offsetString}}</div>`,
                            data: function() {
                                return {
                                    data: {}
                                }
                            },
                        })}
                }
            }
        };
    },
};
</script>

```

{% endtab %}

### Taskbar editing tooltip

The taskbar editing tooltip can be customized using the [`tooltipSettings.editing`](../api/gantt/tooltipSettings/#editing) property. The following code example shows how to customize the taskbar editing tooltip in Gantt.

{% tab template="gantt/tooltip" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' :dataSource="data" id="GanttContainer" :taskFields = "taskFields" :height = "height" :editSettings="editSettings" :tooltipSettings="tooltipSettings"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, Edit } from "@syncfusion/ej2-vue-gantt";
import { editingData  } from './data-source.js';
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: editingData,
            height: '450px',
            taskFields: {
                id: 'TaskID',
                name: 'TaskName',
                startDate: 'StartDate',
                duration: 'Duration',
                baselineStartDate:"BaselineStartDate",
                baselineEndDate:"BaselineEndDate",
                progress: 'Progress',
                dependency: 'Predecessor',
                child: 'subtasks'
            },
            editSettings: {
                allowEditing:true,
                allowTaskbarEditing:true
            },
            tooltipSettings: {
                showTooltip: true,
                editing: function () {
                        return { template : Vue.component('editingTemplate',{
                            template: ` <div>Duration : {{data.duration}}</div>`,
                            data: function() {
                                return {
                                    data: {}
                                }
                            },
                        })}
                }
                },
        };
  },
  provide: {
      gantt: [ Edit ]
  },  
};
</script>

```

{% endtab %}

### Baseline tooltip

A baseline tooltip can be customized using the [`tooltipSettings.baseline`](../api/gantt/tooltipSettings/#baseline) property. The following code example shows how to customize the baseline tooltip in Gantt.

{% tab template="gantt/tooltip" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :renderBaseline="true" :taskFields="taskFields" :columns="columns" :treeColumnIndex="1" :includeWeekend="true" :timelineSettings="timelineSettings" :height="height" :dayWorkingTime="dayWorkingTime" :projectStartDate="projectStartDate" :projectEndDate="projectEndDate" :tooltipSettings="tooltipSettings" baselineColor='red'></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin, DayMarkers } from "@syncfusion/ej2-vue-gantt";
import { baselineData  } from './data-source.js';
import { Internationalization } from '@syncfusion/ej2-base';
let instance = new Internationalization();
Vue.use(GanttPlugin);
export default {
  data: function() {
      return{
            data: baselineData,
            taskFields: {
                id: 'TaskId',
                name: 'TaskName',
                startDate: 'StartDate',
                endDate: 'EndDate',
                baselineStartDate: 'BaselineStartDate',
                baselineEndDate: 'BaselineEndDate'
            },
            columns: [
                { field: 'TaskName', headerText: 'Service Name', width: '250', clipMode: 'EllipsisWithTooltip' },
                { field: 'BaselineStartDate', headerText: 'Planned start time' },
                { field: 'BaselineEndDate', headerText: 'Planned end time' },
                { field: 'StartDate', headerText: 'Start time' },
                { field: 'EndDate', headerText: 'End time' },
            ],
            timelineSettings: {
                timelineUnitSize: 65,
                topTier: {
                    unit: 'None',
                },
                bottomTier: {
                    unit: 'Minutes',
                    count: 15,
                    format: 'hh:mm a'
                },
            },
            dateFormat: 'hh:mm a',
            height: '450px',
            dayWorkingTime: [{ from: 1, to: 24 }],
            projectStartDate: new Date('03/05/2018 09:30:00 AM'),
            projectEndDate: new Date('03/05/2018 07:00:00 PM'),
            tooltipSettings: {
                showTooltip: true,
                baseline: function () {
                        return { template : Vue.component('baselineTemplate',{
                            template: ` <div>Baseline StartDate : {{format(data.BaselineStartDate)}}</div>`,
                            data: function() {
                                return {
                                    data: {}
                                };
                            },
                            methods: {
                                format: function(value) {
                                    return instance.formatDate(value, { skeleton: 'yMd', type: 'date' });
                                }
                            }
                        })}
                }
            },
        };
  },
  provide: {
      gantt: [ DayMarkers ]
  },  
};
</script>

```

{% endtab %}