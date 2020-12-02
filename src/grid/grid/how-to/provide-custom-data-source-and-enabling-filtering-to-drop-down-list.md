---
title: "Provide custom data source and enabling filtering to DropDownList"
component: "Grid"
description: "Learn how to Provide custom data source and enabling filtering to DropDownList."
---

# Provide custom data source and enabling filtering to DropDownList

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
