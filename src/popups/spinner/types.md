---
title: "Types"
component: "Spinner"
description: "This example demonstrates how to change the type of the Essential JS 2 Spinner control based on theme."
---

# Change the type of the Spinner

By default, the Spinner is loaded in the applicable Essential JS 2 component based on the theme imported into
the page. Based on the theme, the type is set to the Spinner.

The available types are:
* Material
* Fabric
* Bootstrap

You can change the Essential JS 2 component spinner type by passing the type of the spinner as parameter to the `setSpinner` method like as below.

```typescript

// Specify the type of the Spinner to be displayed
setSpinner({ type: 'Bootstrap'});
```

> After Essential JS 2 component creation only, you can change the Essential JS 2 component spinner type.

{% tab template="spinner/setspinner", isDefaultActive=true %}

```html
<template>
   <div id="app">
     <ejs-grid  ref='elementRef' id='grid'  :dataSource="data" :created='onGridCreated'>
     <e-columns>
      <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
      <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
      <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
     </e-columns>
    </ejs-grid>
    </div>
</template>

<script>
import Vue from "vue";
import { GridPlugin} from "@syncfusion/ej2-vue-grids";
import { setSpinner } from '@syncfusion/ej2-vue-popups';
import { orderDetails } from './datasource.ts';
Vue.use(GridPlugin);
export default {
  name: 'app',
  data: function(){
        return {
           data: orderDetails.slice(0, 7)
        }
   },
  methods: {
       onGridCreated: function(args){
           setSpinner({ type: 'Bootstrap' });
       },
    }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";

.e-spinner-pane.e-spin-hide {
        display: block;
      }
</style>

```

{% endtab %}