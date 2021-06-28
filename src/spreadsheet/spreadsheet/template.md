---
title: "Template"
component: "Spreadsheet"
description: "This section helps you to learn how to add other controls in the Essential JS 2 Spreadsheet."
---

# Cell Template

Cell Template is used for adding HTML elements into Spreadsheet. You can add the cell template in spreadsheet by using the `template` property and specify the address using the `address` property inside the `ranges` property. You can customize the Html elements similar to Syncfusion components (TextBox, DropDownList, RadioButton, MultiSelect, DatePicker etc) by using the `beforeCellRender` event. In this demo, Cell template is applied to `C2:C9` and instantiated with Html input components like TextBox, RadioButton, TextArea. You need to bind the events to perform any operations through HTML elements or Syncfusion components. Here, we have added `change` event in to the MultiSelect control, and we have updated the selected data into the spreadsheet cell through that change event.

<!-- ```html
<template>
 <ejs-spreadsheet id="spreadsheet" ref="spreadsheet" :showRibbon="false" :allowResizing="false" :showFormulaBar="false" :allowOpen="false" :allowSave="false" :scrollSettings="scrollSettings" :created="created" :allowEditing="false" :selectionSettings="selectionSettings">
        <e-sheets>
          <e-sheet name="Registration Form" :rowCount="40" :colCount="30" :showGridLines="false">
            <e-ranges>
              <e-range :template="nameTextbox" address="C2"></e-range>
              <e-range :template="dobTextbox" address="C3"></e-range>
              <e-range :template="genderRadiobutton" address="C4"></e-range>
              <e-range :template="dropdownlist" address="C5"></e-range>
              <e-range :template="multiselect" address="C6"></e-range>
              <e-range :template="mobileTextbox" address="C7"></e-range>
              <e-range :template="emailTextbox" address="C8"></e-range>
              <e-range :template="addressTextbox" address="C9"></e-range>
              <e-range :template="addButton" address="C11"></e-range>
            </e-ranges>
            <e-rows>
              <e-row height=55>
                        <e-cells>
                            <e-cell index=1 value="Interview Registration Form"></e-cell>
                        </e-cells>
                    </e-row>
                    <e-row height=55>
                        <e-cells>
                            <e-cell index=1 value="Name:"></e-cell>
                        </e-cells>
                    </e-row>
                    <e-row height=45>
                        <e-cells>
                            <e-cell index=1 value="Date of Birth:"></e-cell>
                        </e-cells>
                    </e-row>
                    <e-row height=45>
                        <e-cells>
                            <e-cell index=1 value="Gender:"></e-cell>
                        </e-cells>
                    </e-row>
                    <e-row height=45>
                        <e-cells>
                            <e-cell index=1 value="Year of Experience:"></e-cell>
                        </e-cells>
                    </e-row>
                    <e-row height=45>
                        <e-cells>
                            <e-cell index=1 value="Areas of Interest:"></e-cell>
                        </e-cells>
                    </e-row>
                    <e-row height=45>
                        <e-cells>
                            <e-cell index=1 value="Mobile Number:"></e-cell>
                        </e-cells>
                    </e-row>
                    <e-row height=45>
                        <e-cells>
                            <e-cell index=1 value="Email:"></e-cell>
                        </e-cells>
                    </e-row>
                    <e-row height=82>
                        <e-cells>
                            <e-cell index=1 value="Address:"></e-cell>
                        </e-cells>
                    </e-row>
            </e-rows>
            <e-columns>
                    <e-column index=1 :width="190"></e-column>
                    <e-column :width="350"></e-column>
                </e-columns>
          </e-sheet>
        </e-sheets>
      </ejs-spreadsheet>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";
import nameTextboxTemplate from "./name-textbox.vue";
import dobTextboxTemplate from "./dob-textbox.vue";
import genderRadioTemplate from "./gender-radiobutton.vue";
import dropdownlistTemplate from "./dropdownlist.vue";
import multiselectTemplate from "./multiselect.vue";
import mobileTextboxTemplate  from "./mobile-textbox.vue";
import emailTextboxTemplate  from "./email-textbox.vue";
import addressTextboxTemplate  from "./address-textbox.vue";
import addButtonTemplate  from "./add-button.vue";
Vue.use(SpreadsheetPlugin);
export default {
  name: 'app',
  data () {
    return {
        scrollSettings: { isFinite: true },
      selectionSettings: { mode: 'None' },
      nameTextbox: function() {
        return { template: nameTextboxTemplate }
      },
      dobTextbox: function() {
        return { template: dobTextboxTemplate }
      },
      genderRadiobutton: function() {
        return { template: genderRadioTemplate }
      },
      dropdownlist: function() {
        return { template: dropdownlistTemplate }
      },
      multiselect: function() {
        return { template: multiselectTemplate }
      },
      mobileTextbox: function() {
        return { template: mobileTextboxTemplate }
      },
      emailTextbox: function() {
        return { template: emailTextboxTemplate }
      },
      addressTextbox: function() {
        return { template: addressTextboxTemplate }
      },
      addButton: function() {
        return { template: addButtonTemplate }
      }
    }
  },
  methods: {
    created: function() {
      var spreadsheet = this.$refs.spreadsheet;
      // Applies format to specified range
      spreadsheet.cellFormat({ fontWeight: 'bold' }, 'B2:B9');
      spreadsheet.cellFormat({ fontSize: '12pt', fontWeight: 'bold', textAlign: 'center', verticalAlign: 'middle', textDecoration: 'underline' }, 'B1');
      // Merges B1 and C1 cells
      spreadsheet.merge('B1:C1');
    }
  }
}
</script>

<style>
 @import "../node_modules/@syncfusion/ej2-vue-spreadsheet/styles/material.css";
 @import '../node_modules/@syncfusion/ej2-base/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-grids/styles/material.css';
 @import "../node_modules/@syncfusion/ej2-spreadsheet/styles/material.css";
</style>
``` -->
Sample link: [`Cell template`](https://ej2.syncfusion.com/vue/demos/#/material/spreadsheet/cell-template)

## Note

You can refer to our [Vue Spreadsheet](https://www.syncfusion.com/vue-ui-components/vue-spreadsheet) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Spreadsheet example](https://ej2.syncfusion.com/vue/demos/#/material/spreadsheet/default.html) to knows how to present and manipulate data.

## See Also

* [Worksheet](./worksheet)
* [Rows and columns](./rows-and-columns)
