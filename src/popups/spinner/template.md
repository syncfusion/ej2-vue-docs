---
title: "Template"
component: "Spinner"
description: "This example demonstrates how to customize the Essential JS 2 Spinner control based on different needs."
---

# Set the template to the Spinner

You can use custom templates on the Spinner instead of the default Spinner by specifying the template in the `setSpinner` method.

The following steps explains you on how to define template for Spinner.

* Import the `setSpinner` method from `ej2-vue-popups` library into your `vue` as shown in below.

```typescript
import { setSpinner } from '@syncfusion/ej2-vue-popups';
```

* Pass your custom template to the `setSpinner` method like as below.

```typescript

// Specify the template content to be displayed in the Spinner

setSpinner({ template: '<div style="width:100%;height:100%" class="custom-rolling"><div></div></div>'});
```

> You should set the template to the Spinner before creating the respective Essential JS 2 component.
> Also,until we replace `setSpinner` template, the further Essential JS 2 component rendering is created
> with given template only.

* Now, render the Essential JS 2 component. It's render the Spinner with the template specified in the `setSpinner` method.

> In the below sample, we have rendered the Grid component with custom Spinner using `setSpinner` method.
> You have to define the styles for the template in `index.css`.

{% tab template="spinner/setspinner", isDefaultActive=true %}

```html
<template>
   <div id="app">
     <ejs-grid  ref='elementRef1' id='grid1'  :dataSource="data" :created='onGridCreated'>
     <e-columns>
      <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
      <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
      <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
     </e-columns>
    </ejs-grid>
         <br/>
        <br/>
      <ejs-grid  ref='elementRef2' id='grid2'  :dataSource="data" >
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
        setSpinner({ template: '<div style="width:100%;height:100%" class="custom-rolling"><div></div></div>' });
       },
    }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";

         .e-spinner-pane.e-spin-hide {
             display: block;
        }
        @keyframes custom-rolling {
            0% {
                -webkit-transform: translate(-50%, -50%) rotate(0deg);
                transform: translate(-50%, -50%) rotate(0deg);
            }
            100% {
                -webkit-transform: translate(-50%, -50%) rotate(360deg);
                transform: translate(-50%, -50%) rotate(360deg);
            }
          }

          @-webkit-keyframes custom-rolling {
            0% {
                -webkit-transform: translate(-50%, -50%) rotate(0deg);
                transform: translate(-50%, -50%) rotate(0deg);
            }
            100% {
                -webkit-transform: translate(-50%, -50%) rotate(360deg);
                transform: translate(-50%, -50%) rotate(360deg);
            }
          }

          .custom-rolling {
            position: relative;
          }

          .custom-rolling div,
          .custom-rolling div:after {
            border: 16px solid #51CACC;
            border-radius: 50%;
            border-top-color: transparent;
            height: 160px;
            position: absolute;
            width: 160px;
          }

          .custom-rolling div {
            -webkit-animation: custom-rolling 1.3s linear infinite;
            animation: custom-rolling 1.3s linear infinite;
            top: 100px;
            left: 100px;
          }

          .custom-rolling div:after {
            -ms-transform: rotate(90deg);
            -webkit-transform: rotate(90deg);
            transform: rotate(90deg);
          }

          .custom-rolling {
            -webkit-transform: translate(-31px, -31px) scale(0.31) translate(31px, 31px);
            height: 62px !important;
            transform: translate(-31px, -31px) scale(0.31) translate(31px, 31px);
            width: 62px !important;
          }
</style>

```

{% endtab %}