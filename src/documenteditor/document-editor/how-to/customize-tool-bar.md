---
title: "How to"
component: "DocumentEditor"
description: "Learn how to customize the existing toolbar in document editor."
---

# Customize existing toolbar

## How to customize existing toolbar in DocumentEditorContainer

DocumentEditorContainer allows you to customize(add, show, hide, enable, and disable) existing items in a toolbar.

* Add - New items can defined by [`CustomToolbarItemModel`](../../api/document-editor/customToolbarItemModel/) and with existing items in [`toolbarItems`](../api/document-editor-container/#toolbaritems) property. Newly added item click action can be defined in [`toolbarclick`](../../api/toolbar/clickEventArgs/).

* Show, Hide - Existing items can be shown or hidden using the [`toolbarItems`](../../api/document-editor-container/#toolbaritems) property. Pre-defined toolbar items are available with [`ToolbarItem`](../../api/document-editor/toolbaritem/).

* Enable, Disable -  Toolbar items can be enabled or disable using [`enableItems`](../../api/document-editor-container/toolbar/#enableItems)

```typescript
<template>
  <div id="app">
      <ejs-documenteditorcontainer ref="container" :toolbarItems='items' v-bind:toolbarClick='onToolbarClick' :enableToolbar='true'> </ejs-documenteditorcontainer>
  </div>
</template>

<script>
import Vue from 'vue';
import { DocumentEditorContainerPlugin, DocumentEditorContainerComponent,Toolbar } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorContainerPlugin);
export default {
  data(){
    return{ items: [{
        prefixIcon: "e-de-ctnr-lock",
        tooltipText: "Disable Image",
        text: "Disable Image",
        id: "Custom"
     }, 'Undo','Redo','Separator','Image','Table','Hyperlink','Bookmark','Comments','TableOfContents','Separator','Header','Footer','PageSetup','PageNumber','Break',
     'Separator','Find','Separator','LocalClipboard','RestrictEditing']
    }
  },
  provide: {
    DocumentEditorContainer: [Toolbar]
  },
  methods: {
    onToolbarClick:function(args) {
     switch(args.item.id) {
        case 'Custom':
            //Disable image toolbar item.
            this.$refs.container.ej2Instances.toolbar.enableItems(4, false);
            break;
      }
    }
  }
}
</script>
```

>Note: Default value of `toolbarItems` is `['New', 'Open', 'Separator', 'Undo', 'Redo', 'Separator', 'Image', 'Table', 'Hyperlink', 'Bookmark', 'Comments', 'TableOfContents', 'Separator', 'Header', 'Footer', 'PageSetup', 'PageNumber', 'Break', 'Separator', 'Find', 'Separator', 'LocalClipboard', 'RestrictEditing']`.