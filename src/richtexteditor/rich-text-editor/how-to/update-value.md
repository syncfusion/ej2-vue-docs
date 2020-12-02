---
title: "Rich Text Editor How To capture ctrl+s"
component: "Rich Text Editor"
description: "This section for Syncfusion Vue Rich Text Editor component explains how to capture the ctrl+s to update the value."
---

# Capture ctrl+s to update the value

To achieve this, we need to bind the `keydown` event to the Rich Text Editor content and capture the `ctrl + s` key press using its keyCode.
In the `keydown` event handler, the `updateValue` method is called to update the [`value`](../../api/rich-text-editor/#value) property and then we can save the content in the required database using the same.

{% tab template="rich-text-editor/toolbar", isDefaultActive=true %}

```html
<template>
<div>
<div class="control-section">
    <div class="sample-container">
        <div class="default-section">
        <ejs-richtexteditor ref="rteObj" :toolbarSettings="toolbarSettings" :created="onCreate"><p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
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
<script>
import Vue from "vue";
import { RichTextEditorPlugin, Toolbar, HtmlEditor } from "@syncfusion/ej2-vue-richtexteditor";

Vue.use(RichTextEditorPlugin);

export default {
     data: function() {
        return {
        toolbarSettings: {
            type: 'MultiRow',
            items: ['Bold', 'Italic', 'Underline', 'StrikeThrough',
            'FontName', 'FontSize', 'FontColor', 'BackgroundColor',
            'LowerCase', 'UpperCase', '|',
            'Formats', 'Alignments', 'OrderedList', 'UnorderedList',
            'Outdent', 'Indent', '|',
            'CreateLink', 'Image', '|', 'ClearFormat', 'Print',
            'SourceCode', 'FullScreen', '|', 'Undo', 'Redo'
          ]
        },
        }
    },
    methods: {
    onCreate: function(){
      var instance = this.$refs.rteObj.$el.ej2_instances[0];
      instance.contentModule.getDocument().addEventListener("keydown",function(e: any):void{
            if(e.key === 's' && e.ctrlKey===true){
                  e.preventDefault(); // to prevent default ctrl+s action
                  instance.updateValue(); // to update the value after editing
                  let value: any= instance.value; // you can get the RTE content to save in the desired database
            }

      });
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