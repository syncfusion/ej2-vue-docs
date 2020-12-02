---
title: "Rich Text Editor how to format code block using toolbar button"
component: "Rich Text Editor"
description: "This section for Syncfusion Vue Rich Text Editor component explains about how to format code block using toolbar button."
---

# Format code block using toolbar button

You can configure code block formatting as a separate toolbar button by adding the **InsertCode** keyword within the [`toolbarSettings`](./../../api/rich-text-editor/toolbarSettings/#toolbarsettings) items property.

The InsertCode button has a toggle state to apply code block formatting to the editor and remove code block formatting from the editor.

The following sample demonstrates how to config the InsertCode button in toolbar and set the background color to “pre” tag for highlighting the code block.

{% tab template="rich-text-editor/toolbar", isDefaultActive=true %}

```html
<template>
<div>
<div class="control-section">
    <div class="sample-container">
        <div class="default-section">
        <ejs-richtexteditor ref="rteObj" :toolbarSettings="toolbarSettings"><p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
        <p><b>Key features:</b></p>
          <ul>
            <li><p>Provides IFRAME and DIV modes</p></li>
            <li><p>Capable of handling markdown editing.</p></li>
            <li><p>Contains a modular library to load the necessary functionality on demand.</p></li>
            <li><p>Provides a fully customizable toolbar.</p></li>
          </ul></ejs-richtexteditor>
        </div>
    </div>
</div>

</div>
</template>
<style>
  .e-richtexteditor .e-rte-content .e-content pre {
    padding: 10px;
    background: #F4F5F7;
  }
</style>
<script>
import Vue from "vue";
import { RichTextEditorPlugin, Toolbar, HtmlEditor } from "@syncfusion/ej2-vue-richtexteditor";

Vue.use(RichTextEditorPlugin);

export default {
     data: function() {
        return {
          toolbarSettings: {
          items: ['InsertCode'] },
        }
    },
    provide:{
        richtexteditor:[Toolbar, HtmlEditor]
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
</style>

```

{% endtab %}