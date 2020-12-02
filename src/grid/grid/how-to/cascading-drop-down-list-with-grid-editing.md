---
title: "Cascading DropDownList with Grid editing"
component: "Grid"
description: "Learn how to Cascading DropDownList with Grid editing."
---

# Cascading DropDownList with Grid editing

You can achieve the Cascading DropDownList with grid Editing by using the Cell Edit Template feature.

In the below demo, Cascading DropDownList rendered for `ShipCountry` and `ShipState` column.

{% tab template="grid/how-to/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :editSettings='editSettings' :toolbar='toolbar' height='273px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' :isPrimaryKey='true' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='ShipCountry' headerText='ShipCountry' editType='dropdownedit' :edit='countryParams' width=150></e-column>
               <e-column field='ShipCity' headerText='Ship City' editType='dropdownedit' :edit='stateParams' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { createElement } from '@syncfusion/ej2-base';
import { GridPlugin,Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { DropDownList } from "@syncfusion/ej2-dropdowns";
import { Query } from '@syncfusion/ej2-data';
import { cascadeData } from './datasource.js';

let country= [
        { countryName: 'United States', countryId: '1' },
        { countryName: 'Australia', countryId: '2' }
    ];
let state = [
        { stateName: 'New York', countryId: '1', stateId: '101' },
        { stateName: 'Virginia ', countryId: '1', stateId: '102' },
        { stateName: 'Washington', countryId: '1', stateId: '103' },
        { stateName: 'Queensland', countryId: '2', stateId: '104' },
        { stateName: 'Tasmania ', countryId: '2', stateId: '105' },
        { stateName: 'Victoria', countryId: '2', stateId: '106' }
    ];
let countryElem, stateElem, countryObj, stateObj;
Vue.use(GridPlugin);
export default {
    data: () => {
      return {
        data: cascadeData,
        toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
        editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
        countryParams: {
          create: () => {
            countryElem = document.createElement('input');
            return countryElem;
          },
          read: () => {
            return countryObj.text;
          },
          destroy: () => {
            countryObj.destroy();
          },
          write: () => {
            countryObj = new DropDownList({
              dataSource: country,
              fields: { value: 'countryId', text: 'countryName' },
              change: () => {
                stateObj.enabled = true;
                let tempQuery = new Query().where('countryId', 'equal', countryObj.value);
                stateObj.query = tempQuery;
                stateObj.text = null;
                stateObj.dataBind();
              },
              placeholder: 'Select a country',
              floatLabelType: 'Never'
            });
           countryObj.appendTo(countryElem);
          }
        },
        stateParams: {
          create: () => {
            stateElem = document.createElement('input');
            return stateElem;
          },
          read: () => {
            return stateObj.text;
          },
          destroy: () => {
            stateObj.destroy();
          },
          write: () => {
              stateObj = new DropDownList({
              dataSource: state,
              fields: { value: 'stateId', text: 'stateName' },
              enabled: false,
              placeholder: 'Select a state',
              floatLabelType: 'Never'
            });
            stateObj.appendTo(stateElem);
          }
        },

      };
    },
    provide: {
      grid: [Edit, Toolbar]
    }
  }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}
