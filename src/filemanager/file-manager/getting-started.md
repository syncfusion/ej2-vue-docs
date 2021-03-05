---
title: "Getting Started"
component: "File Manager"
description: "Explains to get started with file manager control with its default functionality."
---

# Getting Started

This section briefly explains how to create File Manager component and configure its available functionalities in VueJS, using Essential JS 2 quickstart seed repository.

## Dependencies

The following are the dependencies required to use the File Manager component in your application:

```js
|-- @syncfusion/ej2-vue-filemanager
    |-- @syncfusion/ej2-vue-base
    |-- @syncfusion/ej2-vue-grids
    |-- @syncfusion/ej2-vue-navigations
        |-- @syncfusion/ej2-vue-inputs
        |-- @syncfusion/ej2-vue-lists
        |-- @syncfusion/ej2-vue-popups
            |-- @syncfusion/ej2-vue-buttons
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-grids
    |-- @syncfusion/ej2-filemanager
    |-- @syncfusion/ej2-navigations
        |-- @syncfusion/ej2-inputs
        |-- @syncfusion/ej2-lists
        |-- @syncfusion/ej2-popups
            |-- @syncfusion/ej2-buttons
```

## Get Started with Vue CLI

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications.
To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

Start a new project using below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install

```

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
You can choose the component that you want to install. For this application, we are going to use FileManager component.

To install FileManager component, use the following command

```bash
npm install @syncfusion/ej2-vue-filemanager --save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the FileManager Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with FileManager Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { FileManagerPlugin } from "@syncfusion/ej2-vue-filemanager";

Vue.use(FileManagerPlugin);
```

>Note: By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the FileManager Component and FileManager Component Plugin from EJ2 Vue Package, register the same using the Vue.component() with name of FileManager Component from FileManager Component Plugin and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { FileManagerComponent, FileManagerPlugin } from "@syncfusion/ej2-vue-filemanager";

Vue.component(FileManagerPlugin.name, FileManagerComponent);
```

>Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Adding Style sheet to the Application

Import the File Manager and its dependent component styles as given below in `<style>` section of the `App.vue` file.

```html
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

>Note: If you want to refer the combined component styles, please make use of our [CRG](https://crg.syncfusion.com/) (Custom Resource Generator) in your application.

## Initialize the File Manager

Add the EJ2 Vue FileManager using `<ejs-filemanager>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the FileManager component is provided as name in data option in the `<script>` section.

>Note: By default, LargeIcons view will be initialized in the File Manager. If Grid view is required then the DetailsView module needs to be injected using `provide`.

```html
<template>
    <div id="app">
        <ejs-filemanager id="file-manager" :ajaxSettings="ajaxSettings">
        </ejs-filemanager>
    </div>
</template>
<script>
import Vue from "vue";
import { FileManagerPlugin } from "@syncfusion/ej2-vue-filemanager";

Vue.use(FileManagerPlugin);
export default {
    data () {
        return {
           ajaxSettings:
            {
                url: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/FileOperations"
            }
        };
    }
}
</script>
```

## Run the application

Now use the `npm run dev` command to run the application in the browser.

```cmd
npm run dev
```

The following example shows the basic File Manager component.

{% tab template="file-manager/getting-started" %}

```html
<template>
    <div id="app">
        <ejs-filemanager id="file-manager" :ajaxSettings="ajaxSettings">
        </ejs-filemanager>
    </div>
</template>
<script>
import Vue from "vue";
import { FileManagerPlugin } from "@syncfusion/ej2-vue-filemanager";

Vue.use(FileManagerPlugin);

export default {
    data () {
        return {
           ajaxSettings:
            {
                url: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/FileOperations"
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

## File Download support

To perform the download operation, initialize the `downloadUrl` property in a [ajaxSettings](../api/file-manager/#ajaxsettings) of File Manager component.

```typescript
<script>
import Vue from "vue";
import { FileManagerPlugin } from "@syncfusion/ej2-vue-filemanager";

Vue.use(FileManagerPlugin);

export default {
    data () {
        return {
           ajaxSettings:
            {
                url: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/FileOperations",
                downloadUrl: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/Download"
            }
        }
    }
}
</script>
```

## File Upload support

To perform the upload operation, initialize the `uploadUrl` property in a [ajaxSettings](../api/file-manager/#ajaxsettings) of File Manager Component.

```typescript
<script>
import Vue from "vue";
import { FileManagerPlugin } from "@syncfusion/ej2-vue-filemanager";

Vue.use(FileManagerPlugin);

export default {
    data () {
        return {
           ajaxSettings:
            {
                url: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/FileOperations",
                uploadUrl: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/Upload"
            }
        }
    }
}
</script>
```

## Image Preview support

To perform the image preview support in the File Manager component, need to initialize the `getImageUrl` property in a [ajaxSettings](../api/file-manager/#ajaxsettings) of File Manager component.

{% tab template="file-manager/getting-started" %}

```html
<template>
    <div id="app">
        <ejs-filemanager id="file-manager" :ajaxSettings="ajaxSettings">
        </ejs-filemanager>
    </div>
</template>
<script>
import Vue from "vue";
import { FileManagerPlugin } from "@syncfusion/ej2-vue-filemanager";

Vue.use(FileManagerPlugin);

export default {
    data () {
        return {
           ajaxSettings:
            {
                url: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/FileOperations",
                getImageUrl: "https://ej2-aspcore-service.azurewebsites.net/api/FileManager/GetImage"
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

## Injecting feature modules

Basically, the file manager component contains large-icons view for displaying the files and folders, a breadcrumbbar for navigation and context menu for performing operations. However, these basic functionalities can be extended by using the additional feature modules like detailsview, toolbar, navigation pane, and context menu to change the layout and to simplify the navigation and file operations within the file system. The above modules can be injected using `provide`.

The following example shows you the File Manager with all feature modules.

{% tab template="file-manager/overview" %}

```html
<template>
<div id="app">
    <div class="wrapper">
     <ejs-filemanager id="overview_filemanager" :ajaxSettings="ajaxSettings" :view="view">
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
            // Initial view of File Manager is set to details view
            view:"Details"
        }
    },
    //Injecting additional modules in FileManager
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
</style>
```

{% endtab %}

>**Note:** The appearance of the File Manager can be customized by using [cssClass](../api/file-manager/#cssclass) property. This adds a css class to the root of the File Manager which can be used to add new styles or override existing styles to the File Manager.

## Switching initial view of the File Manager

The initial view of the File Manager can be changed to details or largeicons view with the help of [view](../api/file-manager/#view) property. By default, the File Manager will be rendered in large icons view.
When the File Manager is initially rendered, [created](../api/file-manager/#created) will be triggered. This event can be utilized for performing operations once the File Manager has been successfully created.

{% tab template="file-manager/view" %}

```html
<template>
    <div id="app">
        <ejs-filemanager id="file-manager" :view="view" :created="onCreate" :ajaxSettings="ajaxSettings">
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
            // Initial view of File Manager is set to details view
            view: "Details"
        };
    },
    provide: {
            filemanager: [DetailsView, NavigationPane, Toolbar]
    },
    methods: {
        // File Manager's created event function
        onCreate(args){
            console.log("File Manager has been created successfully");
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

## Maintaining component state on page reload

The File Manager supports maintaining the component state on page reload. This can be achieved by enabling [enablePersistence](../api/file-manager/#enablepersistence) property which maintains the following,
* Previous view of the File Manager - [View](../api/file-manager/#view)
* Previous path of the File Manager - [Path](../api/file-manager/#path)
* Previous selected items of the File Manager - [SelectedItems](../api/file-manager/#selecteditems)

For every operation in File Manager, ajax request will be sent to the server which then processes the request and sends back the response. When the ajax request is success, [success](../api/file-manager/#success) event will be triggered and [failure](../api/file-manager/#failure) event will be triggered if the request gets failed.

{% tab template="file-manager/persistence" %}

```html
<template>
    <div id="app">
        <ejs-filemanager id="file-manager" :enablePersistence="enablePersistence" :ajaxSettings="ajaxSettings" :success="onAjaxSuccess" :failure="onAjaxFailure">
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
            enablePersistence: true
        };
    },
    provide: {
            filemanager: [DetailsView, NavigationPane, Toolbar]
    },
    methods: {
        // File Manager's file onSuccess function
        onAjaxSuccess(args){
            console.log("Ajax request successful");
        },
        // File Manager's file onError function
        onAjaxFailure(args){
            console.log("Ajax request has failed");
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

>**Note:** The files of the current folder opened in the File manager can be refreshed programatically by calling [refreshFiles](../api/file-manager/#refreshfiles) method.

## Rendering component in right-to-left direction

It is possible to render the File Manager in right-to-left direction by setting the [enableRtl](../api/file-manager/#enablertl) API to true.

{% tab template="file-manager/rtl" %}

```html
<template>
    <div id="app">
        <ejs-filemanager id="file-manager" :enableRtl="enableRtl" :ajaxSettings="ajaxSettings">
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
            enableRtl: true
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
</style>
```

{% endtab %}

## Specifying the current path of the File Manager

The current path of the File Manager can be specified initially or dynamically using the [path](../api/file-manager/#path) property.

The following code snippet demonstrates specifying the current path in File Manager on rendering.

```html
<template>
    <div id="app">
        <ejs-filemanager id="file-manager" :path="path" :ajaxSettings="ajaxSettings">
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
            // Initial view of File Manager is set to details view
            view: "Details",
            // Specify the required current path
            path: '/Food'
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
</style>
```
