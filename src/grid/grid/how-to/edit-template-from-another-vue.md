---
title: "Edit Template from another Vue page"
component: "Grid"
description: "Learn how to Edit Template from another Vue page"
---

# Edit Template from another Vue page

You can achieve the dialog template editing using another vue page.

```html

<template>
    <div id="app">
         <ejs-grid :dataSource="data" :editSettings="editSettings" :actionBegin="actionBegin" :actionComplete="actionComplete" :toolbar="toolbar" height="273px">
      <e-columns>
        <e-column field="OrderID" headerText="Order ID" textAlign="Right" :isPrimaryKey="true" width="100"></e-column>
        <e-column field="CustomerID" headerText="Customer ID" width="120"></e-column>
        <e-column field="ShipCountry" headerText="Ship Country" width="150"></e-column>
      </e-columns>
    </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Toolbar, Edit } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
import DialogTemplate from "./dialogtemp.vue";
import { DatePickerPlugin } from "@syncfusion/ej2-vue-calendars";
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
import { NumericTextBox } from "@syncfusion/ej2-inputs";
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";
import { DataUtil } from '@syncfusion/ej2-data';

Vue.use(GridPlugin);
Vue.use(DropDownListPlugin);
Vue.use(DatePickerPlugin);
Vue.use(NumericTextBoxPlugin)

export default {
  data() {
    return {
      data: data,
      editSettings: {
        allowEditing: true,
        allowAdding: true,
        allowDeleting: true,
        mode: "Dialog",
        template: function() {
          return { template: DialogTemplate };
        }
      },
      toolbar: ["Add", "Edit", "Delete", "Update", "Cancel"]
    };
  },
  provide: {
    grid: [Page, Edit, Toolbar]
  },
  methods: {
    actionBegin(args) {
      if (args.requestType === "save") {
        // cast string to integer value.
        args.data["Freight"] = parseFloat(args.form.querySelector("#Freight").value);
      }
    },
    actionComplete(args) {
      // Set initail Focus
      if (args.requestType === "beginEdit") {
        args.form.elements.namedItem("OrderID").focus();
      }
    }
  }
}
</script>
<style>
 @import "https://cdn.syncfusion.com/ej2/material.css";
 @import "https://stackpath.bootstrapcdn.com/bootstrap/4.1.2/css/bootstrap.min.css";

.form-group.col-md-6 {
    width: 250px;
    height: 54px;
}
.form-group.col-md-12 {
    height: 72px;
}
#ShipAddress {
    resize: vertical;
}

</style>

```

Create new vue page with the name of `dialogtemp.vue` and paste the below code.

```html

<template>
  <div formGroup="orderForm">
    <div class="form-row">
      <div class="form-group col-md-6">
        <div class="e-float-input e-control-wrapper">
          <input  ref="OrderID" id="OrderID" name="OrderID" v-model="data.OrderID" type="text" :disabled="!data.isAdd">
          <span class="e-float-line"></span>
          <label class="e-float-text e-label-top" for="OrderID">Order ID</label>
        </div>
      </div>
      <div class="form-group col-md-6">
        <div class="e-float-input e-control-wrapper">
          <input ref="CustomerID" id="CustomerID" name="CustomerID" v-model="data.CustomerID" type="text">
          <span class="e-float-line"></span>
          <label class="e-float-text e-label-top" for="CustomerID">Customer Name</label>
        </div>
      </div>
    </div>
    <div class="form-row">
      <div class="form-group col-md-6">
        <ejs-numerictextbox id="Freight" placeholder="Freight" v-model="data.Freight" floatLabelType="Always" ></ejs-numerictextbox>
      </div>
      <div class="form-group col-md-6">
        <ejs-datepicker id="OrderDate" placeholder="Order Date" v-model="data.OrderDate" floatLabelType="Always" ></ejs-datepicker>
      </div>
    </div>
    <div class="form-row">
      <div class="form-group col-md-6">
        <ejs-dropdownlist id="ShipCountry" v-model="data.ShipCountry" :dataSource="shipCountryDistinctData"  :fields="{text: 'ShipCountry', value: 'ShipCountry' }" placeholder="Ship Country" popupHeight="300px" floatLabelType="Always" ></ejs-dropdownlist>
    </div>
      <div class="form-group col-md-6">
        <ejs-dropdownlist id="ShipCity" v-model="data.ShipCity" :dataSource="shipCityDistinctData" :fields="{text: 'ShipCity', value: 'ShipCity' }" placeholder="Ship City" popupHeight="300px" floatLabelType="Always"></ejs-dropdownlist>
      </div>
    </div>
    <div class="form-row">
      <div class="form-group col-md-12">
        <div class="e-float-input e-control-wrapper">
          <textarea id="ShipAddress" name="ShipAddress" type="text" v-model="data.ShipAddress"></textarea>
          <span class="e-float-line"></span>
          <label class="e-float-text e-label-top" for="ShipAddress">Ship Address</label>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { data } from './datasource.js';
import { DataUtil } from "@syncfusion/ej2-data";

export default {
  data() {
    let shipCity = DataUtil.distinct(data, "ShipCity", true);
    let shipCountry = DataUtil.distinct(data, "ShipCountry", true);
    return {
      data: {},
      shipCityDistinctData: shipCity,
      shipCountryDistinctData: shipCountry
    };
  },
  mounted() {
    // Set initail Focus
    if (this.data.isAdd) {
      this.$refs.OrderID.focus();
    } else {
      this.$refs.CustomerID.focus();
    }
  }
};
</script>

```