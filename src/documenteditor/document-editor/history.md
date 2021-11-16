---
title: "Undo and redo"
component: "DocumentEditor"
description: "Learn how undo and redo can be done in JavaScript document editor and how to customize its limit."
---

# History

Document Editor tracks the history of all editing actions done in the document, which allows undo and redo functionality.

## Enable or disable history

Inject the `EditorHistory` module in your application to provide history preservation functionality for `DocumentEditor`. Refer to the following code example.

```html
<template>
        <div id="app">
            <ejs-documenteditor ref="documenteditor" :enableEditor='true' :isReadOnly='false' :enableEditorHistory='true' style="width: 100%;height: 100%;"></ejs-documenteditor>
        </div>
</template>
<script>
        import Vue from 'vue'
        import { DocumentEditorPlugin, Editor, Selection, EditorHistory } from '@syncfusion/ej2-vue-documenteditor';

        Vue.use(DocumentEditorPlugin);

        export default {
            data: function() {
                return {
                };
            },
            provide: {
                DocumentEditor : [Editor, Selection, EditorHistory]
            }
        }
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

You can enable or disable history preservation for a Document Editor instance any time using the `enableEditorHistory` property. Refer to the following sample code.

```javascript
this.$refs.documenteditor.enableEditorHistory = false;
```

## Undo and redo

You can perform undo and redo by `CTRL+Z` and `CTRL+Y` keyboard shortcuts. Document Editor exposes API to do it programmatically.
To undo the last editing operation in Document Editor, refer to the following sample code.

```javascript
this.$refs.documenteditor.ej2Instances.editorHistory.undo();
```

To redo the last undone action, refer to the following code example.

```javascript
this.$refs.documenteditor.ej2Instances.editorHistory.redo();
```

## Stack size

History of editing actions will be maintained in stack, so that the last item will be reverted first. By default, Document Editor limits the size of undo and redo stacks to 500 each respectively. However, you can customize this limit. Refer to the following sample code.

```javascript
this.$refs.documenteditor.ej2Instances.editorHistory.undoLimit = 400;
this.$refs.documenteditor.ej2Instances.editorHistory.redoLimit = 400;
```

## See Also

* [Feature modules](../document-editor/feature-module/)
* [Keyboard shortcuts](../document-editor/keyboard-shortcut/)