---
title: "Rich Text Editor file attachments"
component: "Rich Text Editor"
description: "This section for Syncfusion Vue Rich Text Editor control explains on how to attach the files."
---

# File Attachments

The Rich Text Editor allows you to attach a file based on the file upload. You can attach your files using the file upload or drag-and-drop from your local path. When the file upload gets success, the attachment link inserts into the content.

In the below sample, configure the saveUrl and path properties to achieve file attachments.

        1. saveUrl: Provides service URL to save the files.
        2. path: Specifies the location to store the image.

The following sample illustrates how to attach a file in the Rich Text Editor.

```html
<template>
<div>
<div class="control-section">
    <div class="sample-container">
        <div class="default-section">
        <ejs-richtexteditor ref="rteObj" :insertImageSettings="insertImageSettings">
       <p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
        <p><b>Key features:</b></p>
          <ul>
            <li><p>Provides IFRAME and DIV modes</p></li>
            <li><p>Capable of handling markdown editing.</p></li>
            <li><p>Contains a modular library to load the necessary functionality on demand.</p></li>
            <li><p>Provides a fully customizable toolbar.</p></li>
          </ul>
        </ejs-richtexteditor>
             <ejs-uploader ref="uploadObj" :asyncSettings= "path"
            :dropArea = "dropElement" :success= "onImageUploadSuccess" ></ejs-uploader>
        </div>
    </div>
</div>

</div>
</template>

<script>
import Vue from "vue";
import { RichTextEditorPlugin, Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar, Table ,NodeSelection} from "@syncfusion/ej2-vue-richtexteditor";
import {UploaderPlugin} from "@syncfusion/ej2-vue-inputs";
Vue.use(RichTextEditorPlugin);
Vue.use(UploaderPlugin);

export default Vue.extend({
    data: function() {
        return {
           selection: new NodeSelection(),
            range: null,
            dropElement: '.e-richtexteditor',
            saveSelection : null,
          insertImageSettings: {
                    saveUrl: "[SERVICE_HOSTED_PATH]/api/uploadbox/Save",
                    path: "../Files/"
                },
                 path:  {
            saveUrl: '[SERVICE_HOSTED_PATH]/api/uploadbox/Save'
          },
        };
    },
    methods: {
        onImageUploadSuccess: function(args){
        this.$refs.rteObj.ej2Instances.contentModule.getEditPanel().focus();
        this.range = this.selection.getRange(document);
        this.saveSelection = this.selection.save(this.range, document);
        var fileUrl = document.URL + this.$refs.rteObj.ej2Instances.insertImageSettings.path + args.file.name;
        this.$refs.rteObj.ej2Instances.executeCommand('createLink', { url: fileUrl, text: fileUrl, selection: this.saveSelection });

        if (this.$refs.rteObj.ej2Instances.formatter.getUndoRedoStack().length === 0) {
                        this.$refs.rteObj.ej2Instances.formatter.saveData();
                    }
        saveSelection.restore();
        this.$refs.rteObj.ej2Instances.executeCommand('createLink', { url: fileUrl, text: fileUrl, selection: saveSelection });
        this.$refs.rteObj.ej2Instances.formatter.saveData();
        this.$refs.rteObj.ej2Instances.formatter.enableUndo(this.$refs.rteObj.ej2Instances);
        this.$refs.uploadObj.ej2Instances.clearAll();
        }
    },
    provide:{
        richtexteditor:[Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar, Table]
    }
});
</script>

```

To config server-side handler, refer the below code.

``` csharp
int x = 0;
string file;
 [AcceptVerbs("Post")]
        public void Save()
        {
            try
            {
                var httpPostedFile = System.Web.HttpContext.Current.Request.Files["UploadFiles"];
                file = httpPostedFile.FileName;
                if (httpPostedFile != null)
                {
                    Console.WriteLine(System.Web.HttpContext.Current.Server.MapPath("~/Files"));
                    var fileSave = System.Web.HttpContext.Current.Server.MapPath("~/Files");
                    if (!Directory.Exists(fileSave))
                    {
                        Directory.CreateDirectory(fileSave);
                    }
                    var fileName = Path.GetFileName(httpPostedFile.FileName);
                    var fileSavePath = Path.Combine(fileSave, fileName);
                    while (System.IO.File.Exists(fileSavePath))
                    {
                        file = "rte" + x + "-" + fileName;
                        fileSavePath = Path.Combine(fileSave, file);
                        x++;
                    }
                    if (!System.IO.File.Exists(fileSavePath))
                    {
                        httpPostedFile.SaveAs(fileSavePath);
                        HttpResponse Response = System.Web.HttpContext.Current.Response;
                        Response.Clear();
                        Response.Headers.Add("name", file);
                        Response.ContentType = "application/json; charset=utf-8";
                        Response.StatusDescription = "File uploaded succesfully";
                        Response.Headers.Add("url", fileSavePath);
                        Response.End();
                    }
                }
            }
            catch (Exception e)
            {
                HttpResponse Response = System.Web.HttpContext.Current.Response;
                Response.Clear();
                Response.ContentType = "application/json; charset=utf-8";
                Response.StatusCode = 204;
                Response.Status = "204 No Content";
                Response.StatusDescription = e.Message;
                Response.End();
            }
        }
```