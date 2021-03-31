---
title: "Kanban drag and drop"
component: "Kanban"
description: "This article explains how to drag and drop the card information from an external source and vice versa."
---

# Drag and drop

All cards can be dragged and dropped across the columns or within the columns or swimlane row or kanban to an external source and vice versa.

The following drag and drop types are available in the Kanban board.

* Internal drag and drop
    * Column drag and drop
    * Swimlane drag and drop
* External drag and drop
    * Kanban to Kanban
    * Kanban to External source and vice versa.

> Dropped card position varies based on the `sortSettings` property.

## Internal drag and drop

Allows the user to drag and drop the cards within the kanban board. Based on this, we can categorize into two ways.

* Column drag and drop
* Swimlane drag and drop

### Column drag and drop

By default, all cards can be dragged and dropped across the columns and within the columns. You cannot drag and drop the cards when disabling the `allowDragAndDrop` property.

> You can prevent the drag or drop behavior of the particular column by disabling the `allowDrag` or `allowDrop` property.
> You can also control the flow of transition cards between the columns by using the `transitionColumns` property.

In the following example, disable the drag and drop behavior on the Kanban board.

{% tab template="kanban/drag-and-drop", iframeHeight="588px" %}

```html
<template>
  <div id="app">
       <ejs-kanban id="kanban" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :allowDragAndDrop="false">
          <e-columns>
            <e-column headerText="To Do" keyField="Open"></e-column>
            <e-column headerText="In Progress" keyField="InProgress"></e-column>
            <e-column headerText="Testing" keyField="Testing"></e-column>
            <e-column headerText="Done" keyField="Close"></e-column>
          </e-columns>
        </ejs-kanban>
  </div>
</template>

<script>
import Vue from "vue";
import { KanbanPlugin } from '@syncfusion/ej2-vue-kanban';
import { extend } from '@syncfusion/ej2-base';
import { kanbanData } from './datasource.js';
Vue.use(KanbanPlugin);
export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id"
      }
    };
  },
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-kanban/styles/material.css';
</style>

```

{% endtab %}

### Swimlane drag and drop

By default, Swimlane allows drag and drop across the columns within the swimlane row. Kanban does not allow dragging the cards across the swimlane rows.

Enabling the `dragAndDrop` property allows you to drag the cards across the swimlane rows, which is specified inside the `swimlaneSettings` property.

{% tab template="kanban/swimlane-drag-and-drop", iframeHeight="588px" %}

```html

<template>
  <div id="app">
       <ejs-kanban id="kanban" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :swimlaneSettings="swimlaneSettings">
          <e-columns>
            <e-column headerText="To Do" keyField="Open"></e-column>
            <e-column headerText="In Progress" keyField="InProgress"></e-column>
            <e-column headerText="Testing" keyField="Testing"></e-column>
            <e-column headerText="Done" keyField="Close"></e-column>
          </e-columns>
        </ejs-kanban>
  </div>
</template>

<script>
import Vue from "vue";
import { KanbanPlugin } from '@syncfusion/ej2-vue-kanban';
import { extend } from '@syncfusion/ej2-base';
import { kanbanData } from './datasource.js';
Vue.use(KanbanPlugin);
export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id",
      },
      swimlaneSettings: {
        keyField: 'Assignee',
        allowDragAndDrop: true
      }
    };
  },
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-kanban/styles/material.css';
</style>

```

{% endtab %}

## External drag and drop

Allows the user to drag and drop the cards from one kanban to another kanban or Kanban to an external source and vice versa.

### Kanban to kanban

Drag and drop the card from one kanban to another kanban and vice versa. This can be achieved by specifying the `externalDropId` property which is used to specify the id of the dropped kanban element and the `dragStop` event which is used to delete the card on dragged Kanban and add the card on dropped Kanban using the `deleteCard` and `addCard` public methods.

> Before adding a card to dropped kanban, you can manually change the card data `headerField` when the same card data `headerField` is dropped to another Kanban.

In the following example, Drag the card from one Kanban and drop it into another kanban using the `dragStop` event. In this event, remove the card from the dragged Kanban by using the `deleteCard` public method and add the card to the dropped Kanban by using the `addCard` public method.

{% tab template="kanban/kanban-to-kanban", iframeHeight="588px" %}

```html
<template>
  <div id="app">
  <table>
  <tbody>
    <tr>
      <td>
        <h4>Kanban A</h4>
       <ejs-kanban id="kanbanA" ref="kanbanObjA" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :externalDropId='externalKanbanADropId' :dragStop="kanbanDragStopA">
          <e-columns>
            <e-column headerText="To Do" keyField="Open"></e-column>
            <e-column headerText="Done" keyField="Close"></e-column>
          </e-columns>
        </ejs-kanban>
         </td>
      <td>
        <h4>Kanban B</h4>
        <ejs-kanban id="kanbanB" ref="kanbanObjB" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :externalDropId='externalKanbanBDropId' :dragStop="kanbanDragStopB">
          <e-columns>
            <e-column headerText="To Do" keyField="Open"></e-column>
           <e-column headerText="Done" keyField="Close"></e-column>
          </e-columns>
        </ejs-kanban>
        </td>
    </tr>
  </tbody>
</table>
  </div>
</template>

<script>
import Vue from "vue";
import { KanbanPlugin } from '@syncfusion/ej2-vue-kanban';
import { extend, closest } from '@syncfusion/ej2-base';
import { kanbanData } from './datasource.js';
Vue.use(KanbanPlugin);
export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id"
      },
      externalKanbanADropId: ['#kanbanA'],
      externalKanbanBDropId: ['#kanbanB']
    };
  },
   methods: {
      kanbanDragStopA: function (args) {
          let kanbanBElement = closest(args.event.target as Element, '#kanbanB');
          let kanbanObjA = this.$refs.kanbanObjA.ej2Instances;
          let kanbanObjB = this.$refs.kanbanObjB.ej2Instances;
          if (kanbanBElement) {
            kanbanObjA.deleteCard(args.data);
            args.data.forEach((card, i) => {
                const index = kanbanObjB.kanbanData.findIndex((colData) =>
                    colData[kanbanObjB.cardSettings.headerField] === card[kanbanObjB.cardSettings.headerField]);
                if (index !== -1) {
                    card[kanbanObjB.cardSettings.headerField] = Math.max(...kanbanObjB.kanbanData.map(
                        (obj) => parseInt(obj[kanbanObjB.cardSettings.headerField], 10))) + ++i;
                }
            });
            kanbanObjB.addCard(args.data, args.dropIndex);
            args.cancel = true;
        }
      },
      kanbanDragStopB: function (args) {
        let kanbanAElement = closest(args.event.target, '#kanbanA');
        let kanbanObjA = this.$refs.kanbanObjA.ej2Instances;
        let kanbanObjB = this.$refs.kanbanObjB.ej2Instances;
        if (kanbanAElement) {
            kanbanObjB.deleteCard(args.data);
            args.data.forEach((card, i) => {
            const index = kanbanObjA.kanbanData.findIndex((colData) =>
                colData[kanbanObjA.cardSettings.headerField] === card[kanbanObjA.cardSettings.headerField]);
            if (index !== -1) {
                card[kanbanObjA.cardSettings.headerField] = Math.max(...kanbanObjA.kanbanData.map(
                    (obj) => parseInt(obj[kanbanObjA.cardSettings.headerField], 10))) + ++i;
            }
        });
        kanbanObjA.addCard(args.data, args.dropIndex);
        args.cancel = true;
        }
      }
   }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-kanban/styles/material.css';
</style>

```

{% endtab %}

### Treeview to Kanban

Drag the card from the Kanban board and drop it to the Treeview component and vice versa.

In the following sample, remove the data from the Kanban board using the `deleteCard` public method and add to the Treeview component using the `addNodes` public method at Kanban `dragStop` event when dragging the card and dropping it to the Treeview component. Remove the data from Treeview using the `removeNodes` public method and add to Kanban board using the `openDialog` public method when dragging the list from the Treeview component and dropping it to the kanban board.

{% tab template="kanban/kanban-to-treeview", iframeHeight="588px" %}

```html
<template>
  <div id="app">
  <table>
  <tbody>
    <tr>
      <td>
        <h4>Kanban</h4>
       <ejs-kanban id="kanban" ref="kanbanObj" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :externalDropId='externalKanbanADropId' :dragStop="kanbanDragStop">
          <e-columns>
            <e-column headerText="To Do" keyField="Open"></e-column>
            <e-column headerText="Done" keyField="Close"></e-column>
          </e-columns>
        </ejs-kanban>
         </td>
      <td>
        <h4>TreeView</h4>
            <ejs-treeview id='treeView' ref="treeViewObj" :nodeTemplate="treeTemplate" :fields='treeViewFields' :allowDragAndDrop=true :nodeDragStop="onTreeDragStop"></ejs-treeview>
        </td>
    </tr>
  </tbody>
</table>
</div>
</template>

<script>
import Vue from "vue";
import { KanbanPlugin } from '@syncfusion/ej2-vue-kanban';
import { extend, closest } from '@syncfusion/ej2-base';
import { kanbanData, treeViewData } from './datasource.js';
Vue.use(KanbanPlugin);
import { TreeViewPlugin } from "@syncfusion/ej2-vue-navigations";
Vue.use(TreeViewPlugin);

 var treeVue = Vue.component("tree-template", {
        template: '<div id="treelist"><div id="treeviewlist">{{Id}} - {{Status}}</div></div>',
        data() {
            return {
                data: {}
            };
        }
    });
export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id"
      },
      externalKanbanDropId: ['#treeView'],
      treeViewFields: { dataSource: treeViewData, id: 'Id', text: 'Status' },
      treeTemplate: function(e) {
          return { template: treeVue }
      }
    };
  },
   methods: {
      kanbanDragStop: function (args) {
          let treeViewElement = closest(args.event.target as Element, '#treeView');
          let kanbanObj = this.$refs.kanbanObj.ej2Instances;
          let treeObj = this.$refs.treeViewObj.ej2Instances;
          if (treeViewElement) {
            kanbanObj.deleteCard(args.data);
            treeObj.addNodes(args.data);
            args.cancel = true;
          }
      },
      onItemDrag: function (args) {
        let kanbanElement = closest(args.event.target as Element, '#kanban');
        let kanbanObj = this.$refs.kanbanObj.ej2Instances;
        let treeObj = this.$refs.treeViewObj.ej2Instances;
        if (kanbanElement) {
          let treeData =
            treeObj.fields.dataSource as { [key: string]: Object }[];
          const filteredData =
            treeData.filter((item) => item.Id === parseInt(args.draggedNodeData.id as string, 10));
          treeObj.removeNodes([args.draggedNodeData.id] as string[]);
          kanbanObj.openDialog('Add', filteredData[0]);
          args.cancel = true;
        }
      }
   }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-kanban/styles/material.css';
</style>

```

{% endtab %}

### Schedule to Kanban

Drag the card from the Kanban board and drop it to the Schedule component and vice versa.

In the following sample, remove the data from the Kanban board using the `deleteCard` public method and add to the schedule component using the `addNodes` public method at Kanban `dragStop` event when dragging the card and dropping it to the Treeview component. Remove the data from Treeview using the `removeNodes` public method and add to Kanban board using the `addCard` public method when dragging the list from the Treeview component and dropping it to the kanban board.

{% tab template="kanban/kanban-to-schedule", iframeHeight="588px" %}

```html
<template>
  <div id="app">
  <table>
  <tbody>
    <tr>
      <td>
        <h4>Kanban</h4>
       <ejs-kanban id="kanban" ref="kanbanObj" keyField="Status" :dataSource="kanbanData"
        :cardSettings="cardSettings" :externalDropId='externalKanbanADropId' :dragStop="kanbanDragStop">
          <e-columns>
            <e-column headerText="To Do" keyField="Open"></e-column>
            <e-column headerText="Done" keyField="Close"></e-column>
          </e-columns>
        </ejs-kanban>
         </td>
      <td>
        <h4>TreeView</h4>
          <ejs-schedule id='schedule' ref="scheduleObj" height="650px" :cssClass='cssClass' :selectedDate='selectedDate' :eventSettings='eventSettings'
                  :group='group' :currentView='currentView' :resourceHeaderTemplate='resourceHeaderTemplate' :dragStop="onItemDragStop">
                  <e-views>
                      <e-view option="TimelineDay"></e-view>
                      <e-view option="TimelineMonth"></e-view>
                  </e-views>
                  <e-resources>
                      <e-resource field='DepartmentID' title='Department' name='Departments' :dataSource='departmentDataSource'
                          textField='Text' idField='Id' colorField='Color'>
                      </e-resource>
                      <e-resource field='ConsultantID' title='Consultant' name='Consultants' :dataSource='consultantDataSource'
                          textField='Text' idField='Id' groupIDField='GroupId' colorField='Color'>
                      </e-resource>
                  </e-resources>
              </ejs-schedule>
        </td>
    </tr>
  </tbody>
</table>
</div>
</template>

<script>
import Vue from "vue";
import { KanbanPlugin } from '@syncfusion/ej2-vue-kanban';
import { extend, closest } from '@syncfusion/ej2-base';
import { kanbanData, treeViewData } from './datasource.js';
Vue.use(KanbanPlugin);
import { SchedulePlugin, TimelineViews, TimelineMonth, View, Resize, DragAndDrop } from "@syncfusion/ej2-vue-schedule";
Vue.use(SchedulePlugin);

var resourceHeaderVue = Vue.component("resource-headerTemplate", {
      template: '<div className="template-wrap"><div class="specialist-category"><div v-if=getConsultantImageName(data)><img class="specialist-image" :src="getImage" :alt="getImage"/></div><div class="specialist-name">' +
                '{{getConsultantName(data)}}</div><div class="specialist-designation">{{getConsultantDesignation(data)}}</div></div></div>',
      data() {
          return {
              data: {}
          };
      },
      computed: {
          getImage: function() {
              return './source/schedule/images/' + this.getConsultantName(this.data).toLowerCase() + '.png';
          }
      },
      methods: {
          getConsultantName: function (data) {
              let value = JSON.parse(JSON.stringify(data));
              return (value.resourceData) ? value.resourceData[value.resource.textField] : value.resourceName;
          },
          getConsultantImageName: function (data) {
              let value = JSON.parse(JSON.stringify(data));
              let resourceName = (value.resourceData) ? value.resourceData[value.resource.textField] : value.resourceName;
              if (resourceName === 'GENERAL' || resourceName === 'DENTAL') {
                  return false;
              } else {
                  return true;
              }
          },
          getConsultantDesignation: function (data) {
              let value = JSON.parse(JSON.stringify(data));
              var resourceName = value.resourceData[value.resource.textField];
              if (resourceName === "GENERAL" || resourceName === "DENTAL") {
                  return '';
              } else {
                  return value.resourceData.Designation;
              }
          }
      }
});

export default {
  data: function() {
    return {
      kanbanData: extend([], kanbanData, null, true),
      cardSettings: {
        contentField: "Summary",
        headerField: "Id"
      },
      externalKanbanDropId: ['#schedule'],
      eventSettings: {
          dataSource: extend([], scheduleData, null, true),
          fields: {
              subject: { title: 'Patient Name', name: 'Name' },
              startTime: { title: "From", name: "StartTime" },
              endTime: { title: "To", name: "EndTime" },
              description: { title: 'Reason', name: 'Description' }
          },
      },
      selectedDate: new Date(2018, 7, 1),
      currentView: 'TimelineDay',
      cssClass: 'schedule-drag-drop',
      group: {
          enableCompactView: false,
          resources: ['Departments', 'Consultants']
      },
      departmentDataSource: [
          { Text: 'GENERAL', Id: 1, Color: '#bbdc00' },
          { Text: 'DENTAL', Id: 2, Color: '#9e5fff' }
      ],
      consultantDataSource: [
          { Text: 'Alice', Id: 1, GroupId: 1, Color: '#bbdc00', Designation: 'Cardiologist' },
          { Text: 'Nancy', Id: 2, GroupId: 2, Color: '#9e5fff', Designation: 'Orthodontist' },
          { Text: 'Robert', Id: 3, GroupId: 1, Color: '#bbdc00', Designation: 'Optometrist' },
          { Text: 'Robson', Id: 4, GroupId: 2, Color: '#9e5fff', Designation: 'Periodontist' },
          { Text: 'Laura', Id: 5, GroupId: 1, Color: '#bbdc00', Designation: 'Orthopedic' },
          { Text: 'Margaret', Id: 6, GroupId: 2, Color: '#9e5fff', Designation: 'Endodontist' }
      ],
      resourceHeaderTemplate: function (e) {
          return { template: resourceHeaderVue }
      },
    };
  },
  methods: {
     kanbanDragStop: function (args) {
        let scheduleElement: Element = closest(args.event.target as Element, '#schedule');
        let kanbanObj = this.$refs.kanbanObj.ej2Instances;
        let scheduleObj = this.$refs.scheduleObj.ej2Instances;
        if (scheduleElement) {
            kanbanObj.deleteCard(args.data);
            scheduleObj.openEditor(args.data[0], 'Add', true);
            args.cancel = true;
        }
      },
      onItemDragStop: function (args) {
        let kanbanElement: Element = closest(args.event.target as Element, '#kanban');
        let kanbanObj = this.$refs.kanbanObj.ej2Instances;
        let scheduleObj = this.$refs.scheduleObj.ej2Instances;
        if (kanbanElement) {
            scheduleObj.deleteEvent(args.data.Id);
             removeClass([scheduleObj.element.querySelector('.e-selected-cell')], 'e-selected-cell');
             kanbanObj.openDialog('Add', args.data);
             args.cancel = true;
        }
      }
   },
   provide: {
      schedule: [TimelineViews, TimelineMonth, Resize, DragAndDrop]
   }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-layouts/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-calendars/styles/material.css';
@import '../node_modules/@syncfusion/ej2-excel-export/styles/material.css';
@import '../node_modules/@syncfusion/ej2-file-utils/styles/material.css';
@import '../node_modules/@syncfusion/ej2-schedule/styles/material.css';
@import '../node_modules/@syncfusion/ej2-compression/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-kanban/styles/material.css';
</style>

```

{% endtab %}
