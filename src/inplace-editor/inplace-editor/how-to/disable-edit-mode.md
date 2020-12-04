---
title: "Disable the edit mode specifically"
component: "In-place Editor"
description: "Learn how to disable the edit mode in the Essential JS 2 Vue In-place Editor component."
---

# Disable the edit mode specifically

The edit mode of In-place Editor can be disabled by setting the [disabled](../../api/inplace-editor/#disabled) property value to `true`. In the following sample, when check or uncheck the checkbox, In-place Editor component will disable or enable the edit mode.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html
<template>
<div id="app">
<table class="table-section">
    <tr>
        <td>
            <div>Disabled</div>
        </td>
        <td>
            <div>
                <ejs-checkbox ref="checkObj2" id="editorEnable" :change="onChangeEnable" label='Disable'></ejs-checkbox>
                </div>
        </td>
    </tr>
    <tr>
        <td class="sample-td">
            <div>Enter your name: </div>
        </td>
        <td class="sample-td">
            <ejs-inplaceeditor ref="editObj" id="inplace_editor" mode="Inline" type="Text" actionOnBlur='Ignore' value="Andrew" submitOnEnter= "true">
            </ejs-inplaceeditor>
        </td>
    </tr>
  </table>
  </div>
</template>

<script>
import Vue from 'vue';
import { InPlaceEditorPlugin } from "@syncfusion/ej2-vue-inplace-editor";
import { CheckBoxPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(InPlaceEditorPlugin);
Vue.use(CheckBoxPlugin);

export default {
  data (){
    return {
       labelPosition: 'Before',
    };
  },
    mounted: function(){
        this.editObj = this.$refs.editObj.ej2Instances;
    },
    methods: {
        onChangeEnable: function(args) {
            var checkObj1 = this.$refs.checkObj2.ej2Instances;
            checkObj1.checked ? this.editObj.disabled = true : this.editObj.disabled = false;
        },
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