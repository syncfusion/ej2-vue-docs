---
title: "Rich Text Editor How To customize the placeholder style"
component: "Rich Text Editor"
description: "This section for Syncfusion Vue Rich Text Editor component explains the customization of placeholder style."
---

# How to customize the placeholder style

By using `e-rte-placeholder` class, you can customize the placeholder style.

{% tab template="rich-text-editor/getting-started", isDefaultActive=true %}

```html
<template>
  <div>
    <ejs-richtexteditor ref="defaultRTE" :placeholder="placeholder" >
    </ejs-richtexteditor>
  </div>
  <style>
        .e-richtexteditor .e-rte-placeholder {
            font-family: monospace;
            color: deeppink;
        }
    </style>
</template>

<script>
  import Vue from 'vue';
  import { RichTextEditorPlugin, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-vue-richtexteditor';

  Vue.use(RichTextEditorPlugin);

  export default {
    data() {
      return {
          placeholder: "Type Something",
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
