# Nested FileManager

FileManager can be rendered inside the other components like Tab, Dialog, and more.

* [Adding file manager inside the dialog](#adding-file-manager-inside-the-dialog)
* [Adding  file manager inside the tab](#adding-file-manager-inside-the-tab)

## Adding file manager inside the dialog

The following example shows the file manager component rendered inside the dialog. Click the browse button in the Uploader element to open the File Manager inside the Dialog control.

{% tab template="file-manager/file-upload" %}

```html
<template>
    <div>
        <div class="control-section">
            <div id='container' class="fileupload">
                <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles">
                </ejs-uploader>
                <ejs-button id="openBtn" v-on:click.native="btnClick">Browse...</ejs-button>
            </div>
            <div id='target' class="control-section">
                <ejs-dialog ref="uploadDialog" id="dialog" v-bind:visible="false" :header='dialogHeader' :animationSettings='animationSettings' :showCloseIcon='showCloseIcon' :open="dialogOpen" :close="dialogClose" :target='target'
                :width='dialogWidth'>
                    <ejs-filemanager ref="filemanagerObj" id="filemanager" :ajaxSettings='ajaxSettings' v-bind:allowMultiSelection="false" :fileOpen="onFileOpen" >
                    </ejs-filemanager>
                </ejs-dialog>
            </div>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';
import { FileManagerPlugin, NavigationPane, Toolbar, DetailsView, FileManagerComponent } from "@syncfusion/ej2-vue-filemanager";

Vue.use(FileManagerPlugin);
Vue.use(DialogPlugin);
Vue.use(UploaderPlugin);
Vue.use(ButtonPlugin);

let hostUrl = 'https://ej2-aspcore-service.azurewebsites.net/';

export default {
    data () {
        return {
            dialogHeader: 'Open',
            showCloseIcon: true,
            target: '#target',
            animationSettings: { effect: 'None' },
            dialogWidth: '850px',
            ajaxSettings:  {
                url: hostUrl + 'api/FileManager/FileOperations',
                getImageUrl: hostUrl + 'api/FileManager/GetImage',
                uploadUrl: hostUrl + 'api/FileManager/Upload',
                downloadUrl: hostUrl + 'api/FileManager/Download'
            }
        };
    },
    provide: {
            filemanager: [DetailsView, NavigationPane, Toolbar]
    },
    methods:{
        btnClick: function(event) {
            this.$refs.uploadDialog.show();
        },
        // Uploader will be hidden, if Dialog is opened
        dialogOpen: function() {
            var fileObj = this.$refs.filemanagerObj.ej2Instances;
            fileObj.refreshLayout();
            document.getElementById('container').style.display = 'none';
        },
        // Uploader will be shown, if Dialog is closed
        dialogClose: function() {
            var fileObj = this.$refs.filemanagerObj.ej2Instances;
            fileObj.path = "/";
            document.getElementById('container').style.display = 'block';
        },
        // File Manager's fileOpen event function
        onFileOpen: function(args) {
            let file = args.fileDetails;
            if (file.isFile) {
                args.cancel = true;
                this.$refs.uploadObj.files = [{name: file.name, size: file.size, type: file.type }];
                this.$refs.uploadDialog.hide();
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

   .fileupload {
        max-width: 500px;
        margin: auto;
    }
    #openBtn {
        position: absolute;
        top: 25px;
        margin-left: 13px;
    }
    #target {
        height: 550px;
    }
    #dialog {
        top: 20px !important;
        max-height: 500px !important;
        left: 30px !important;
    }
</style>
```

{% endtab %}

## Adding file manager inside the tab

The following example demonstrate that the file manager component is placed inside the content area of tab element.

{% tab template="file-manager/file-tab" %}

```html
<template>
    <div class="e-tab-section">
        <div class="col-lg-8 content-wrapper control-section">
            <div class="e-sample-resize-container">
            <ejs-tab ref="tabObj" id="tab_orientation" :showCloseButton=true heightAdjustMode='Auto'>
                <e-tabitems>
                    <e-tabitem :header='headerText0' :content='OverviewTemplate'></e-tabitem>
                    <e-tabitem :header='headerText1' :content='FilemanagerTemplate'></e-tabitem>
                </e-tabitems>
            </ejs-tab>
            </div>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { FileManagerPlugin, DetailsView, NavigationPane, Toolbar } from "@syncfusion/ej2-vue-filemanager";
import { TabPlugin } from "@syncfusion/ej2-vue-navigations";

Vue.use(TabPlugin);
Vue.use(FileManagerPlugin);

var Template1 = Vue.component("demo", {
  template: ` <div><div class="cnt-text">Overview</div><div>The file manager component contains a context menu for performing file operations, large-icons view for displaying the files and folders, and a breadcrumb for navigation. However, these basic functionalities can be extended by using the additional feature modules like toolbar, navigation pane, and details view to simplify the navigation and file operations within the file system</div></div>`,
  data() {
    return {
      data: {}
    };
  }
});

var Template2 = Vue.component("demo", {
   template: ` <div><div class="content-title">
                   <div class="cnt-text">File manager with default functionalities</div>
              </div>
              <ejs-filemanager id="file-manager" :ajaxSettings="ajaxSettings">
        </ejs-filemanager></div>`,

  data() {
    return {
       ajaxSettings:
            {
                url: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/FileOperations",
                getImageUrl: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/GetImage",
                uploadUrl: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/Upload",
                downloadUrl: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/Download"
            },
    };
  },
   provide: {
            filemanager: [DetailsView, NavigationPane, Toolbar]
    }
});

export default {
    data () {
        return {
            headerText0: { text: 'Overview' },
            headerText1: { text: 'FileManager' },
            OverviewTemplate: function () {
              return {
                  template : Template1
              }
            },
            FilemanagerTemplate: function () {
              return {
                  template : Template2
              }
            },
        };
    },
    provide: {
            filemanager: [DetailsView, NavigationPane, Toolbar]
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

.content-title {
    height: 50px;
    display: table;
    margin: 0 auto;
}
.cnt-text {
    text-align: center;
    font-size: 18px;
    font-weight: 600;
    padding: 10px;
}

</style>
```

{% endtab %}