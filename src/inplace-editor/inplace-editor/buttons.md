---
title: "Buttons"
component: "In-place Editor"
description: "Learn how to show or hide buttons, customize its behavior, and the appearance in the Essential JS 2 Vue In-place Editor component."
---

# Buttons

The In-place Editor had an action for save and cancel using buttons. The [saveButton](../api/inplace-editor/#savebutton) and [cancelButton](../api/inplace-editor/#cancelbutton) properties accept the [ButtonModel](../api/button/buttonModel/) objects for customizing the save and cancel button properties.

Buttons can be show or hide by sets a Boolean value to the [showButtons](../api/inplace-editor/#showbuttons) property.

> Without buttons value will be processed via the following ways.

* **[actionOnBlur](../api/inplace-editor/#actiononblur)**: By clicking out side the editor component get focus out and do action based on this property value.
* **[submitOnEnter](../api/inplace-editor/#submitonenter)**: Pressing `Enter` key it performs the submit action, if this property set to `true`.

In the following sample, the [content](../api/button#content) and [cssClass](../api/button#cssclass) properties of `Button` value assigned to the [saveButton](../api/inplace-editor/#savebutton) and [cancelButton](../api/inplace-editor/#cancelbutton) properties to customize its appearance. Also check or uncheck a checkbox buttons render or removed from the editor.

To restrict either save or cancel button rendering into a DOM, simply pass empty object `{}` in the  `saveButton` or `cancelButton` properties.

> For more details about buttons, refer this documentation [section](../button/).

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html
<template>
<div id="app">
    <table class="table-section">
        <tr>
            <td>ShowButtons:</td>
            <td>
        <ejs-checkbox ref="checkObj" id="showbuttons" checked=true :change="onChange" :labelPosition="labelPosition" :label="label"></ejs-checkbox>
        </td>
    </tr>
    <tr>
        <td class="sample-td">Enter your name:</td>
        <td class="sample-td">
      <ejs-inplaceeditor ref="editObj" mode="Inline" :model="textModel" type="Text" value="Andrew" data-underline="false">
      </ejs-inplaceeditor>
      </td>
    </tr>
    </div>
</template>

<script>
import Vue from 'vue';
import { InPlaceEditorPlugin } from '@syncfusion/ej2-vue-inplace-editor';
import { CheckBoxPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(InPlaceEditorPlugin);
Vue.use(CheckBoxPlugin);

export default {
  name: 'app',
      data () {
        return {
            textModel: {
                placeholder: 'Enter Some Text'
            },
            labelPosition: 'Before',
            label: 'show',
        };
    },
    mounted: function() {
    this.editObj = this.$refs.editObj.ej2Instances;
    },
    methods: {
        onChange: function(args) {
        args.checked ? this.editObj.showButtons = true : this.editObj.showButtons = false
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

## See Also

* [In-place editor buttons](./how-to/dynamic-edit-mode)