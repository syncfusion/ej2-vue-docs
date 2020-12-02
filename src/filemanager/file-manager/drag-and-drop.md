---
title: "Drag and Drop"
component: "File Manager"
description: "Drag and Drop Support in file manager"
---

# Drag And Drop

The file manager allows files or folders to be moved from one folder to another by using the  [allowDragAndDrop](../api/file-manager/#allowdraganddrop) property. It also supports uploading a file by dragging it from Windows Explorer to  FileManager control. You can enable or disable this support by using the [allowDragAndDrop](../api/file-manager/#allowdraganddrop) property of file manager.

The event triggered in drag and drop support are

* [fileDragStart](../api/file-manager/#filedragstart) - Triggers when the file/folder dragging is started.
* [fileDragging](../api/file-manager/#filedragging) - Triggers while dragging the file/folder.
* [fileDragStop](../api/file-manager/#filedragstop) - Triggers when the file/folder is about to be dropped at the target.
* [fileDropped](../api/file-manager/#filedropped) - Triggers when the file/folder is dropped.

{% tab template="file-manager/drag-and-drop" %}

```html
<template>
    <div id="app">
        <ejs-filemanager id="file-manager" :allowDragAndDrop="allowDragAndDrop"  :fileDragStart="onFileDragStart"  :fileDragStop="onFileDragStop" :fileDragging="onFileDragging" :fileDropped="onFileDropped" :ajaxSettings="ajaxSettings">
        </ejs-filemanager>
    </div>
</template>
<script>
import Vue from "vue";
import { FileManagerPlugin, DetailsView, NavigationPane, Toolbar } from "@syncfusion/ej2-vue-filemanager";

Vue.use(FileManagerPlugin);
export default {
    data () {
        return {
             ajaxSettings:
            {
                url: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/FileOperations",
                getImageUrl: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/GetImage",
                uploadUrl: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/Upload",
                downloadUrl: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/Download"
            },
            allowDragAndDrop: true
        };
    },
    provide: {
            filemanager: [DetailsView, NavigationPane, Toolbar]
    },
    methods: {
        // File Manager's file Drag start event function
        onFileDragStart: function(args){
            console.log("File Drag Start");
        },
        // File Manager's file Drag stop event function
        onFileDragStop: function(args){
            console.log("File Drag Stop");
        },
        // File Manager's file Dragging event function
        onFileDragging: function(args){
            console.log("File Dragging");
        },
        // File Manager's file Dropped event function
        onFileDropped: function(args){
            console.log("File Dropped");
        }
    }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-icons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-layouts/styles/material.css";
@import "../node_modules/@syncfusion/ej2-grids/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-filemanager/styles/material.css";
</style>
```

{% endtab %}