---
title: "Use Edit Template in Foreign Key Column"
component: "Grid"
description: "Learn how to Use Edit Template in Foreign Key Column."
---

# Use Edit Template in Foreign Key Column

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
