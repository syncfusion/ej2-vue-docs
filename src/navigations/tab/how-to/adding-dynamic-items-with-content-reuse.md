---
title: "Adding dynamic items with content reuse"
component: "Tab"
description: "This example demonstrates how to add the Essential JS 2 Tabs component with vue component content reuse."
---

# Adding dynamic items with content reuse

You can add dynamic tabs by reusing the content using Vue **template**. Tabs can be added dynamically by passing array of items and index value to the [`addTab`](../../api/tab#addtab) method.

Content reuse can be achieved by using the following steps:
1. Declare a template in the **template** section of the “.vue” file. An empty object “data” needs to be initialized in the data option of the default export object in **script** section.
2. The template function needs to be assigned to the content property of the EJ2 Vue Tab Component.
3. Provide separate template function for each vue component
and pass content by dynamically adding tab. It will reuse the content of vue component.

Refer to the following sample.

{% tab template="tab/how-to/content-reuse", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <button id="add" class="e-btn" v-on:click="addButtonClicked">Click to add</button>
    <button id="remove" class="e-btn" v-on:click="removeButtonClicked">Click to remove</button>
    <ejs-tab id="tabElement" ref=tabObj>
                <e-tabitems>
                    <e-tabitem :header='DatePickerHeaderText' :content='DatePickerTemplate'></e-tabitem>
                    <e-tabitem :header='DropdownHeaderText' :content='DropDownTemplate'></e-tabitem>
                    <e-tabitem :header='ReusedDropdownHeaderText' :content='DropDownTemplate'></e-tabitem>
                </e-tabitems>
            </ejs-tab>
  </div>
</template>
<script>
import Vue from 'vue';
import { TabPlugin } from '@syncfusion/ej2-vue-navigations';
import { DatePickerComponent, DatePickerPlugin } from '@syncfusion/ej2-vue-calendars';
import { DropDownListComponent, DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(TabPlugin);
Vue.component(DatePickerPlugin.name, DatePickerComponent);
Vue.component(DropDownListPlugin.name, DropDownListComponent);
export default {
  name: 'app',
  data: function () {
    return {
      DatePickerHeaderText: { text: "DatePicker" },
      DropdownHeaderText: { text: "Dropdown" },
      ReusedDropdownHeaderText: { text: "Reused Dropdown" },
      DatePickerTemplate: function () {
        return {
          template: Vue.component("DatePickerComponent", {
            template:
              "<div><h1>{{target}} Content</h1><br /><ejs-datepicker></ejs-datepicker></div>",
            data() {
              return {
                target: document.querySelector(
                  ".e-toolbar-item.e-active .e-tab-text"
                ).innerHTML,
              };
            },
          }),
        };
      },
      DropDownTemplate: function () {
        return {
          template: Vue.component("DropDownListComponent", {
            template:
              "<div><h1>{{target}} Content</h1><br /><ejs-dropdownlist height='200px' :dataSource='sportsData' placeholder='Select a game'></ejs-dropdownlist></div>",
            data() {
              return {
                sportsData: [
                  "Badminton",
                  "Basketball",
                  "Cricket",
                  "Golf",
                  "Hockey",
                  "Rugby",
                ],
                target: document.querySelector(
                  ".e-toolbar-item.e-active .e-tab-text"
                ).innerHTML,
              };
            },
          }),
        };
      },
    };
  },
  methods: {
    addButtonClicked: function (e) {
      var tabObj = this.$refs.tabObj.ej2Instances;
      let newTabItem = {
        header: { text: "DynamicTabItem" },
        content: this.DropDownTemplate,
      };
      tabObj.addTab([newTabItem], 1);
    },
    removeButtonClicked: function (e) {
      var tabObj = this.$refs.tabObj.ej2Instances;
      tabObj.removeTab(1);
    },
  },
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