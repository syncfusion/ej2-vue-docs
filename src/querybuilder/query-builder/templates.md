---
title: "Templates"
component: "QueryBuilder"
description: "Documentation on templates in the Essential JS 2 QueryBuilder control."
---

# Templates

Templates allows users to define customized header and own user interface for columns.

## Header Template

Header Template allows to define your own user interface for Header, which includes creating or deleting rules and groups and to customize the AND/OR condition and NOT condition options. To implement header template, you can create the user interface as `vue` component and assign the values when requestType is header-template-create in  `actionBegin` event.

In the following sample dropdown, splitbutton and button are used as the custom components in the header.
{% tab template="query-builder/header-template", sourceFiles="headertemp.vue" %}

```html
<template>
    <div class="control-section">
            <ejs-querybuilder id="querybuilder" ref="querybuilder" :dataSource="dataSource" :rule="importRules" :headerTemplate="headerTemplate" enableNotCondition = true>
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
                'condition': 'and', 'not': true,
                'rules': [{
                    'label': 'Age',
                    'field': 'Age',
                    'type': 'number',
                    'operator': 'equal',
                    'value': 34
                },
                {
                    'label': 'FirstName',
                    'field': 'FirstName',
                    'type': 'string',
                    'operator': 'equal',
                    'value': 'Nancy'
                },
                {
                    'condition': 'or',
                    'rules': [{
                        'label': 'Age',
                        'field': 'Age',
                        'type': 'number',
                        'operator': 'equal',
                        'value': 34
                    }]
                }]
            },
            headerTemplate: () => {
                return {
                    template : Vue.component('headerTemplate', {
                        template:
                        `<div class="e-groupheader">
                            <button  v-if="data.notCondition !== undefined" class='e-cb-wrapper'>
                             <ejs-checkbox :id="notID" label='not' :checked="data.notCondition" :change="onChange"></ejs-checkbox>
                            </button>
                            <ejs-dropdownlist :id="ddlID"  cssClass="e-custom-group-btn"  :dataSource="ds" :fields="fields"  v-model="data.condition"  :change="conditionChange"></ejs-dropdownlist>
                            <ejs-dropdownbutton :id = 'ddbID' :items='ddbitems' cssClass= "e-round e-small e-caret-hide e-addrulegroup e-add-btn" iconCss="e-icons e-add-icon" :select='onSelect'></ejs-dropdownbutton>
                            <ejs-button v-if="data.ruleID !== 'querybuilder_group0'" :id="dltbtnID" class= "e-btn e-delete-btn e-lib e-small e-round e-icon-btn" iconCss="e-btn-icon e-icons e-delete-icon" v-on:click.native='btnClick'>
                            </ejs-button>
                        </div>`,
                        data(args) {
                            return {
                                qryBldrObj: getComponent(document.getElementById('querybuilder'), 'query-builder'),
                                ds:  [{'key': 'AND', 'value': 'and'},{'key': 'OR', 'value': 'or'}],
                                fields: { text: 'key', value: 'value' },
                                ddbitems:[
                                    {
                                        text: 'AddGroup',
                                        iconCss: 'e-icons e-add-icon e-addgroup'
                                    },
                                    {
                                        text: 'AddCondition',
                                        iconCss: 'e-icons e-add-icon e-addrule'
                                    }
                                ]
                            }
                        },
                        computed: {
                            ddbID: function(){
                                return `${this.data.ruleID}_addbtn`;
                            },
                            notID: function(){
                                return `${this.data.ruleID}_notOption`;
                            },
                            ddlID: function(){
                                return `${this.data.ruleID}_cndtn`;
                            },
                            dltbtnID: function(){
                                return `${this.data.ruleID}_dltbtn`;
                            }
                        },
                        methods: {
                            onSelect: function(event){
                               var addbtn = closest(event.element,'.e-dropdown-popup');
                               var ddbId = addbtn.id; var ddb = ddbId.split('_');
                               if (event.item.text === 'AddGroup') {
                                   this.qryBldrObj.addGroups([{condition: 'or', 'rules': [{}], not: false}], ddb[1]);
                                } else if (event.item.text === 'AddCondition') {
                                    this.qryBldrObj.addRules([{}], ddb[1]);
                                }
                            },
                            onChange: function(args){
                                this.qryBldrObj.notifyChange(args.checked, args.event.target, 'not');
                            },
                            conditionChange: function(args){
                                this.qryBldrObj.notifyChange(args.value, args.element, 'condition');
                            },
                            btnClick: function(args){
                                this.qryBldrObj.deleteGroup(closest(args.target.offsetParent, '.e-group-container'));
                            }
                        }
                    })
                }
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

.e-query-builder {
    margin: 0 auto;
}
.e-rule-template {
    padding-bottom: 12px;
}
.e-query-builder .e-add-btn {
    margin-left: 10px;
    margin-right: 10px;
}
.e-query-builder .cndtnbtn.e-control.e-dropdownlist.e-lib.e-input {
    padding-left: 10px;
}
.e-query-builder span.e-custom-group-btn {
    max-width: 100px;
    border-radius: 5px !important;
    border-width: 1px !important;
}
.e-query-builder .e-custom-group-btn.e-input-focus::before, .e-custom-group-btn.e-input-focus::after {
    background: transparent !important;
}
.e-query-builder .e-group-header .e-addrulegroup, .e-group-header .e-delete-btn {
    border: 1px solid grey !important;
}
.e-query-builder .e-group-header .e-addrulegroup:hover, .e-group-header .e-delete-btn:hover {
    border: 1px solid grey !important;
}
.e-query-builder .e-toggle{
    background: #317ab9;
    border-color: #317ab9;
    color: #fff;
}
.e-query-builder .e-cb-wrapper {
    margin-right: 5px;
    height: 32px;
    border-radius: 5px;
    border: 1px solid gray;
    background-color: white;
}
.e-query-builder .e-custom-group-btn{
    padding-left: 10px;
    height: 32px;
}
.e-control {
display: inline;
}
.e-query-builder div.e-rule-container{
   width: 800px;
}
</style>
```

{% endtab %}

## Column Template

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
                    <e-column field='Category' label='Category' type='string' />
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

### Using Template

Template allows you to define your own input widgets for columns. To implement template, you can create the user interface as `vue` component.

{% tab template="query-builder/template", sourceFiles="template.vue" %}

```html
<template>
    <div class="control-section">
            <ejs-querybuilder  id="querybuilder" ref="querybuilder" :rule="importRules" width="100%" >
                <e-columns>
                    <e-column field='Category' label='Category' type='string'/>
                    <e-column field='PaymentMode' label='Payment Mode' type='string' :operators="customOperators" :template='paymentTemplate' />
                    <e-column field='TransactionType' label='Transaction Type' type='string' :operators="customOperators" :template='transactionTemplate' />
                    <e-column field='Description' label='Description' type='string' />
                    <e-column field='Date' label='Date' type='date' />
                    <e-column field='Amount' label='Amount' type='number' />
                </e-columns>
            </ejs-querybuilder>
    </div>
</template>

<script>
import Vue from "vue";
import { QueryBuilderPlugin } from "@syncfusion/ej2-vue-querybuilder";
import { RadioButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { DropDownList, MultiSelect, CheckBoxSelection } from '@syncfusion/ej2-dropdowns';
import { Slider, TextBox } from '@syncfusion/ej2-inputs';
import { CheckBox } from '@syncfusion/ej2-buttons';
import { createElement, getComponent, isNullOrUndefined } from "@syncfusion/ej2-base";
import { CheckBoxPlugin } from "@syncfusion/ej2-vue-buttons";
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";


MultiSelect.Inject(CheckBoxSelection);
Vue.use(QueryBuilderPlugin);
Vue.use(CheckBoxPlugin);
Vue.use(DropDownListPlugin);

export default {
    data: function() {
        return {
            customOperators: [{value: 'equal', key: 'Equal'}, {value: 'notequal', key: 'Not Equal'}],
            importRules:{
                'condition': 'or',
                'rules': [{
                    'label': 'TransactionType',
                    'field': 'TransactionType',
                    'type': 'boolean',
                    'operator': 'equal',
                    'value': 'Income'
                },
                {
                    'label': 'PaymentMode',
                    'field': 'PaymentMode',
                    'type': 'string',
                    'operator': 'equal',
                    'value': 'Cash'
                }]
            },
            paymentTemplate: () => {
                return {
                    template: Vue.component('paymentTemplate', {
                        template:
                        `<div >
                        <ejs-dropdownlist  :dataSource="ds"  v-model="data.rule.value" :change="paymentChange"></ejs-dropdownlist>
                        </div>`,
                        data(args) {
                            return{
                               qryBldrObj: getComponent(document.getElementById('querybuilder'), 'query-builder'),
                                data: Object.assign({}, args, true),
                                ds: ['Cash', 'Debit Card', 'Credit Card', 'Net Banking'];
                            }
                        },
                        methods: {
                            paymentChange: function(event){
                                var elem = document.getElementById(ruleID).querySelector('.e-rule-value');
                                this.qryBldrObj.notifyChange(event.value as string, elem, 'value');
                            }
                        }
                    })
                }
            },
            transactionTemplate: () => {
                return{
                    template: Vue.component('transactionTemplate', {
                        template:
                        `<div >
                        <ejs-checkbox  label='Is Expense' :checked="data.rule.value" :change="transactionChange"></ejs-checkbox>
                        </div>`,
                        data(args) {
                            return{
                                qryBldrObj: getComponent(document.getElementById('querybuilder'), 'query-builder'),
                                data: Object.assign({}, args, true)
                            }
                        },
                        methods: {
                           transactionChange: function(event){
                               var elem = document.getElementById(ruleID).querySelector('.e-rule-value');
                               this.qryBldrObj.notifyChange(event.checked === true ? 'Expense' : 'Income', elem, 'value');
                            }
                        }
                    })
                }
            }
        };
    }
}

</script>

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
                                    <ejs-slider :min="min" :max="max" ref="slider" :ticks="rangeticks" :change="valueChange" :value="value" :id="valueID">
                                    </ejs-slider>
                                </div>
                                <div class="e-rule-btn">
                                    <button class="e-removerule e-rule-delete e-css e-btn e-small e-round">
                                        <span class="e-btn-icon e-icons e-delete-icon"/>
                                    </button>
                                </div>
                            </div>
                        </div>`,
                        data(args) {
                            return {
                                qryBldrObj: getComponent(document.getElementById('querybuilder'), 'query-builder'),
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
                            value: function() {
                                var num = 30;
                                if (this.data.rule.value !== '') {
                                    num = this.data.rule.value;
                                }
                                return num;
                            }
                        },
                        methods: {
                            fieldChange: function(args) {
                                this.qryBldrObj.notifyChange(args.value, args.element, 'field');
                            },
                            valueChange: function(args) {
                                if (args.isInteracted) {
                                    var elem = this.$refs.slider.$el;
                                    this.qryBldrObj.notifyChange(args.value, elem, 'value');
                                }
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
