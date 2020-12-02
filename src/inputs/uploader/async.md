---
title: "Asynchronous upload"
component: "Uploader"
description: "Explains how to upload single or multiple files using asynchronous mode with auto-upload, preload, and additional HTTP headers."
---

# Asynchronous upload

The uploader component allows you to upload the files asynchronously. The upload process requires save and remove action URL to manage the upload process in the server.

    *   The save action is necessary to handle the upload operation
    *   The remove action is optional, can handle the removed files from server

The File can be uploaded automatically or manually. For more information, you can refer to the [Auto Upload](../api/uploader/#autoupload) section from the documentation.

## Multiple file upload

By Default, the uploader component allows you to select and upload multiple files simultaneously. The selected files are
organized in a list for every file selection until you clear it by clicking clear button that is shown in footer.

You can enable the multiple file selection by using `multiple` API.

The following example explains about [multiple](../api/uploader/#multiple) file upload settings.

In the following example, explains about multiple file upload settings.

{% tab template="uploader/asynchronous" %}

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :asyncSettings= "path" ></ejs-uploader>
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

## Single file upload

You can select and upload a single file by disabling the multiple file selection property. The file list item is removed for every selection and it always maintain a single file to upload.

The following example explains about single file upload settings.

{% tab template="uploader/asynchronous" %}

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :asyncSettings= "path" :multiple = 'multiple'></ejs-uploader>
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
            multiple: false
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

## Save Action

The save action handler upload the files that needs to be specified in the [saveUrl](../api/uploader/asyncSettingsModel/#saveurl) property.
The save handler receives the submitted files and manages the save process in server. After uploading the files to server location, the color of the selected file name changes to green and the remove icon is changed as bin icon.

    *   When the file is uploaded successfully, the event “success” triggers to handle the operation after upload.
    *   When the file is failed to upload, the event “failure” triggers with information, which cause this failure.

You can cancel the upload process by setting the upload event argument **eventargs.cancel** to true.

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :asyncSettings= "path" ></ejs-uploader>
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
                saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save'
            }
        }
    }
}
</script>
```

### Server-side configuration for save action

This section explains how to handle the server-side action for saving the file from server.

```csharp
[AcceptVerbs("Post")]
public void Save()
{
    try
    {
        if (HttpContext.Current.Request.Files.AllKeys.Length > 0)
        {
            var httpPostedFile = HttpContext.Current.Request.Files["UploadFiles"];

            if (httpPostedFile != null)
            {
                var fileSave = HttpContext.Current.Server.MapPath("UploadedFiles");
                var fileSavePath = Path.Combine(fileSave, httpPostedFile.FileName);
                if (!File.Exists(fileSavePath))
                {
                    httpPostedFile.SaveAs(fileSavePath);
                    HttpResponse Response = HttpContext.Current.Response;
                    Response.Clear();
                    Response.ContentType = "application/json; charset=utf-8";
                    Response.StatusDescription = "File uploaded succesfully";
                    Response.End();
                }
                else
                {
                    HttpResponse Response = HttpContext.Current.Response;
                    Response.Clear();
                    Response.Status = "400 File already exists";
                    Response.StatusCode = 400;
                    Response.StatusDescription = "File already exists";
                    Response.End();
                }
            }
        }
    }
    catch (Exception e)
    {
        HttpResponse Response = System.Web.HttpContext.Current.Response;
        Response.Clear();
        Response.ContentType = "application/json; charset=utf-8";
        Response.StatusCode = 400;
        Response.Status = "400 No Content";
        Response.StatusDescription = e.Message;
        Response.End();
    }
}

```

## Remove Action

The remove action is optional. Specify the URL to handle remove process from server. The remove handler receives the posted files and handle the remove operation in server.

    *   When the files are removed successfully from server, the success event triggers to denote the process has completed.
    *   When remove action fails, the event “failure” triggers with information, which cause failure in remove process.

> You can differentiate the file operation whether the success event triggers from save or remove action in its arguments **eventArgs.operation**.

You can remove the files which is not uploaded locally by clicking the remove icon. In this case, the success or failure events will not be triggered.

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :asyncSettings= "path" ></ejs-uploader>
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
            }
        }
    }
}
</script>
```

### Server-side configuration for remove action

This section explains how to handle the server-side action for removing the file from server.

```csharp
[AcceptVerbs("Post")]
public void Remove()
{
    try
    {
        var fileSave = "";
        if (HttpContext.Current.Request.Form["cancel-uploading"] != null)
        {
            fileSave = HttpContext.Current.Server.MapPath("UploadingFiles");
        }
        else
        {
            fileSave = HttpContext.Current.Server.MapPath("UploadedFiles");
        }
        var fileName = HttpContext.Current.Request.Files["UploadFiles"].FileName;
        var fileSavePath = Path.Combine(fileSave, fileName);
        if (File.Exists(fileSavePath))
        {
            File.Delete(fileSavePath);
        }
    }
    catch (Exception e)
    {
        HttpResponse Response = HttpContext.Current.Response;
        Response.Clear();
        Response.Status = "404 File not found";
        Response.StatusCode = 404;
        Response.StatusDescription = "File not found";
        Response.End();
    }
}

```

## Auto Upload

By default, the uploader processes the files to upload once the files are selected and added in upload queue. To upload manually, disable the [autoUpload](../api/uploader/#autoupload) &nbsp;property. When you disable this property, you can use the action buttons to call upload all or clear all actions manually. You can change those buttons text using the [buttons](../api/uploader/#buttons) &nbsp;property in the Uploader component.

{% tab template="uploader/asynchronous" %}

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :asyncSettings= "path" :autoUpload= 'autoUpload'></ejs-uploader>
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
            autoUpload: false
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

## Sequential Upload

By default, the uploader component process multiple files to upload simultaneously. When you enable the [sequentialUpload](../api/uploader/#sequentialupload) property, the selected files will process sequentially (one after the other) to the server. If the file uploaded successfully or failed, the next file will upload automatically in this sequential upload. This feature helps to reduce the upload traffic and reduce the failure of file upload.

{% tab template="uploader/sequential-upload" %}

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :asyncSettings= "path" :sequentialUpload= 'sequentialUpload'></ejs-uploader>
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
            sequentialUpload: true
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

## Preload Files

The uploader component allows you to preload the list of files that are uploaded in the server. The preloaded files are useful to view and remove the files from server that can be achieved by the [files](../api/uploader/#files) property. By default, the files are configured with uploaded successfully state on rendering file list. By default, the files are configured with uploaded successfully state on rendering file list. The following properties are mandatory to configure the preloaded files:

    *   Name
    *   Size
    *   Type

{% tab template="uploader/asynchronous" %}

```html
<template>
  <div>
  <ejs-uploader id='preloadFiles' ref="uploadObj" name="UploadFiles" :asyncSettings= "path" >
    <e-files>
        <e-uploadedfiles name='Nature' size=11000 type='.png'></e-uploadedfiles>
        <e-uploadedfiles name='TypeScript Succintly' size=20000 type='.pdf'></e-uploadedfiles>
        <e-uploadedfiles name='ASP.NET Webhooks' size=35000 type='.docx'></e-uploadedfiles>
    </e-files>
    </ejs-uploader>
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

## Adding additional HTTP headers with upload action

The Uploader component allows you to add the additional headers with `save` and `remove` action requests using the `uploading` and `removing` events, which helps to send validation token on file upload. Access the current request and set the request header within these events.

The following code block shows how to add the additional headers with save and remove action request.

```html
<template>
  <div>
  <ejs-uploader id='preloadFiles' ref="uploadObj" name="UploadFiles" :asyncSettings= "path"
  :uploading= "addHeaders" :removing= "addHeaders" ></ejs-uploader>
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
            }
        }
    },
    methods: {
         addHeaders: function (args) {
            args.currentRequest.setRequestHeader('custom-header', 'Syncfusion');
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

## See Also

* [How to add additional data on upload](./how-to/add-additional-data-on-upload)
* [How to add confirm dialog to remove the files](./how-to/add-confirm-dialog-to-remove-the-files)
* [Check the MIME type of file before uploading it](./how-to/check-the-mime-type-of-file-before-upload-it)
* [How to open and edit the uploaded files](./how-to/open-and-edit-the-uploaded-files)
