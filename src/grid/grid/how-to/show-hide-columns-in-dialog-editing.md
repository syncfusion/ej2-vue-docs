---
title: "Show or Hide columns in Dialog editing"
component: "Grid"
description: "Learn how to Show or Hide columns in Dialog editing."
---

# Show or Hide columns in Dialog editing

You can show hidden columns or hide visible column's editor in the dialog while editing the grid record using [`actionBegin`](../../api/grid/#actionbegin) and [`actionComplete`](../../api/grid/#actioncomplete) events.

In the `actionBegin` event, based on `requestType` as `beginEdit` or  `add`. We can show or hide the editor by using `column.visible` property.

In the `actionComplete` event, based on `requestType` as `save`. We can reset the properties back to the column state.

In the below example, we have rendered the grid columns `CustomerID` as hidden column and `ShipCountry` as visible column. In the edit mode, we have changed the `CustomerID` column to visible state and `ShipCountry` column to hidden state.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px' :actionBegin = 'actionBegin' :actionComplete = 'actionComplete'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='CustomerID' :visible = 'false' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign= 'Right' editType= 'numericedit' width=120 format= 'C2'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Dialog' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
  },
  methods: {
    actionBegin(args) {
        if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {
            for (var i = 0; i < this.$refs.grid.getColumns().length; i++) {
                if (this.$refs.grid.getColumns()[i].field == "CustomerID") {
                    this.$refs.grid.getColumns()[i].visible = true;
                }
                else if (this.$refs.grid.getColumns()[i].field == "ShipCountry") {
                    this.$refs.grid.getColumns()[i].visible = false;
                }
            }
        }
    }
    actionComplete(args) {
        if ((args.requestType === 'save')) {
            for (var i = 0; i < this.$refs.grid.getColumns().length; i++) {
                if (this.$refs.grid.getColumns()[i].field == "CustomerID") {
                    this.$refs.grid.getColumns()[i].visible = false;
                }
                else if (this.$refs.grid.getColumns()[i].field == "ShipCountry") {
                    this.$refs.grid.getColumns()[i].visible = true;
                }
            }
        }
    }
  },
  provide: {
    grid: [Page, Edit, Toolbar]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

{% endtab %}
