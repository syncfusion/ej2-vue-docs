---
title: "Perform aggregation in Foreign Key Column"
component: "Grid"
description: "Learn how to Perform aggregation in Foreign Key Column."
---

# Perform aggregation in Foreign Key Column

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
