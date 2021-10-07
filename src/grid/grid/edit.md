---
title: "Editing"
component: "Grid"
description: "Learn how to perform CRUD operations in various edit modes, use different cell editors, and persist data on the server side in the Essential JS 2 DataGrid control."
---

# Editing

The Grid component has options to dynamically insert, delete and update records.
Editing feature requires a primary key column for CRUD operations.
To define the primary key, set [`columns.isPrimaryKey`](../api/grid/column/#isprimarykey) to **true** in particular column.

You can start the edit action either by double clicking the particular row or by selecting the required row and click on **Edit**
button in the toolbar. Similarly, you can add a new record to grid either by clicking on **Add** button in the toolbar
or on an external button which is bound to invoke the [`addRecord`](../api/grid/edit/#addrecord) method of the grid,
**Save** and **Cancel** while in edit mode is possible using respective toolbar icon in grid.

Deletion of the record is possible by selecting the required row and click on **Delete** button in the toolbar.

To use CRUD, inject the [`Edit`](../api/grid/edit/) module in the **provide** section.

To get start quickly with Edit Options, you can check on this video:

`youtube:VUWaKKppBEg`

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' height='315px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign= 'Right' width=120 format= 'C2'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Edit } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true }
    };
  },
  provide: {
    grid: [Page, Edit]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

{% endtab %}

> * If [`columns.isIdentity`](../api/grid/column/#isidentity) is enabled,
then it will be considered as a read-only column when editing and adding a record.
> * You can disable editing for a particular column, by specifying
[`columns.allowEditing`](../api/grid/column/#allowediting) to **false**.

## Toolbar with edit option

The grid toolbar has the [built-in items](./tool-bar#built-in-toolbar-items) to execute Editing actions.
You can define this by using the [`toolbar`](../api/grid/#toolbar) property.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' height='270' :toolbar='toolbar'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign= 'Right' width=120 format= 'C2'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' width=150></e-column>
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
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
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

## Cell edit type and its params

The [`columns.editType`](../api/grid/column/#edittype) is used to define the editor component for any particular column.
You can set the [`columns.editType`](../api/grid/column/#edittype) based on data type of the column.

* [`NumericTextBox`](../numerictextbox) component for integers, double, and decimal data types.

* [`TextBox`](../textbox) component for string data type.

* [`DropDownList`](../drop-down-list) component to show all unique values related to that field.

* [`Checkbox`](../check-box) component for boolean type.

* [`DatePicker`](../datepicker) component for date type.

Also, you can customize model of the [`columns.editType`](../api/grid/column/#edittype) component through the [`columns.edit.params`](../api/grid/column/#edit).

The following table describes cell edit type component and their corresponding edit params of the column.

Component |Example
-----|-----
[`NumericTextBox`](../numerictextbox) | params: { decimals: 2, value: 5 }
[`TextBox`](../textbox) | -
[`DropDownList`](../drop-down-list) | params: { value: 'Germany' }
[`DatePicker`](../datepicker) | params: { value: new Date()}
[`Checkbox`](../check-box) | params: { checked: true}

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign= 'Right' editType= 'numericedit' :edit='numericParams' width=120 format= 'C2'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' :edit='ddParams' width=150></e-column>
                <e-column field='ShippedDate' headerText='Shipped Date' editType= 'datepickeredit' :edit='dpParams' width=150></e-column>
                <e-column field='Verified' headerText='Verified' editType= 'booleanedit' :edit='boolParams' width=150></e-column>
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
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      numericParams: { params: { decimals: 2, value: 5 } },
      ddParams: { params: { value: 'Germany' } },
      dpParams: { params: {value: new Date() } },
      boolParams: { params: {checked: true } }
    };
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

> If edit type is not defined in the column, then it will be considered as the **stringedit** type (Textbox component).

## Cell Edit Template

The cell edit template is used to add a custom component for a particular column by invoking the following functions:

* **create** - It is used to create the element at the time of initialization.

* **write** - It is used to create custom component or assign default value at the time of editing.

* **read** - It is used to read the value from the component at the time of save.

* **destroy** - It is used to destroy the component.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign= 'Right' editType= 'numericedit' width=120 format= 'C2'></e-column>
                <e-column field='OrderDate' headerText='Order Date' type= 'date' format= 'yMd' :edit='dpParams' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { DatePicker } from '@syncfusion/ej2-calendars';
import { data } from './datasource.js';

Vue.use(GridPlugin);

let elem;
let datePickerObj;

export default {
  data() {
    return {
      data: data,
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      dpParams: {
            create: function() {
                elem = document.createElement('input');
                return elem;
            },
            read: () => {
                return datePickerObj.value;
            },
            destroy: () => {
                datePickerObj.destroy();
            },
            write: (args) => {
                datePickerObj = new DatePicker({
                    value: new Date(args.rowData[args.column.field]),
                    floatLabelType: 'Never'
                });
                datePickerObj.appendTo(elem);
            }
        }
    };
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

### Using template

The cell editor for a particular column can be specified using a Vue Component. The [`column.editTemplate`](../api/grid/column/#edittemplate) property used to define the corresponding column editor.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign= 'Right' editType= 'numericedit' width=120 format= 'C2'></e-column>
                <e-column field='OrderDate' headerText='Order Date' type='date' format= 'yMd' width=150 :editTemplate='editTemplate'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
import { DatePickerPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(GridPlugin);
Vue.use(DatePickerPlugin);

export default {
  data() {
    return {
      data: data,
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
  },
  methods: {
      editTemplate: function() {
          return {template: Vue.component('datePicker', {
              template: `<ejs-datepicker id="OrderDate" placeholder="Order Date" v-model="data.OrderDate" floatLabelType='Never'></ejs-datepicker>`,
              data() {
                  return {data:{}}
              }
          })}
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

## Edit Modes

Grid supports the following types of edit modes, they are:

* Normal
* Dialog
* Batch

### Normal

In Normal edit mode, when you start editing the currently selected record is changed to edit state.
You can change the cell values and save edited data to the data source.
To enable Normal edit, set the [`editSettings.mode`](../api/grid/editSettings/#mode) as **Normal**.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
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
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
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

> **Normal** edit mode is default mode of editing.

### Automatically update the column based on another column edited value

You can update the column value based on another column edited value by using the Cell Edit Template feature.

In the below demo, we have update the `TotalCost` column value based on the `UnitPrice` and `UnitInStock` column value while editing.

{% tab template="grid/edit/default" %}

```html

<template>
  <div id="app">
    <ejs-grid id="grid" :dataSource="data" :editSettings="editSettings" :toolbar="toolbar" height="273px">
      <e-columns>
        <e-column field="ProductID" headerText="Product ID" textAlign="Right" :isPrimaryKey="true" width="100"></e-column>
        <e-column field="ProductName" headerText="Product Name" width="120"></e-column>
        <e-column field="UnitPrice" headerText="Unit Price" editType="numericedit" :edit="priceParams"
          width="150" format="C2" textAlign="Right" ></e-column>
        <e-column field="UnitsInStock" headerText="Units In Stock" editType="numericedit"
          :edit="stockParams" width="150" textAlign="Right"></e-column>
        <e-column field="TotalCost" headerText="Total Cost" width="150" :allowEditing="false" format="C2" textAlign="Right" ></e-column>
      </e-columns>
    </ejs-grid>
  </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { NumericTextBox } from "@syncfusion/ej2-inputs";
import { productData } from "./datasource.js";

let priceElem, stockElem, priceObj, stockObj;
Vue.use(GridPlugin);
export default {
  data: () => {
    return {
      data: productData,
      toolbar: ["Add", "Edit", "Delete", "Update", "Cancel"],
      editSettings: {
        allowEditing: true,
        allowAdding: true,
        allowDeleting: true,
      },
      priceParams: {
        create: () => {
          priceElem = document.createElement("input");
          return priceElem;
        },
        read: () => {
          return priceObj.value;
        },
        destroy: () => {
          priceObj.destroy();
        },
        write: (args) => {
          priceObj = new NumericTextBox({
            value: args.rowData[args.column.field],
            change: function (args) {
              let formEle = document
                .getElementById("grid")
                .querySelector("form").ej2_instances[0];
              var totalCostFieldEle = formEle.getInputElement("TotalCost");
              totalCostFieldEle.value = priceObj.value * stockObj.value;
            },
          });
          priceObj.appendTo(priceElem);
        },
      },
      stockParams: {
        create: () => {
          stockElem = document.createElement("input");
          return stockElem;
        },
        read: () => {
          return stockObj.value;
        },
        destroy: () => {
          stockObj.destroy();
        },
        write: (args) => {
          stockObj = new NumericTextBox({
            value: args.rowData[args.column.field],
            change: function (args) {
              let formEle = document
                .getElementById("grid")
                .querySelector("form").ej2_instances[0];
              var totalCostFieldEle = formEle.getInputElement("TotalCost");
              totalCostFieldEle.value = priceObj.value * stockObj.value;
            },
          });
          stockObj.appendTo(stockElem);
        },
      },
    };
  },
  provide: {
    grid: [Edit, Toolbar],
  },
};
</script>

<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

{% endtab %}

#### Cancel edit based on condition

You can prevent the CRUD operations of the Grid by using condition in the [`actionBegin`](../api/grid/#actionbegin) event with requestType as `beginEdit` for editing, `add` for adding and `delete` for deleting actions.

In the below demo, we prevent the CRUD operation based on the `Role` column value. If the Role Column is ‘employee’, we are unable to edit/delete that row.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <button v-on:click="btnClick">Grid is Addable</button>
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' :actionBegin="actionBegin" height='240px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='Role' headerText='Role' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign= 'Right' editType= 'numericedit' width=120 format= 'C2'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { employeeData } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: employeeData,
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      isAddable: true
    };
  },
  methods: {
    actionBegin: function (args) {
      if (args.requestType === "beginEdit") {
        if (args.rowData["Role"].toLowerCase() == "employee") {
          args.cancel = true;
        }
      }
      if (args.requestType === "delete") {
        if (args.data[0]["Role"].toLowerCase() === "employee") {
          args.cancel = true;
        }
      }
      if (args.requestType === "add") {
        if (!this.isAddable) {
          args.cancel = true;
        }
      }
    },
    btnClick: function (args) {
      args.target.innerText === "Grid is Addable" ? (args.target.innerText = "Grid is Not Addable") : (args.target.innerText = "Grid is Addable");
      this.isAddable = !this.isAddable;
    },
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

### Dialog

In Dialog edit mode, when you start editing the currently selected row data will be shown on a dialog.
You can change the cell values and save edited data to the data source.
To enable Dialog edit, set the [`editSettings.mode`](../api/grid/editSettings/#mode) as **Dialog**.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
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

### Batch

In Batch edit mode, when you double-click on the grid cell, then the target cell changed to edit state.
You can bulk save (added, changed and deleted data in the single request) to data source by click on the toolbar's **Update**
button or by externally invoking the [`batchSave`](../api/grid/edit/#batchsave) method.
To enable Batch edit, set the [`editSettings.mode`](../api/grid/editSettings/#mode) as **Batch**.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
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
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Batch' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
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

### Automatically update the column based on another column edited value in Batch mode

You can update the column value based on another column edited value in Batch mode by using the Cell Edit Template feature.

In the below demo, we have update the `TotalCost` column value based on the `UnitPrice` and `UnitInStock` column value while editing.

{% tab template="grid/edit/default" %}

```html

<template>
  <div id="app">
    <ejs-grid id="Grid1" :dataSource="data" :editSettings="editSettings" :toolbar="toolbar" height="273px" :cellEdit="cellEdit">
      <e-columns>
        <e-column field="ProductID" headerText="Product ID" textAlign="Right" :isPrimaryKey="true" width="100"></e-column>
        <e-column field="ProductName" headerText="Product Name" width="120"></e-column>
        <e-column field="UnitPrice" headerText="Unit Price" editType="numericedit" :edit="priceParams"
          width="150" format="C2" textAlign="Right" ></e-column>
        <e-column field="UnitsInStock" headerText="Units In Stock" editType="numericedit"
          :edit="stockParams" width="150" textAlign="Right"></e-column>
        <e-column field="TotalCost" headerText="Total Cost" width="150" format="C2" textAlign="Right" ></e-column>
      </e-columns>
    </ejs-grid>
  </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { NumericTextBox } from "@syncfusion/ej2-inputs";
import { productData } from "./datasource.js";
import { getComponent } from "@syncfusion/ej2-base";

let priceElem, stockElem, priceObj, stockObj;
var grid;
Vue.use(GridPlugin);
export default {
  data: () => {
    return {
      data: productData,
      toolbar: ["Add", "Delete", "Update", "Cancel"],
      editSettings: {
        allowEditing: true,
        allowAdding: true,
        allowDeleting: true,
        mode: "Batch",
      },
      priceParams: {
        create: () => {
          priceElem = document.createElement("input");
          return priceElem;
        },
        read: () => {
          return priceObj.value;
        },
        destroy: () => {
          priceObj.destroy();
        },
        write: (args) => {
         grid = new getComponent("Grid1", "grid");
          var rowData = args.rowData;
          var rowIndex = grid.getRowInfo(args.row).rowIndex;
          priceObj = new NumericTextBox({
            value: args.rowData[args.column.field],
            change: function (args) {
              var totalCostValue = args.value * rowData["UnitsInStock"];
              grid.updateCell(rowIndex, "TotalCost", totalCostValue);
            },
          });
          priceObj.appendTo(priceElem);
        },
      },
      stockParams: {
        create: () => {
          stockElem = document.createElement("input");
          return stockElem;
        },
        read: () => {
          return stockObj.value;
        },
        destroy: () => {
          stockObj.destroy();
        },
        write: (args) => {
          grid = new getComponent("Grid1", "grid");
          var rowData = args.rowData;
          var rowIndex = grid.getRowInfo(args.row).rowIndex;
          stockObj = new NumericTextBox({
            value: args.rowData[args.column.field],
            change: function (args) {
              var totalCostValue = args.value * rowData["UnitPrice"];
              grid.updateCell(rowIndex, "TotalCost", totalCostValue);
            },
          });
          stockObj.appendTo(stockElem);
        },
      },
    };
  },
  methods: {
    cellEdit: function (args) {
      if (args.columnName === "TotalCost") {
        args.cancel = true;
      }
    },
  },
  provide: {
    grid: [Edit, Toolbar],
  },
};
</script>

<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

{% endtab %}

## Dialog/Inline template

The dialog/inline template editing provides an option to customize the default behavior of dialog editing. Using the dialog template, you can render your own editors by defining the [`editSettings.mode`](../api/grid/editSettings/#mode) as **Dialog/Normal** and [`editSetting.template`](../api/grid/editSettings/#template) as Vue component.

In some cases, you need to add the new field editors in the dialog which are not present in the column model. In that situation, the dialog template will help you to customize the default edit dialog.

To get start quickly with Dialog/Inline template edit Option, you can check on this video:

`youtube:Mrrgrb8nRlE`

In the following sample, grid enabled with dialog template editing.

{% tab template="grid/edit/dialogtemplate", sourceFiles="*.vue" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :actionBegin="actionBegin" :actionComplete="actionComplete" :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
import DialogTemplate from "./dialogtemp.vue";
import { DatePickerPlugin } from "@syncfusion/ej2-vue-calendars";
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
import { NumericTextBox } from "@syncfusion/ej2-inputs";
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";
import { DataUtil } from '@syncfusion/ej2-data';

Vue.use(GridPlugin);
Vue.use(DropDownListPlugin);
Vue.use(DatePickerPlugin);
Vue.use(NumericTextBoxPlugin)

export default {
  data() {
    return {
      data: data,
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Dialog',  template: function () {
          return { template : Vue.component('todo-item', {
            template: `<div formGroup="orderForm">
        <div class="form-row">
            <div class="form-group col-md-6">
                <div class="e-float-input e-control-wrapper">
                    <input id="OrderID" name="OrderID" v-model='data.OrderID' type="text" :disabled="!data.isAdd">
                    <span class="e-float-line"></span>
                    <label class="e-float-text e-label-top" for="OrderID"> Order ID</label>
                </div>
            </div>
            <div class="form-group col-md-6">
                <div class="e-float-input e-control-wrapper">
                    <input id="CustomerID" name="CustomerID" v-model='data.CustomerID' type="text">
                    <span class="e-float-line"></span>
                    <label class="e-float-text e-label-top" for="CustomerID">Customer Name</label>
                </div>
            </div>
        </div>
        <div class="form-row">
            <div class="form-group col-md-6">
                <ejs-numerictextbox id="Freight" placeholder="Freight" v-model='data.Freight' floatLabelType='Always'></ejs-numerictextbox>
            </div>
            <div class="form-group col-md-6">
                <ejs-datepicker id="OrderDate" placeholder="Order Date" v-model='data.OrderDate' floatLabelType='Always'></ejs-datepicker>
            </div>
        </div>
        <div class="form-row">
            <div class="form-group col-md-6">
                <ejs-dropdownlist id="ShipCountry" v-model='data.ShipCountry' :dataSource='shipCountryDistinctData' :fields="{text: 'ShipCountry', value: 'ShipCountry' }" placeholder="Ship Country" popupHeight='300px' floatLabelType='Always'></ejs-dropdownlist>
            </div>
            <div class="form-group col-md-6">
                <ejs-dropdownlist id="ShipCity" v-model='data.ShipCity' :dataSource='shipCityDistinctData' :fields="{text: 'ShipCity', value: 'ShipCity' }" placeholder="Ship City" popupHeight='300px' floatLabelType='Always'></ejs-dropdownlist>
            </div>
        </div>
        <div class="form-row">
            <div class="form-group col-md-12">
                <div class="e-float-input e-control-wrapper">
                    <textarea id="ShipAddress" name="ShipAddress" type="text" v-model='data.ShipAddress'></textarea>
                    <span class="e-float-line"></span>
                    <label class="e-float-text e-label-top" for="ShipAddress">Ship Address</label>
                </div>
            </div>
        </div>
    </div>`,
    data () {
        return {
            data: {}
        }
  },
   computed: {
      shipCityDistinctData: () => {
        return DataUtil.distinct(data, 'ShipCity', true);
      },
      shipCountryDistinctData: () => {
        return DataUtil.distinct(data, 'ShipCountry', true);
      }
    }
    })}
    } },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
  },
  provide: {
    grid: [Page, Edit, Toolbar]
  },
  methods: {
    actionBegin (args) {
        if (args.requestType === 'save') {
            // cast string to integer value.
            args.data['Freight'] = parseFloat(args.form.querySelector("#Freight").value);
        }
    },
    actionComplete(args) {
        // Set initail Focus
        if (args.requestType === 'beginEdit') {
            (args.form.elements.namedItem('CustomerName')).focus();
        }
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
 @import "https://stackpath.bootstrapcdn.com/bootstrap/4.1.2/css/bootstrap.min.css";

.form-group.col-md-6 {
    width: 250px;
    height: 54px;
}
.form-group.col-md-12 {
    height: 72px;
}
#ShipAddress {
    resize: vertical;
}

</style>

```

{% endtab %}

> The Dialog/Inline template form editors should have **name** attribute.

### Template context

The template should be a Vue Component. You can access the row information inside the Component and you can bind the attribute or value based on this row information.

The following properties will be available at the time of template execution.

| Property Name | Usage |
|---------------|--------|
| <kbd>isAdd</kbd> |  A Boolean property; it defines whether the current row should be a new record or not. |

In the following code example, the **OrderID** textbox has been disabled by using the **isAdd** property.

```html
// The disabled attributes will be added based on the isAdd property.
<input id="OrderID" name="OrderID" v-model='data.OrderID' type="text" :disabled="!data.isAdd">

```

### Get value from editor

You can read, format, and update the current editor value in the  [`actionBegin`](../api/grid/#actionbegin) event at the time of setting **requestType** to **save**.

In the following code example, the **Freight** value has been formatted and updated.

``` typescript
 actionBegin(args) {
        if (args.requestType === 'save') {
            // cast string to integer value.
            args.data['Freight'] = parseFloat(args.form.querySelector("#Freight").value);
        }
    },

```

### Set focus to editor

By default, the first input element in the dialog will be focused while opening the dialog.
If the first input element is in disabled or hidden state, focus the valid input element in the
[`actionComplete`](../api/grid/#actioncomplete)
event based on **requestType** as **beginEdit**.

```typescript

actionComplete(args) {
        if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {
            // Set initail Focus
            if (args.requestType === 'beginEdit') {
                (args.form.elements.namedItem('CustomerID')).focus();
            }
        }
    }

```

### Adding validation rules for custom editors

If you have used additional fields that are not present in the column model, then add the validation rules to the [`actionComplete`](../api/grid/#actioncomplete) event.

```typescript

actionComplete(args) {
        if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {
            // Add Validation Rules
            args.form.ej2_instances[0].addRules('Freight', {max: 500});
        }
    }

```

## Adding a new row at the Bottom of the Grid

By default, a new row will be added at the top of the grid. You can change it by setting [`editSettings.newRowPosition`](../api/grid/editSettings/#newrowposition) as **Bottom**.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' height='270' :toolbar='toolbar'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign= 'Right' width=120 format= 'C2'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' width=150></e-column>
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
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, newRowPosition: 'Bottom' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
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

> Add newRowPostion is supported for **Normal** and **Batch** editing modes.

## Command column

The command column provides an option to add CRUD action buttons in a column. This can be defined by the
[`column.commands`](../api/grid/column/#commands) property.

To use command column, inject the **CommandColumn** module in the **provide** section.

The available built-in command buttons are:

| Command Button | Actions |
|----------------|---------|
| Edit | Edit the current row.|
| Delete | Delete the current row.|
| Save | Update the edited row.|
| Cancel | Cancel the edited state. |

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' height='310px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign= 'Right' editType= 'numericedit' width=120 format= 'C2'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width=150></e-column>
                <e-column headerText='Commands' width=120 :commands='commands'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Toolbar, Edit, CommandColumn } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      editSettings: { allowEditing: true, allowDeleting: true },
      commands: [{ type: 'Edit', buttonOption: { cssClass: 'e-flat', iconCss: 'e-edit e-icons' } },
        { type: 'Delete', buttonOption: { cssClass: 'e-flat', iconCss: 'e-delete e-icons' } },
        { type: 'Save', buttonOption: { cssClass: 'e-flat', iconCss: 'e-update e-icons' } },
        { type: 'Cancel', buttonOption: { cssClass: 'e-flat', iconCss: 'e-cancel-icon e-icons' } }]
    };
  },
  provide: {
    grid: [Page, Edit, Toolbar, CommandColumn]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

{% endtab %}

### Custom command

 The custom command buttons can be added in a column by using the [`column.commands`](../api/grid/column/#commands) property and
the action for the custom buttons can be defined using [`commandClick`](../api/grid/#commandClick) event.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :editSettings='editSettings' :commandClick='commandClick' height='310px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width=150></e-column>
                <e-column headerText='Commands' width=150 :commands='commands'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Toolbar, Edit, CommandColumn } from "@syncfusion/ej2-vue-grids";
import { closest } from "@syncfusion/ej2-base";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      editSettings: { allowEditing: true, allowDeleting: true },
      commands: [{ buttonOption: { content: 'Details', cssClass: 'e-flat' } }]
    };
  },
  provide: {
    grid: [Page, Edit, Toolbar, CommandColumn]
  },
  methods: {
    commandClick: function(args) {
        alert(JSON.stringify(args.rowData));
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

{% endtab %}

## Confirmation messages

### Delete confirmation

The delete confirm dialog can be shown when deleting a record by defining the
[`showDeleteConfirmDialog`](../api/grid/editSettings/#showdeleteconfirmdialog) as **true**

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
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
      editSettings: { showDeleteConfirmDialog: true, allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
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

> The **showDeleteConfirmDialog** supports all type of edit modes.

### Batch confirmation

By default, grid will show the confirm dialog when saving or cancelling or performing any actions like filtering, sorting, etc.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
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
      editSettings: { showConfirmDialog: true, showDeleteConfirmDialog: true, allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Batch' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
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

> * [`editSettings.showConfirmDialog`](../api/grid/editSettings/#showconfirmdialog) requires the [`editSettings.mode`](../api/grid/editSettings/#mode) to be **Batch**
> * If [`editSettings.showConfirmDialog`](../api/grid/editSettings/#showconfirmdialog)
set to **false**, then confirmation dialog does not display in batch editing.

## Column validation

Column validation allows you to validate the edited or added row data and it display errors for invalid fields before saving data.
Grid uses **Form Validator** component for column validation.
You can set validation rules by defining the [`columns.validationRules`](../api/grid/column/#validationrules).

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' :validationRules='orderIDRules' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' :validationRules='customerIDRules' width=120></e-column>
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
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      orderIDRules: { required: true },
      customerIDRules: { required: true, minLength: 3 }
    };
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

### Custom validation

You can define your own custom validation rules for the specific columns by using **Form Validator custom rules**.

In the below demo, custom validation applied for **CustomerID** column.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' :validationRules='orderIDRules' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' :validationRules='customerIDRules' width=120></e-column>
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
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      orderIDRules: { required: true },
      customerIDRules: { required: true, minLength: [(args) => {return args['value'].length >= 5;}, 'Need atleast 5 letters'] }
    };
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

## Persisting data in server

Edited data can be persisted in the database using the RESTful web services.

All the CRUD operations in the grid are done through [`DataManager`](../../data).
The [`DataManager`](../../data) has an option to bind all the CRUD related data in server-side.

> For your information, the ODataAdaptor persists data in the server as per OData protocol.

In the below section, we have explained how to get the edited data details on the server-side using the
[`UrlAdaptor`](../../data/adaptors/#url-adaptor).

### URL adaptor

You can use the [`UrlAdaptor`](../../data/adaptors/#url-adaptor) of [`DataManager`](../../data) when binding data source from remote data.
In the initial load of grid, data are fetched from remote data and bound to the grid using **url** property of [`DataManager`](../../data).
You can map The CRUD operation in grid can be mapped to server-side Controller actions using the properties
**insertUrl**, **removeUrl**, **updateUrl**, **crudUrl** and **batchUrl**.

To learn about Server side CRUD operation with UrlAdaptor, you can check on this video:

`youtube:X4UlR-Q_AtI`

The following code example describes the above behavior.

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' :validationRules='orderIDRules' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' :validationRules='customerIDRules' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign= 'Right' editType= 'numericedit' width=120 format= 'C2'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { DataManager, UrlAdaptor } from '@syncfusion/ej2-data';

Vue.use(GridPlugin);

export default Vue.extend({
  data() {
    return {
      data: new DataManager({
        url: "Home/DataSource",
        updateUrl: "Home/Update",
        insertUrl: "Home/Insert",
        removeUrl: "Home/Delete",
        adaptor: new UrlAdaptor
    }),
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      orderIDRules: { required: true },
      customerIDRules: { required: true, minLength: 3 }
    };
  },
  provide: {
    grid: [Page, Edit, Toolbar]
  }
});
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

Also, when using the [`UrlAdaptor`](../../data/adaptors/#url-adaptor), you need to return the data as JSON from the controller action and the JSON object must contain
a property as **result** with dataSource as its value and one more property **count** with the dataSource total records count as its value.

The following code example describes the above behavior.

```typescript
public ActionResult DataSource(DataManager dm)
{
    var DataSource = OrderRepository.GetAllRecords();
    DataResult result = new DataResult();
    result.result = DataSource.Skip(dm.Skip).Take(dm.Take).ToList();
    result.count = result.result.Count;
    return Json(result, JsonRequestBehavior.AllowGet);
}

public class DataResult
{
    public List<EditableOrder> result { get; set; }
    public int count { get; set; }
}

```

### Insert record

Using the **insertUrl** property, you can specify the controller action mapping URL to perform insert operation on the server-side.

The following code example describes the above behavior.

```typescript
public ActionResult Insert(EditableOrder value)
{
    //Insert record in database
}

```

The newly added record details are bound to the **value** parameter. Please refer to the following screenshot.

![Insert](images/insert.jpg)

### Update record

Using the **updateUrl** property, the controller action mapping URL can be specified to perform save/update operation on the server-side.

The following code example describes the previous behavior.

```typescript
public ActionResult Update(EditableOrder value)
{
    //Update record in database
}

```

The updated record details are bound to the **value** parameter. Please refer to the following screenshot.

![Update](images/update.jpg)

### Delete record

Using the **removeUrl** property, the controller action mapping URL can be specified to perform delete operation on the server-side.

The following code example describes the previous behavior.

```typescript
public ActionResult Delete(int key)
{
    //Delete record in database
}

```

The deleted record primary key value is bound to the **key** parameter. Please refer to the following screenshot.

![Delete](images/delete.jpg)

### CRUD URL

Using the **crudUrl** property, the controller action mapping URL can be specified to perform all the CRUD operation at server-side using
a single method instead of specifying separate controller action method for CRUD (insert, update and delete) operations.

The action parameter of **crudUrl** is used to get the corresponding CRUD action.

The following code example describes the above behavior.

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' :validationRules='orderIDRules' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' :validationRules='customerIDRules' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign= 'Right' editType= 'numericedit' width=120 format= 'C2'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { DataManager, UrlAdaptor } from '@syncfusion/ej2-data';

Vue.use(GridPlugin);

export default Vue.extend({
  data() {
    return {
      data: new DataManager({
            url: "Home/DataSource",
            crudUrl: "Home/CrudUpdate",
            adaptor: new UrlAdaptor
        }),
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      orderIDRules: { required: true },
      customerIDRules: { required: true, minLength: 3 }
    };
  },
  provide: {
    grid: [Page, Edit, Toolbar]
  }
});
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

```typescript
public ActionResult CrudUpdate(EditableOrder value, string action)
{
    if(action == "update"){
        //Update record in database
    }
    else if (action == "insert")
    {
        //Insert record in database
    }
    else
    {
        //Delete record in database
    }
}

```

Please refer to the following screenshot to know about the action parameter.

![CRUD Update](images/crudupdate.jpg)

> If you specify **insertUrl** along with **crudUrl**, then while adding **insertUrl** only will be invoked.

### Batch URL

The **batchUrl** property supports only for batch editing mode.
You can specify the controller action mapping URL to perform batch operation on the server-side.

The following code example describes the above behavior.

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' :validationRules='orderIDRules' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' :validationRules='customerIDRules' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign= 'Right' editType= 'numericedit' width=120 format= 'C2'></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { DataManager, UrlAdaptor } from '@syncfusion/ej2-data';

Vue.use(GridPlugin);

export default Vue.extend({
  data() {
    return {
      data: new DataManager({
            url: "Home/DataSource",
            batchUrl: "Home/BatchUpdate",
            adaptor: new UrlAdaptor
        });
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Batch' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      orderIDRules: { required: true },
      customerIDRules: { required: true, minLength: 3 }
    };
  },
  provide: {
    grid: [Page, Edit, Toolbar]
  }
});
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>

```

```typescript
public ActionResult BatchUpdate(string action, List<EditableOrder> added, List<EditableOrder> changed, List<EditableOrder> deleted, int? key)
{
//Save the batch changes in database
}
```

![Batch](images/batch.jpg)

## Default column values on add new

The grid provides an option to set the default value for the columns when adding a new record in it.
To set a default value for the particular column by defining the [`columns.defaultValue`](../api/grid/column/#defaultvalue).

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' :validationRules='orderIDRules' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' defaultValue= 'HANAR' :validationRules='customerIDRules' width=120></e-column>
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
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      orderIDRules: { required: true },
      customerIDRules: { required: true, minLength: 3 }
    };
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

## Disable editing for particular column

You can disable editing for particular columns by using the [`columns.allowEditing`](../api/grid/column/#allowediting).

In the following demo, editing is disabled for the **CustomerID** column.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' :validationRules='orderIDRules' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' :allowEditing= 'false' :validationRules='customerIDRules' width=120></e-column>
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
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      orderIDRules: { required: true },
      customerIDRules: { required: true, minLength: 3 }
    };
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

## Troubleshoot: Editing works only for the first row

The Editing functionalities can be performed based upon the primary key value of the selected row.
If **primaryKey** is not defined in the grid, then edit or delete action take places the first row.

## See also

* [Editing with template column](./how-to/editing-with-template-column)
* [Customize dialog when editing](./how-to/customize-the-edit-dialog)
* [Cascading DropDownList with Grid Editing](./how-to/cascading-drop-down-list-with-grid-editing)
* [Customize the Edit Dialog](./how-to/customize-the-edit-dialog)
* [Restrict to type decimal points in a NumericTextBox while editing the numeric column](./how-to/restrict-decimal-points-while-grid-editing)
