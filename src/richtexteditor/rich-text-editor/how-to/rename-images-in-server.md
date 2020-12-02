---
title: "How To rename uploaded images before inserting in Rich Text Editor"
component: "Rich Text Editor"
description: "This section for Syncfusion Vue Rich Text Editor control explains on how to rename images in server and get the updated name for the image"
---

# Rename uploaded images in server before inserting it in the Rich Text Editor

By using the [`insertImageSettings`](../../api-richTextEditor.html#insertimagesettings) property, you can specify the server handler to upload the selected image. Then you can bind the [`imageUploadSuccess`](../../api-richTextEditor.html#imageUploadSuccess) event, to receive the modified file name from the server and update it in the Rich Text Editor's insert image dialog.

```html
<template>
<div>
<div class="control-section">
    <div class="sample-container">
        <div class="default-section">
        <ejs-richtexteditor ref="rteObj" :imageUploadSuccess="onImageUploadSuccess" :insertImageSettings="insertImageSettings" :toolbarSettings="toolbarSettings" ><p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
        <p><b>Key features:</b></p>
          <ul>
            <li><p>Provides IFRAME and DIV modes</p></li>
            <li><p>Capable of handling markdown editing.</p></li>
            <li><p>Contains a modular library to load the necessary functionality on demand.</p></li>
            <li><p>Provides a fully customizable toolbar.</p></li>
          </ul></ejs-richtexteditor>
        </div>
    </div>
</div>
</template>
<script>
    import Vue from "vue";
    import { RichTextEditorPlugin, Toolbar, Link, Count, Image, HtmlEditor, QuickToolbar } from "@syncfusion/ej2-vue-richtexteditor";

    Vue.use(RichTextEditorPlugin);

    export default {
        data: function() {
            return {
            toolbarSettings: {
                items: ['Bold', 'Italic', 'Underline', 'StrikeThrough','|',
                    'FontName', 'FontSize', 'FontColor', 'BackgroundColor',
                    'LowerCase', 'UpperCase', '|',
                    'Formats', 'Alignments', 'OrderedList', 'UnorderedList',
                    'Outdent', 'Indent', '|',
                    'CreateLink', 'Image', '|', 'ClearFormat', 'Print',
                    'SourceCode', 'FullScreen', '|', 'Undo', 'Redo']
            },
            insertImageSettings: {
                saveUrl: "[SERVICE_HOSTED_PATH]/api/uploadbox/Rename",
                path: "../Images/"
            },
        }
        },
        methods: {
            onImageUploadSuccess: function(args){
                if (args.e.currentTarget.getResponseHeader('name') != null) {
                    args.file.name = args.e.currentTarget.getResponseHeader('name');
                    let filename: any = document.querySelectorAll(".e-file-name")[0];
                    filename.innerHTML = args.file.name.replace(document.querySelectorAll(".e-file-type")[0].innerHTML, '');
                    filename.title = args.file.name;
                }
            },
            provide:{
                richtexteditor: [Toolbar, Link, Count, Image, HtmlEditor, QuickToolbar]
            },
        }
    }
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
</style>

```

To configure the server-side handler, refer the below code.

```csharp
[AcceptVerbs("Post")]
public void Rename()
{
    try
    {
        var httpPostedFile = System.Web.HttpContext.Current.Request.Files["UploadFiles"];
        imageFile = httpPostedFile.FileName;
        if (httpPostedFile != null)
        {
            var fileSave = System.Web.HttpContext.Current.Server.MapPath("~/Images");
            if (!Directory.Exists(fileSave))
            {
                Directory.CreateDirectory(fileSave);
            }
            var fileName = Path.GetFileName(httpPostedFile.FileName);
            var fileSavePath = Path.Combine(fileSave, fileName);
            while (System.IO.File.Exists(fileSavePath))
            {
                imageFile = "rteImage" + x + "-" + fileName;
                fileSavePath = Path.Combine(fileSave, imageFile);
                x++;
            }
            if (!System.IO.File.Exists(fileSavePath))
            {
                httpPostedFile.SaveAs(fileSavePath);
                HttpResponse Response = System.Web.HttpContext.Current.Response;
                Response.Clear();
                Response.Headers.Add("name", imageFile);
                Response.ContentType = "application/json; charset=utf-8";
                Response.StatusDescription = "File uploaded succesfully";
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
