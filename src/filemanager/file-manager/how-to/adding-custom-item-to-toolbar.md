# How to add custom button in toolbar

The toolbar items can be customized using the [toolbarSettings](../../api/file-manager/#toolbarsettings) API and [toolbarClick](../../api/file-manager/#toolbarclick) events.

The following example shows adding a custom item in the toolbar.

The new toolbar button is added using [toolbarSettings](../../api/file-manager/#toolbarsettings). The [toolbarClick](../../api/file-manager/#toolbarclick) event is used to add an event handler to the new toolbar button.

{% tab template="file-manager/toolbar" %}

```html
<template>
    <div id="app">
        <ejs-filemanager id="file-manager"  ref="file_instance" :toolbarSettings="toolbarSettings" :ajaxSettings="ajaxSettings" :toolbarClick="toolbarClick" :toolbarCreate="toolbarCreate">
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
            //Custom item added along with default items
            toolbarSettings: {items: ["NewFolder", "Custom", "Upload", "Delete", "Download", "Rename", "SortBy", "Refresh", "Selection", "View", "Details"]}
        };
    },
    provide: {
            filemanager: [DetailsView, NavigationPane, Toolbar]
    },
    methods: {
        // Alert displayed for custom toolbar item in toolbarClick event
        toolbarClick: function(args){
            if (args.item.text === "Custom") {
                alert("You have clicked custom toolbar item")
            }
        },
        toolbarCreate: function(args) {
             for(let i: number = 0; i<args.items.length; i++) {
                if(args.items[i].id === this.$refs.file_instance.$el.id +"_tb_custom") {
                    args.items[i].prefixIcon= "e-icons e-fe-tick";
                }
            }
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

.e-fe-tick::before {
    content: '\e614';
}
</style>
```

{% endtab %}
