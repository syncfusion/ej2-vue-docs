---
title: "File source"
component: "Uploader"
description: "Explains various sources to file upload such as drag and drop (customizable), paste the images, folder selection (directory upload)."
---

# File source

## Paste to upload

The uploader component allows you to upload the files using the select or drop files option from the file
explorer.  It also supports pasting to upload the image files. You can upload any currently copied images in the clipboard.

> When you paste the image, it will be saved in the server with the filename as `image.png`. The file name can
be renamed in the server end. You can generate a random name for the file name using [getUniqueID](../api/uploader/#getuniqueid) method.
Refer to the following example.

{% tab template="uploader/asynchronous" %}

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :asyncSettings= "path" :autoUpload= 'autoUpload' :uploading="onUploadBegin"></ejs-uploader>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin, UploadingEventArgs } from '@syncfusion/ej2-vue-inputs';
import { getUniqueID } from '@syncfusion/ej2-base';
Vue.use(UploaderPlugin);

export default {
    data: function() {
        return {
            path:  {
                saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
                removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
            },
            autoUpload: false
        }
    },
    methods:{
        onUploadBegin: function(args) {
            // check whether the file is uploading from paste.
            if (args.fileData.fileSource === 'paste') {
                let newName: string = getUniqueID(args.fileData.name.substring(0, args.fileData.name.lastIndexOf('.'))) + '.png';
                args.customFormData = [{'fileName': newName}];
            }
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
</style>
```

{% endtab %}

### Save action for paste to upload

```csharp
public void Save()
{
    var httpPostedFile = System.Web.HttpContext.Current.Request.Files["UploadFiles"];
    var fileSave = System.Web.HttpContext.Current.Server.MapPath("UploadedFiles");
    var fileSavePath = Path.Combine(fileSave, httpPostedFile.FileName);
    if (!System.IO.File.Exists(fileSavePath))
    {
        httpPostedFile.SaveAs(fileSavePath);
        var newName = System.Web.HttpContext.Current.Request.Form["fileName"];
        var filePath = Path.Combine(fileSavePath.Substring(0, fileSavePath.LastIndexOf("\\")), newName);
        // Rename the file
        System.IO.File.Move(fileSavePath, newName);
        HttpResponse Response = System.Web.HttpContext.Current.Response;
        Response.Clear();
        Response.ContentType = "application/json; charset=utf-8";
        Response.StatusDescription = fileSavePath;
        Response.End();
    }
}
```

## Directory upload

The uploader component allows you to upload all files in the folders to server by using
the [directoryUpload](../api/uploader/#directoryupload) property. When this property is enabled,
the uploader component processes the files by iterating through the files and sub-directories in a directory.
It allows you to select only folders instead of files to upload.

> The directory upload is available only in browsers that supports **HTML5 directory**. The uploader will
process directory upload by dragging and dropping in the Edge browser.
Refer to the following example to upload files to the server.

{% tab template="uploader/asynchronous" %}

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :asyncSettings= "path" :directoryUpload = 'directory'></ejs-uploader>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(UploaderPlugin);

export default {
    data: function() {
        return {
            path:  {
                saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
                removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
            },
            directory: true
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
</style>
```

{% endtab %}

### Save action for directory upload

```csharp
public void Save() {
    var httpPostedFile = HttpContext.Current.Request.Files["UploadFiles"];
    var fileSave = HttpContext.Current.Server.MapPath("UploadedFiles");
    // split the folders by using file name
    string[] folders = httpPostedFile.FileName.Split('/');
    string fileSavePath = "";
    if (folders.Length > 1)
    {
        for (var i = 0; i < folders.Length - 1; i++)
        {
            var newFolder = Path.Combine(fileSave, folders[i]);
            // create folder
            Directory.CreateDirectory(newFolder);
            fileSave = newFolder;
        }
        fileSavePath = Path.Combine(fileSave, folders[folders.Length - 1]);
    }
    else
    {
        fileSavePath = Path.Combine(fileSave, httpPostedFile.FileName);
    }
    if (!System.IO.File.Exists(fileSavePath))
    {
        // save file in the corresponding server location
        httpPostedFile.SaveAs(fileSavePath);
        HttpResponse Response = System.Web.HttpContext.Current.Response;
        Response.Clear();
        Response.ContentType = "application/json; charset=utf-8";
        // Sending the file path to client side
        Response.StatusDescription = fileSavePath;
        Response.End();
    }
}
```

## Drag and drop

The uploader component allows you to drag and drop the files to upload. You can drag the files from file explorer and drop into the drop area. By default, the uploader component act as drop area element. The drop area gets highlighted when you drag the files over drop area.

### Custom drop area

The uploader component allows you to set external target element as drop area using the [dropArea](../api/uploader/#droparea) property. The element can be represented as HTML element or element’s id.

{% tab template="uploader/draganddrop" %}

```html
<template>
  <div>
    <div id='droparea'  >
            Drop files here to upload
    </div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :asyncSettings= "path" :dropArea= 'dropTarget' ></ejs-uploader>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(UploaderPlugin);

export default {
    data: function() {
        return {
            path:  {
                saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
                removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
            },
            dropTarget: '#droparea'
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
    .fileupload {
        margin: 20px auto;
        width: 400px;
    }
    #droparea {
        padding: 50px 25px;
        margin: 30px auto;
        border: 1px solid #c3c3c3;
        text-align: center;
        width: 20%;
        display: inline-flex;
    }
    .e-file-select,
    .e-file-drop {
        display: none;
    }
    body .e-upload-drag-hover {
         outline: 2px dashed brown;
    }
    #uploadfile {
        width: 60%;
        display: inline-flex;
        margin-left: 5%;
    }
</style>
```

{% endtab %}

### Customize drop area

You can customize the appearance of drop area by overriding the default drop area styles. The class “” and “” is available to handle this customization.

{% tab template="uploader/custom-drop-area" %}

```html
<template>
  <div id="UploaderDropTarget">
         <div id='dropArea' style='height: auto; overflow: auto'>
            <span id='drop'> Drop files here or <a href="" id='browse'><u>Browse</u></a> </span>
        <ejs-uploader id='templateupload' name="UploadFiles" :asyncSettings= "path" ref="uploadObj" :dropArea= "dropElement">
        </ejs-uploader>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(UploaderPlugin);

export default {
    data: function() {
        return {
            path:  {
                saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
                removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
            },
            dropElement: '#drop'
        }
    },
     mounted: function () {
        document.getElementById('browse').onclick = () => {
        document.getElementsByClassName('e-file-select-wrap')[0].querySelector('#templateupload').click();
        return false;
    }
}
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
   #UploaderDropTarget {
        min-height: 50px;
        padding-top: 15px;
        position: relative;
        display: inline-block;
        font-size: 13px;
        top: -3px;
        width: 100%;
    }

.e-file-select-wrap {
    display: none;
}
#dropArea .e-upload {
    border: 0;
    margin-top: 15px;
}
#drop {
    padding-left: 30%;
}
#dropArea {
    min-height: 18px;
    border: 1px dashed #c3c3cc;
    padding-top: 15px;
    margin: 20px auto;
    width: 400px;
}

</style>
```

{% endtab %}

## See Also

* [Achieve file upload programmatically](./how-to/achieve-file-upload-programmatically)
* [Validate image/* on drop](./how-to/validate-image-on-drop)
