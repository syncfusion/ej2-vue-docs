---
title: "Achieve invisible upload"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Achieve invisible upload

You can achieve the invisible upload feature by using selected event in uploader component. In the
following example, explains how to achieve invisible upload in uploader component.

{% tab template="uploader/invisible" %}

```html
<template>
  <div>
  <div id='preview'></div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :selected = "onupload" :autoUpload= "autoUpload" :asyncSettings= "path" :allowedExtensions = "extensions" ></ejs-uploader>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin, SelectedEventArgs } from '@syncfusion/ej2-vue-inputs';
import { createElement, detach, EventHandler } from '@syncfusion/ej2-base';
Vue.use(UploaderPlugin);

export default {
  data: function(){
        return {
          path:  {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
          },
          extensions: '.png, .jpg, .jpeg',
          autoUpload: false
        }
    },
    methods: {
        onupload:function(args: SelectedEventArgs){
    for(let i = 0; i< args.filesData.length ; i++){
        let liparentDiv = createElement('div',  { className: 'image-list'});
        let liImage = createElement('img',  { className: 'image'});
        liparentDiv.appendChild(liImage);
        this.readURL(liImage, args.filesData[i]);
        document.getElementById('preview').appendChild(liparentDiv);
    }
    args.cancel=true;
},

 readURL: function(liImage: HTMLElement, file: any) {
    let imgPreview: HTMLImageElement = liImage as HTMLImageElement;
    let imageFile: File = file.rawFile;
    let reader: FileReader = new FileReader();
    reader.addEventListener( 'load', () => {
        imgPreview.src = reader.result;
    }, false);
    if (imageFile) {
        reader.readAsDataURL(imageFile);
    }
};
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
    #preview {
  border: 2px dashed #ddd;
  padding: 15px;
}

.image-list {
  width: 134px;
  height: 117px;
  margin-right: 4px;
  border: 1px solid lightgrey;
  display: inline-block;
}

.image {
  width: 134px;
  height: 117px;
  margin-right: 4px;
  display: inline-block;
}

.e-control {
  border : 0;
}

.e-control ul {
  border: 1px solid #ddd;
}

.e-control .e-file-select,
.e-control .e-file-drop {
  display: none;
}

.e-upload.e-lib.e-keyboard {
  margin-top: 20px;
}
</style>
```

{% endtab %}
