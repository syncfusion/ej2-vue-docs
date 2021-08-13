---
title: "Enable editing in single click"
component: "Grid"
description: "Learn how to enable single click editing in the Essential JS 2 DataGrid control."
---

# Enable editing in single click

## Normal Editing

You can make a row editable on a single click with **Normal** mode of editing in Grid, by using the [`startEdit`](../../api/grid/#startedit) and [`endEdit`](../../api/grid/#endedit) methods.

Bind the **mouseup** event for Grid and in the event handler call the [`startEdit`](../../api/grid/#startedit) and [`endEdit`](../../api/grid/#endedit), based on the clicked target element.

{% tab template="grid/edit/single-click" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' id='grid' :dataSource='data' :load='load' :editSettings='editSettings' :toolbar='toolbar' :allowPaging="true">
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100 :isPrimaryKey='true'></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Right' width=120 format='C2'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Edit  } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data: function() {
    return {
      data: data,
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
       toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
  },
  methods: {
      load: function() {
        this.$refs.grid.ej2Instances.element.addEventListener('mouseup', function(e) {
            var instance = this.ej2_instances[0];
            if (e.target.classList.contains("e-rowcell")) {
            if (instance.isEdit)
                instance.endEdit();
                let index = parseInt(e.target.getAttribute("Index"));
                instance.selectRow(index);
                instance.startEdit();
            };
        });
      }
  },
  provide: {
    grid: [Edit]
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### Open dropdown edit popup on single click

You can open the default dropdown edit popup with single click edit by focusing the dropdown element and calling the EJ2 dropdown list's [`showPopup`](../../api/drop-down-list/#showpopup) method in the Grid's [`actionComplete`](../../api/grid/#actioncomplete) event. In this demo we have used a global flag variable in the **mouseup** event to ensure if the dropdown column is the clicked edit target.

{% tab template="grid/edit/single-click" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' id='grid' :dataSource='data' :load='load' :actionComplete='onActionComplete' :editSettings='editSettings' :toolbar='toolbar' :allowPaging="true">
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100 :isPrimaryKey='true'></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Right' width=120 format='C2'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' editType='dropdownedit' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Edit  } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data: function() {
    return {
      data: data,
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
       toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
       isDropdown: false
    };
  },
  methods: {
      load: function() {
        this.$refs.grid.ej2Instances.element.addEventListener('mouseup', function(e) {
            if (e.target.classList.contains("e-rowcell")) {
              if (this.$refs.grid.ej2Instances.isEdit)
                  this.$refs.grid.ej2Instances.endEdit();
              let rowInfo = this.$refs.grid.ej2Instances.getRowInfo(e.target);
              if (rowInfo.column.field === "ShipCountry")
                  this.isDropdown = true;
              this.$refs.grid.ej2Instances.selectRow(rowInfo.rowIndex);
              this.$refs.grid.ej2Instances.startEdit();
        }.bind(this));
      },
      onActionComplete: function(args) {
        if (args.requestType =="beginEdit" && this.isDropdown) {
            this.isDropdown = false;
            let dropdownObj = args.form.querySelector('.e-dropdownlist').ej2_instances[0];
            dropdownObj.element.focus();
            dropdownObj.showPopup();
        }
    }
  },
  provide: {
    grid: [Edit]
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Batch Editing

You can make a cell editable on a single click with **Batch** mode of editing in Grid, by using the [`editCell`](../../api/grid/edit/#editcell) method.

Bind the **mouseup** event for Grid and in the event handler call the [`editCell`](../../api/grid/edit/#editcell) method, based on the clicked target element.

{% tab template="grid/edit/single-click" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' id='grid' :dataSource='data' :load='load' :editSettings='editSettings' :toolbar='toolbar' :allowPaging="true">
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100 :isPrimaryKey='true'></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Right' width=120 format='C2'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Edit  } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data: function() {
    return {
      data: data,
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Batch' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
  },
  methods: {
      load: function() {
        this.$refs.grid.ej2Instances.element.addEventListener('mouseup', function(e) {
          var instance = this.ej2_instances[0];
          if (e.target.classList.contains("e-rowcell")) {
            let index = parseInt(e.target.getAttribute("Index"));
            let colindex = parseInt(e.target.getAttribute("aria-colindex"));
            let field = instance.getColumns()[colindex].field;
            instance.editModule.editCell(index, field);
          };
        });
      }
  },
  provide: {
    grid: [Edit]
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}