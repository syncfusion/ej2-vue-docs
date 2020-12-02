---
title: "Render other components in Toolbar using template"
component: "Toolbar"
description: "This example demonstrates how to render other Essential JS 2 components into Essential JS 2 Toolbar component content using template."
---

# Render other components in Toolbar using template

You can render other components inside Toolbar using Vue **template**. Through this, we can add content as other components directly with all functionalities to our Toolbar. Follow the below guidelines for using the other components as template in Toolbar.

* Declare a template in the **template** section of the “.vue” file. An empty object “data” needs to be initialized in the data option of the default export object in **script** section.

* The template function needs to be assigned to the content property of the EJ2 Vue Toolbar Component.

{% tab template="toolbar/how-to/direct-components", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-toolbar >
           <e-items>
             <e-item :template='Template1' ></e-item>
             <e-item text='Italic' ></e-item>
             <e-item text='Underline' ></e-item>
             <e-item type='Separator'></e-item>
             <e-item :template='Template2'></e-item>
          </e-items>
      </ejs-toolbar>
  </div>
</template>
<script>
import Vue from 'vue';
import { ToolbarPlugin } from '@syncfusion/ej2-vue-navigations';
Vue.use(ToolbarPlugin);
import { DatePickerComponent,CalendarComponent, DatePickerPlugin,CalendarPlugin } from '@syncfusion/ej2-vue-calendars';
Vue.use(DatePickerPlugin);
Vue.use(CalendarPlugin);
import { NumericTextBoxComponent,NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(NumericTextBoxPlugin);

export default {
  name: 'app',
  data: function(){
    return {
      Template1: function () {
        return {
          template: Vue.component('NumericTextBoxComponent', {
            template: '<ejs-numerictextbox value="10"></ejs-numerictextbox>',
            data() { return { }; }
          })
        }
      },
        Template2: function () {
        return {
          template: Vue.component('DatePickerComponent', {
            template: ' <ejs-datepicker :min="minDate" :max="maxDate" :value="dateVal" ></ejs-datepicker>',
            data() { return { minDate : new Date("05/09/2017"),
                             maxDate : new Date("05/15/2017"),
                             dateVal : new Date("05/11/2017") }; }
          })
        }
      },

   }
 }
}
</script>

<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
</style>

```

{% endtab %}