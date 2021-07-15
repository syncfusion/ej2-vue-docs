---
title: "Trigger click event of input file from external button"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Trigger click event of input file from external button

You can trigger the input type file click event from external button. In the below sample, click event of input file was triggered from `Essential JavaScript 2 Button`.

{% tab template="uploader/invisible" %}

```html
<template>
  <div id="uploaderContainer">
    <!-- Initialize Uploader -->
<div id="dropArea">
    <span id="drop"> Drop image (JPG, PNG) files here or <button class='e-btn e-control' id="browse">Browse</button></span>
</div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles"  :asyncSettings= "path"></ejs-uploader>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(UploaderPlugin);

export default {
  data: function(){
        return {
          path:  {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
          }
        }
    },
    mounted:function {
    document.getElementById('browse').onclick = () => {
        document.getElementsByClassName('e-file-select-wrap')[0].querySelector('button').click();
    };
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
 #container {
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
    #dropArea {
        border: 1px dashed #c3c3cc;
        text-align: center;
        padding: 20px 0 10px;
    }
    .e-file-select-wrap {
        display: none;
    }
    .e-upload.e-lib.e-keyboard {
      border-bottom: 0px;
      border-top: 0px
    }
</style>
```

{% endtab %}

>You can also explore [Vue File Upload](https://www.syncfusion.com/vue-ui-components/vue-file-upload) feature tour page for its groundbreaking features. You can also explore our [Vue File Upload example](https://ej2.syncfusion.com/vue/demos/#/material/uploader/default.html) to understand how to browse the files which you want to upload to the server.