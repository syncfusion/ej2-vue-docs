---
title: "Custom animation for popup mode"
component: "In-place Editor"
description: "Learn how to configure custom animation for popup and customize it dynamically in the Essential JS 2 Vue In-place Editor component."
---

# Set custom animation for popup mode

In popup mode, the In-place Editor rendered with the Essential JS 2 `Tooltip` component. You can use tooltip properties and events to customize the popup by configure properties into the [model](../../api/inplace-editor/popupSettings/#model) property inside the [popupSettings](../../api/inplace-editor/popupSettings/) API.

In the following sample, popup animation can be customized by passing animation effect using the [model](../../api/inplace-editor/popupSettings/#model) property and the dynamic animation effect changes configured from the Essential JS 2 Vue `DropDownList` component `change` event.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html

<template>
<div id="app">
    <table class="table-section">
        <tr>
            <td>Open Animation:</td>
            <td>
         <ejs-dropdownlist ref="editorMode" id="editorMode" width='90%' :dataSource='dataPlace' :change='valueChange' :value='dataValue' :fields='placeFields'>
         </ejs-dropdownlist>
         </td>
        </tr>
        <tr>
            <td class="sample-td">Enter your name:</td>
            <td class="sample-td">
               <ejs-inplaceeditor ref="editObj" id="inplace_editor" mode="Popup" type="Text" value="Andrew" submitOnEnter= "true" :model="textModel" :popupSettings=textPopupSettings>
              </ejs-inplaceeditor>
            </td>
        </tr>
    <table>
  </div>
</template>

<script>
import Vue from 'vue';
import { InPlaceEditorPlugin } from "@syncfusion/ej2-vue-inplace-editor";
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(InPlaceEditorPlugin);
Vue.use(DropDownListPlugin);

export default {
  data (){
    return {
        placeFields: { text: 'data', value: 'id' },
        dataPlace: [{ id: 'None', data: 'None' }, { id: 'FadeIn', data: 'FadeIn' }, { id: 'FadeZoomIn', data: 'FadeZoomIn'}, { id: 'ZoomIn', data: 'ZoomIn' }],
        dataValue: 'ZoomIn',
        textModel: {
            placeholder: 'Enter some text'
        },
        textPopupSettings: {
            title: 'Enter Employee Name',
            model: {
                animation: {
                    open: { effect: 'ZoomIn', duration: 1000, delay: 0 }
                }
            }
        },
    };
  },
    mounted: function(){
        this.editObj = this.$refs.editObj.ej2Instances;
    },
    methods: {
        valueChange: function(e) {
            this.$refs.editObj.popupSettings.model.animation.open.effect = e.value;
            this.$refs.editObj.dataBind();
        }
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-lists/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-splitbuttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inplace-editor/styles/material.css";

.table-section {
    margin: 0 auto;
}

tr td:first-child {
    text-align: right;
    padding-right: 20px;
}

.sample-td {
    padding-top: 10px;
    min-width: 230px;
    height: 100px;
}
</style>
```

{% endtab %}