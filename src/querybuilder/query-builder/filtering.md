---
title: "Filtering"
component: "QueryBuilder"
description: "Learn how to filtering in the Essential JS 2 QueryBuilder control."
---

# Filtering

Query Builder allows you to create or delete conditions and groups. You can use [`showButtons`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#showbuttons) to enable/disable these buttons.

You can create or delete conditions by interacting through the user interface and methods.

* Use the [`addRules`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#addrules), and [`deleteRules`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#deleterules) methods to create/delete conditions.
* Use [`addGroups`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#addgroups), and [`deleteGroups`](https://ej2.syncfusion.com/vue/documentation/api/query-builder/#deletegroups) methods to create/delete groups.

Install Syncfusion `Buttons` packages using below command.

```bash
npm install @syncfusion/ej2-vue-buttons --save
```

{% tab template="query-builder/default", isDefaultActive=true %}

```html
<template>
    <div class="control-section">
        <div class="col-lg-12 querybuilder-control">
            <ejs-querybuilder width="70%" id="querybuilder" ref="querybuilder" :dataSource="dataSource" :rule="importRules" :showButtons="showButtons">
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
             <ejs-button cssClass="e-qb-button" :isPrimary="true" v-on:click.native="addRule">Add Rule</ejs-button>
             <ejs-button cssClass="e-qbr-button" :isPrimary="true" v-on:click.native="addGroup">Add Group</ejs-button>
             <ejs-button cssClass="e-qbr-button" :isPrimary="true" v-on:click.native="deleteGroup">Delete Group</ejs-button>
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
            showButtons:{ruleDelete: true, groupInsert: true, groupDelete: true},
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
    },
     methods: {
    addRule: function(event) {
       this.$refs.querybuilder.ej2Instances.addRules([{'label': 'City','field': 'City','type': 'string','operator': 'equal','value': 'US'}], 'group0');
    }
     addGroup: function(event) {
        this.$refs.querybuilder.ej2Instances.addGroups([{'condition': 'and','rules': [{'label': 'First Name','field': 'FirstName','type': 'string','operator': 'startswith','value': 'v' }]}], 'group0');
    }
     deleteGroup: function(event) {
        this.$refs.querybuilder.ej2Instances.deleteGroups(['group1']);
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

.e-qbr-button {
  margin: 2% 1% 0 1%;
}

#datatable {
  margin-left: 15%;
  margin-top: 2%;
}

#datatable.e-table {
  border: solid 1px #e0e0e0;
  border-collapse: collapse;
  font-family: Roboto;
}

#datatable.e-table td, #datatable.e-table th {
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