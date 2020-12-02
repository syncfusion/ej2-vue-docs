---
title: "State Persistence"
component: "Grid"
description: "Learn how to persist the DataGrid state and model in the browser’s local storage."
---

# State Persistence

State persistence refers to the Grid's state maintained in the browser's
[`localStorage`](https://www.w3schools.com/html/html5_webstorage.asp#)
even if the browser is refreshed or if you move to the next page within the browser.
State persistence stores grid’s model object in the local storage when the
[`enablePersistence`](../api/grid/#enablepersistence) is defined as true.

## Maintaining Custom Query in State Persistence

Grid does not maintain the query params after page load event when
[`enablePersistence`](../api/grid/#enablepersistence) is set to true.
This is because the Grid refreshes its query params for every page load. You can maintain the custom query params by resetting the
`addParams`
method in the [`actionBegin`](../api/grid/#actionbegin) event.

{% tab template="grid/sort/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref="grid" :dataSource='data' :allowSorting='true' :enablePersistence='true' :allowPaging='true' :allowFiltering='true' height='210px' :actionBegin='actionHandler'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Sort, Page, Filter } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  methods: {
    actionHandler: function (){
        this.$refs.grid.ej2Instances.query.addParams('$filter', 'EmployeeID eq 1');
    }
  }
  provide: {
    grid: [Sort, Page, Filter]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## How to get or set localStorage value

If the [`enablePersistence`](../api/grid/#enablepersistence) property set as true,
The Grid property value is saved in the `window.localStorage` for reference. You can get/set the localStorage value by using the
`getItem`/`setItem` method in `window.localStorage`.

```typescript
//get the Grid model.
let value = window.localStorage.getItem('gridGrid'); //"gridGrid" is component name + component id.
let model = JSON.parse(model);

```

```typescript
//set the Grid model.
window.localStorage.setItem('gridGrid', JSON.stringify(model)); //"gridGrid" is component name + component id.

```
