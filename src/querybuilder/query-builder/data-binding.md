---
title: "Querybuilder Data Binding"
component: "QueryBuilder"
description: "Learn how to bind local data in the Essential JS 2 QueryBuilder control."
---

# Data Binding

The Query Builder uses `DataManager`, which supports both RESTful JSON data services binding and local JavaScript object array binding. The [`dataSource`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#datasource) property can be assigned either with the instance of `DataManager` or JavaScript object array collection. It supports two kinds of data binding method:

* Local data
* Remote data

## Local data

To bind local data to the query builder, you can assign the [`dataSource`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#datasource) property  with a JavaScript object array. The local data source can also be provided as an instance of the `DataManager`.

{% tab template="query-builder/default", isDefaultActive=true %}

```html
<template>
    <div class="control-section">
        <div class="col-lg-12 querybuilder-control">
            <ejs-querybuilder width="70%" :dataSource="dataSource" :rule="importRules">
                <e-columns>
                    <e-column field='EmployeeID' label='Employee ID' type='number' />
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
                    'value': 1
                },
                {
                    'label': 'Title',
                    'field': 'Title',
                    'type': 'string',
                    'operator': 'equal',
                    'value': 'Sales Manager'
                }]
            }
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

> By default, `DataManager` uses `JsonAdaptor` for local data-binding.

## Remote data

To bind remote  data to the query builder, assign service data as an instance of  `DataManager` to the [`dataSource`](https://ej2.syncfusion.com/documentation/api/query-builder/#datasource) property. To interact with remote data source, provide the endpoint `url`.

{% tab template="query-builder/default", isDefaultActive=true %}

```html
<template>
    <div class="control-section">
        <div class="col-lg-12 querybuilder-control">
            <ejs-querybuilder width="70%" :dataSource="data" :rule="importRules">
                <e-columns>
                    <e-column field='EmployeeID' label='Employee ID' type='number' />
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
import { DataManager, ODataAdaptor } from "@syncfusion/ej2-data";
Vue.use(QueryBuilderPlugin);

export default {
   data(){
        return {
            values: ['Mr.', 'Mrs.'],
            data: new DataManager({
            url: "https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders/";
            adaptor: new ODataAdaptor(),
          }),
          importRules: {
                'condition': 'and',
                'rules': [{
                    'label': 'Employee ID',
                    'field': 'EmployeeID',
                    'type': 'number',
                    'operator': 'equal',
                    'value': 1
                },
                {
                    'label': 'Title',
                    'field': 'Title',
                    'type': 'string',
                    'operator': 'equal',
                    'value': 'Sales Manager'
                }]
            }
        };
    };
}
</script>
<style>
    @import "../node_modules/@syncfusion/ej2-vue-querybuilder/styles/material.css";
    .e-query-builder {
        margin: 0 auto;
    }
</style>
```

{% endtab %}

> By default, `DataManager` uses `ODataAdaptor` for remote data-binding.

### Binding with OData services

[`OData`](https://www.odata.org/documentation/odata-version-3-0/) is a standardized protocol for creating and consuming data. You can retrieve data from OData service using the DataManager. Refer to the following code example for remote Data binding using OData service.

{% tab template="query-builder/default", isDefaultActive=true %}

```html
<template>
    <div class="control-section">
        <div class="col-lg-12 querybuilder-control">
            <ejs-querybuilder width="70%" :dataSource="data" :rule="importRules">
                <e-columns>
                    <e-column field='EmployeeID' label='Employee ID' type='number' />
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
import { DataManager, ODataAdaptor } from "@syncfusion/ej2-data";
Vue.use(QueryBuilderPlugin);

export default {
    data(){
        return {
            values: ['Mr.', 'Mrs.'],
            data: new DataManager({
            url: "https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders/";
            adaptor: new ODataAdaptor(),
            crossDomain: true
          }),
            importRules: {
                'condition': 'and',
                'rules': [{
                    'label': 'Employee ID',
                    'field': 'EmployeeID',
                    'type': 'number',
                    'operator': 'equal',
                    'value': 1
                },
                {
                    'label': 'Title',
                    'field': 'Title',
                    'type': 'string',
                    'operator': 'equal',
                    'value': 'Sales Manager'
                }]
            }
        };
    };
}
</script>
<style>
    @import "../node_modules/@syncfusion/ej2-vue-querybuilder/styles/material.css";
    .e-query-builder {
        margin: 0 auto;
    }
</style>
```

{% endtab %}

### Binding with OData v4 services

The ODataV4 is an improved version of OData protocols, and the `DataManager` can also retrieve and consume OData v4 services. For more details on OData v4 services, refer to the [`odata documentation`](http://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part1-protocol/odata-v4.0-errata03-os-part1-protocol-complete.html#_Toc453752197). To bind OData v4 service, use the `ODataV4Adaptor`.

{% tab template="query-builder/default", isDefaultActive=true %}

```html
<template>
    <div class="control-section">
        <div class="col-lg-12 querybuilder-control">
            <ejs-querybuilder width="70%" :dataSource="data" :rule="importRules">
                <e-columns>
                    <e-column field='EmployeeID' label='Employee ID' type='number' />
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
import { DataManager, ODataV4Adaptor } from "@syncfusion/ej2-data";
Vue.use(QueryBuilderPlugin);

export default {
    data(){
        return {
            values: ['Mr.', 'Mrs.'],
            data: new DataManager({
            url: "https://services.odata.org/V4/Northwind/Northwind.svc/Orders/";
            adaptor: new ODataV4Adaptor(),
            crossDomain: true
          }),
            importRules: {
                'condition': 'and',
                'rules': [{
                    'label': 'Employee ID',
                    'field': 'EmployeeID',
                    'type': 'number',
                    'operator': 'equal',
                    'value': 1
                },
                {
                    'label': 'Title',
                    'field': 'Title',
                    'type': 'string',
                    'operator': 'equal',
                    'value': 'Sales Manager'
                }]
            }
        };
    };
}
</script>
<style>
    @import "../node_modules/@syncfusion/ej2-vue-querybuilder/styles/material.css";
    .e-query-builder {
        margin: 0 auto;
    }
</style>
```

{% endtab %}

### Web API

You can use `WebApiAdaptor` to bind query builder with Web API created using OData endpoint.

```html
<template>
    <div class="control-section">
        <div class="col-lg-12 querybuilder-control">
            <ejs-querybuilder width="70%" :dataSource="data" :rule="importRules">
                <e-columns>
                    <e-column field='EmployeeID' label='Employee ID' type='number' />
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
import { DataManager, WebApiAdaptor } from "@syncfusion/ej2-data";
Vue.use(QueryBuilderPlugin);

export default {
    data: function() {
        return {
            values: ['Mr.', 'Mrs.'],
            data: new DataManager({
            url: 'api/OrderAPI',
            adaptor: new WebApiAdaptor(),
            crossDomain: true
      }),
            importRules: {
                'condition': 'and',
                'rules': [{
                    'label': 'Employee ID',
                    'field': 'EmployeeID',
                    'type': 'number',
                    'operator': 'equal',
                    'value': 1
                },
                {
                    'label': 'Title',
                    'field': 'Title',
                    'type': 'string',
                    'operator': 'equal',
                    'value': 'Sales Manager'
                }]
            }
        };
    }
}
</script>
<style>
    @import "../node_modules/@syncfusion/ej2-vue-querybuilder/styles/material.css";
    .e-query-builder {
        margin: 0 auto;
    }
</style>
```

## Data Manager

You can use the created conditions in DataManager through the [`getPredicate`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#getpredicate) method. This method creates predicates which is used as conditions in DataManager.

Install Syncfusion `Buttons` packages using below command.

```bash
npm install @syncfusion/ej2-vue-buttons --save
```

{% tab template="query-builder/default" %}

```html
<template>
    <div class="control-section">
        <div class="col-lg-12 querybuilder-control">
            <ejs-querybuilder ref="querybuilder" width="70%" :dataSource="dataSource" :rule="importRules">
                <e-columns>
                    <e-column field='EmployeeID' label='Employee ID' type='number' />
                    <e-column field='FirstName' label='First Name' type='string' />
                    <e-column field='TitleOfCourtesy' label='Title Of Courtesy' type='boolean' :values="values"/>
                    <e-column field='Title' label='Title' type='string' />
                    <e-column field='HireDate' label='Hire Date' type='date' format='dd/MM/yyyy' />
                    <e-column field='Country' label='Country' type='string' />
                    <e-column field='City' label='City' type='string' />
                </e-columns>
            </ejs-querybuilder>
             <ejs-button cssClass="e-qb-button" :isPrimary="true" v-on:click.native="btnClick">Get Data</ejs-button>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { QueryBuilderPlugin } from "@syncfusion/ej2-vue-querybuilder";
import { DataManager, Query } from '@syncfusion/ej2-data';
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { Compile } from '@syncfusion/ej2-base'

Vue.use(ButtonPlugin);
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
                    'value': 1
                }]
            }
        };
    },
      methods: {
    btnClick: function(event) {
        var validRule = this.$refs.querybuilder.ej2Instances.getValidRules(this.$refs.querybuilder.ej2Instances.rule);
        var predicate = this.$refs.querybuilder.ej2Instances.getPredicate(validRule);
        var dataManagerQuery = new Query().select(['EmployeeID', 'Title', 'City']);
        var fltrDataSource = [];
          new DataManager(employeeData).executeQuery(dataManagerQuery)
            .then((e) => {
                (e.result).forEach((data) => {
                      fltrDataSource.push(data);
                    //recieve the result data
                });
            });
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

## Complex Data Binding

Complex Data Binding allows you to create subfield for columns. To implement complex data binding, either bind the complex data in nested columns or specify complex data source and separator must be given in querybuilder.

In the following sample, complex data was bound in nested columns.

{% tab template="query-builder/complex-data-binding", sourceFiles="complex-data-binding.vue,datasource.js" %}

```html
<template>
<div class="control-section">
<div>
    <table>
        <tr>
            <td> <ejs-button id="reset" class="e-control e-danger e-btn e-small"  v-on:click.native='onReset'>Reset</ejs-button> </td>
            <td> <ejs-button id="rule" class="e-control e-success e-btn e-small"  v-on:click.native='onSetsqlRules'>SetSqlRules</ejs-button> </td>
            <td> <ejs-button id="sql" class="e-control e-success e-btn e-small"  v-on:click.native='onSetrules' >SetRules</ejs-button> </td>
        </tr>
    </table>
</div>
 <ejs-querybuilder id="querybuilder" ref="querybuilder" :rule="importRules" separator ="." enableNotCondition = true>
                <e-columns>
                    <e-column field="Employee" label="Employee" :columns='columns1'/>
                    <e-column field="Name" label="Name" :columns="columns2" />
                    <e-column field='Country' label='Country' :columns="columns3"/>
                </e-columns>
</ejs-querybuilder>

</div>
</template>

<script>
import Vue from "vue";
import { QueryBuilderPlugin } from '@syncfusion/ej2-vue-querybuilder';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
import { getComponent, compile,closest } from '@syncfusion/ej2-base';
import { CheckBoxPlugin, ButtonPlugin, RadioButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { DropDownButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";

Vue.use(QueryBuilderPlugin);
Vue.use(DropDownListPlugin);
Vue.use(CheckBoxPlugin);
Vue.use(DropDownButtonPlugin);
Vue.use(ButtonPlugin);
Vue.use(RadioButtonPlugin);

export default {
    data: function() {
        return {
            importRules: {
                condition: 'and',
                rules: [{
                    label: 'ID',
                    field: 'Employee.ID',
                    type: 'string',
                    operator: 'equal',
                    value: 0
                },
                {
                    label: 'Last Name',
                    field: 'Name.LastName',
                    type: 'string',
                    operator: 'contains',
                    value: 'malan'
                },
                {
                    condition: 'or',
                    rules: [{
                        label: 'City',
                        field: 'Country.State.City',
                        operator: 'startswith',
                        type: 'string',
                        value: 'U'
                    },
                    {
                        label: 'Region',
                        field: 'Country.Region',
                        operator: 'endswith',
                        type: 'string',
                        value: 'c'
                    },
                    {
                        label: 'Name',
                        field: 'Country.Name',
                        operator: 'isnotempty'
                    }]
                }]
            },
            columns1: [
                { field: 'ID', label: 'ID', type: 'number'},
                { field: 'DOB', label: 'Date of birth', type: 'date'},
                { field: 'HireDate', label: 'Hire Date', type: 'date'},
                { field: 'Salary', label: 'Salary', type: 'number'},
                { field: 'Age', label: 'Age', type: 'number'},
                { field: 'Title', label: 'Title', type: 'string'}
            ],
            columns2: [
                { field: 'FirstName', label: 'First Name', type: 'string'},
                { field: 'LastName', label: 'Last Name', type: 'string'}
            ],
            columns3: [
                { field: 'State', label: 'State', columns : [
                    { field: 'City', label: 'City', type: 'string'},
                    { field: 'Zipcode', label: 'Zip Code', type: 'number'}] },
                { field: 'Region', label: 'Region', type: 'string'},
                { field: 'Name', label: 'Name', type: 'string'}
            ],
        };  
    },
     methods: {
        onReset: function(event){
            this.$refs.querybuilder.ej2Instances.reset();
        },
        onSetsqlRules: function(event){
            this.$refs.querybuilder.ej2Instances.setRulesFromSql("Employee.ID = 0 AND Name.LastName LIKE ('%malan%') AND (Country.State.City LIKE ('U%') AND Country.Region LIKE ('%c') AND Country.Name IS NOT EMPTY)");
        },
        onSetrules: function(event){
            this.$refs.querybuilder.ej2Instances.setRules(this.importRules);
        }  
    }
}


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
    .e-query-builder .e-group-body .e-horizontal-mode .e-rule-sub-filter{
        display: inline-block;
    }
    .e-query-builder .e-group-body .e-rule-container .e-rule-sub-filter{
        padding: 12px 0 12px 12px;
        width: auto;
    }
</style>

```

{% endtab %}