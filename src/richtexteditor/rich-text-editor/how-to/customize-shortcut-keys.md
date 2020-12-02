---
title: " Rich Text Editor How To customize the shorcut key"
component: "Rich Text Editor"
description: "This section for Syncfusion Vue Rich Text Editor component explains on how to customize the shortcut keys."
---

# Customize shortcut keys

It can be achieved by using [`formatter`](../../api/rich-text-editor/#formatter) property. We need to create `customformatterModel` to configure the `keyConfig` using `IHtmlFormatterModel` class and assign the same to the formatter property. Here, `ctrl+q` is configured to open the `Insert Hyperlink` dialog.

{% tab template="rich-text-editor/toolbar", isDefaultActive=true %}

```html
<template>
  <ejs-richtexteditor ref="defaultRTE" :placeholder="placeholder" :formatter="formatter" >
    <p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
    <p><b>Key features:</b></p>
    <ul>
      <li>
        <p>Provides IFRAME and DIV modes</p>
      </li>
      <li>
        <p>Capable of handling markdown editing.</p>
      </li>
      <li>
        <p>Contains a modular library to load the necessary functionality on demand.</p>
      </li>
      <li>
        <p>Provides a fully customizable toolbar.</p>
      </li>
    </ul>
  </ejs-richtexteditor>
</template>

<script>
  import Vue from 'vue';
  import { RichTextEditorPlugin, Toolbar, Link, Image, HtmlEditor, QuickToolbar, IHtmlFormatterModel, HTMLFormatter } from '@syncfusion/ej2-vue-richtexteditor';

  Vue.use(RichTextEditorPlugin);

  export default {
    data() {
    var customHTMLModel = {
  keyConfig: {
'insert-link': 'ctrl+q', // confite the desired key
}
}
      return {
        placeholder: "Type Something",
        formatter: new HTMLFormatter(customHTMLModel), // to configure custom key
    }
    },
    provide: {
      richtexteditor: [Toolbar, Link, Image, HtmlEditor, QuickToolbar]
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

> We need to import `IHtmlFormatterModel` and `HTMLFormatter` to configure the shortcut key.
