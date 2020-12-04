---
title: "Integrate HTML5 components"
component: "In-place Editor"
description: "Learn how to configure template and integrate HTML5 components, get and pass a modified value to the server in the Essential JS 2 Vue In-place Editor component."
---

# Integrate HTML5 components (Template)

The In-place Editor supports adding HTML5 input components using the [template](../api/inplace-editor/#template) property. The Template property can be given as either a `string` or a `query selector`.

## As a string

The HTML element tag can be given as a string for the template property. Here, the input is rendered as an HTML template.

```typescript
template: "<div><input type='text' id='name'></input></div>"

```

## As a selector

The template property also allows getting template content through query `selector`. Here, the input wrapper element 'ID' attribute is specified in the template.

```typescript
template: "#date"

```

## As a template

You can render other components inside In-place Editor using Vue template . Follow the below guildlines for using other the components as template in In-place Editor.

Declare a template in the template section of the “.vue” file. An empty object “data” needs to be initialized in the data option of the default export object in script section.

The template function needs to be assigned to the template property of the EJ2 Vue In-place Editor Component.

Template mode, the `value` property not handled by the In-place Editor component. So, before sending a value to the server, you need to modify at [actionBegin](../api/inplace-editor/#actionbegin) event, otherwise, an empty string will pass. In the following template sample, before submitting a data to the server, event argument and [value](../api/inplace-editor/#value) property content updated in the `actionBegin` event handler.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html
<template>
<div class="app">
    <table class="table-section">
        <tr>
            <td>Select date:</td>
        <td>
            <ejs-inplaceeditor ref="dropObj" id="dropdownEle" mode="Inline" :template = "Template1" value="1/2/2018" :actionBegin="actionBegin" actionOnBlur="ignore">
            </ejs-inplaceeditor>
      </td>
      </tr>
    </table>
    </div>
</template>

<script>
import Vue from 'vue';
import { InPlaceEditorPlugin } from "@syncfusion/ej2-vue-inplace-editor";
import { DatePickerComponent, DatePickerPlugin } from '@syncfusion/ej2-vue-calendars';
import { isNullOrUndefined as isNOU } from '@syncfusion/ej2-base';

Vue.component(DatePickerPlugin.name, DatePickerComponent);
Vue.use(InPlaceEditorPlugin);

export default {
  name: 'app',
      data () {
        return {
            Template1: function () {
                return {
                    template: Vue.component('DatePickerComponent', {
                        template: ' <ejs-datepicker value="1/2/2018"></ejs-datepicker>',
                        data() { return { }; }
                    })
                }
            }
        }
    },
    mounted: function() {
   this.dropObj = this.$refs.dropObj.ej2Instances;
    },
    methods: {
        actionBegin: function(args) {
           var date = (document.getElementsByClassName('e-datepicker')[0]).ej2_instances[0].value;
           if(!(isNOU(date))) {
                this.$refs.dropObj.ej2Instances.value = date.toLocaleDateString();
                args.data.value = date;
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
    margin-top: 45px;
}

tr td:first-child {
    text-align: right;
    padding-right: 20px;
}
</style>

```

{% endtab %}

## See Also

* [Built-in Components](./components/)