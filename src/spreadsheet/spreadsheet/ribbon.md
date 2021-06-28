---
title: "Ribbon"
component: "Spreadsheet"
description: "Learn the various operations that you can perform in ribbon of the Angular Spreadsheet."
---

# Ribbon

It helps to organize a spreadsheet’s features into a series of tabs. By clicking the expand or collapse icon, you can expand or collapse the ribbon toolbar dynamically.

## Ribbon Customization

You can customize the ribbon using the following methods,

| Method | Action |
|-------|---------|
| [`hideRibbonTabs`](../api/spreadsheet/#hideribbontabs) | Used to show or hide the existing ribbon tabs. |
| [`enableRibbonTabs`](../api/spreadsheet/#enableribbontabs) | Used to enable or disable the existing ribbon tabs. |
| [`addRibbonTabs`](../api/spreadsheet/#addribbontabs) | Used to add custom ribbon tabs. |
| [`hideToolbarItems`](../api/spreadsheet/#hidetoolbaritems) | Used to show or hide the existing ribbon toolbar items. |
| [`enableToolbarItems`](../api/spreadsheet/#enabletoolbaritems) | Used to enable or disable the specified toolbar items. |
| [`addToolbarItems`](../api/spreadsheet/#addtoolbaritems) | Used to add the custom items in ribbon toolbar. |
| [`hideFileMenuItems`](../api/spreadsheet/#hidefilemenuitems) | Used to show or hide the ribbon file menu items. |
| [`enableFileMenuItems`](../api/spreadsheet/#enablefilemenuitems) | Used to enable or disable file menu items. |
| [`addFileMenuItems`](../api/spreadsheet/#addfilemenuitems) | Used to add custom file menu items. |

The following code example shows the usage of ribbon customization.

{% tab template="spreadsheet/ribbon", iframeHeight="450px" , isDefaultActive=true %}

```html
<template>
   <ejs-spreadsheet ref="spreadsheet" :created="created" :fileMenuBeforeOpen="fileMenuBeforeOpen"
                :fileMenuItemSelect="fileMenuItemSelect" :openUrl="openUrl" :saveUrl="saveUrl" :showFormulaBar="false" :showSheetTabs="false" :allowInsert="false" :allowDelete="false" :allowMerge="false">
                <e-sheets>
                  <e-sheet>
                    <e-ranges>
                      <e-range :dataSource="dataSource"></e-range>
                    </e-ranges>
                    <e-columns>
                      <e-column :width=180></e-column>
                      <e-column :width=130></e-column>
                      <e-column :width=130></e-column>
                      <e-column :width=180></e-column>
                      <e-column :width=130></e-column>
                      <e-column :width=120></e-column>
                    </e-columns>
                  </e-sheet>
                </e-sheets>
              </ejs-spreadsheet>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";
import { data } from './data.js';
Vue.use(SpreadsheetPlugin);
export default {
   data: () => {
    return {
      dataSource: data,
      openUrl: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/open';
    saveUrl: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save';
    }
  },
  methods: {
  created: function () {
      var spreadsheet = this.$refs.spreadsheet;
       spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A1:F1');
        // Hiding the `Insert` from ribbon.
        spreadsheet.hideRibbonTabs(['Insert']);
        // Set disabled state to `View` ribbon tab.
        spreadsheet.enableRibbonTabs(['View'], false);
        /// Adding the `Help` ribbon tab at the last index.
        // Specify the ribbon tab header text in last optional argument(`insertBefore`) for inserting new tab before any existing tab.
        spreadsheet.addRibbonTabs([{ header: { text: 'Help' }, content: [{ text: 'Feedback', tooltipText: 'Feedback',
            click : function() { /* Any click action for this toolbar item will come here. */ } }] }]);
        // Hiding the unwanted toobar items from `Home` by specifying its index.
        spreadsheet.hideToolbarItems('Home', [0, 1, 2, 4, 14, 15, 21, 24]);
        // Set diable state to `Underline`, 'Wrap text` toobar items from `Home` by specifying the item id.
        spreadsheet.enableToolbarItems(
            'Home', [`${spreadsheet.ej2Instances.element.id}_underline`, `${spreadsheet.ej2Instances.element.id}_wrap`], false);
        // Set disable state to `Protect Sheet` toolbar item from `Data` by mentioning its index.
        spreadsheet.enableToolbarItems('Data', [0], false);
        // Adding the new `Custom Formulas` toolbar item under `Formulas` tab for adding custom formulas.
        spreadsheet.addToolbarItems(
            'Formulas', [{ type: 'Separator' }, {
                text: 'Custom Formulas', tooltipText: 'Custom Formulas',
                // You can set click handler for each new custom toolbar item
                click: function() {
                    // You can add custom formualas here.
                }
            }]);
        // Adding new custom item `Import` after the existing `Open` item. By default, new item will add after the specified item.
        spreadsheet.addFileMenuItems([{ text: 'Import', iconCss: 'e-open e-icons' }], 'Open');
        // Adding new custom item `Export As` after the existing `Save As` item.
        // Set `insertAfter` optional argument as `false` for adding new item before the specified item.
        spreadsheet.addFileMenuItems(
            [{
                text: 'Export As', iconCss: 'e-save e-icons', items: [{ text: 'XLSX', iconCss: 'e-xlsx e-icons' },
                    { text: 'XLS', iconCss: 'e-xls e-icons' }, { text: 'CSV', iconCss: 'e-csv e-icons' }]
            }],
            'Save As', false);
      },
       fileMenuBeforeOpen: function () {
           var spreadsheet = this.$refs.spreadsheet;
        // Because the file menu items are created dynamically, you need to perform the hide or show and enable/disable operations
        // under filemenu before open event.
        // Hiding the `Save As` and `Open` item.
        spreadsheet.hideFileMenuItems(['Save As', 'Open']);
         // Set disable state to `New` item. You can perform any file menu items customization by specifying the item id,
        // if it has more than one same item text. Set the last argument `isUniqueId` as true for using the item id.
        spreadsheet.enableFileMenuItems([`${spreadsheet.ej2Instances.element.id}_New`], false, true);
    },

    fileMenuItemSelect : function (args) {
        var spreadsheet = this.$refs.spreadsheet;
        // Custom file menu items select handler
        switch (args.item.text) {
            case 'Import': select(`#${spreadsheet.element.id}_fileUpload`, spreadsheet.element).click();
                break;
            case 'XLSX': spreadsheet.save({ saveType: 'Xlsx' });
                break;
            case 'XLS': spreadsheet.save({ saveType: 'Xls' });
                break;
            case 'CSV': spreadsheet.save({ saveType: 'Csv' });
                break;
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

## Note

You can refer to our [Vue Spreadsheet](https://www.syncfusion.com/vue-ui-components/vue-spreadsheet) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Spreadsheet example](https://ej2.syncfusion.com/vue/demos/#/material/spreadsheet/default.html) to knows how to present and manipulate data.

## See Also

* [Worksheet](./worksheet)
* [Rows and columns](./rows-and-columns)
