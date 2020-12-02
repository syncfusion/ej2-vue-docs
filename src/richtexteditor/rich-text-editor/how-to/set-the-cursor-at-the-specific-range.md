---
title: "Rich Text Editor How To set the cursor position"
component: "Rich Text Editor"
description: "This section for Syncfusion Vue Rich Text Editor component explains on how to set the cursor postion at the specific range."
---

# Set the cursor at the specific range

This can be achieved by using `setRange` method in the Rich Text Editor using `NodeSelection` instance. In this below sample, we have passed the text node (specific location in Rich Text Editor content) in `setStart` method and passed the range in `setRange` method of Rich Text Editor.

{% tab template="rich-text-editor/toolbar", isDefaultActive=true %}

```html
<template>
<div>
  <ejs-richtexteditor ref="defaultRTE" :placeholder="placeholder" >
    <p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
    <p id="key"><b>Key features:</b></p>
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
  <button v-on:click="onClick" class="e-btn">Set Cursor Position</button>
  </div>
</template>

<script>
  import Vue from 'vue';
  import { RichTextEditorPlugin, NodeSelection, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-vue-richtexteditor';

  Vue.use(RichTextEditorPlugin);

  export default {
    data() {
      return {
        placeholder: "Type Something",
    }
    },
   methods: {
     onClick: function(event){
       var instance = this.$refs.defaultRTE.$el.ej2_instances[0];
      let element: Element= instance.contentModule.getDocument().getElementById("key");
      let selectioncursor: NodeSelection = new NodeSelection();
      let range: Range = document.createRange();
      range.setStart(element, 1); // to set the range
      selectioncursor.setRange(document, range); // to set the cursor
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
