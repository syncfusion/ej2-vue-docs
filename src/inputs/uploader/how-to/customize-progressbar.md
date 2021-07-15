---
title: "Customize progressbar"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Customize progressbar

You can customize the progress bar by override the styles in uploader component.
In the following example, showcase about how to customize the progress bar's size, color and progress background.

{% tab template="uploader/invisible" %}

```html
<template>
  <div id='upload_container' class='custom_progress'>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :asyncSettings= "path"></ejs-uploader>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin, SelectedEventArgs } from '@syncfusion/ej2-vue-inputs';
Vue.use(UploaderPlugin);

export default {
  data: function(){
        return {
          path:  {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
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

    .custom_progress .e-upload .e-upload-files .e-upload-file-list .e-file-container .e-progress-inner-wrap .e-upload-progress-bar.e-upload-progress {
      background: yellow;
      height: 4px;
    }

     .custom_progress .e-upload .e-upload-files .e-upload-file-list .e-file-container .e-progress-inner-wrap {
      height: 4px;
      background-color: lightblue;
    }

</style>
```

{% endtab %}

>You can also explore [Vue File Upload](https://www.syncfusion.com/vue-ui-components/vue-file-upload) feature tour page for its groundbreaking features. You can also explore our [Vue File Upload example](https://ej2.syncfusion.com/vue/demos/#/material/uploader/default.html) to understand how to browse the files which you want to upload to the server.
