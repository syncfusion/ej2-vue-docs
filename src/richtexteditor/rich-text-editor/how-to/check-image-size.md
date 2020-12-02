---
title: " Rich text editor restricts the image uploading while uploading with large size"
component: "Rich Text Editor"
description: "This section for Syncfusion Vue Rich Text Editor control explains about, how to restrict the image to upload, when the given image size is greater than the allowed size"
---

# Restrict the image uploading while uploading with large size

By using the Rich text editor's `imageUploading` event, you can get the image size before uploading and restrict the image to upload, when the given image size is greater than the allowed size.

In the following, we have validated the image size before uploading and determined whether the image has been uploaded or not.

{% tab template="rich-text-editor/getting-started", isDefaultActive=true %}

```html
<template>
<div>
<div class="control-section">
    <div class="sample-container">
        <div class="default-section">
        <ejs-richtexteditor :imageUploading="onImageUploading" :insertImageSettings="insertImageSettings" :toolbarSettings="toolbarSettings" >
          </ejs-richtexteditor>
        </div>
    </div>
</div>
</div>
</template>
<script>
    import Vue from "vue";
    import { RichTextEditorPlugin, Toolbar, Link, Count, Image, HtmlEditor, QuickToolbar } from "@syncfusion/ej2-vue-richtexteditor";

    Vue.use(RichTextEditorPlugin);

    export default {
        data: function() {
            return {
            toolbarSettings: {
                items: ['Bold', 'Italic', 'Underline', 'StrikeThrough','|',
                    'FontName', 'FontSize', 'FontColor', 'BackgroundColor',
                    'LowerCase', 'UpperCase', '|',
                    'Formats', 'Alignments', 'OrderedList', 'UnorderedList',
                    'Outdent', 'Indent', '|',
                    'CreateLink', 'Image', '|', 'ClearFormat', 'Print',
                    'SourceCode', 'FullScreen', '|', 'Undo', 'Redo']
            },
            insertImageSettings: {
                saveUrl: "https://aspnetmvc.syncfusion.com/services/api/uploadbox/Save",
                path: "../Images/"
            },
        }
        },
        methods: {
            onImageUploading: function(args){
                console.log("file is uploading");
                var imgSize = 500000;
                var sizeInBytes = args.fileData.size;
                if ( imgSize < sizeInBytes ) {
                args.cancel = true;
            }
            }
            },
            provide:{
                richtexteditor: [Toolbar, Link, Count, Image, HtmlEditor, QuickToolbar]
            }
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