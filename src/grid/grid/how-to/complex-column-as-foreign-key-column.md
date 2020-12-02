---
title: "Set complex column as Foreignkey column"
component: "Grid"
description: "Learn how to set complex column as Foreignkey column."
---

# Set complex column as Foreignkey column

The following example shows how to set the complex column as foreign key column.

In the following example, `Employee.EmployeeID` is a complex column and also declared as a foreign column which shows `FirstName` column from foreign data.

{% tab template="grid/column/foreigncolumn" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' height='315'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='Employee.EmployeeID' headerText='Employee Name' width=120 foreignKeyValue='FirstName' foreignKeyField='EmployeeID' :dataSource='employeeData'></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Right' width=80></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=130  ></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, ForeignKey } from "@syncfusion/ej2-vue-grids";
import { data, employeeData } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data.slice(0, 5),
      employeeData: employeeData.slice(0, 5)
    };
  },
  provide: {
      grid: [ForeignKey]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> * For remote data, the sorting and grouping is done based on [`column.foreignKeyField`](../../api/grid/column/#foreignkeyfield) instead of
[`column.foreignKeyValue`](../../api/grid/column/#foreignkeyvalue).
> * If [`column.foreignKeyField`](../../api/grid/column/#foreignkeyfield) is not defined, then the column uses [`column.field`](../../api/grid/column/#field).