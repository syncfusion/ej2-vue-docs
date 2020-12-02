---
title: "Validation"
component: "Uploader"
description: "Explains how to validate files before uploading it to a server such as valid file extensions, min and max file size, and duplicate files."
---

# Validation

The uploader component validate the selected files extension and size using the [allowedExtensions](../api/uploader/#allowedextensions),
[minFileSize](../api/uploader/#minfilesize) and [maxFileSize](../api/uploader/#maxfilesize) properties.
The files can be validated before uploading to the server and can be ignored on uploading.
Also, you can validate the files by setting the HTML attributes to the original input element.
The validation process occurs on drag-and-drop the files also.

## File type

You can allow the specific types of files alone to upload using the [allowedExtensions](../api/uploader/#allowedextensions) property.
The extension can be represented as collection by comma separators. The uploader component
filters the selected or dropped files matched against the specified file types and processes the
upload operation. The validation happens when you specify value to inline attribute accept to original input element.

{% tab template="uploader/file-type" %}

```html
<template>
    <div class="col-lg-8 control-section uploader chunk">
        <div class="control_wrapper">
            <ejs-uploader id='validation' name="UploadFiles" :asyncSettings= "path" ref="uploadObj" :allowedExtensions = "extensions"></ejs-uploader>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
import { FileInfo } from '@syncfusion/ej2-vue-inputs/uploader';
Vue.use(UploaderPlugin);
export default {
 data: function(){
        return {
          path:  {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
          },
          extensions: '.doc, .docx, .xls, .xlsx'
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

## File size

The uploader component allows you to validate the files based on its size.
The validation helps to restrict uploading large files or empty files to the server. The size can be represented in `bytes`.
By default, the uploader component allows you to upload **minimum file size** as 0 byte and
 **maximum file size** as 28.4 MB using using `minFileSize` and `maxFileSize` properties.

{% tab template="uploader/file-size" %}

```html
<template>
    <div class="col-lg-8 control-section uploader chunk">
        <div class="control_wrapper">
            <ejs-uploader id='validation' name="UploadFiles" :asyncSettings= "path" ref="uploadObj"  minFileSize=10000 maxFileSize=4000000>
            </ejs-uploader>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
import { FileInfo } from '@syncfusion/ej2-vue-inputs/uploader';
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
</style>
```

{% endtab %}

## Maximum files count

You can restrict uploading the maximum number of files using the **selected** event. In the selected event arguments,
you can get the currently selected files details using the `getFilesData()`.
You can modify the files details and assign the modified file list to the `eventArgs.modifiedFilesData`.

{% tab template="uploader/file-count" %}

```html
<template>
    <div class="col-lg-8 control-section uploader chunk">
        <div class="control_wrapper">
            <ejs-uploader id='validation' name="UploadFiles" :autoUpload= "autoUpload" :asyncSettings= "path" ref="uploadObj" :selected= "onFileSelect" :removing= "onFileRemove">
            </ejs-uploader>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
import { FileInfo } from '@syncfusion/ej2-vue-inputs/uploader';
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
        onFileSelect: function(args) {
            args.filesData.splice(5);
            let filesData = this.$refs.uploadObj.getFilesData();
            let allFiles = filesData.concat(args.filesData);
            if (allFiles.length > 5) {
                for (let i = 0; i < allFiles.length; i++) {
                    if (allFiles.length > 5) {
                        allFiles.shift();
                    }
                }
                args.filesData = allFiles;
                args.modifiedFilesData = args.filesData;
            }
            args.isModified = true;
        },

        onFileRemove: function (args) {
            args.postRawFile = false;
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

## Duplicate files

You can validate the duplicate files before uploading to server using the selected event.
Compare the selected files with the existing files data and filter the file list by removing the duplicate files.

{% tab template="uploader/validation" %}

```html
<template>
    <div class="col-lg-8 control-section uploader chunk">
        <div class="control_wrapper">
            <ejs-uploader id='validation' name="UploadFiles" :autoUpload= "autoUpload" :asyncSettings= "path" ref="uploadObj"
            :selected= "onFileSelect">
            </ejs-uploader>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
import { FileInfo } from '@syncfusion/ej2-vue-inputs/uploader';
import { detach, isNullOrUndefined, enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
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
        onFileSelect: function(args) {
        let existingFiles: FileInfo[] = this.$refs.uploadObj.getFilesData();
    for (let i: number = 0; i < args.filesData.length; i++) {
        for(let j: number = 0; j < existingFiles.length; j++) {
            if (!isNullOrUndefined(args.filesData[i])) {
                if (existingFiles[j].name == args.filesData[i].name) {
                    args.filesData.splice(i, 1);
                }
            }
        }
    }
    existingFiles = existingFiles.concat(args.filesData);
    args.modifiedFilesData = existingFiles;
    args.isModified = true;
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

## See Also

* [Validate image/* on drop](./how-to/validate-image-on-drop)
* [Determine whether uploader has file input (required validation)](./how-to/determine-whether-uploader-has-file-input)
* [Check file size before uploading it](./how-to/check-file-size-before-uploading-it)
* [Check the MIME type of file before uploading it](./how-to/check-the-mime-type-of-file-before-upload-it)
