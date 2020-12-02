# How to add custom menu item in context menu

The context menu can be customized using the [contextMenuSettings](../../api/file-manager/#contextmenusettings), [menuOpen](../../api/file-manager/#menuopen), and [menuClick](../../api/file-manager/#menuclick) events.

The following example shows adding a custom item in the context menu.

The [contextMenuSettings](../../api/file-manager/#contextmenusettings) is used to add new menu item. The [menuOpen](../../api/file-manager/#menuopen) event is used to add the icon to the new menu item. The [menuClick](../../api/file-manager/#menuclick) event is used to add an event handler to the new menu item.

{% tab template="file-manager/contextmenu" %}

```html
<template>
    <div id="app">
        <ejs-filemanager id="file-manager" ref="file_instance" :contextMenuSettings="contextMenuSettings" :ajaxSettings="ajaxSettings" :menuOpen="menuOpen" :menuClick="menuClick">
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
            // Custom menu item added to context menu
            contextMenuSettings: {
                file: ["Custom", "Open", "|", "Delete", "Rename", "|", "Details"],
                folder: ["Custom", "Open", "|", "Delete", "Rename", "|", "Details","Custom"],
                layout: ["Custom", "SortBy", "View", "Refresh", "|", "NewFolder", "Upload", "|", "Details", "|", "SelectAll"],
                visible: true
            }
        };
    },
    provide: {
            filemanager: [DetailsView, NavigationPane, Toolbar]
    },
    methods: {
        // Icon added to custom menu item in menuOpen event
        menuOpen: function(args){
            for(let i: number = 0; i<args.items.length; i++) {
                if(args.items[i].id === this.$refs.file_instance.$el.id +"_cm_custom") {
                    args.items[i].iconCss= "e-icons e-fe-tick";
                }
            }
        },
        // Displaying alert for custom menu in menuClick event
        menuClick: function(args) {
            if (args.item.text === "Custom") {
                alert("You have clicked custom menu item")
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
</style>
```

{% endtab %}
