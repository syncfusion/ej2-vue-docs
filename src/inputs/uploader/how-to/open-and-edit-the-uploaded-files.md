---
title: "Open and edit the uploaded files"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Open and edit the uploaded files

The uploader component allows you to modify the file after uploading to the server, which can be achieved using success event of the uploader.

You can retrieve the saved file path in the uploader success event and assign it to custom attribute (data-file-name) value of the respective file list element to open the uploaded file. Click the respective file element to create a new request along with saved file path using http header. In the server-side, get the file path from the header and open the file using process.start method

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' :success="onUploadSuccess" name="UploadFiles" :asyncSettings= "path"></ejs-uploader>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin, SelectedEventArgs } from '@syncfusion/ej2-vue-inputs';
import { createElement } from '@syncfusion/ej2-base';
Vue.use(UploaderPlugin);

export default {
  data: function(){
        return {
          path:  {
            saveUrl: 'YourHosedService/Home/Save',
            removeUrl: 'YourHosedService/Home/Remove'
          }
        }
    },
    methods: {
        onUploadSuccess: function(args) {
        let liElements = document.body.querySelectorAll('.e-upload-file-list');
        for (let i = 0; i < liElements.length; i++) {
            if (liElements[i].getAttribute('data-file-name') == args.file.name) {
                liElements[i].addEventListener('click', () => { this.openFile(args, event); });
                // File path have to update from server end in response status description.
                liElements[i].setAttribute('file-path', args.e.target.statusText);
            }
        }
   },
   openFile: function(args, e) {
    if (!e.target.classList.contains('e-file-delete-btn') && !e.target.classList.contains('e-file-remove-btn'))
    {
        let ajax = new XMLHttpRequest();
        // create new request for open the selected file
        ajax.open("POST", "YourHosedService/Home/openFile');
        let liElements = document.getElementsByClassName('e-upload')[0].querySelectorAll('.e-upload-file-list');
        for (let i = 0; i < liElements.length; i++) {
            if (liElements[i].getAttribute('data-file-name') == args.file.name) {
                // Added the file path in header to get it in server side.
            ajax.setRequestHeader('filePath', liElements[i].getAttribute('file-path').toString());
            }
        }
        ajax.send();
    }
}
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
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

## Server side for open and edit the uploaded files

```csharp
        public void Save()
        {
            var httpPostedFile = System.Web.HttpContext.Current.Request.Files["UploadFiles"];
            var currentPath = System.Web.HttpContext.Current.Server;
            var fileSave = currentPath.MapPath("UploadedFiles");
            var fileSavePath = System.IO.Path.Combine(fileSave, httpPostedFile.FileName);
            if (!System.IO.File.Exists(fileSavePath))
            {
                httpPostedFile.SaveAs(fileSavePath);
                HttpResponse Response = System.Web.HttpContext.Current.Response;
                Response.Clear();
                Response.ContentType = "application/json; charset=utf-8";
                Response.StatusDescription = fileSavePath;
                Response.End();
            }
        }

        [AcceptVerbs("Post")]
        public void openFile()
        {
            // Check whether the file is available in the corresponding location
            if (System.IO.File.Exists(Request.Headers.GetValues("filePath").First()))
            {
                // This will open the selected file from server location in desktop
                Process.Start(Request.Headers.GetValues("filePath").First());
            }
        }
```

> Add the `filePath` in allow-headers in `web.config` file.

```csharp
    <customHeaders>
        <add name="Access-Control-Allow-Headers" value="accept, maxdataserviceversion, origin, x-requested-with, dataserviceversion,content-type, chunk-index, Authorization, filePath" />
    </customHeaders>
```