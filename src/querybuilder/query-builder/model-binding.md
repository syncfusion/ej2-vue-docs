---
title: "Model Binding"
component: "QueryBuilder"
description: "Documentation on model binding in the Essential JS 2 QueryBuilder control."
---

# Model Binding

Model binding allows to bind properties for the components used in field, operator, and value columns. To implement model binding, assign fieldModel, operatorModel, and valueModel properties in QueryBuilder.

{% tab template="query-builder/model-binding", sourceFiles="model-binding.vue" %}

```html
<template>
    <div class="control-section">
            <ejs-querybuilder id="querybuilder" ref="querybuilder" :dataSource="dataSource" :rule="importRules" enableNotCondition = true :fieldModel = "{allowFiltering: true, popupHeight: '500px'}" :operatorModel = "{allowFiltering: true, popupHeight: '400px'}" :valueModel = "{numericTextBoxModel:
        {
            cssClass: 'e-custom'
        },
        multiSelectModel: {
            cssClass: 'e-custom'
        },
        datePickerModel: {
            cssClass: 'e-custom'
        },
        textBoxModel: {
            cssClass: 'e-custom'
        },
        radioButtonModel: {
            cssClass: 'e-custom'
        }}">
                <e-columns>
                    <e-column field="EmployeeID" label="Employee ID" type="number"/>
                    <e-column field="FirstName" label="First Name" type="string"/>
                    <e-column field="Age" label="Age" type="number" />
                    <e-column field='City' label='City' type='string' />
                    <e-column field='Country' label='Country' type='string' />
                </e-columns>
            </ejs-querybuilder>
            </div>
  </template>

<script>
import Vue from "vue";
import { QueryBuilderPlugin } from '@syncfusion/ej2-vue-querybuilder';
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
import { getComponent, compile,closest } from '@syncfusion/ej2-base';
import { DataManager, Predicate, Query } from '@syncfusion/ej2-data';
import { CheckBoxPlugin, ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { DropDownButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";

Vue.use(QueryBuilderPlugin);
Vue.use(SliderPlugin);
Vue.use(DropDownListPlugin);
Vue.use(CheckBoxPlugin);
Vue.use(DropDownButtonPlugin);
Vue.use(ButtonPlugin);

export default {
    data: function() {
        return {
            dataSource: employeeData,
            importRules: {
                'condition': 'and',
                'rules': [{
                    'label': 'Employee ID',
                    'field': 'EmployeeID',
                    'type': 'number',
                    'operator': 'equal',
                    'value': 1001
                }]
            }
        };
    }  
}

var employeeData = [
    { 'EmployeeID': 1, 'FirstName': 'Nancy', 'Age': 31, 'City': 'Seattle', 'Country': 'USA' },
    { 'EmployeeID': 2, 'FirstName': 'Andrew', 'Age': 32, 'City': 'Tacoma', 'Country': 'USA' },
    { 'EmployeeID': 3, 'FirstName': 'Janet', 'Age': 33, 'City': 'Kirkland', 'Country': 'USA' },
    { 'EmployeeID': 4, 'FirstName': 'Margaret', 'Age': 33, 'City': 'Redmond', 'Country': 'USA' },
    { 'EmployeeID': 5, 'FirstName': 'Steven', 'Age': 34, 'City': 'London', 'Country': 'UK' },
    { 'EmployeeID': 6, 'FirstName': 'Michael', 'Age': 35, 'City': 'London', 'Country': 'UK' },
    { 'EmployeeID': 7, 'FirstName': 'Robert', 'Age': 36, 'City': 'London', 'Country': 'UK' },
    { 'EmployeeID': 8, 'FirstName': 'Laura', 'Age': 37, 'City': 'Seattle', 'Country': 'USA' },
    { 'EmployeeID': 9, 'FirstName': 'Anne', 'Age': 38, 'City': 'London', 'Country': 'UK' }
]

</script>
<style>
    @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-lists/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-vue-querybuilder/styles/material.css";

</style>
```

{% endtab %}