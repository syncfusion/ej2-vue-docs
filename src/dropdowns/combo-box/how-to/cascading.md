---
title: "Combo box cascading"
component: "ComboBox"
description: "This section explains cascading of the Syncfusion Vue combo box component."
---

# Configure the cascading ComboBox

The cascading ComboBox is a series of ComboBox, where the value of one ComboBox depends
upon  another's value. This can be configured by using the [`change`](../../api/combo-box/#change) event of the parent ComboBox.
Within that change event handler, data has to be loaded to the child ComboBox based on the selected
value of the parent ComboBox.

The following example, shows the cascade behavior of country, state, and city
ComboBox. Here, the [`dataBind`](../../api/combo-box/#databind) method is used to reflect the property changes immediately
to the ComboBox.

{% tab template="combobox/cascade", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
          <ejs-combobox id='countries' :dataSource='countryData' :fields='countryfields' :change='onCountryChange' placeholder='Select a country'></ejs-combobox>
        <div class="padding-top">
          <ejs-combobox id='states' :dataSource='stateData' :enabled='stateenabled' :fields='statefields' :change='onStateChange' placeholder='Select a state'></ejs-combobox>
        </div>
        <div class="padding-top">
          <ejs-combobox id='cities' :dataSource='cityData' :enabled='cityenabled' :fields='cityfields' placeholder='Select a city'></ejs-combobox>
        </div>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ComboBoxPlugin);
import { Query } from '@syncfusion/ej2-data';

export default {
  data () {
    return {
      countryData: [
        { CountryName: 'Australia', CountryId: '2' },
        { CountryName: 'United States', CountryId: '1' }
      ],
      stateData: [
        { StateName: 'New York', CountryId: '1', StateId: '101' },
        { StateName: 'Virginia ', CountryId: '1', StateId: '102' },
        { StateName: 'Tasmania ', CountryId: '2', StateId: '105' }
      ],
      cityData : [
        { CityName: 'Albany', StateId: '101', CityId: 201 },
        { CityName: 'Beacon ', StateId: '101', CityId: 202 },
        { CityName: 'Emporia', StateId: '102', CityId: 206 },
        { CityName: 'Hampton ', StateId: '102', CityId: 205 },
        { CityName: 'Hobart', StateId: '105', CityId: 213 },
        { CityName: 'Launceston ', StateId: '105', CityId: 214 }
      ]
      countryfields : { value: 'CountryId', text: 'CountryName' }
      statefields : { value: 'StateId', text: 'StateName' },
      cityfields : { text: 'CityName', value: 'CityId' },
      stateenabled : false,
      cityenabled : false
    }
  },
  methods: {
        onCountryChange: function(e) {
          var countryObj = document.getElementById('countries').ej2_instances[0];
          var stateObj = document.getElementById('states').ej2_instances[0];
          var cityObj = document.getElementById('cities').ej2_instances[0];
           //Query the data source based on country ComboBox selected value
          stateObj.query = new Query().where('CountryId', 'equal', countryObj.value);
          // enable the state ComboBox
          stateObj.enabled = true;
          //clear the existing selection.
          stateObj.text = null;
          // bind the property changes to state ComboBox
          stateObj.dataBind();
          //clear the existing selection in city ComboBox
          cityObj.text = null;
          //disabe the city ComboBox
          cityObj.enabled = false;
          //bind the property cahnges to City ComboBox
          cityObj.dataBind();
        },
        onStateChange: function(e) {
          var stateObj = document.getElementById('states').ej2_instances[0];
          var cityObj = document.getElementById('cities').ej2_instances[0];
          cityObj.query = new Query().where('StateId', 'equal', stateObj.value);
          // enable the city ComboBox
          cityObj.enabled = true;
          //clear the existing selection
          cityObj.text = null;
          // bind the property change to city ComboBox
          cityObj.dataBind();
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
  #container .padding-top {
    padding-top: 35px;
}
</style>
```

{% endtab %}