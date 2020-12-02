---
title: "Customize filter UI in foreign key column"
component: "Grid"
description: "Learn how to Customize filter UI in foreign key column."
---

# Customize filter UI in foreign key column

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
