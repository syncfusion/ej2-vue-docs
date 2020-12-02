---
title: "Appearance customization"
component: "Gantt"
description: "The overview section describes how to customize the Gantt taskbar and task labels in Gantt"
---

# Appearance customization

## Taskbar customization

### Taskbar height

The height of child taskbars and parent taskbars can be customized by using [`taskbarHeight`](../api/gantt/#taskbarheight) property. The following code example shows how to use the [`taskbarHeight`](../api/gantt/#taskbarheight) property.

{% tab template= "gantt/appearance-customization" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :taskbarHeight="taskbarHeight" :rowHeight="rowHeight"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
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
            isParent:true,
            subtasks: [
                { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 0, Progress: 50,isParent:false },
                { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50, resources: [2, 3, 5],isParent:false   },
                { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 4,Predecessor:"2FS", Progress: 50,isParent:false  },
            ]
        },
        {
            TaskID: 5,
            TaskName: 'Project Estimation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            isParent:true,
            subtasks: [
                { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50, resources: [4],isParent:false  },
                { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50, resources: [4, 8],isParent:false  },
                { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: 0,Predecessor:"6SS", Progress: 50, resources: [12, 5],isParent:false  }
            ]
        },
    ],
            height: '450px',
            taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        taskbarHeight:60,
        rowHeight: 60
      };
  },
};
</script>

```

{% endtab %}

> NOTE
The [`taskbarHeight`](../api/gantt/#taskbarheight) value should be lower than [`rowHeight`](../api/gantt/#rowheight) property value and these properties accept only pixel values.

### Taskbar template

You can design your own taskbars to view the tasks in Gantt using the [`taskbarTemplate`](../api/gantt/#taskbartemplate) property. You can customize the parent taskbars and milestones with custom templates using the [`parentTaskbarTemplate`](../api/gantt/#parenttaskbartemplate) and [`milestoneTemplate`](../api/gantt/#milestonetemplate) properties.

{% tab template= "gantt/appearance-customization" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :rowHeight="rowHeight" :taskbarTemplate="taskbarTemplate" :parentTaskbarTemplate="parentTaskbarTemplate" :milestoneTemplate="milestoneTemplate"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
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
            isParent:true,
            subtasks: [
                { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 0, Progress: 50,isParent:false },
                { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50, resources: [2, 3, 5],isParent:false   },
                { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 4,Predecessor:"2FS", Progress: 50,isParent:false  },
            ]
        },
        {
            TaskID: 5,
            TaskName: 'Project Estimation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            isParent:true,
            subtasks: [
                { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50, resources: [4],isParent:false  },
                { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50, resources: [4, 8],isParent:false  },
                { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: 0,Predecessor:"6SS", Progress: 50, resources: [12, 5],isParent:false  }
            ]
        },
    ],
            height: '450px',
            taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        rowHeight:75,
        taskbarTemplate: function() {
            return { template : Vue.component('taskbarTemplate',{
                template: `<div class="e-gantt-child-taskbar e-custom-moments"
                style="height:100%;border-radius:5px;">
                <span class="e-task-label" style="position:absolute;top:5px;font-size:12px;text-overflow:ellipsis;height:90%;overflow:hidden;">{{data.TaskName}}</span>
                </div>`,
                    data: function() {
                        return {
                                data: {}
                        }
                    },
            })}
        },
        parentTaskbarTemplate: function() {
            return { template : Vue.component('parentTaskbarTemplate',{
                template: `
                <div class="e-gantt-child-taskbar e-custom-parent" style="height:100%;border-radius:5px;">
                    <span class="e-task-label" style="position:absolute;top:5px;font-size:12px;text-overflow:ellipsis;height:90%;overflow:hidden;">{{data.TaskName}}</span>
                    </div>`,
                    data: function() {
                        return {
                            data: {}
                        }
                    },
          })}
        },
        milestoneTemplate: function() {
        return { template : Vue.component('milestoneTemplate',{
                template: `<div class="e-gantt-milestone" style="position:absolute;">
                                <div class="e-milestone-top" style="border-right-width:26px; margin-top: -9px;border-left-width:26px;border-bottom-width:26px;"></div>
                                <div class="e-milestone-bottom" style="top:26px;border-right-width:26px; border-left-width:26px; border-top-width:26px;"></div>
                            </div>`,
                    data: function() {
                        return {
                            data: {}
                        }
                    },
          })}
        },
      };
  },
};
</script>

<style>
.e-custom-parent {
  background-color: #6d619b;
  border: 1px solid #3f51b5;
}

.e-custom-moments {
  background-color: #7ab748;
  border: 1px solid #3f51b5;
}

.e-custom-performance {
  background-color: #ad7a66;
  border: 1px solid #3f51b5;
}
#taskbarTemplate .e-milestone-top {
  border-bottom-color: #7ab748 !important;
  border-bottom: 1px solid #3f51b5;
}

#taskbarTemplate .e-milestone-bottom {
  border-top-color: #7ab748 !important;
  border-top: 1px solid #3f51b5;
}
</style>

```

{% endtab %}

### Conditional formatting

The default taskbar UI can be replaced with custom templates by using the [`queryTaskbarInfo`](../api/gantt/iQueryTaskbarInfoEventArgs) event. The following code example shows customizing the taskbar UI based on task progress values in Gantt component.

{% tab template= "gantt/appearance-customization" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :queryTaskbarInfo = "queryTaskbarInfo"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
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
            isParent:true,
            subtasks: [
                { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 0, Progress: 50,isParent:false },
                { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 70, resources: [2, 3, 5],isParent:false   },
                { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 4,Predecessor:"2FS", Progress: 50,isParent:false  },
            ]
        },
        {
            TaskID: 5,
            TaskName: 'Project Estimation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            isParent:true,
            subtasks: [
                { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50, resources: [4],isParent:false  },
                { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 80, resources: [4, 8],isParent:false  },
                { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: 0,Predecessor:"6SS", Progress: 70, resources: [12, 5],isParent:false  }
            ]
        },
    ],
            height: '450px',
            taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            progress: 'Progress',
            child: 'subtasks'
        },
        queryTaskbarInfo: function(args) {
            if (args.data.Progress == 50) {
                    args.progressBarBgColor = "red";
                } else if (args.data.Progress == 70) {
                    args.progressBarBgColor = "yellow";
                } else if (args.data.Progress == 80) {
                    args.progressBarBgColor = "lightgreen";
                }
            }
  };
},
};
</script>

```

{% endtab %}

## Task labels

The Gantt component maps any data source fields to task labels using the [`labelSettings.leftLabel`](../api/gantt/labelSettings/#leftlabel), [`labelSettings.rightLabel`](../api/gantt/labelSettings/#rightlabel), and [`labelSettings.taskLabel`](../api/gantt/labelSettings/#tasklabel) properties. You can customize the task labels with templates.

{% tab template= "gantt/appearance-customization" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :height = "height" :taskFields = "taskFields" :labelSettings="labelSettings" :projectStartDate="projectStartDate" :projectEndDate="projectEndDate"></ejs-gantt>
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
            labelSettings: {
            leftLabel: 'Task ID: ${taskData.TaskID}',
            rightLabel:'Progress Value: ${taskData.Progress}'
            taskLabel: '${Progress}%'
        },
        projectStartDate: new Date('03/28/2019'),
        projectEndDate: new Date('04/14/2019'),
      };
  },
};
</script>

```

{% endtab %}

## Connector lines

The width and background color of connector lines in Gantt can be customized using the [`connectorLineWidth`](../api/gantt/#connectorlinewidth) and [`connectorLineBackground`](../api/gantt/#connectorlinebackground) properties. The following code example shows how to use these properties.

{% tab template= "gantt/appearance-customization" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :connectorLineBackground="connectorLineBackground" :connectorLineWidth="connectorLineWidth"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
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
                { TaskID: 2, TaskName: 'Identify Site location', StartDate: new Date('04/02/2019'), Duration: 0, Progress: 50 },
                { TaskID: 3, TaskName: 'Perform Soil test', StartDate: new Date('04/02/2019'), Duration: 4, Progress: 50  },
                { TaskID: 4, TaskName: 'Soil test approval', StartDate: new Date('04/02/2019'), Duration: 4,Predecessor:"2FS", Progress: 50 },
            ]
        },
        {
            TaskID: 5,
            TaskName: 'Project Estimation',
            StartDate: new Date('04/02/2019'),
            EndDate: new Date('04/21/2019'),
            subtasks: [
                { TaskID: 6, TaskName: 'Develop floor plan for estimation', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 },
                { TaskID: 7, TaskName: 'List materials', StartDate: new Date('04/04/2019'), Duration: 3, Progress: 50 },
                { TaskID: 8, TaskName: 'Estimation approval', StartDate: new Date('04/04/2019'), Duration: 0,Predecessor:"6SS", Progress: 50 }
            ]
        },
    ],
            height: '450px',
            taskFields: {
            id: 'TaskID',
            name: 'TaskName',
            startDate: 'StartDate',
            duration: 'Duration',
            dependency:'Predecessor',
            progress: 'Progress',
            child: 'subtasks'
        },
        connectorLineBackground:"red",
        connectorLineWidth:3
      };
  },
};
</script>

```

{% endtab %}

## Customize rows and cells

While rendering the TreeGrid part in Gantt, the [`rowDataBound`](../api/gantt/#rowdatabound) and [`queryCellInfo`](../api/gantt/#querycellinfo) events trigger for every row and cell. Using these events, you can customize the rows and cells. The following code example shows how to customize the cell and row elements using these events.

{% tab template= "gantt/appearance-customization" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :columns = "columns" :splitterSettings = "splitterSettings" :rowDataBound = "rowDataBound"  :queryCellInfo = 'queryCellInfo'></ejs-gantt>
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
            dependency:'Predecessor',
            progress: 'Progress',
            child: 'subtasks'
        },
        columns: [
            { field: 'TaskID', headerText: 'Task ID', textAlign: 'Left', width: '100' },
            { field: 'TaskName', headerText: 'Task Name', width: '150' },
            { field: 'Progress', headerText: 'Progress', width: '150' },
            { field: 'StartDate', headerText: 'Start Date', width: '150' },
            { field: 'Duration', headerText: 'Duration', width: '150' },
        ],
        splitterSettings:{
            columnIndex:3
            },
            queryCellInfo: function (args) {
                if (args.column.field == "Progress") {
                    if (args.data.Progress < 25)
                  args.cell.style.backgroundColor="lightgreen"
               else
                  args.cell.style.backgroundColor="yellow"
            }
        },
        rowDataBound: function (args) {
             if(args.data.TaskID==4)
             args.row.style.backgroundColor="red"
             }
      };
  },
};
</script>

```

{% endtab %}

## Grid lines

In Gantt component, you can show or hide the grid lines in the TreeGrid side and chart side by using the [`gridLines`](../api/gantt/#gridlines) property.

The following options are available in Gantt component for rendering grid lines,

* Horizontal: The horizontal grid lines alone will be visible.
* Vertical: The vertical grid lines alone will be visible.
* Both: Both the horizontal and vertical grid lines will be visible on the TreeGrid and chart sides.
* None: Gridlines will not be visible on TreeGird and chart sides.

> By default, the [`gridLines`](../api/gantt/#gridLines) property is set with `Horizontal` type.

The following code example shows how to change the gridlines rendering mode in the Gantt component.

{% tab template= "gantt/appearance-customization" %}

```html

<template>
     <div>
        <ejs-gantt ref='gantt' id="GanttContainer" :dataSource="data" :height = "height" :taskFields = "taskFields" :gridLines="gridLines"></ejs-gantt>
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
            gridLines : 'Both',
      };
  },
};
</script>

```

{% endtab %}

## Splitter

In the Gantt component, the Splitter separates the TreeGrid section from the Chart section. You can change the position of the Splitter when loading the Gantt component using the [`splitterSettings`](../api/gantt/splitterSettings/) property. By splitting the TreeGrid from the chart, the width of the TreeGrid and chart sections will vary in the component. The [`splitterSettings.position`](../api/gantt/splitterSettings/#position) property denotes the percentage of the TreeGrid section’s width to be rendered and this property supports both pixels and percentage values. You can define the splitter position as column index value using the [`splitterSettings.columnIndex`](../api/gantt/splitterSettings/#columnindex) property. You can also define the splitter position with built-in splitter view modes by using the [`splitterSettings.view`](../api/gantt/splitterSettings/#view) property. The following list is the possible values for this property:

* `Default`: Shows Grid side and Gantt side.
* `Grid`: Shows Grid side alone in Gantt.
* `Chart`: Shows chart side alone in Gantt.

{% tab template="gantt/appearance-customization" %}

```html

<template>
     <div>
        <ejs-gantt id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height" :splitterSettings="splitterSettings"></ejs-gantt>
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
            splitterSettings:{
                position: "50%"
                },
        };
    },
};
</script>

```

{% endtab %}

## Change splitter position dynamically

In Gantt, we can change the splitter position dynamically by using [`setSplitterPosition`](../api/gantt/#setsplitterposition) method. Either We can change the splitter position with splitter position or columnIndex values by passing these values as arguments to [`setSplitterPosition`](../api/gantt/#setsplitterposition) method. The following code example shows how to use this methods.

{% tab template="gantt/appearance-customization" %}

```html

<template>
     <div>
        <ejs-button id="changebypostion" cssClass="e-info" v-on:click.native="changep">Change By Postion</ejs-button>
        <br><br><br>
        <ejs-button id="changebyindex" cssClass="e-info" v-on:click.native="changei">Change By Index</ejs-button>
        <br><br><br>
        <table>
            <tr>
                <td style="width: 70%">
                    <ejs-dropdownlist id="splitter-type" value='Default' :dataSource="dataSource" :fields = "fields" :change ="change"> Splitter View </ejs-dropdownlist>
                </td>
            </tr>
        </table>
        <ejs-gantt id="GanttContainer" :dataSource="data" :taskFields = "taskFields" :height = "height"></ejs-gantt>
    </div>
</template>
<script>
import Vue from "vue";
import { GanttPlugin } from "@syncfusion/ej2-vue-gantt";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
import { editingData  } from './data-source.js';
Vue.use(GanttPlugin);
Vue.use(ButtonPlugin);
Vue.use(DropDownListPlugin);
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
            dataSource: [
            { id: 'Default', mode: 'Default' },
            { id: 'Grid', mode: 'Grid' },
            { id: 'Chart', mode: 'Chart' },
          ],
        fields: { text: 'mode', value: 'id' },
        };
    },
    methods: {
        changep: function(e){
            var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
            ganttChart.setSplitterPosition('50%', 'position');
        }

        changei: function(e){
            var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
            ganttChart.setSplitterPosition(1, 'columnIndex');
        }

        change: function (e) {
            var ganttChart = document.getElementById('GanttContainer').ej2_instances[0];
            var viewType = e.value;
            ganttChart.setSplitterPosition(viewType, 'view');
        }

    },
};
</script>

```

{% endtab %}