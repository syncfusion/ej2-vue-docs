---
title: "Complex Data Binding with list of Array Of Objects"
component: "Grid"
description: "Learn how to set Complex data for datasource having Array Of Objects."
---

# Complex Data Binding with list of Array Of Objects

The following example shows how to set Complex field for datasource having Array Of Objects.

{% tab template="grid/column/complex" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :height='315'>
            <e-columns>
                <e-column field='EmployeeID' headerText='Employee ID' textAlign='Right' width=120></e-column>
                <e-column field='Names.0.FirstName' headerText='First Name' width=120></e-column>
                <e-column field='Names.0.LastName' headerText='Last Name' width=120></e-column>
                <e-column field='Title' headerText='Title' width=150></e-column>
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
      data: data.slice(0, 5)
    };
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}