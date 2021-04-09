---
title: "Open and Save"
component: "Spreadsheet"
description: "This section helps to learn how to open and save excel file in Spreadsheet control"
---

# Open and Save

The native data format for Spreadsheet is `JSON`. When you open an excel file, it needs to be read and converted to client side Spreadsheet model. The converted client side Spreadsheet model is sent as JSON which is used to render Spreadsheet. Similarly, when you save the Spreadsheet, the client Spreadsheet model is sent to the server as JSON for processing and saved as Excel file formats. [`Server configuration`](./open-save/#server-configuration) is used for this process.

## Open

The Spreadsheet control opens an Excel document with its data, style, format, and more. To enable this feature, set [`allowOpen`](../api/spreadsheet/#allowopen) as `true` and assign service url to the [`openUrl`](../api/spreadsheet/#openurl) property.

**User Interface**:

In user interface you can open an Excel document by clicking `File > Open` menu item in ribbon.

The following code example shows `Open` option in the Spreadsheet control.

{% tab template="spreadsheet/open", iframeHeight="450px" , isDefaultActive=true %}

```html
<template>
   <ejs-spreadsheet :openUrl="openUrl" :allowOpen="true"></ejs-spreadsheet>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";

Vue.use(SpreadsheetPlugin);
export default {
   data: () => {
    return {
      openUrl: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/open',
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

> * Use `Ctrl + O` keyboard shortcut to open Excel documents.
> * The default value of the [allowOpen](../api/spreadsheet/#allowopen) property is `true`. For demonstration purpose, we have showcased the [allowOpen](../api/spreadsheet/#allowopen) property in previous code snippet.

## Save

The Spreadsheet control saves its data, style, format, and more as Excel file document. To enable this feature, set [`allowSave`](../api/spreadsheet/#allowsave) as `true` and assign service url to the [`saveUrl`](../api/spreadsheet/#saveurl) property.

**User Interface**:

In user interface, you can save Spreadsheet data as Excel document by clicking `File > Save As` menu item in ribbon.

The following code example shows `Save` option in the Spreadsheet control.

{% tab template="spreadsheet/open-save", iframeHeight="450px" , isDefaultActive=true %}

```html
<template>
   <ejs-spreadsheet :saveUrl="saveUrl" :allowSave="true">
   <e-sheets>
          <e-sheet>
            <e-ranges>
              <e-range :dataSource="dataSource"></e-range>
            </e-ranges>
            <e-columns>
              <e-column :width="width1"></e-column>
              <e-column :width="width2"></e-column>
              <e-column :width="width2"></e-column>
              <e-column :width="width1"></e-column>
              <e-column :width="width2"></e-column>
              <e-column :width="width3"></e-column>
            </e-columns>
          </e-sheet>
        </e-sheets></ejs-spreadsheet>
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
      width1: 180,
      width2: 130,
      width3: 120,
      saveUrl: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save'
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

> * Use `Ctrl + S` keyboard shortcut to save the Spreadsheet data as Excel file.
> * The default value of [allowSave](../api/spreadsheet/#allowsave) property is `true`. For demonstration purpose, we have showcased the [allowSave](../api/spreadsheet/#allowsave) property in previous code snippet.

### Methods

To save the Spreadsheet document as an `xlsx, xls, csv, or pdf` file, by using [save](../api/spreadsheet/#save) method should be called with the `url`, `fileName` and `saveType` as parameters. The following code example shows to save the spreadsheet file as an `xlsx, xls, csv, or pdf` in the button click event.

{% tab template="spreadsheet/undo-redo", iframeHeight="450px" %}

```html
<template>
  <div>
    <ejs-button id='xlsx' v-on:click.native="xlsx">Save As xlsx</ejs-button>
    <ejs-button id='xls' v-on:click.native="xlsx">Save As xls</ejs-button>
    <ejs-button id='csv' v-on:click.native="xlsx">Save As csv</ejs-button>
    <ejs-button id='pdf' v-on:click.native="xlsx">Save As pdf</ejs-button>
    <ejs-spreadsheet ref="spreadsheet">
      <e-sheets>
          <e-sheet>
            <e-ranges>
              <e-range :dataSource="dataSource"></e-range>
            </e-ranges>
             <e-columns>
              <e-column :width="width1"></e-column>
              <e-column :width="width2"></e-column>
            </e-columns>
          </e-sheet>
        </e-sheets></ejs-spreadsheet>
        <div>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin, getRangeIndexes } from "@syncfusion/ej2-vue-spreadsheet";
import { addClass, removeClass } from '@syncfusion/ej2-base';
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { defaultData } from './data.js';
Vue.use(SpreadsheetPlugin);
Vue.use(ButtonPlugin);
export default {
   data: () => {
    return {
      dataSource: defaultData,
      width1: 130,
      width2: 96,
    }
  },
  methods: {
  xlsx: function(event) {
      var spreadsheet = this.$refs.spreadsheet;
      spreadsheet.save({url: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save', fileName: "Sample", saveType: "Xlsx"});
    },
    xls: function(event) {
      var spreadsheet = this.$refs.spreadsheet;
      spreadsheet.save({url: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save', fileName: "Sample", saveType: "Xls"});
    },
    csv: function(event) {
      var spreadsheet = this.$refs.spreadsheet;
      spreadsheet.save({url: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save', fileName: "Sample", saveType: "Csv"});
    },
    pdf: function(event) {
      var spreadsheet = this.$refs.spreadsheet;
      spreadsheet.save({url: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save', fileName: "Sample", saveType: "Pdf"});
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

## Server Configuration

Import and export are processed in `server-side` using Spreadsheet server library. The following code snippets shows server configuration using `WebAPI` service,

```csharp

    [Route("api/[controller]")]
    public class SpreadsheetController : Controller
    {
        //To open excel file
        [AcceptVerbs("Post")]
        [HttpPost]
        [EnableCors("AllowAllOrigins")]
        [Route("Open")]
        public IActionResult Open(IFormCollection openRequest)
        {
            OpenRequest open = new OpenRequest();
            open.File = openRequest.Files[0];
            return Content(Workbook.Open(open));
        }

        //To save as excel file
        [AcceptVerbs("Post")]
        [HttpPost]
        [EnableCors("AllowAllOrigins")]
        [Route("Save")]
        public IActionResult Save(SaveSettings saveSettings)
        {
            return Workbook.Save(saveSettings);
        }
    }
```

## Server Dependencies

Open and save helper functions are shipped in the Syncfusion.EJ2.Spreadsheet package, which is available in Essential Studio and [`nuget.org`](https://www.nuget.org/). Following list of dependencies required for Spreadsheet open and save operations.

* Syncfusion.EJ2
* Syncfusion.EJ2.Spreadsheet
* Syncfusion.Compression.Base
* Syncfusion.XlsIO.Base

## Supported File Formats

The following list of Excel file formats are supported in Spreadsheet:

* MS Excel (.xlsx)
* MS Excel 97-2003 (.xls)
* Comma Separated Values (.csv)

## See Also

* [Filtering](./filter)
* [Sorting](./sort)
* [Hyperlink](./link)