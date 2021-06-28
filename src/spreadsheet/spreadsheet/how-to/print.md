---
title: "How to print the single/multiple sheets"
component: "Spreadsheet"
description: "Learn how to print sheets in the spreadsheet"
---

# How to print the single/multiple sheets

You can use the `print` method by importing from ej2-base package. Here, the `Select` event in the dropdown and the `dataBound` event are used to print the single/multiple sheets of data. To print the single/multiple sheets, use the dropdown button and select the `Print` (or) `Print All` option. In the following sample, you can be able to print the single/multiple sheets.

{% tab template="spreadsheet/print", iframeHeight="450px" , isDefaultActive=true %}

```html
<template><div>
<ejs-dropdownbutton :items='items' :select='itemSelect'>Print</ejs-dropdownbutton>
  <ejs-spreadsheet id="spreadsheet" ref="spreadsheet" :created="created" :dataBound="dataBound">
                <e-sheets>
                  <e-sheet name="Budget">
                    <e-ranges>
                      <e-range :dataSource="dataSource1"></e-range>
                    </e-ranges>
                    <e-columns>
                      <e-column :width=100></e-column>
                      <e-column :width=100></e-column>
                      <e-column :width=100></e-column>
                      <e-column :width=100></e-column>
                    </e-columns>
                  </e-sheet>
                  <e-sheet name="Salary">
                    <e-ranges>
                      <e-range :dataSource="dataSource2"></e-range>
                    </e-ranges>
                    <e-columns>
                      <e-column :width=100></e-column>
                      <e-column :width=100></e-column>
                      <e-column :width=100></e-column>
                      <e-column :width=100></e-column>
                      </e-columns>
                  </e-sheet>
                </e-sheets>
              </ejs-spreadsheet></div>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";
import { salaryData, budgetData  } from './data.js';
import { DropDownButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";
import { createElement, getComponent, print } from '@syncfusion/ej2-base';
Vue.use(SpreadsheetPlugin);
Vue.use(DropDownButtonPlugin);

var printElement = createElement("div", {
  className: "e-sheet-panel",
  innerHTML:
    '<div class="e-spreadsheet-print"></div><div class="e-sheet"><div class="e-main-panel style="height:100%" style="overflow: unset"><div class="e-sheet-content" ></div></div></div>'
}) // creating same hierarchy of element as DOM
var isPrint = false;
export default {
   data: () => {
    return {
      dataSource1: budgetData,
      dataSource2: salaryData,
      items:[
        {
          text: "Print"
        },
        {
          text: "Print All"
        }]
    }
  },
  methods: {
   created: function () {
       var spreadsheet = this.$refs.spreadsheet;
     spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A1:D1');
        spreadsheet.cellFormat({ fontWeight: 'bold'}, 'A11:D11');
        spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'Salary!A1:D1');
      },
      itemSelect: function(args) {
      var spreadsheet = getComponent(document.getElementById("spreadsheet"), "spreadsheet");
      if (args.item.text === 'Print') {
      printElement.querySelector(".e-sheet-content").innerHTML = document.querySelector(
        ".e-sheet-content"
      ).outerHTML; //  To add the spreadsheet table
      var usedRange = spreadsheet.getActiveSheet().usedRange;
      var tbody = printElement.querySelector('tbody');
      for (var i = tbody.getElementsByClassName('e-row').length; i >= 0; i--) {
        if (tbody.getElementsByClassName('e-row')[i] && parseInt(tbody.getElementsByClassName('e-row')[i].getAttribute('aria-rowindex'), 10) > usedRange.rowIndex + 1) {
          tbody.getElementsByClassName('e-row')[i].remove();
        }
      }
      (printElement.querySelector('.e-sheet-content').children[0].getElementsByClassName('e-virtualtrack')[0]).style.height = 'auto';
      print(printElement);
      printElement.querySelector(".e-sheet-content").innerHTML = '';
    }
    if (args.item.text === 'Print All') {
      var sheets = spreadsheet.sheets;
      if (spreadsheet.activeSheetIndex === 0) {
        printElement.querySelector(".e-sheet-content").innerHTML = document.querySelector(
          ".e-sheet-content"
        ).outerHTML; //  To add the spreadsheet table

        var usedRange1 = spreadsheet.getActiveSheet().usedRange;
        var tbody1 = printElement.querySelector('tbody');
        for (var a = tbody1.getElementsByClassName('e-row').length; a >= 0; a--) {
          if (tbody1.getElementsByClassName('e-row')[a] && parseInt(tbody1.getElementsByClassName('e-row')[a].getAttribute('aria-rowindex'), 10) > usedRange1.rowIndex + 1) {
            tbody1.getElementsByClassName('e-row')[a].remove();
          }
        }

        if (sheets[spreadsheet.activeSheetIndex + 1]) {
          spreadsheet.goTo(sheets[spreadsheet.activeSheetIndex + 1].name + "!A1");
          isPrint = true;
        } else {
          print(printElement);
          printElement.querySelector(".e-sheet-content").innerHTML = '';
        }
      } else {
        if (sheets[0]) {
          spreadsheet.goTo(sheets[0].name + "!A1");
          isPrint = true;
        }
      }
    }
   },
   dataBound() {
       var spreadsheet = getComponent(document.getElementById("spreadsheet"), "spreadsheet");
    if (isPrint) {
      printElement.querySelector(
        '.e-sheet-content'
      ).innerHTML += document.querySelector('.e-sheet-content').outerHTML;
      var usedRange = spreadsheet.getActiveSheet()
        .usedRange;
      var tbody = printElement
        .querySelector('.e-sheet-content')
        .children[spreadsheet.activeSheetIndex].querySelector('tbody');
      for (
        var i = tbody.getElementsByClassName('e-row').length;
        i >= 0;
        i--
      ) {
        if (
          tbody.getElementsByClassName('e-row')[i] &&
          parseInt(tbody.getElementsByClassName('e-row')[i].getAttribute('aria-rowindex'), 10) > usedRange.rowIndex + 1) {
          tbody.getElementsByClassName('e-row')[i].remove();
        }
      }
      var sheets = spreadsheet.sheets;
      if (sheets.length - 1 === spreadsheet.activeSheetIndex) {
        var count = printElement.querySelector('.e-sheet-content')
          .childElementCount;
        if (count > 1) {
          for (var j = 0; j < count; j++) {
            (printElement
              .querySelector('.e-sheet-content')
              .children[j].getElementsByClassName(
                'e-virtualtrack'
              )[0]).style.height = 'auto';
            printElement
              .querySelector('.e-sheet-content')
              .children[j].setAttribute('style', 'page-break-after: always;');
          }
        }
        print(printElement);
        isPrint = false;
        printElement.querySelector('.e-sheet-content').innerHTML = '';
      } else {
        if (sheets[spreadsheet.activeSheetIndex + 1]) {
          spreadsheet.goTo(
            sheets[spreadsheet.activeSheetIndex + 1].name + '!A1'
          );
        }
      }
    }
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
```

{% endtab %}