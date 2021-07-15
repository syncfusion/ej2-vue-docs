---
title: "Customize button with HTML element"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Customize button with HTML element

The uploader component allows you to customize the action buttons by using
[buttons](../../api/uploader/#buttons) &nbsp;property.

In the following example explains about how to customize the action buttons.

{% tab template="uploader/invisible" %}

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :buttons="buttons" :autoUpload="autoUpload" :asyncSettings= "path"></ejs-uploader>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin, SelectedEventArgs } from '@syncfusion/ej2-vue-inputs';
import { createElement } from '@syncfusion/ej2-base';
Vue.use(UploaderPlugin);
let uploadEle = createElement('span', { className: 'upload e-icons' });
uploadEle.innerHTML = 'Upload All';
let clearEle = createElement('span', { className: 'remove e-icons' });
clearEle.innerHTML = 'Clear All';

export default {
  data: function(){
        return {
          path:  {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
          },
        autoUpload: false,
        buttons: {
        browse: 'Choose file',
        clear: clearEle,
        upload: uploadEle
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

.e-upload .e-upload-actions .e-file-clear-btn,
.e-upload .e-upload-actions .e-file-upload-btn {
  -webkit-tap-highlight-color: transparent;
    background-color: #ddd;
    border-color: #c3c3c3;
    color: #000000;
    box-shadow: none;
    width: 50%;
    margin: 0;
    text-transform: none;
    padding: 8px 0;
}
.upload::before {
  content: '\e60f';
  position: relative;
  font-size: 10px;
  right: 10px;
}
.remove::before {
  content: '\e932';
  position: relative;
  font-size: 10px;
  right: 10px;
}
.e-upload .e-upload-actions {
  width: 100%;
}

</style>
```

{% endtab %}

>You can also explore [Vue File Upload](https://www.syncfusion.com/vue-ui-components/vue-file-upload) feature tour page for its groundbreaking features. You can also explore our [Vue File Upload example](https://ej2.syncfusion.com/vue/demos/#/material/uploader/default.html) to understand how to browse the files which you want to upload to the server.
