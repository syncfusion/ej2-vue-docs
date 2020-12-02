---
title: "Render other components in Accordion using template"
component: "Accordion"
description: "This example demonstrates how to render other Essential JS 2 components into Essential JS 2 Accordion component content using template."
---

# Render other components in Accordion using template

You can render other components inside Accordion using Vue **template**. Through this, we can add content as other components directly with all functionalities to our Accordion. Follow the below guidelines for using the other components as template in Accordion.

* Declare a template in the **template** section of the “.vue” file. An empty object “data” needs to be initialized in the data option of the default export object in **script** section.

* The template function needs to be assigned to the content property of the EJ2 Vue Accordion Component.

{% tab template="accordion/how-to/direct-components", isDefaultActive=true %}

```html
<template>
    <div id="app">
   <ejs-accordion >
        <e-accordionitems>
        <e-accordionitem expanded='true' header='Calender' :content='Template1'></e-accordionitem>
        <e-accordionitem header='DatePicker' :content='Template2'></e-accordionitem>
        <e-accordionitem header='Numeric Textbox' :content='Template3'></e-accordionitem>
      </e-accordionitems>
    </ejs-accordion>
  </div>
</template>
<script>
import Vue from 'vue';
import { AccordionPlugin } from "@syncfusion/ej2-vue-navigations";
Vue.use(AccordionPlugin);
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
          template: Vue.component('CalenderComponent', {
            template: '<ejs-calendar ></ejs-calendar>',
            data() { return {  }; }
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
      Template3: function () {
        return {
          template: Vue.component('NumericTextBoxComponent', {
            template: '<ejs-numerictextbox value="100"></ejs-numerictextbox>',
            data() { return { }; }
          })
        }
      }
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