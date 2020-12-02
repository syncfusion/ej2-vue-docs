---
title: "How To"
component: "Grid"
description: "Learn how to refresh the datasource, exporting filtered data, enable and disable grid actions, customize the pager dropdown in Essential JS 2 DataGrid."
---

# How-to

<!--markdownlint-disable MD009-->

## Register the Grid using Vue.Component

Import the `GridComponent` from the `@syncfuion/ej2-vue-grids` package,register the same using the `Vue.component()` with name of
the grid selector and the GridComponent as its arguments.

Refer to the code example given below.

```typescript
import { GridComponent } from '@syncfusion/ej2-vue-grids';

Vue.component('ejs-grid', GridComponent);
```

Using `Vue.component` will register the grid component alone. Child directives such as `Columns` and `Aggregates` need to be registered separately.

Refer to the code example given below to register column directives

```typescript
import { ColumnsDirective, ColumnDirective } from '@syncfusion/ej2-vue-grids';

Vue.component('e-columns', ColumnsDirective);
Vue.component('e-column', ColumnDirective);
```

Refer to the code example given below to register aggregates directives

```typescript
import { AggregatesDirective, AggregateDirective, AggregateColumnsDirective, AggregateColumnDirective } from '@syncfusion/ej2-vue-grids';

Vue.component('e-aggregates', AggregatesDirective);
Vue.component('e-aggregate', AggregateDirective);
Vue.component('e-columns', AggregateColumnsDirective);
Vue.component('e-column', AggregateColumnDirective);
```

## How to Refresh the Datasource

You can add/delete the datasource records through an external button. To reflect the datasource changes in grid,
you need to invoke the [`refresh`](../../api/grid/#refresh) method.

Please follow the below steps to refresh the grid after datasource change.

**Step 1**:

Add/delete the datasource record by using the following code.

```typescript
    this.data.unshift(customData); // Add a new record.

    this.data.splice(selectedRow, 1); // Delete a record.
```

**Step 2**:

When applied the changes in dataSource then refresh Grid at own.

```typescript
    this.data = [...this.data]; // Refresh the Grid dataSource.
```

{% tab template="grid/how-to/default" %}

```html
<template>
    <div id="app">
     <ejs-button @click.native='addAction'>Add</ejs-button>
     <ejs-button @click.native='deleteAction'>Delete</ejs-button>
        <ejs-grid ref='grid' :dataSource='data' height='280px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Center' format='C2'  width=80></e-column>
             <e-column field='OrderDate' headerText='Order Date' type='date' format='yMd' width=120></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { data } from './datasource.js';

Vue.use(GridPlugin);
Vue.use(ButtonPlugin);

export default {
  data: () => {
    return {
      data: data,
    };
  },
  methods: {
    addAction: function() {
      let customData = { OrderID: 10247, CustomerID: "ASDFG", Freight: 40.4, OrderDate: new Date(8367642e5) };
      this.data.unshift(customData);
      this.data = [...this.data];
    },
    deleteAction: function() {
      let selectedRow = this.$refs.grid.getSelectedRowIndexes()[0];
      if (selectedRow !== undefined) {
        this.data.splice(selectedRow, 1);
      }
      else {
        alert("No records selected for delete operation");
      }
      this.data = [...this.data];
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Enable/Disable Grid and its actions

You can enable/disable the Grid and its actions by applying/removing corresponding CSS styles.

To enable/disable the grid and its actions, follow the given steps:

**Step 1**:

Create CSS class with custom style to override the default style of Grid.

```css
    .disablegrid {
        pointer-events: none;
        opacity: 0.4;
    }
    .wrapper {
        cursor: not-allowed;
    }

```

**Step 2**:

Add/Remove the CSS class to the Grid in the click event handler of Button.

```typescript
    btnClick(args) {
      if (this.$refs.Grid.$el.classList.contains('disablegrid')) {
          this.$refs.Grid.$el.classList.remove('disablegrid');
          document.getElementById("GridParent").classList.remove('wrapper');
      }
      else {
          this.$refs.Grid.$el.classList.add('disablegrid');
          document.getElementById("GridParent").classList.add('wrapper');
      }
    }

```

In the below demo, the button click will enable/disable the Grid and its actions.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <div>
            <ejs-button  iconCss="e-icons e-play-icon" cssClass="e-flat" :isPrimary="true" :isToggle="true" v-on:click.native="btnClick">Enable/Disable Grid</ejs-button>
            <div id="GridParent">
              <ejs-grid ref='Grid' :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
                  <e-columns>
                      <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
                      <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                      <e-column field='Freight' headerText='Freight' textAlign= 'Right' editType= 'numericedit' width=120 format= 'C2'></e-column>
                      <e-column field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width=150></e-column>
                  </e-columns>
              </ejs-grid>
            </div>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { data } from './datasource.js';

Vue.use(GridPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      data: data,
      editSettings: { allowAdding:true, allowDeleting:true, allowEditing: true },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
  },
  methods: {
    btnClick(args) {
      if (this.$refs.Grid.$el.classList.contains('disablegrid')) {
          this.$refs.Grid.$el.classList.remove('disablegrid');
          document.getElementById("GridParent").classList.remove('wrapper');
      }
      else {
          this.$refs.Grid.$el.classList.add('disablegrid');
          document.getElementById("GridParent").classList.add('wrapper');
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
  .disablegrid {
    pointer-events: none;
    opacity: 0.4;
  }
  .wrapper {
    cursor: not-allowed;
  }
</style>

```

{% endtab %}

## Columns

### Customize Column Styles

You can customise the appearance of header and content of the particular column using the
[`customAttributes`](../../api/grid/column/#customattributes) property.

To customize the grid column, follow the given steps:

**Step 1**:

Create a css class with custom style to override the default style for rowcell and headercell.

```css
.e-grid .e-rowcell.customcss{
    background-color: #ecedee;
    color: 'red';
    font-family: 'Bell MT';
    font-size: 20px;
}

.e-grid .e-headercell.customcss{
    background-color: #2382c3;
    color: white;
    font-family: 'Bell MT';
    font-size: 20px;
}
```

**Step 2**:

Add the custom css class to particular column by using [`customAttributes`](../../api/grid/column/#customattributes) property.

{% tab template="grid/how-to/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' height='315px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
                <e-column field='CustomerID' headerText='Customer ID' :customAttributes="customAttributes" width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
                <e-column field='OrderDate' headerText='Order Date' textAlign='Right' type='date' format='yMd' width=120></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
       customAttributes : {class: 'customcss'}
    };
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
  .e-grid .e-rowcell.customcss{
    background-color: #ecedee;
    color: 'red';
    font-family: 'Bell MT';
    font-size: 20px;
}

.e-grid .e-headercell.customcss{
    background-color: #2382c3;
    color: white;
    font-family: 'Bell MT';
    font-size: 20px;
}
</style>
```

{% endtab %}

### Custom Tooltip for Columns

You can achieve the custom tooltip([`EJ2 Tooltip`](../../tooltip/getting-started)) for Grid by using the
[`queryCellInfo`](../../api/grid/#querycellinfo) event.

Render the ToolTip component for the grid cells by using the following code in the
[`queryCellInfo`](../../api/grid/#querycellinfo) event.

```typescript
tooltip (args) {
    let tooltip = new Tooltip({
        content: args.data[args.column.field].toString();
    }, args.cell);
}
```

{% tab template="grid/how-to/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :queryCellInfo='queryCellInfoEvent' height='315px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
               <e-column field='ShipName' headerText='Ship Name' width=120></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import{ Tooltip } from "@syncfusion/ej2-popups";
import { data } from './datasource.js';

Vue.use(GridPlugin);

  export default {
    data() {
      return {
        data: data
      };
    },
    methods: {
      queryCellInfoEvent: function (args) {
        let tooltip = new Tooltip({
          content: args.data[args.column.field].toString()
        }, args.cell);
      },
    },
  }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### Render other components in a column

You can render any component in a grid column using the [`template`](../../api/grid/column/#template) property.

{% tab template="grid/how-to/dropdown" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' height='315px' >
            <e-columns>
                <e-column headerText='Order Status' :template="dropdownTemplate" width=200></e-column>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
               <e-column field='ShipName' headerText='Ship Name' width=120></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
import { data } from './datasource.js';

Vue.use(GridPlugin);
Vue.use(DropDownListPlugin);

export default {
  data() {
    return {
      data: data,
      dropdownTemplate: function () {
        return {
          template: Vue.component('bindDropdown', {
            template: `<ejs-dropdownlist id='dropdownlist' :dataSource='dropData'> </ejs-dropdownlist>`,
            data() {
              return {
                dropData: ['Order Placed', 'Processing', 'Delivered']
              }
            }
          })
        }
      }
    };
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### How to change the Orientation of Header Text

You can change the orientation of the header text by using the [`customAttributes`](../../api/grid/column/#customattributes) property.

To change the Orientation of Header Text, Ensure the following steps:

**Step 1**:

Create a css class with orientation style for grid header cell.

```css
.orientationcss .e-headercelldiv {
    transform: rotate(90deg);
}
```

**Step 2**:

Add the custom css class to particular column by using [`customAttributes`](../../api/grid/column/#customattributes) property.

```html
    <e-column field='Freight' headerText='Freight' textAlign='Center' format='C2' :customAttributes='customAttributes' width=80></e-column>
```

**Step 3**:

Resize the header cell height by using the following code.

```typescript
setHeaderHeight(args) {
    let textWidth = document.querySelector(".orientationcss > div").scrollWidth;//Obtain the width of the headerText content.
    let headerCell = document.querySelectorAll(".e-headercell");
    for(let i = 0; i < headerCell.length; i++) {
       (headerCell.item(i)).style.height = textWidth + 'px'; //Assign the obtained textWidth as the height of the headerCell.
    }
}

```

{% tab template="grid/how-to/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :created='setHeaderHeight' height='240px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Center' format='C2' :customAttributes='customAttributes' width=80></e-column>
               <e-column field='ShipCity' headerText='Ship City' width=100></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data: () => {
    return {
      data: data,
      customAttributes : {class : 'orientationcss'},
    };
  },
  methods: {
    setHeaderHeight: function(args) {
      let textWidth = document.querySelector(".orientationcss > div").scrollWidth;//Obtain the width of the headerText content.
      let headerCell = document.querySelectorAll(".e-headercell");
      for (let i = 0; i < headerCell.length; i++) {
        (headerCell.item(i)).style.height = textWidth + 'px'; //Assign the obtained textWidth as the height of the headerCell.
      }
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
   .orientationcss .e-headercelldiv {
    transform: rotate(90deg);
    padding-top:5px;
}
</style>
```

{% endtab %}

### Customize the icon for column menu

You can customize the column menu icon by overriding the default grid class `.e-icons.e-columnmenu` with a custom property `content` as mentioned below,

```css
.e-grid .e-columnheader .e-icons.e-columnmenu::before {
              content: "\e941";
      }
```

In the below sample, grid is rendered with a customized column menu icon.

{% tab template="grid/how-to/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data':showColumnMenu='true' height='315px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' width=90></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' format='C2' width=90></e-column>
               <e-column field='ShipName' headerText='Ship Name' width=120></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, ColumnMenu } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

  export default {
    data() {
      return {
        data: data
      };
    },
  provide: {
    grid: [ColumnMenu]
    }
  }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
  .e-grid .e-columnheader .e-icons.e-columnmenu::before {
              content: "\e941";
      }
</style>
```

{% endtab %}

### How to get grid column instance in column template

You can emit values from one component and listen emitted values in other component by using `eventHub`. `eventHub` is a global event bus used to communicate between any components.

In the below example, we have defined template column in grid column definition which emits a value and listen the emitted value in `created` event of the grid component.

{% tab template="grid/column/template" %}

```html
<template>
    <div id="app">
         <ejs-grid :dataSource="data" height=310>
            <e-columns>
                <e-column field='EmployeeID' headerText='Employee ID' width='125' textAlign='Right'></e-column>
                <e-column field='FirstName' headerText='Name' width='120'></e-column>
                <e-column field='Title' headerText='Title' width='170'></e-column>
                <e-column headerText='templateColumn' width='150' textAlign='Center' :template='cTemplate'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { employeeData } from "./datasource.js";

Vue.use(GridPlugin);

Vue.prototype.$eventHub = new Vue();

export default {
  data: () => {
    return {
      data: employeeData,
      cTemplate: function () {
        return {
          template: Vue.component('columnTemplate', {
            template: `<button v-on:click="click(event)">buttton</button>`,
            data: function () {
              return {
                data: {}
              }
            },
            methods: {
              click: function (e) {
                this.$eventHub.$emit('detail', this.data.index);
              }
            }
          })
        }
      }
    };
  },
  created() {
    this.$eventHub.$on('detail', (e) => {
      alert("passed value: " + e);
    });
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Editing

### Editing with template column

You can edit template column value by defining `field` for that particular column.

In the below demo, the `ShipCountry` column is rendered with the template.

{% tab template="grid/how-to/default" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='280px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' :isPrimaryKey='true' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Center' format='C2' editType='numericedit' width=80></e-column>
             <e-column field='ShipCountry' headerText='Ship Country' :template='editTemplate' editType='dropdownedit'  width=120></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin,Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);
export default {
  data: () => {
    return {
      data: data,
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
      editTemplate: function () {
        return {
          template: Vue.component('editOption', {
            template: '<a href="#">{{data.ShipCountry}}</a>',
            data() { return { data: { data: {} } }; }
          })
        }
      },
    };
  },
  provide: {
    grid: [Edit, Toolbar]
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

### Customize the Edit Dialog

You can customize the appearance of the edit dialog in the [`actionComplete`](../../api/grid/#actioncomplete) event based on `requestType` as `beginEdit` or `add`.

In the below example, we have changed the dialog's header text for editing and adding records.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px' :actionComplete = 'actionComplete'>
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
  methods: {
    actionComplete(args) {
        if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {
            let dialog = args.dialog;
            dialog.height = 400;
            // change the header of the dialog
            dialog.header = args.requestType === 'beginEdit' ? 'Record of ' + args.rowData['CustomerID'] : 'New Customer';
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

### Show or Hide columns in Dialog editing

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

### Cascading DropDownList with Grid editing

You can achieve the Cascading DropDownList with grid Editing by using the Cell Edit Template feature.

In the below demo, Cascading DropDownList rendered for `ShipCountry` and `ShipState` column.

{% tab template="grid/how-to/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' :isPrimaryKey='true' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='ShipCountry' headerText='ShipCountry' editType='dropdownedit' :edit='countryParams' width=150></e-column>
               <e-column field='ShipCity' headerText='Ship City' editType='dropdownedit' :edit='stateParams' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { createElement } from '@syncfusion/ej2-base';
import { GridPlugin,Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { DropDownList } from "@syncfusion/ej2-dropdowns";
import { Query } from '@syncfusion/ej2-data';
import { cascadeData } from './datasource.js';

let country= [
        { countryName: 'United States', countryId: '1' },
        { countryName: 'Australia', countryId: '2' }
    ];
let state = [
        { stateName: 'New York', countryId: '1', stateId: '101' },
        { stateName: 'Virginia ', countryId: '1', stateId: '102' },
        { stateName: 'Washington', countryId: '1', stateId: '103' },
        { stateName: 'Queensland', countryId: '2', stateId: '104' },
        { stateName: 'Tasmania ', countryId: '2', stateId: '105' },
        { stateName: 'Victoria', countryId: '2', stateId: '106' }
    ];
let countryElem, stateElem, countryObj, stateObj;
Vue.use(GridPlugin);
export default {
    data: () => {
      return {
        data: cascadeData,
        toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
        editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
        countryParams: {
          create: () => {
            countryElem = document.createElement('input');
            return countryElem;
          },
          read: () => {
            return countryObj.text;
          },
          destroy: () => {
            countryObj.destroy();
          },
          write: () => {
            countryObj = new DropDownList({
              dataSource: country,
              fields: { value: 'countryId', text: 'countryName' },
              change: () => {
                stateObj.enabled = true;
                let tempQuery = new Query().where('countryId', 'equal', countryObj.value);
                stateObj.query = tempQuery;
                stateObj.text = null;
                stateObj.dataBind();
              },
              placeholder: 'Select a country',
              floatLabelType: 'Never'
            });
           countryObj.appendTo(countryElem);          
          }
        },
        stateParams: {
          create: () => {
            stateElem = document.createElement('input');
            return stateElem;
          },
          read: () => {
            return stateObj.text;
          },
          destroy: () => {
            stateObj.destroy();
          },
          write: () => {
              stateObj = new DropDownList({
              dataSource: state,
              fields: { value: 'stateId', text: 'stateName' },
              enabled: false,
              placeholder: 'Select a state',
              floatLabelType: 'Never'
            });
            stateObj.appendTo(stateElem);
          }
        },

      };
    },
    provide: {
      grid: [Edit, Toolbar]
    }
  }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### Provide custom data source and enabling filtering to DropDownList

You can provide data source to the DropDownList by using the `columns.edit.params` property.

While setting new data source using edit params, you must specify a new `query` property too for the DropDownList as follows,

```typescript
countryParams: {
          params:   {
            allowFiltering: true,
            dataSource: country,
            fields: {text:"countryName",value:"countryName"},
            query: new Query(),
            actionComplete: () => false
            }
      };
```

You can also enable filtering for the DropDownList by passing the `allowFiltering` as `true` to the edit params.

In the below demo, DropDownList is rendered with custom Datasource for the `ShipCountry` column and enabled filtering to search DropDownList items.

{% tab template="grid/how-to/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' :isPrimaryKey='true' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='ShipCountry' headerText='ShipCountry' editType='dropdownedit' :edit='countryParams' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { createElement } from '@syncfusion/ej2-base';
import { GridPlugin,Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { DropDownList } from "@syncfusion/ej2-dropdowns";
import { Query } from '@syncfusion/ej2-data';
import { cascadeData } from './datasource.js';

let country= [
        { countryName: 'United States', countryId: '1' },
        { countryName: 'Australia', countryId: '2' },
        { countryName: 'India', countryId: '3' }
    ];
Vue.use(GridPlugin);
export default {
    data: () => {
      return {
        data: cascadeData,
        toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
        editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
        countryParams: {
          params:   {
            allowFiltering: true,
            dataSource: country,
            fields: {text:"countryName",value:"countryName"},
            query: new Query(),
            actionComplete: () => false
            }
        }
      };
    },
    provide: {
      grid: [Edit, Toolbar]
    }
  }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### Disable editing for a particular row/cell

You can disable the editing for a particular row by using the [`actionBegin`](../../api/grid/#actionbegin) event of Grid based on `requestType` as `beginEdit`.

In the below demo, the rows which are having the value for `ShipCountry` column as "France" is prevented from editing.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px' :actionBegin = 'actionBegin'>
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
      editSettings: { allowEditing: true },
      toolbar: ['Edit', 'Update', 'Cancel']
    };
  },
  methods: {
    actionBegin(args) {
        if (args.requestType === 'beginEdit') {
            if (args.rowData.ShipCountry == "France") {
                args.cancel = true;
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

For batch mode of editing, you can use [`cellEdit`](../../api/grid/#celledit) event of Grid. In the below demo, the cells which are having the value as "France" is prevented from editing.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px' :cellEdit = 'cellEdit'>
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
      editSettings: { allowEditing: true, mode: 'Batch' },
      toolbar: ['Edit', 'Update', 'Cancel']
    };
  },
  methods: {
    cellEdit(args) {
        if (args.value == "France") {
            args.cancel = true;
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

### Perform Grid actions by keyboard shortcut keys

Using keyboard shortcuts, Grid performs navigation and actions.

In addition, You can also perform grid actions with custom keyboard shortcuts. This operation has to be achieved outside of the grid with the help of `keydown` event.

The following example demonstrates on `Adding` a new row when `Enter` key is pressed in the grid.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px' :load = 'load'>
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
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
  },
  methods: {
    load(args) {
      this.$refs.grid.$el.addEventListener('keydown', this.keyDownHandler);
    }

    keyDownHandler(e: any) {
      if(e.keyCode) {
        let gridIns = this.$refs.grid.ej2Instances;
        gridIns.addRecord();
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

### Make a cell editable on a single click with batch editing

You can make a cell editable on a single click with `batch` mode of editing in Grid, by using the **editCell** method.

Bind the click event for the Grid and in the click event handler call the **editCell** method, based on the clicked target element.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid id="Grid" v-on:click.native="click" ref="grid" :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px'>
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
      editSettings: { allowEditing: true, mode: 'Batch' },
      toolbar: ['Edit', 'Update', 'Cancel']
    };
  },
  methods: {
    click(event) {
      if((event.target as any).classList.contains("e-rowcell")){
          let index: number = parseInt((event.target as any).getAttribute("Index"));
          let colindex:number = parseInt((event.target as any).getAttribute("aria-colindex"));
          let field:string = this.$refs.grid.ej2Instances.getColumns()[colindex].field;
          this.$refs.grid.ej2Instances.editModule.editCell(index, field);
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

## Filter

### Customizing filter menu operators list

 You can customize the default filter operator list by defining the
  [`filterSettings.operators`](../../api/grid/filterSettings/#operators) property. The available options are:

* `stringOperator`- defines customized string operator list.
* `numberOperator` - defines customized number operator list.
* `dateOperator` - defines customized date operator list.
* `booleanOperator` - defines customized boolean operator list.

In the following sample, we have customized string filter operators.
{% tab template="grid/how-to/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' allowFiltering='true' :filterSettings='filterOptions' height='273px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
             <e-column field='ShipCity' headerText='Ship City'  width=100></e-column>
             <e-column field='ShipName' headerText='Ship Name'  width=100></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin,Filter } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);
export default {
      data: () => {
        return {
          data: data,
          filterOptions: {
            type: 'Menu',
            operators: {
              stringOperator: [
                { value: 'startsWith', text: 'starts with' },
                { value: 'endsWith', text: 'ends with' },
                { value: 'contains', text: 'contains' }
              ],
            }
          },
        };
      },
      provide: {
        grid: [Filter],
      },
    }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Sort

### Perform single/multi sorting dynamically

You can perform single-column or multi-column sorting dynamically through an external button.

To perform single-column sorting, use the [`sortColumn`](../api/grid/#sortcolumn) method of Grid.

```typescript
    singleSort: function() {
      this.$refs.grid.sortColumn("OrderID","Descending")
    }
```

To perform multi-column sorting, you need to push the columns to be sorted into the [`sortSettings.columns`](../api/grid/sortSettings/#columns).

```typescript
    multiSort: function() {
      this.$refs.grid.ej2Instances.sortModule.sortSettings.columns.push({ field: 'ShipCity',  direction: 'Ascending' },{ field: 'CustomerID', direction: 'Descending' });
      this.$refs.grid.refresh();
    }
```

In the below demo, click on the corresponding button to perform single-column or multi-column sorting.

{% tab template="grid/how-to/sort" %}

```html
<template>
    <div id="app">
     <ejs-button @click.native='singleSort'>SingleSort</ejs-button>
     <ejs-button @click.native='multiSort'>MultiSort</ejs-button>
        <ejs-grid ref='grid' :dataSource='data' :allowSorting='true' height='280px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Center' format='C2'  width=80></e-column>
                <e-column field='OrderDate' headerText='Order Date' type='date' format='yMd' width=120></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=120></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Sort } from "@syncfusion/ej2-vue-grids";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { data } from './datasource.js';

Vue.use(GridPlugin);
Vue.use(ButtonPlugin);

export default {
  data: () => {
    return {
      data: data,
    };
  },
  provide: {
    grid: [Sort]
  },
  methods: {
    singleSort: function() {
      this.$refs.grid.sortColumn("OrderID","Descending")
    },
    multiSort: function() {
      this.$refs.grid.ej2Instances.sortModule.sortSettings.columns.push({ field: 'ShipCity',  direction: 'Ascending' },{ field: 'CustomerID', direction: 'Descending' });
      this.$refs.grid.refresh();
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### Dynamically clear sort for particular/entire sorted columns in Grid

You can clear the sorting for a particular column or the entire sorted columns in Grid dynamically through an external button.

To clear sort for a particular column, you need to splice the particular column from the [`sortSettings.columns`](../api/grid/sortSettings/#columns).

```typescript
    SingleClearSort: function() {
      let column: Column = this.$refs.grid.ej2Instances.sortModule.sortSettings.columns;
      for(let i=0;i < column.length;i++){
          if(column[i].field === "OrderID") {
              column.splice(i,1);
              this.$refs.grid.refresh();
          }
      }
    }
```

To clear sorting for all the sorted columns, use the [`clearSorting`](../api/grid/#clearsorting) method of Grid.

```typescript
    MultiClearSort: function() {
      this.$refs.grid.clearSorting();
    }
```

In the below demo, click on the corresponding button to clear sort for particular or entire sorted columns in Grid.

{% tab template="grid/how-to/sort" %}

```html
<template>
    <div id="app">
     <ejs-button @click.native='SingleClearSort'>Clear the sort for <b>OrderID</b> column</ejs-button>
     <ejs-button @click.native='MultiClearSort'>Clear sorting for entire sorted columns</ejs-button>
        <ejs-grid ref='grid' :dataSource='data' :allowSorting='true' :sortSettings='sortOptions' height='280px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Center' format='C2'  width=80></e-column>
                <e-column field='OrderDate' headerText='Order Date' type='date' format='yMd' width=120></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=120></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Sort } from "@syncfusion/ej2-vue-grids";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { data } from './datasource.js';

Vue.use(GridPlugin);
Vue.use(ButtonPlugin);

export default {
  data: () => {
    return {
      data: data,
      sortOptions: { columns: [{ field: 'OrderID', direction: 'Ascending' }, { field: 'ShipCity', direction: 'Descending' }] }
    };
  },
  provide: {
    grid: [Sort]
  },
  methods: {
    SingleClearSort: function() {
      let column: Column = this.$refs.grid.ej2Instances.sortModule.sortSettings.columns;
      for(let i=0;i < column.length;i++){
          if(column[i].field === "OrderID") {
              column.splice(i,1);
              this.$refs.grid.refresh();
          }
      }
    },
    MultiClearSort: function() {
      this.$refs.grid.clearSorting();
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Foreign Key

### Use Edit Template in Foreign Key Column

By default, foreign key column uses dropdown component for editing.
You can render other than the dropdown by using the [`column.edit`](../../api/grid/column/#edit) property.
The following example demonstrates the way of using edit template in foreign column.

In the following example, The `Employee Name` is a foreign key column and while editing, AutoComplete component is rendered instead of DropDownList.

{% tab template="grid/how-to/foreignKey" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :editSettings='editoption' :Toolbar='toolbar' height='270px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='EmployeeID' headerText='Employee Name' :dataSource='employeeData' foreignKeyValue='FirstName' :edit='edit' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Center' format='C2' width=80></e-column>
                 <e-column field='ShipCity' headerText='Ship City' width=130></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { createElement } from '@syncfusion/ej2-base';
import { GridPlugin, Edit, Toolbar,ForeignKey  } from "@syncfusion/ej2-vue-grids";
import { AutoComplete } from "@syncfusion/ej2-dropdowns";
import { DataManager,Query } from '@syncfusion/ej2-data';
import { data,fEmployeeData } from './datasource.js';

Vue.use(GridPlugin);
export default {
      data: () => {
        return {
          data: data,
          employeeData: fEmployeeData,
          toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
          editoption: { allowEditing: true },
          edit: {
            create: () => { // to create input element
              return createElement('input');
            },
            read: () => { // return edited value to update data source
              let value = new DataManager(fEmployeeData).executeLocal(new Query().where('FirstName', 'equal', this.autoComplete.value));
              return value.length && value[0]['EmployeeID']; // to convert foreign key value to local value.
            },
            destroy: () => { // to destroy the custom component.
              this.autoComplete.destroy();
            },
            write: (args) => { // to show the value for date picker
              this.autoComplete = new AutoComplete({
                dataSource: fEmployeeData,
                fields: { value: args.column.foreignKeyValue },
                value: args.foreignKeyData[0][args.column.foreignKeyValue]
              });
              this.autoComplete.appendTo(args.element);
            }
          },
        };
      },
      provide: {
        grid: [Edit, ForeignKey]
      },
    }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

### Customize filter UI in foreign key column

You can create your own filtering UI by using [`column.filter`](../../api/grid/column/#filter) property.
The following example demonstrates the way to create a custom filtering UI in the foreign column.

In the following example, The `Employee Name` is a foreign key column. DropDownList is rendered using Filter UI.

{% tab template="grid/how-to/foreignKey" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :allowFiltering='true' :filterSettings='filteroption' height='270px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
               <e-column field='EmployeeID' headerText='Employee Name' :dataSource='employeeData' foreignKeyValue='FirstName' :filter='filter' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Center' format='C2' width=80></e-column>
                 <e-column field='ShipCity' headerText='Ship City' width=130></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { createElement } from '@syncfusion/ej2-base';
import { GridPlugin, Edit, Toolbar, ForeignKey, Filter  } from "@syncfusion/ej2-vue-grids";
import { DropDownList } from "@syncfusion/ej2-dropdowns";
import { DataManager } from '@syncfusion/ej2-data';
import { data,fEmployeeData } from './datasource.js';

let dropInstance;

Vue.use(GridPlugin);
export default {
      data: () => {
        return {
          data: data,
          employeeData: fEmployeeData,
          filteroption: { type: 'Menu' },
          filter: {
            ui: {
              create: (args) => {
                let flValInput = createElement('input', { className: 'flm-input' });
                args.target.appendChild(flValInput);
                dropInstance = new DropDownList({
                  dataSource: new DataManager(fEmployeeData),
                  fields: { text: 'FirstName', value: 'EmployeeID' },
                  placeholder: 'Select a value',
                  popupHeight: '200px'
                });
                dropInstance.appendTo(flValInput);
              },
              write: (args) => {
                dropInstance.text = args.filteredValue || '';
              },
              read: (args) => {
                args.fltrObj.filterByColumn(args.column.field, args.operator,dropInstance.text);
              }
            }
          },
        };
      },
      provide: {
        grid: [Filter, ForeignKey, Edit, Toolbar]
      }
    }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### Perform aggregation in Foreign Key Column

Default aggregations are not supported in a foreign key column.
You can achieve aggregation for the foreign key column by using custom the aggregates.
The following example demonstrates the way to achieve aggregation in foreign key column.

In the following example, The `Employee Name` is a foreign key column and the aggregation for the foreign column was calculated in customAggregateFn.

{% tab template="grid/how-to/foreignKey" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :allowFiltering='true'  height='260px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
               <e-column field='EmployeeID' headerText='Employee Name' :dataSource='employeeData' foreignKeyValue='FirstName' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Center' format='C2' width=80></e-column>
                 <e-column field='ShipCity' headerText='Ship City' width=130></e-column>
            </e-columns>
             <e-aggregates>
              <e-aggregate>
                <e-columns>
                    <e-column field="EmployeeID" type="Custom" :customAggregate='customAggregateFn' :footerTemplate='footerTemplate'></e-column>
                </e-columns>
             </e-aggregate>
          </e-aggregates>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Aggregate ,ForeignKey, Filter } from "@syncfusion/ej2-vue-grids";
import { getValue } from "@syncfusion/ej2-base";
import { getForeignData } from "@syncfusion/ej2-grids";
import { data,fEmployeeData } from './datasource.js';

Vue.use(GridPlugin);
export default {
      data: () => {
        return {
          data: data,
          employeeData: fEmployeeData,
          footerTemplate: function () {
            return {
              template: Vue.component('customTemplate', {
                template: `<span>Count of Margaret:  {{data.Custom}}</span>`,
                data() { return { data: { data: {} } }; }
              })
            }
          },

        };
      },
      methods: {
        customAggregateFn: function (data, column) {
          return data.result.filter((dObj) => {
            return getValue('FirstName', getForeignData(this.$refs.grid.getColumnByField(column.field), dObj)[0]) === 'Margaret';
          }).length;
        }
      },
      provide: {
        grid: [Aggregate, ForeignKey, Filter],
      },
    }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

### Bind foreign key dataSource on dropdown edit

When editing, you can bind foreign key datasource to a dropdown list by using [`column.dataSource`](../../api/grid/column/#datasource) property.

{% tab template="grid/column/foreigncolumn" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='315'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='EmployeeID' headerText='Employee Name' width=120 foreignKeyValue='FirstName' :dataSource='employeeData'></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Right' width=80></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=130  ></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, ForeignKey, Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { data, employeeData } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      employeeData: employeeData,
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
  },
  provide: {
      grid: [ForeignKey, Toolbar, Edit]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> * By default, the foreign key column's `editType` will be set as `dropdownedit`.

## Exporting

### Exporting Grid in Cordova application

Cordova application does not support direct file download. So we have to use the Blob stream to export the Grid.
You can use corresponding exporting methods and exportComplete events to get the Blob stream.

{% tab template="grid/how-to/foreignKey" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :toolbar='toolbarOptions' height='272px' :allowExcelExport='true' :excelExportComplete='excelExpComplete' :pdfExportComplete='pdfExportComplete' :allowPdfExport='true' :toolbarClick='toolbarClick' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin,Toolbar,PdfExport,ExcelExport } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);
export default {
      data: () => {
        return {
          data: data,
          toolbarOptions: ['Add', 'PdfExport', 'ExcelExport'],


        };
      },
      methods: {
        toolbarClick: function (args) {

          if (args['item'].id.indexOf("pdfexport") != -1) {
            this.$refs.grid.pdfExport(null, null, null, true);
          }
          if (args['item'].id.indexOf("excelexport") != -1) {
            this.$refs.grid.excelExport(null, null, null, true);
          }

        },
        excelExpComplete: function (args) {
          //This event will be triggered when excel exporting.
          args.promise.then((e) => {
            //In this `then` function, we can get blob data through the arguments after promise resolved.
            this.exportBlob(e.blobData);
          });
        },
        pdfExportComplete: function (args) {
          //This event will be triggered when pdf exporting.
          args.promise.then((e) => {
            //In this `then` function, we can get blob data through the arguments after promise resolved.
            this.exportBlob(e.blobData);
          });
        },
        exportBlob: function (blob) {
          let a = document.createElement('a');
          document.body.appendChild(a);
          a.style.display = 'none';
          let url = window.URL.createObjectURL(blob);
          a.href = url;
          a.download = 'Export';
          a.click();
          window.URL.revokeObjectURL(url);
          document.body.removeChild(a);
        }
      },
      provide: {
        grid: [Toolbar, ExcelExport, PdfExport]
      },
    }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### Exporting Filtered Data Only

You can export the filtered data by defining the resulted data in `exportProperties.dataSource` before export.

In the below Pdf exporting demo, We have gotten the filtered data by applying filter query to the grid data and then defines the resulted data in `exportProperties.dataSource` and pass it to `pdfExport` method.

{% tab template="grid/how-to/export-filtered-data" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :toolbar='toolbarOptions' :allowPaging='true' :allowFiltering='true' :allowPdfExport='true' :pageSettings='pageSettings' 
        :toolbarClick='toolbarClick'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin,Toolbar,PdfExport,Filter,Page  } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
import { DataManager } from "@syncfusion/ej2-data";

Vue.use(GridPlugin);
export default {
      data: () => {
        return {
          data: data,
          toolbarOptions: ['PdfExport'],
          pageSettings: { pageSize: 5, pageCount:5 }

        };
      },
      methods: {
        toolbarClick: function (args) {
          if (args['item'].id.indexOf("pdfexport") != -1) {
           let pdfdata;         
           let query = this.$refs.grid.ej2Instances.renderModule.data.generateQuery(); // get grid corresponding query  
         for(var i=0; i<query.queries.length; i++ ){
            if(query.queries[i].fn=='onPage'){
            query.queries.splice(i,1);      // remove page query to get all records
            break;
            }
          }
          let fdata = new DataManager({ json: data}).executeQuery(query).then((e) => {
          pdfdata = e.result;   // get all filtered records
          let exportProperties = { 
           dataSource: pdfdata, 
          }; 
          this.$refs.grid.pdfExport(exportProperties); 
        }).catch((e) => true); 
          }
        },     
      },
      provide: {
        grid: [Toolbar, PdfExport, Filter, Page]
      },
    }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Pager

### Customize Pager DropDown

To customize default values of pager dropdown, you need to define `pageSizes` as array of strings.

{% tab template="grid/how-to/pagerdropdown" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :allowPaging='true' :pageSettings='pageSettings' height='280px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' :isPrimaryKey='true' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Center' format='C2' width=80></e-column>
             <e-column field='ShipCountry' headerText='Ship Country' width=120></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin,Toolbar, Page } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);
export default {
  data: () => {
    return {
      data: data,
      pageSettings: {pageSizes: ['5','10','All']}
     };
  },
  provide: {
    grid: [Page]
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Hide the expand/collapse icon in parent row when no records in child grid

By default, the expand/collapse icon will be visible even if the child grid is empty.

You can use [`rowDataBound`](../../api/grid/#rowdatabound) event to hide the icon when there are no records in child grid.

To hide the expand/collapse icon in parent row when no records in child grid, follow the given steps:

**Step 1**:

Create CSS class with custom style to override the default style of Grid.

```css
    .e-row[aria-selected="true"] .e-customizedExpandcell {
        background-color: #e0e0e0;
    }

    .e-grid.e-gridhover tr[role='row']:hover {
        background-color: #eee;
    }

```

**Step 2**:

Add the CSS class to the Grid in the [`rowDataBound`](../../api/grid/#rowdatabound) event handler of Grid.

```typescript
    rowDataBound(args){
      let filter:string = args.data.EmployeeID;
      let childrecord: any = new DataManager(this.$refs.Grid.childGrid.dataSource).executeLocal(new Query().where("EmployeeID", "equal", parseInt(filter), true));
      if(childrecord.length == 0) { 
        //here hide which parent row has no child records
        args.row.querySelector('td').innerHTML=" ";
        args.row.querySelector('td').className = "e-customizedExpandcell";
      }
    }

```

In the below demo, the expand/collapse icon in the row with `EmployeeID` as `1` is hidden as it does not have record in child Grid.

{% tab template="grid/edit/default" %}

```html

<template>
    <div id="app">
        <ejs-grid ref='Grid' :dataSource="data" height='315px' :childGrid='childGrid' :rowDataBound='rowDataBound'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='EmployeeID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
            <e-column field='OrderDate' headerText='Order Date' textAlign='Right' format='yMd' type='date' width=120></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, DetailRow } from "@syncfusion/ej2-vue-grids";
import { DataManager, Query } from '@syncfusion/ej2-data';
import { employeeData } from './datasource.js';

let dataManger: Object = [{Order:100, ShipName:'Berlin', EmployeeID:2},
                         {Order:101, ShipName:'Capte', EmployeeID:3},
                         {Order:102, ShipName:'Marlon', EmployeeID:4},
                         {Order:103, ShipName:'Black pearl', EmployeeID:5},
                         {Order:104, ShipName:'Pearl', EmployeeID:6},
                         {Order:105, ShipName:'Noth bay', EmployeeID:7},
                         {Order:106, ShipName:'baratna', EmployeeID:8},
                         {Order:107, ShipName:'Charge', EmployeeID:9}]; 

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: employeeData,
      childGrid: {
        dataSource: dataManger,
        queryString: 'EmployeeID',
        columns: [
            { field: 'Order', headerText: 'Order ID', textAlign: 'Right', width: 120 },
            { field: 'EmployeeID', headerText: 'Employee ID', width: 150 },
            { field: 'ShipName', headerText: 'Ship Name', width: 150 }
        ]
      }
    };
  },
  methods: {
    rowDataBound(args){
      let filter:string = args.data.EmployeeID;
      let childrecord: any = new DataManager(this.$refs.Grid.childGrid.dataSource).executeLocal(new Query().where("EmployeeID", "equal", parseInt(filter), true));
      if(childrecord.length == 0) { 
        //here hide which parent row has no child records
        args.row.querySelector('td').innerHTML=" ";
        args.row.querySelector('td').className = "e-customizedExpandcell";
      }
    }
  },
  provide: {
    grid: [DetailRow]
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
  .e-row[aria-selected="true"] .e-customizedExpandcell {
      background-color: #e0e0e0;
  }

  .e-grid.e-gridhover tr[role='row']:hover {
      background-color: #eee;
  }
</style>

```

{% endtab %}