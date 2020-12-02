---
title: "Render other components in Tab using template"
component: "Accordion"
description: "This example demonstrates how to render other Essential JS 2 components into Essential JS 2 Tab component content using template."
---

# Render other components in Tab using template

You can render other components inside Tab using Vue **template**. Through this, we can add content as other components directly with all functionalities to our Tab. Follow the below guidelines for using the other components as template in tab.

* Declare a template in the **template** section of the “.vue” file. An empty object “data” needs to be initialized in the data option of the default export object in **script** section.

* The template function needs to be assigned to the content property of the EJ2 Vue Tab Component.

{% tab template="tab/how-to/direct-components", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-tab id="element" ref=element>
                <e-tabitems>
                    <e-tabitem :header='headerText0' :content='Template1'></e-tabitem>
                    <e-tabitem :header='headerText1' :content='Template2'></e-tabitem>
                </e-tabitems>
            </ejs-tab>
  </div>
</template>
<script>
import Vue from 'vue';
import { TabPlugin } from '@syncfusion/ej2-vue-navigations';
import { DatePickerComponent,CalendarComponent, DatePickerPlugin,CalendarPlugin } from '@syncfusion/ej2-vue-calendars';
Vue.use(TabPlugin);
Vue.use(TabPlugin);
Vue.component(DatePickerPlugin.name, DatePickerComponent);
Vue.component(CalendarPlugin.name, CalendarComponent);
export default {
  name: 'app',
  data: function(){
    return {
        headerText0: { text: 'Tab1' },
        headerText1: { text: 'Tab2' },
        headerText2: { text: 'Tab3' },
        Template1: function () {
        return {
          template: Vue.component('DatePickerComponent', {
            template: ' <ejs-datepicker :min="minDate" :max="maxDate" :value="dateVal" ></ejs-datepicker>',
            data() { return { minDate : new Date("05/09/2017"),
                             maxDate : new Date("05/15/2017"),
                             dateVal : new Date("05/11/2017") }; }
          })
        }
      },
      Template2: function () {
        return {
          template: Vue.component('DatePickerComponent', {
            template: '<ejs-calendar id="calendar" ></ejs-calendar>',
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
</style>

```

{% endtab %}