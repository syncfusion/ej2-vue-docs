---
title: "Achieve file upload programmatically"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Achieve file upload programmatically

You can upload a file programmatically using [upload](../../api/uploader/#upload) method.
The selected files data, get from [getFilesData](../../api/uploader/#getfilesdata) public method in uploader.

{% tab template="uploader/invisible" %}

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles"  :autoUpload="autoUpload" :asyncSettings= "path"></ejs-uploader>
    <div id="btnContainer">
        <span style='padding-left: 40px;'>
        <button id='first' style='margin-top: 30px' class='e-btn e-control'>Upload first file</button>
    </span>
    <span style=' padding-left: 40px;'>
        <button style='margin-top: 30px' id='full' class='e-btn e-control'>Upload all files</button>
    </span>
  </div>
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
          },
            autoUpload: false
        }
    },
    mounted: function() {
       document.getElementById('first').onclick = (args) => {
    this.$refs.uploadObj.upload(this.$refs.uploadObj.getFilesData()[0]);
};

document.getElementById('full').onclick = (args) => {
    this.$refs.uploadObj.upload(this.$refs.uploadObj.getFilesData());
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
    .e-upload-actions {
        display: none;
    }
    .e-btn {
        text-transform: none;
    }

</style>
```

{% endtab %}

>You can also explore [Vue File Upload](https://www.syncfusion.com/vue-ui-components/vue-file-upload) feature tour page for its groundbreaking features. You can also explore our [Vue File Upload example](https://ej2.syncfusion.com/vue/demos/#/material/uploader/default.html) to understand how to browse the files which you want to upload to the server.
