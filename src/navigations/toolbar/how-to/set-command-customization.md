---
title: "Set command customization"
component: "Toolbar"
description: "This example demonstrates how to set the HTML attribute commands to Essential JS 2 Toolbar control items."
---

# Set command customization

The `htmlAttributes` property of the Toolbar item is used to set the HTML attributes ('ID', 'class', 'style' ,'role') for the commands.

When style attributes are added, if the same attributes were already present, they will be replaced. This is not so in the case of `class`
 attribute. Classes will be added to the element instead of replacing the existing ones.

Single or multiple CSS classes can be added to the Toolbar commands using the Toolbar item `cssClass` property.

{% tab template="toolbar/how-to/customization", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:100%;">
        <br>
         <ejs-toolbar >
           <e-items>
             <e-item text='Bold'  :htmlAttributes = 'boldAttribute'></e-item>
             <e-item text='Italic' :htmlAttributes = 'italicAttribute'></e-item>
             <e-item text='Underline' :htmlAttributes = 'underAttribute'></e-item>
             <e-item type='Separator'></e-item>
             <e-item text='Uppercase' cssClass = 'e-txt-casing'></e-item>
          </e-items>
    </ejs-toolbar>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ToolbarPlugin } from "@syncfusion/ej2-vue-navigations";
Vue.use(ToolbarPlugin);

export default {

name: 'app',


   data() {
  return {
      boldAttribute: { 'class': 'custom_bold', 'id': 'itemId' }
      italicAttribute :{ 'class': 'custom_italic' }
      underAttribute : { 'class': 'custom_underline' }
   }
   }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";

.custom_bold .e-tbar-btn-text {
     font-weight: 900;
}

.custom_italic .e-tbar-btn-text {
   font-style: italic;
}

.custom_underline .e-tbar-btn-text {
   text-decoration: underline red;
}

.e-txt-casing .e-tbar-btn-text {
   font-variant: small-caps;
}


.e-undo-icon:before {
    content: "\e76e"
}

.e-redo-icon:before {
    content: "\e726"
}

.e-cut-icon:before {
    content: "\e759"
}

.e-copy-icon:before {
    content: "\e70a"
}

.e-paste-icon:before {
    content: "\e77e"
}

.e-color-icon:before {
    content: "\e778"
}

.e-bold-icon:before {
    content: "\e71c"
}

.e-underline-icon:before {
    content: "\e75a"
}

.e-alignleft-icon:before {
    content: "\e75e"
}

.e-alignright-icon:before {
    content: "\e75f"
}

.e-aligncenter-icon:before {
    content: "\e74b"
}

.e-alignjustify-icon:before {
    content: "\e756"
}

.e-upload-icon:before {
    content: "\e725"
}

.e-download-icon:before {
    content: "\e824"
}

.e-indent-icon:before {
    content: "\e742"
}

.e-outdent-icon:before {
    content: "\e746"
}

.e-clear-icon:before {
    content: "\e760"
}

.e-reload-icon:before {
    content: "\e837"
}

.e-export-icon:before {
    content: "\e7fb"
}

.e-italic-icon:before {
    content: "\e709"
}

.e-bullets-icon:before {
    content: "\e75c"
}

.e-numbering-icon:before {
    content: "\e733"
}

.e-ascending-icon:before {
    content: "\e73f"
}

.e-descending-icon:before {
    content: "\e79d"
}

.e-zoomin-icon:before {
    content: "\e7d8"
}

.e-zoomout-icon:before {
    content: "\e7ea"
}
</style>
```

{% endtab %}