---
title: "Custom indication for unsaved value"
component: "In-place Editor"
description: "Learn how to add a custom indication to the unsaved value of the Essential JS 2 Vue In-place Editor component."
---

# Add custom indication to unsaved value

You can add custom indication to unsaved input value by using the [actionSuccess](../../api/inplace-editor/#actionsuccess) event, when data not submitted to the server.

In this sample, the `actionSuccess` event configured and the [URL](../../api/inplace-editor/#url) property not included. Then submit button clicked, the current editor value saved into input and data sending to server action prevented due to the `URL` property not configured.

But [actionSuccess](../../api/inplace-editor/#actionsuccess) event will trigger the handler function with `null` argument values. In handler function data property [primaryKey](../../api/inplace-editor/#primarykey) value checked, whether it empty or not. If it is empty custom class, added in the `e-value-wrapper` element to customize its styles.

> To send input value to local, set the `URL` property as empty.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```typescript
<template>
<div id="app">
    <table class="table-section">
        <tr>
           <td>Enter your name: </td>
           <td>
        <ejs-inplaceeditor ref="editObj" id="inplace_editor" mode="Inline" type="Text" value="Andrew" :actionSuccess="actionSuccess" submitOnEnter= "true">
        </ejs-inplaceeditor>
        </td>
    </table>
  </div>
</template>

<script>
import Vue from 'vue';
import { InPlaceEditorPlugin } from "@syncfusion/ej2-vue-inplace-editor";
import { isNullOrUndefined as isNOU } from '@syncfusion/ej2-base';

Vue.use(InPlaceEditorPlugin);

export default {
  data (){
    return {
    };
  },
    mounted: function(){
        this.editObj = this.$refs.editObj.ej2Instances;
    },
    methods: {
        actionSuccess: function(e) {
        let pk = e.data['PrimaryKey'];
        if (isNOU(pk) || pk === '') {
            document.querySelector('.e-editable-value').classList.add('e-send-error');
        }
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
.e-inplaceeditor .e-editable-value-wrapper .e-editable-value.e-send-error {
    color: red;
}
</style>
```

{% endtab %}