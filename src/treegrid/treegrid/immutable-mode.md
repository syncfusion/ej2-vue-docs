---
title: "Immutable"
component: "TreeGrid"
description: "Learn how to use immutable data in the Essential JS 2 TreeGrid control."
---

# Immutable Mode

The immutable mode optimizes the TreeGrid re-rendering performance by using the object reference and [`deep compare`](https://dmitripavlutin.com/how-to-compare-objects-in-javascript/#4-deep-equality) concept. When performing the TreeGrid actions, it will only re-render the modified or newly added rows and prevent the re-rendering of the unchanged rows.

To enable this feature, you have to set the [`enableImmutableMode`](../api/treegrid#enableimmutablemode) property as **true**.

> * This feature uses the primary key value for data comparison. So, you need to provide the [`isPrimaryKey`](../api/treegrid/column/#isprimarykey) column.

{% tab template="treegrid/immutable-mode/default" %}

```html
<template>
    <div id="app">
    <div id='container'>
        <table>
      <tbody>
        <tr>
          <td>
            <span id="immutableDelete"></span>
          </td>
        </tr>
        <tr>
          <td>
            <span id="normalDelete"></span>
          </td>
        </tr>
        <tr>
          <td>
            <div>
              <ejs-button cssClass="e-info" v-on:click.native="addTopEvent">Add row at top</ejs-button>
              <ejs-button cssClass="e-info" v-on:click.native="addBottomEvent">Add row at bottom</ejs-button>
              <ejs-button cssClass="e-info" v-on:click.native="deleteEvent">Delete 5 rows</ejs-button>
              <ejs-button cssClass="e-info" v-on:click.native="sortEvent">Sort Task ID</ejs-button>
              <ejs-button cssClass="e-info" v-on:click.native="pageEvent">Paging</ejs-button>
            </div>
          </td>
        </tr>
        <tr>
          <td>
        <span><b>Immutable TreeGrid</b></span>
        <ejs-treegrid ref="immutablegrid" :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' height=350 :allowPaging='true' :pageSettings='pageSettings' :editSettings='editSettings' :selectionSettings='selectionOptions' :enableImmutableMode='true' :beforeDataBound="immutableBeforeDataBound" :dataBound="immutableDataBound">
        <e-columns>
                <e-column field='taskID' :isPrimaryKey='true' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='200'></e-column>
                <e-column field='startDate' headerText='Start Date' textAlign='Right' width='90' format='yMd' type='date'></e-column>
                <e-column field='endDate' headerText='End Date' textAlign='Right' width='90' format='yMd' type='date'></e-column>
                <e-column field='duration' headerText='Duration' width='90' textAlign='Right'></e-column>
                <e-column field='priority' headerText='Priority' width='90' textAlign='Right'></e-column>
                <e-column field='approved' headerText='Approved' width='90' textAlign='Right'></e-column>
                </e-columns>
        </ejs-treegrid>
          </td>
          <td>
            <span><b>Normal TreeGrid</b></span>
        <ejs-treegrid ref="nomalgrid" :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' height=350 :allowPaging='true' :pageSettings='pageSettings' :editSettings='editSettings' :selectionSettings='selectionOptions' :enableImmutableMode='true'  :beforeDataBound="beforeDataBound" :dataBound="dataBound">
        <e-columns>
                <e-column field='taskID' :isPrimaryKey='true' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='200'></e-column>
                <e-column field='startDate' headerText='Start Date' textAlign='Right' width='90' format='yMd' type='date'></e-column>
                <e-column field='endDate' headerText='End Date' textAlign='Right' width='90' format='yMd' type='date'></e-column>
                <e-column field='duration' headerText='Duration' width='90' textAlign='Right'></e-column>
                <e-column field='priority' headerText='Priority' width='90' textAlign='Right'></e-column>
                <e-column field='approved' headerText='Approved' width='90' textAlign='Right'></e-column>
                </e-columns>
        </ejs-treegrid>
          </td>
        </tr>
      </tbody>
    </table>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Edit } from "@syncfusion/ej2-vue-treegrid";
import { sampleData, sampleData2, dataSource1 } from "./datasource.js";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(TreeGridPlugin);
Vue.use(ButtonPlugin);

if(sampleData2.length == 0){
  dataSource1();
}

export default {
  data() {
    return {
      data: sampleData2,
      pageSettings: { pageSize: 50 },
      selectionOptions: { type: 'Multiple' },
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Cell' },
      immutableStart: 0,
      normalStart: 0,
      immutableInit: true,
      init: true
    };
  },
  provide: {
    treegrid: [Page, Edit],
  },
  methods: {
    addTopEvent: function () {
      let immutableInstance = this.$refs.immutablegrid;
      let instance = this.$refs.nomalgrid;
      immutableInstance.addRecord(sampleData[0], 0, "Top");
      instance.addRecord(sampleData[0], 0, "Top");

    },
    addBottomEvent: function () {
      let immutableInstance = this.$refs.immutablegrid;
      let instance = this.$refs.nomalgrid;
      immutableInstance.addRecord(sampleData[0], 0, "Bottom");
      instance.addRecord(sampleData[0], 0, "Bottom");
    },
    deleteEvent: function () {
      let immutableInstance = this.$refs.immutablegrid;
      let instance = this.$refs.nomalgrid;
      immutableInstance.selectRows([0, 2, 4]);
      instance.selectRows([0, 2, 4]);
      immutableInstance.deleteRecord();
      instance.deleteRecord();

    },
    sortEvent: function () {
      let immutableInstance = this.$refs.immutablegrid;
      let instance = this.$refs.nomalgrid;
      let aData = immutableInstance.dataSource.reverse();
      immutableInstance.setProperties({ dataSource: aData });
      instance.setProperties({ dataSource: aData });
    },
    pageEvent: function () {
      let immutableInstance = this.$refs.immutablegrid;
      let instance = this.$refs.nomalgrid;
      let page = instance.ej2Instances.pageSettings.currentPage + 1;
      immutableInstance.goToPage(page);
      instance.goToPage(page);
    },
    immutableBeforeDataBound: function () {
      this.immutableStart = new Date().getTime();
    },
    immutableDataBound: function () {
      let val = this.immutableInit ? '' : new Date().getTime() - this.immutableStart;
      document.getElementById("immutableDelete").innerHTML =
        "Immutable rendering Time: " + "<b>" + val + "</b>" + "<b>ms</b>";
      this.immutableStart = 0; this.immutableInit = false;
    },
    beforeDataBound: function () {
      this.normalStart = new Date().getTime();
    },
    dataBound: function () {
      let val = this.init ? '' : new Date().getTime() - this.normalStart;
      document.getElementById("normalDelete").innerHTML =
        "Normal rendering Time: " + "<b>" + val + "</b>" + "<b>ms</b>";
      this.normalStart = 0; this.init = false;
    },
  },
};
</script>
<style>
.e-treegrid {
  pointer-events: none;
}
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Limitations

The following features are not supported in the immutable mode:

* Frozen rows and columns
* Row Template
* Detail Template
* Column reorder
* Virtualization