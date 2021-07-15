---
title: "Validate image on drop"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Validate image/* on drop

The uploader component allows you to upload all type of images by setting
`image/*` to [allowedExtensions](../../api/uploader/#allowedextensions) property or directly
you can set it to accept attribute of uploader element.

By default, the behavior is working with select a file using browse button. But, this behavior doesn’t support
on drag and drop the files. You can handle this behavior manually using [selected](../../api/uploader/#selected)
event by filtering the file types from application.

In the following example, validated image files using images/*. You are able to drag and drop the image files with extension of png, jpg, bpg, gif and tiff to upload it.

{% tab template="uploader/invisible" %}

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' :selected="onSelect" name="UploadFiles" :autoUpload="autoUpload" :asyncSettings= "path" :allowedExtensions="extensions"></ejs-uploader>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin, SelectedEventArgs } from '@syncfusion/ej2-vue-inputs';
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';
import { createElement, detach } from '@syncfusion/ej2-base';
Vue.use(UploaderPlugin);
Vue.use(DialogPlugin);

export default {
  data: function(){
        return {
          path:  {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
          },
            autoUpload: false,
            extensions: 'image/*'
        }
    },
    methods: {
          onSelect:function(args: SelectedEventArgs): void {
                if (args.event.type === 'drop') {
            let allImages: Array<string> = ['png', 'jpg', 'jpeg', 'gif', 'tiff', 'bpg'];
            let files = args.filesData;
            let modifiedFiles = [];
            for (let file of files) {
            if (allImages.indexOf(file.type) === -1) {
                file.status = 'File type is not allowed';
                file.statusCode = '0';
            }
            modifiedFiles.push(file);
            }
            args.isModified = true;
        }
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
 #container {
        visibility: hidden;
        padding-left: 5%;
        width: 100%;
    }
    #loader {
        color: #008cff;
        font-family: 'Helvetica Neue','calibiri';
        font-size: 14px;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }

</style>
```

{% endtab %}

>You can also explore [Vue File Upload](https://www.syncfusion.com/vue-ui-components/vue-file-upload) feature tour page for its groundbreaking features. You can also explore our [Vue File Upload example](https://ej2.syncfusion.com/vue/demos/#/material/uploader/default.html) to understand how to browse the files which you want to upload to the server.
