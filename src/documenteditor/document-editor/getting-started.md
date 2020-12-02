---
title: "Getting Started"
component: "DocumentEditor"
description: "Learn how to get started using JavaScript document editor component through simple steps."
---

# Getting Started

This section explains the steps to create a Word document editor within your application and demonstrates the basic usage of the DocumentEditor component.

## Dependencies

The list of dependencies required to use the DocumentEditor component in your application is given below:

```javascript
|-- @syncfusion/ej2-vue-documenteditor
|-- @syncfusion/ej2-vue-base
    |-- @syncfusion/ej2-documenteditor
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-dropdowns
    |-- @syncfusion/ej2-file-utils
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-splitbuttons
    |-- @syncfusion/ej2-charts
```

## Get Started with Vue CLI

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli/) to setup your vue applications.
To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
```

Start a new project using below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install

```

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg/) registry.
You can choose the component that you want to install. For this application, we are going to use DocumentEditor component.

To install DocumentEditor component, use the following command

```bash
npm install @syncfusion/ej2-vue-documenteditor
```

## Adding CSS Reference

The DocumentEditor has different themes. They are:
* Material
* Fabric
* Bootstrap
* High Contrast

import DocumentEditor component CSS as given below in `<style>` section of the `App.vue` file.

```html
<style>
<!-- Material theme used for this sample -->
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

## Adding Component

## DocumentEditor Component

DocumentEditor Component is used to create , view and edit word documents. In this , you can customize the UI options based on your requirements to modify the document.

### Registering DocumentEditor Component

You can register the DocumentEditor component in your application by using the `Vue.use()`.

Refer to the code example given below.

```typescript
import { DocumentEditorPlugin } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);
```

> Registering `DocumentEditorPlugin` in vue, will register the DocumentEditor component along with its required child directives globally.

### Adding DocumentEditor Component

Add the Vue DocumentEditor by using `<ejs-documenteditor>` selector in `<template>` section of the `App.vue` file.

{% raw %}

```html
<template>
  <div id="app">
      <ejs-documenteditor :serviceUrl='serviceUrl' :isReadOnly='false' :enablePrint='true' :enableSfdtExport='true' :enableSelection='true' :enableContextMenu='true' :enableSearch='true' :enableOptionsPane='true' :enableWordExport='true' :enableTextExport='true' :enableEditor='true' :enableImageResizer='true' :enableEditorHistory='true' :enableHyperlinkDialog='true' :enableTableDialog='true' :enableBookmarkDialog='true' :enableTableOfContentsDialog='true' :enablePageSetupDialog='true' :enableStyleDialog='true' :enableListDialog='true' :enableParagraphDialog='true' :enableFontDialog='true' :enableTablePropertiesDialog='true' :enableBordersAndShadingDialog='true' :enableTableOptionsDialog='true'> </ejs-documenteditor>
  </div>
</template>

<script>
import Vue from 'vue';
import { DocumentEditorPlugin, DocumentEditorComponent, Print, SfdtExport, WordExport, TextExport, Selection, Search, Editor, ImageResizer, EditorHistory, ContextMenu, OptionsPane, HyperlinkDialog, TableDialog, BookmarkDialog, TableOfContentsDialog, PageSetupDialog, StyleDialog, ListDialog, ParagraphDialog, BulletsAndNumberingDialog, FontDialog, TablePropertiesDialog, BordersAndShadingDialog, TableOptionsDialog, CellOptionsDialog, StylesDialog } from '@syncfusion/ej2-vue-documenteditor';
Vue.use(DocumentEditorPlugin);
export default {
  data () {
    return {
      serviceUrl:'https://ej2services.syncfusion.com/production/web-services/api/documenteditor/'
    },
    provide: {
      DocumentEditor: [Print, SfdtExport, WordExport, TextExport, Selection, Search, Editor, ImageResizer, EditorHistory, ContextMenu, OptionsPane, HyperlinkDialog, TableDialog, BookmarkDialog, TableOfContentsDialog, PageSetupDialog, StyleDialog, ListDialog, ParagraphDialog, BulletsAndNumberingDialog, FontDialog, TablePropertiesDialog, BordersAndShadingDialog, TableOptionsDialog, CellOptionsDialog, StylesDialog]
    }
  }
}
</script>
```

{% endraw %}

> The DocumentEditor requires server-side interactions for the following operations:
>
> * Paste with formatting
> * Restrict editing
> * Spellcheck
>
> Refer to this [link](https://github.com/SyncfusionExamples/EJ2-DocumentEditor-WebServices) to configure the web service and set the [serviceUrl](../api/document-editor#serviceurl).

### Run the DocumentEditor application

The Vue DocumentEditor application is configured to compile and run the application in a browser. Use the following command to run the application.

```bash
npm run dev
```

Output will be displayed as follows.

{% tab template="document-editor/getting-started", isDefaultActive=true %}

{% raw %}

```html
<template>
  <div id="app">
    <ejs-documenteditor id="container6"  style="width: 100%;height: 100%;" :serviceUrl='serviceUrl' :isReadOnly='false' :enablePrint='true' :enableSfdtExport='true' :enableSelection='true' :enableContextMenu='true' :enableSearch='true' :enableOptionsPane='true' :enableWordExport='true' :enableTextExport='true' :enableEditor='true' :enableImageResizer='true' :enableEditorHistory='true' :enableHyperlinkDialog='true' :enableTableDialog='true' :enableBookmarkDialog='true' :enableTableOfContentsDialog='true' :enablePageSetupDialog='true' :enableStyleDialog='true' :enableListDialog='true' :enableParagraphDialog='true' :enableFontDialog='true' :enableTablePropertiesDialog='true' :enableBordersAndShadingDialog='true' :enableTableOptionsDialog='true'></ejs-documenteditor>
  </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin, DocumentEditorComponent, Print, SfdtExport, WordExport, TextExport, Selection, Search, Editor, ImageResizer, EditorHistory, ContextMenu, OptionsPane, HyperlinkDialog, TableDialog, BookmarkDialog, TableOfContentsDialog, PageSetupDialog, StyleDialog, ListDialog, ParagraphDialog, BulletsAndNumberingDialog, FontDialog, TablePropertiesDialog, BordersAndShadingDialog, TableOptionsDialog, CellOptionsDialog, StylesDialog } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);

export default {
  data() {
    return {
      serviceUrl:'https://ej2services.syncfusion.com/production/web-services/api/documenteditor/'
    };
  },
  provide: {
    DocumentEditor: [Print, SfdtExport, WordExport, TextExport, Selection, Search, Editor, ImageResizer, EditorHistory, ContextMenu, OptionsPane, HyperlinkDialog, TableDialog, BookmarkDialog, TableOfContentsDialog, PageSetupDialog, StyleDialog, ListDialog, ParagraphDialog, BulletsAndNumberingDialog, FontDialog, TablePropertiesDialog, BordersAndShadingDialog, TableOptionsDialog, CellOptionsDialog, StylesDialog]
  }
}
</script>
<style>
 @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

## DocumentEditorContainer Component

DocumentEditorContainer Component is also used to create, view and edit word document. But here, you can use predefined toolbar and properties pane to view and modify word document.

### Registering DocumentEditorContainer Component

You can register the DocumentEditorContainer component in your application by using the `Vue.use()`.

Refer to the code example given below.

```typescript
import { DocumentEditorContainerPlugin } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorContainerPlugin);
```

> Registering `DocumentEditorContainerPlugin` in vue, will register the DocumentEditorContainer component along with its required child directives globally.

### Adding DocumentEditorContainer Component

Add the Vue DocumentEditorContainer by using `<ejs-documenteditorcontainer>` selector in `<template>` section of the `App.vue` file.

{% raw %}

```html
<template>
  <div id="app">
      <ejs-documenteditorcontainer :serviceUrl='serviceUrl' :enableToolbar='true'> </ejs-documenteditorcontainer>
  </div>
</template>

<script>
import Vue from 'vue';
import { DocumentEditorContainerPlugin, DocumentEditorContainerComponent,Toolbar } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorContainerPlugin);
export default {
  data(){
    return { serviceUrl:'https://ej2services.syncfusion.com/production/web-services/api/documenteditor/' }
  },
  provide: {
    DocumentEditorContainer: [Toolbar]
  }
}
</script>
```

{% endraw %}

> The DocumentEditorContainer requires server-side interactions for the following operations:
>
> * Opening word documents
> * Paste with formatting
> * Restrict editing
> * Spellcheck
>
> Refer to this [link](https://github.com/SyncfusionExamples/EJ2-DocumentEditor-WebServices) to configure the web service and set the [serviceUrl](../api/document-editor-container#serviceurl).

### Run the DocumentEditorContainer application

The Vue DocumentEditorContainer application is configured to compile and run the application in a browser. Use the following command to run the application.

```bash
npm run dev
```

DocumentEditorContainer output will be displayed as follows.

{% tab template="document-editor/getting-started", isDefaultActive=true %}

{% raw %}

```html
<template>
  <div id="app">
    <ejs-documenteditorcontainer ref='documenteditor' :serviceUrl='serviceUrl' style='height:600px;' id='container' :enableToolbar='true'></ejs-documenteditorcontainer>
  </div>
</template>
<script>
import Vue from 'vue';
import { DocumentEditorContainerPlugin, DocumentEditorContainerComponent,Toolbar} from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorContainerPlugin);

export default {
  data() {
    return { serviceUrl:'https://ej2services.syncfusion.com/production/web-services/api/documenteditor/' };
  },
  provide: {
    DocumentEditorContainer: [Toolbar]
  }
}
</script>
<style>
 @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}