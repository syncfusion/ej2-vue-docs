---
title: "Multiple Selection"
component: "File Manager"
description: "Multiple Selection present in file manager"
---

# Multiple Selection

The file manager allows you to select multiple files by enabling the [allowMultiSelection](../api/file-manager/#allowmultiselection) property (enabled by default). The multiple selection can be done by pressing the `Ctrl` key or `Shift` key and selecting the files. The check box can also be used to do multiple selection. `Ctrl + A` can be used to select all files in the current directory. The [fileSelect](../api/file-manager/#fileselect) event will be triggered when the items of file manager control is selected or unselected.

{% tab template="file-manager/multiselect" %}

```html
<template>
    <div id="app">
        <ejs-filemanager id="file-manager" :fileSelect="onFileSelect" :allowMultiSelection="allowMultiSelection" :ajaxSettings="ajaxSettings">
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
            // allowMultiSelection is true by default
            allowMultiSelection: true
        };
    },
    provide: {
            filemanager: [DetailsView, NavigationPane, Toolbar]
    },
    methods: {
        // File Manager's file select event function
        onFileSelect: function(args){
            console.log(args.fileDetails.name + " has been " + args.action + "ed");
        }
    }
});
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

>Note: The File Manager has support to select files and folders initially or dynamically by specifying their names in [selectedItems](../api/file-manager/#selecteditems) property.