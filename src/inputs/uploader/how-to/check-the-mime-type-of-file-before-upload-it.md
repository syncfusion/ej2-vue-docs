---
title: "Check the MIME type of file before upload it"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Check the MIME type of file before upload it

By using [uploading](../../api/uploader/#uploading) event, you can get the file MIME type before uploading it to server.
In the below sample, file MIME type is shown in the alert box before file start to upload.

{% tab template="uploader/invisible" %}

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles"  :autoUpload="autoUpload" :asyncSettings= "path" :uploading="onBeforeUpload"></ejs-uploader>
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
    methods: {
onBeforeUpload: function(args): void {
 // get the file MIME type
    alert("File MIME type is: " + args.fileData.rawFile.type)
}
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
</style>
```

{% endtab %}
