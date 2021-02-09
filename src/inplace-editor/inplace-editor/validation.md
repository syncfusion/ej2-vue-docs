---
title: "Validation"
component: "In-place Editor"
description: "Learn how to add rules and to use validation, and then customize the error message in the Essential JS 2 Vue In-place Editor component."
---

# Validation

In-place Editor component supports validation and it can be achieved by adding rules to the [validationRules](../api/inplace-editor/#validationrules) property, its child property `key` must be same as [name](../api/inplace-editor/#name) property, otherwise validation not performed. Submitting data to the server or calling the [validate](../api/inplace-editor/#validate) method validation executed.

## Validation Rules

In-place Editor has following validation rules, which are used to perform validation.

| Rules | Description | Example |
|------|------|------|
| `required` | The input element must have any input values | a or 1 or - |
| `email` | The input element must have valid `email` format values | <inplace@syncfusion.com> |
| `url` | The  input element must have valid `url` format values| <http://syncfusion.com/> |
| `date` | The  input element must have valid `date` format values | 12/25/2019 |
| `dateIso` | The  input element must have valid `dateIso` format values | 2019-12-25 |
| `number` | The  input element must have valid `number` format values | 1.0 or 1 |
| `maxLength` | Input value must have less than or equal to `maxLength` character length | if `maxLength: 5`, [check] is valid and [checking] is invalid |
| `minLength` | Input value must have less than or equal to `minLength` character length | if `minLength: 5`, [testing] is valid and [test] is invalid |
| `rangeLength` | Input value must have value between `rangeLength` character length | if `rangeLength: [4,5]`, [test] is valid and [key] is invalid
| `range` | Input value must have value between `range` number | if `range: [4,5]`, [4] is valid and [6] is invalid |
| `max` | Input value must have less than or equal to `max` number | if `max: 3`, [3] is valid and [4] is invalid |
| `min` | Input value must have less than or equal to `min` number | if `min: 4`, [5] is valid and [2] is invalid |
| `regex` | Input value must have valid `regex` format | if `regex: '^[A-z]+$'`, [a] is valid and [1] is invalid |

## Step by Step validation configuration

The following steps are used to configure validation in In-place Editor.

Step 1: To perform default validation in In-place Editor the `name` property is mandatory. And the specified name must be the same as the key name.

Step 2:  The corresponding name specified in the name property should bind with the `validationRules` property. For example, in the below code snippet, the `Number`  in the name property is bind with the `maxLength`  of validationRules.  Likewise, you can bind with the in-build validation configurations in the above table.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html
<template>
  <div>
    <table class="table-section">
            <tr>
                <td>
                    <ejs-inplaceeditor  mode="Inline" type="Numeric" name= "Number" :validationRules="ValidationRules">
                    </ejs-inplaceeditor>
                </td>
            </tr>
            </table>
  </div>
</template>
<script>
import Vue from 'vue';
import { InPlaceEditorPlugin } from '@syncfusion/ej2-vue-inplace-editor';

Vue.use(InPlaceEditorPlugin);

export default {
   name: 'app',
  data: function() {
    return {
            ValidationRules: {
                Number: { maxLength: 5 },
            },
    };
  },
};
</script>

```

{% endtab %}

In the following sample, first editor value submitted without select any date, so the default error message will be displayed below the `DatePicker` element. Second editor configured with the [validating](../api/inplace-editor/#validating) event with the handler. In handler event [errorMessage](../api/inplace-editor/validateEventArgs/#errormessage) argument value modified and it will show below the `DatePicker` element.

{% tab template="in-place-editor/getting-started", isDefaultActive=true %}

```html

          <template>
    <div id="app">
        <table class="table-section">
            <tr>
                <td>Default Error Message </td>
                <td>
                    <ejs-inplaceeditor ref="dateObj" id="datePickerEle" mode="Inline" type="Date"  emptyText="dd/mm/yyyy" :model="datePickerModel" name= "Today" :validationRules="dateValidationRules">
                    </ejs-inplaceeditor>
                </td>
            </tr>
            <tr>
                <td class="sample-td">Customized Error Message </td>
                <td class="sample-td">
                     <ejs-inplaceeditor ref="dateObj1" id="datePickerEle" mode="Inline" type="Date" :model="datePickerModel" name= "date" :validationRules="dateValidationRule" :validating="valid"  emptyText="dd/mm/yyyy">
                    </ejs-inplaceeditor>
                </td>
            </tr>
        </table>
    </div>
</template>

<script>
import Vue from 'vue';
import { InPlaceEditorPlugin } from '@syncfusion/ej2-vue-inplace-editor';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(InPlaceEditorPlugin);
Vue.use(DropDownListPlugin);

export default {
  name: 'app',
      data () {
        return {
            datePickerModel: {
                placeholder: 'Select a date',
            },
            dateValidationRules: {
                Today: { required: true },
            },
            dateValidationRule: {
                date: { required: true },
            },
        };
    },
    mounted: function(){
        this.dateObj = this.$refs.dateObj.ej2Instances;
        this.dateObj1 = this.$refs.dateObj1.ej2Instances;
    },
    methods: {
        valid: function(e) {
            e.errorMessage = "empty field";
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
    text-align: center;
    margin-top: 50px;
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

* For more details about validation configuration, refer this documentation [section](https://ej2.syncfusion.com/documentation/api/form-validator/).

* For custom validation except specifying validationRules, specify errorMessage at validating event, message will be shown when the value is `Empty`.

## See Also

* [Indication to unsaved value](./how-to/custom-indication)