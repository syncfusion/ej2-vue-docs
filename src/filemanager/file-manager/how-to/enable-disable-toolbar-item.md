# How to enable/disable toolbar item/items

The toolbar items can be enabled/disabled by specifying the items in [enableToolbarItems](../../api/file-manager/#enabletoolbaritems) or [disableToolbarItems](../../api/file-manager/#disabletoolbaritems) methods respectively.

The following example shows enabling and disabling toolbar items on button click.

{% tab template="file-manager/toolbar-items" %}

```html
<template>
    <div id="app">
        <ejs-button id="enable" cssClass="e-success">Enable New Folder toolbar item</ejs-button>
        <ejs-button id="disable" cssClass="e-danger">Disable New Folder toolbar item</ejs-button>
        <ejs-filemanager :created="onCreated" id="file-manager" ref="fileManagerinstance" :height="height" :ajaxSettings="ajaxSettings">
        </ejs-filemanager>
    </div>
</template>
<script>
import Vue from "vue";
import { FileManagerPlugin, DetailsView, NavigationPane, Toolbar } from "@syncfusion/ej2-vue-filemanager";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(FileManagerPlugin);
Vue.use(ButtonPlugin);

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
            view: "Details",
            height: "330px"
        };
    },
    provide: {
            filemanager: [DetailsView, NavigationPane, Toolbar]
    },
    methods: {
        onCreated: function(args){
            // Click event for enable button
            document.getElementById("enable").addEventListener('click', (event) => {
                // Enable new folder toolbar item
                this.$refs.fileManagerinstance.enableToolbarItems(["newfolder"]);
            });
            // Click event for disable button
            document.getElementById("disable").addEventListener('click', (event) => {
                // Disable new folder toolbar item
                this.$refs.fileManagerinstance.disableToolbarItems(["newfolder"]);
            });
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

#enable {
    position: relative;
    left: 20%;
    top: -10px;
}

#disable {
    position: relative;
    left: 30%;
    top: -10px;
}

</style>
```

{% endtab %}
