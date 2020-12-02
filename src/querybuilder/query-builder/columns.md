---
title: "Querybuilder Columns"
component: "QueryBuilder"
description: "Documentation on column step, format, labels, operators, validations, template in the Essential JS 2 QueryBuilder control."
---

# Columns

The column definitions are used as the [`dataSource`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#datasource) schema in the Query Builder. This plays a vital role in rendering column values. The query builder operations such as create or delete conditions and create or delete group they are performed based on the column definitions. The [`field`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/columnsModel/#field) property of the columns is necessary to map the data source values in the query builder columns.

> If the column field is not specified in the [dataSource](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#datasource), the column values will be empty.

## Auto generation

The [`columns`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#columns) are automatically generated when the [`columns`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#columns) declaration is empty or undefined while initializing the query builder. All the columns in the [dataSource](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#datasource) are bound as the query builder columns.

{% tab template="query-builder/default", isDefaultActive=true %}

```html
<template>
    <div class="control-section">
        <div class="col-lg-12 querybuilder-control">
            <ejs-querybuilder width="70%" :dataSource="dataSource">
            </ejs-querybuilder>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { QueryBuilderPlugin } from "@syncfusion/ej2-vue-querybuilder";
import { employeeData } from './datasource.js';
Vue.use(QueryBuilderPlugin);

export default {
    data: function() {
        return {
            dataSource: employeeData,
            values: ['Mr.', 'Mrs.']
        };
    }
}
var employeeData = [{
      'EmployeeID': 1,
      'FirstName': 'Nancy',
      'Title': 'Sales Representative',
      'TitleOfCourtesy': 'Ms.',
      'HireDate': '22/07/2001',
      'City': 'Seattle',
      'Country': 'USA'
    },
    {
      'EmployeeID': 2,
      'FirstName': 'Andrew',
      'Title': 'Vice President',
      'TitleOfCourtesy': 'Dr.',
      'HireDate': '21/04/2003',
      'City': 'Tacoma',
      'Country': 'USA'
    },
    {
      'EmployeeID': 3,
      'FirstName': 'Janet',
      'Title': 'Sales Representative',
      'TitleOfCourtesy': 'Ms.',
      'HireDate': '22/07/2001',
      'City': 'Kirkland',
      'Country': 'USA'
    }];

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
    .e-query-builder {
        margin: 0 auto;
    }
</style>
```

{% endtab %}

> When columns are auto-generated, the column type will be determined from the first record of the [`dataSource`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#datasource).

## Labels

By default, the column label is displayed from the column [`field`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/columnsModel/#field) value. To override the default label, you have to define the [`label`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/columnsModel/#label) value.

## Operators

The operator for a column can be defined in the [`operators`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/columnsModel/#operators) property.
The available operators and its supported data types are:

| Operators | Description | Supported Types |
| ------------ | ----------------------- | ------------------ |
| startswith  | Checks whether the value begins with the specified value. | String |
| endswith  | Checks whether the value ends with the specified value. | String |
| contains | Checks whether the value contains the specified value. | String |
| equal | Checks whether the value is equal to the specified value. | String Number Date Boolean |
| notequal | Checks whether the value is not equal to the specified value. | String Number Date Boolean |
| greaterthan | Checks whether the value is greater than the specified value. | Date Number |
| greaterthanorequal | Checks whether a value is greater than or equal to the specified value. | Date Number |
| lessthan | Checks whether the value is less than the specified value.| Date Number |
| lessthanorequal | Checks whether the value is less than or equal to the specified value. | Date Number |
| between | Checks whether the value is between the two-specific value. | Date  Number |
| notbetween | Checks whether the value is not between the two-specific value. | Date  Number |
| in | Checks whether the value is one of the specific values. | String  Number |
| notin | Checks whether the value is not in the specific values. | String  Number |

## Step

The Query Builder allows you to set the step values to the number fields. So that you can easily access the numeric textbox. Use the [`step`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/columnsModel/#step) property, to set the step value for number values.

## Format

The Query Builder formats date and number values. Use the [`format`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/columnsModel/#format) property to format date and number values.

{% tab template="query-builder/default" %}

```html
<template>
    <div class="control-section">
        <div class="col-lg-12 querybuilder-control">
            <ejs-querybuilder width="70%" :dataSource="dataSource" :rule="importRules">
                <e-columns>
                    <e-column field='EmployeeID' label='Employee ID' type='number' step=10 :operators="employeeOperators" />
                    <e-column field='FirstName' label='First Name' type='string' />
                    <e-column field='TitleOfCourtesy' label='Title Of Courtesy' type='boolean' :values="values"/>
                    <e-column field='Title' label='Title' type='string' />
                    <e-column field='HireDate' label='Hire Date' type='date' format='dd/MM/yyyy' />
                    <e-column field='Country' label='Country' type='string' />
                    <e-column field='City' label='City' type='string' />
                </e-columns>
            </ejs-querybuilder>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { QueryBuilderPlugin } from "@syncfusion/ej2-vue-querybuilder";
Vue.use(QueryBuilderPlugin);

export default {
    data: function() {
        return {
            dataSource: employeeData,
            values: ['Mr.', 'Mrs.'],
            importRules: {
        'condition': 'and',
        'rules': [{
            'label': 'Employee ID',
            'field': 'EmployeeID',
            'type': 'number',
            'operator': 'equal',
            'value': 1001
        },
        {
            'label': 'Hire Date',
            'field': 'HireDate',
            'type': 'date',
            'operator': 'equal',
            'value': '07/05/1991'
        }]
    },
     employeeOperators:  [
        { value: 'equal', key: 'Equal' },
        { value: 'notequal', key: 'Not Equal' },
        { value: 'in', key: 'In' },
        { value: 'notin', key: 'Not In' }
    ]
        };
    }
}
var employeeData = [{
      'EmployeeID': 1,
      'FirstName': 'Nancy',
      'Title': 'Sales Representative',
      'TitleOfCourtesy': 'Ms.',
      'HireDate': '22/07/2001',
      'City': 'Seattle',
      'Country': 'USA'
    },
    {
      'EmployeeID': 2,
      'FirstName': 'Andrew',
      'Title': 'Vice President',
      'TitleOfCourtesy': 'Dr.',
      'HireDate': '21/04/2003',
      'City': 'Tacoma',
      'Country': 'USA'
    },
    {
      'EmployeeID': 3,
      'FirstName': 'Janet',
      'Title': 'Sales Representative',
      'TitleOfCourtesy': 'Ms.',
      'HireDate': '22/07/2001',
      'City': 'Kirkland',
      'Country': 'USA'
    }];
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
    .e-query-builder {
        margin: 0 auto;
    }
</style>
```

{% endtab %}

## Validations

Validation allows you to validate the conditions and it display errors for invalid fields while using  the [`validateFields`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#validatefields) method.  To enable validation in the query builder , set the allowValidation to true. Column fields are validated after setting [`allowValidation`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#allowvalidation) as to true. So, you should manually configure the validation for Operator and, Value fields through [`validation`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/columnsModel/#validation).

Install Syncfusion `Buttons` packages using below command.

```bash
npm install @syncfusion/ej2-vue-buttons --save
```

{% tab template="query-builder/default" %}

```html
<template>
    <div class="control-section">
        <div class="col-lg-12 querybuilder-control">
            <ejs-querybuilder ref="querybuilder" width="70%" :dataSource="dataSource" allowValidation="true">
                <e-columns>
                    <e-column field='EmployeeID' label='Employee ID' type='number' validation="validateRule" />
                    <e-column field='FirstName' label='First Name' type='string' />
                    <e-column field='TitleOfCourtesy' label='Title Of Courtesy' type='boolean' :values="values"/>
                    <e-column field='Title' label='Title' type='string' validation="validateRule" />
                    <e-column field='HireDate' label='Hire Date' type='date' format='dd/MM/yyyy'  />
                    <e-column field='Country' label='Country' type='string' validation="validateRule"/>
                    <e-column field='City' label='City' type='string' validation="validateRule"/>
                </e-columns>
            </ejs-querybuilder>
             <ejs-button cssClass="e-qb-button" :isPrimary="true" v-on:click.native="btnClick">Validate Fields</ejs-button>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { QueryBuilderPlugin } from "@syncfusion/ej2-vue-querybuilder";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(ButtonPlugin);
Vue.use(QueryBuilderPlugin);

export default {
    data: function() {
        return {
            dataSource: employeeData,
             values: ['Mr.', 'Mrs.'],
            validateRule: { isRequired: true }
        };
    },
    methods: {
    btnClick: function(event) {
     this.$refs.querybuilder.$el.ej2_instances[0].validateFields();
    }
  }

}
var employeeData = [{
      'EmployeeID': 1,
      'FirstName': 'Nancy',
      'Title': 'Sales Representative',
      'TitleOfCourtesy': 'Ms.',
      'HireDate': '22/07/2001',
      'City': 'Seattle',
      'Country': 'USA'
    },
    {
      'EmployeeID': 2,
      'FirstName': 'Andrew',
      'Title': 'Vice President',
      'TitleOfCourtesy': 'Dr.',
      'HireDate': '21/04/2003',
      'City': 'Tacoma',
      'Country': 'USA'
    },
    {
      'EmployeeID': 3,
      'FirstName': 'Janet',
      'Title': 'Sales Representative',
      'TitleOfCourtesy': 'Ms.',
      'HireDate': '22/07/2001',
      'City': 'Kirkland',
      'Country': 'USA'
    }];
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
    .e-query-builder {
        margin: 0 auto;
    }
    .e-qb-button {
        margin: 2% 1% 0 15%;
    }
</style>
```

{% endtab %}

> Set [`isRequired`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/validation/#isrequired) validation for `Operator` and `Value` fields.
> Set [`max`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/validation/#max), [`min`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/validation/#min) values for number values.

## Template

Template allows you to define your own input widgets for columns. To implement [`template`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/columnsModel/#template), you can define the following functions

* `create`: Creates the custom component.
* `write`: Wire events for the custom component.
* `Destroy`: Destroy the custom component.

In the following sample, dropdown is used as the custom component in the PaymentMode column.

{% tab template="query-builder/default" %}

```html
<template>
    <div class="control-section">
        <div class="col-lg-12 querybuilder-control">
             <ejs-querybuilder ref="querybuilder" :dataSource="dataSource" :rule="importRules" width="70%">
                <e-columns>
                    <e-column field='Category' label='Category' type='string'' />
                    <e-column field='PaymentMode' label='Payment Mode' type='string' :template='paymentTemplate' />
                    <e-column field='TransactionType' label='Transaction Type' type='boolean' />
                    <e-column field='Description' label='Description' type='string' />
                    <e-column field='Date' label='Date' type='date' />
                    <e-column field='Amount' label='Amount' type='number' />
                </e-columns>
            </ejs-querybuilder>
        </div>
    </div>
</template>

<script>
import Vue from "vue";
import { QueryBuilderPlugin } from "@syncfusion/ej2-vue-querybuilder";
import { DropDownList } from '@syncfusion/ej2-dropdowns'
import { createElement, getComponent} from "@syncfusion/ej2-base";

let inOperators = ['in', 'notin'];
Vue.use(QueryBuilderPlugin);

export default {
    data: function() {
        return {
            dataSource: expenseData,
             paymentTemplate: {
                create: () => {
                    return createElement('input', { attrs: { 'type': 'text' } });
                },
                destroy: (args) => {
                    let multiselect = getComponent(document.getElementById(args.elementId), 'multiselect');
                    if(multiselect)
                        multiselect.destroy();
                    let dropdownlist = getComponent(document.getElementById(args.elementId), 'dropdownlist');
                    if(dropdownlist)
                        dropdownlist.destroy();
                },
                write: (args) => {
                    let ds = ['Cash', 'Debit Card', 'Credit Card', 'Net Banking', 'Wallet'];
                    if (inOperators.indexOf(args.operator) > -1) {
                        let multiSelectObj = new MultiSelect({
                            dataSource: ds,
                            value: args.values,
                            mode: 'CheckBox',
                            placeholder: 'Select Transaction',
                            change: (e) => {
                                this.$refs.querybuilder.$el.ej2_instances[0].notifyChange(e.value, e.element);
                            }
                        });
                        multiSelectObj.appendTo('#' + args.elements.id);
                    } else {
                        let dropDownObj = new DropDownList({
                            dataSource: ds,
                            value: args.values,
                            change: (e) => {
                                this.$refs.querybuilder.$el.ej2_instances[0].notifyChange(e.itemData.value, e.element);
                            }
                        });
                        dropDownObj.appendTo('#' + args.elements.id);
                    }
                }
            },
            importRules: {
        'condition': 'and',
        'rules': [{
                'label': 'Payment Mode',
                'field': 'PaymentMode',
                'type': 'string',
                'operator': 'equal',
                'value': 'Cash'
            }]
        }
        };
    }
}
var expenseData = [{
    'Category': 'Food',
    'PaymentMode': 'Credit Card',
    'TransactionType': 'Expense',
    'Description': 'Boiled peanuts',
    'Amount': '7',
    'Date': '06/01/2017'
  }, {

    'Category': 'Food',
    'PaymentMode': 'Cash',
    'TransactionType': 'Expense',
    'Description': 'Peanuts in Coke',
    'Amount': '8',
    'Date': '06/04/2017'
  }, {
    'Category': 'Food',
    'PaymentMode': 'Cash',
    'TransactionType': 'Expense',
    'Description': 'Palmetto Cheese, Mint julep',
    'Amount': '11',
    'Date': '06/04/2017'
  }];
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

    .e-query-builder {
        margin: 0 auto;
    }
</style>
```

{% endtab %}

## Rule Template

Rule Template allows to define your own user interface for columns. To implement [`ruleTemplate`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/columnsModel/#ruleTemplate), you can create the user interface as `vue` component and assign the values through `actionBegin` event.

In the following sample, dropdown and slider are used as the custom component and applied `greaterthanorequal` operator to `Age` column.

{% tab template="query-builder/rule-template", sourceFiles="agetemp.vue" %}

```html
<template>
    <div class="control-section">
        <div id="listbox-selection">
            <ejs-querybuilder id="querybuilder" ref="querybuilder" :actionBegin="actionBegin" :dataSource="dataSource" :rule="importRules">
                <e-columns>
                    <e-column field="EmployeeID" label="Employee ID" type="number"/>
                    <e-column field="FirstName" label="First Name" type="string"/>
                    <e-column field="LastName" label="LastName" type="string"/>
                    <e-column field="Age" label="Age" type="number" :ruleTemplate='ageTemplate'/>
                    <e-column field='City' label='City' type='string' />
                    <e-column field='Country' label='Country' type='string' />
                </e-columns>
            </ejs-querybuilder>
        </div>
    </div>
</template>

<script>
import Vue from "vue";
import { QueryBuilderPlugin } from '@syncfusion/ej2-vue-querybuilder';
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
import { getComponent, compile } from '@syncfusion/ej2-base';
import { DataManager, Predicate, Query } from '@syncfusion/ej2-data';

Vue.use(QueryBuilderPlugin);
Vue.use(SliderPlugin);
Vue.use(DropDownListPlugin);

export default {
    data: function() {
        return {
            dataSource: employeeData,
            importRules: {
                'condition': 'and',
                'rules': [{
                    'label': 'Age',
                    'field': 'Age',
                    'type': 'number',
                    'operator': 'greaterthanorequal',
                    'value': 30
                }]
            },
            ageTemplate: () => {
                return {
                    template : Vue.component('ruleTemplate', {
                        template:
                        `<div class="e-rule e-rule-template">
                            <div class="e-rule-filter e-custom-filter">
                                <ejs-dropdownlist :change='fieldChange' :value="data.rule.field" :dataSource="data.columns" :fields="data.fields">
                                </ejs-dropdownlist>
                            </div>
                            <div>
                                <div class="e-slider-value">
                                    <ejs-slider :min="min" :max="max" ref="slider" :ticks="rangeticks" :created="created" :change="valueChange" :value="value" :id="valueID">
                                    </ejs-slider>
                                </div>
                                <div class="e-rule-btn">
                                    <button :id='optionID' @click="myFunction(data.ruleID)" class="e-primary e-btn e-small">
                                        View Details
                                    </button>
                                    <button class="e-removerule e-rule-delete e-css e-btn e-small e-round">
                                        <span class="e-btn-icon e-icons e-delete-icon"/>
                                    </button>
                                </div>
                            </div>
                            <div :id='sectionID' class="e-rule-value-group e-hide">
                                <div>
                                    <table id='datatable' class='e-rule-table e-hide'>
                                    <thead>
                                    <tr><th>EmployeeID</th><th>FirstName</th><th>Age</th></tr>
                                    </thead>
                                    <tbody>
                                    </tbody>
                                    </table>
                                </div>
                            </div>
                        </div>`,
                        data(args) {
                            return {
                                qryBldrObj: getComponent(document.getElementById('querybuilder'), 'query-builder'),
                                data: Object.assign({}, args, true),
                                rangeticks: {
                                    placement: 'Before',
                                    largeStep: 5,
                                    smallStep: 1,
                                    showSmallTicks: true
                                },
                                min: 30,
                                max: 50
                            }
                        },
                        computed: {
                            valueID: function() {
                                return `${this.data.ruleID}_valuekey0`;
                            },
                            optionID: function() {
                                return `${this.data.ruleID}_option`;
                            },
                            sectionID: function() {
                                return `${this.data.ruleID}_section`;
                            },
                            value: function() {
                                var num = 30;
                                if (this.data.rule.value !== '') {
                                    num = this.data.rule.value;
                                }
                                return num;
                            }
                        },
                        methods: {
                            created: function() {
                                var elem = document.getElementById(this.$refs.slider.$el.id.split('_valuekey0')[0]);
                                this.refreshTable(this.qryBldrObj.getRule(elem), elem.id);
                            },
                            fieldChange: function(args) {
                                this.qryBldrObj.notifyChange(args.value, args.element, 'field');
                            },
                            valueChange: function(args) {
                                if (args.isInteracted) {
                                    var elem = this.$refs.slider.$el;
                                    this.qryBldrObj.notifyChange(args.value, elem, 'value');
                                    this.refreshTable(this.qryBldrObj.getRule(elem), elem.id.split('_valuekey0')[0]);
                                }
                            },
                            myFunction: function(ruleID) {
                                var element = document.getElementById(ruleID + '_section');
                                if (element.className.indexOf('e-hide') > -1) {
                                    element.className = element.className.replace('e-hide', '');
                                    document.getElementById(ruleID + '_option').textContent = 'Hide Details';
                                } else {
                                    element.className += ' e-hide';
                                    document.getElementById(ruleID + '_option').textContent = 'View Details';
                                }
                            },
                            refreshTable(rule, ruleID) {
                                var template = '<tr><td>${EmployeeID}</td><td>${FirstName}</td><td>${Age}</td></tr>';
                                var compiledFunction = compile(template);
                                var predicate = this.qryBldrObj.getPredicate({condition: 'and', rules: [rule]});
                                var dataManagerQuery = new Query().select(['EmployeeID', 'FirstName', 'Age']).where(predicate);
                                var result = new DataManager(employeeData).executeLocal(dataManagerQuery);
                                var table = document.querySelector('#' + ruleID + "_section #datatable");
                                if (result.length) {
                                    table.style.display = 'block';
                                } else {
                                    table.style.display = 'none';
                                }
                                table.querySelector('tbody').innerHTML = '';
                                result.forEach((data) => {
                                    table.querySelector('tbody').appendChild(compiledFunction(data)[0].querySelector('tr'));
                                });
                            }
                        }
                    })
                }
            }
        };
    },
    methods: {
        actionBegin: function(args) {
            args.rule.operator = 'greaterthanorequal';
            if (args.requestType === 'template-initialize') {
                if (args.rule.value === '') {
                    args.rule.value = 30;
                }
            }
            if (args.requestType === 'template-create') {
                getComponent(document.getElementById(args.ruleID + '_valuekey0'), 'slider').refresh();
            }
        }
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
];

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

    .e-query-builder {
        margin: 0 auto;
    }
    .e-rule-template {
        padding-bottom: 12px;
    }
    .e-rule-btn {
        float: right;
        padding-top: 12px;
    }
    .e-rule-value-group {
        margin: 12px;
        border-top: 1px solid #e0e0e0;
        min-height: 40px;
    }
    .e-query-builder .e-slider-container.e-horizontal {
        padding: 0px 0 0 18px;
        height: 0;
    }
    .e-query-builder .e-hide {
        display: none;
    }
    .e-query-builder .e-custom-filter {
        width: 40% !important;
    }

    .e-query-builder .e-slider-container.e-horizontal .e-slider {
        top: calc(50% - 10px);
    }

    .e-query-builder .e-slider-value {
        width: 40% !important;
        padding: 12px 0 12px 0;
        display: inline-block;
    }

    .e-rule-table {
        margin: 20px 0 0 20px;
        border: solid 1px #e0e0e0;
        border-collapse: collapse;
        font-family: Roboto;
        width: 320px;
        height: 180px;
        overflow-y: auto;
    }
    .e-rule-table th,
    .e-rule-table td {
        border: solid #e0e0e0;
        border-width: 1px 0 0;
        display: table-cell;
        font-size: 14px;
        line-height: 20px;
        overflow: hidden;
        padding: 8px 21px;
        vertical-align: middle;
        white-space: nowrap;
        width: auto;
    }
</style>
```

{% endtab %}
