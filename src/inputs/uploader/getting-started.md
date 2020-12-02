---
title: "Getting Started"
component: "Uploader"
description: "Explains to get started with HTML5 file upload control with its key features such as asynchronous mode, handle success, fail action, etc."
---

# Getting Started

This section explains how to create and configure the simple uploader component.

## Dependencies

The following are the dependencies required to use the uploader component in your application:

```js
|-- @syncfusion/ej2-vue-inputs
    |-- @syncfusion/ej2-inputs
|-- @syncfusion/ej2-vue-base
    |-- @syncfusion/ej2-base
|-- @syncfusion/ej2-buttons

```

## Get Started with Vue CLI

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications.
To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
```

Start a new project using below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install

```

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
You can choose the component that you want to install. For this application, we are going to use Uploader component.

To install Uploader component, use the following command

```bash
npm install @syncfusion/ej2-vue-inputs –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { UploaderPlugin } from '@syncfuion/ej2-vue-inputs';

Vue.use(UploaderPlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with name of Component from ComponentPlugin
and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { UploaderComponent, UploaderPlugin } from '@syncfusion/ej2-vue-inputs';

Vue.component(UploaderPlugin.name, UploaderComponent);
```

> By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the EJ2 Vue uploader using `<ejs-Uploader>` to the `<template>` section of the `App.vue` file in src directory.

```html
<template>
    <div id="app">
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles"></ejs-uploader>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';

Vue.use(UploaderPlugin);
export default {
  name: 'app',
  data () {
    return { }
  }
}
</script>
```

## Adding CSS Reference

Add uploader component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
</style>
```

> The [Custom Resource Generator (CRG)](https://crg.syncfusion.com/) is an online web tool, which can be used to generate the custom script and styles for a set of specific components.
> This web tool is useful to combine the required component scripts and styles in a single file.

## Running the Application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

> The `Essential JS2 AJAX` library has been integrated for uploader server requests.
Hence, use the third party `promise` library like blue-bird to use the uploader in Internet Explorer.

{% tab template="uploader/getting-started" %}

```html
<template>
  <div>
    <div id="modalTarget" class="control-section; position:relative" style="height:350px;">
        <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles"></ejs-uploader>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(UploaderPlugin);

export default {
    data: function() {
        return {  }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
    #app {
        color: #008cff;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }
    .control-section {
        height: 100%;
        min-height: 200px;
    }
</style>
```

{% endtab %}

## Adding drop area

By default, the uploader component allows to upload files by drag the files from file explorer, and drop into the drop area.  You can configure any other external element as drop target using dropArea property.

In the following sample, drop target is configured.

{% tab template="uploader/getting-started" %}

```html
<template>
  <div>
    <div id='droparea'  >
            Drop files here to upload
    </div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles"  :dropArea = "dropElement"></ejs-uploader>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(UploaderPlugin);

export default {
    data: function() {
        return {
        dropElement: '#droparea'
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
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
    .fileupload {
        margin: 20px auto;
        width: 400px;
    }
    #droparea {
        padding: 50px 25px;
        margin: 30px auto;
        border: 1px solid #c3c3c3;
        text-align: center;
        width: 20%;
        display: inline-flex;
    }
    .e-file-select,
    .e-file-drop {
        display: none;
    }
    body .e-upload-drag-hover {
         outline: 2px dashed brown;
    }
    #uploadfile {
        width: 60%;
        display: inline-flex;
        margin-left: 5%;
    }
</style>
```

{% endtab %}

## Configure asynchronous settings

The uploader component process the files to upload in Asynchronous mode by default. Define the properties
[saveUrl](../api/uploader/asyncSettings/#saveurl) and [removeUrl](../api/uploader/asyncSettings/#removeurl) to
handle the save and remove action as follows.

{% tab template="uploader/getting-started" %}

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :asyncSettings= "path" ></ejs-uploader>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(UploaderPlugin);

export default {
    data: function() {
        return {
        path:  {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
        }
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
</style>
```

{% endtab %}

## Handle success and failed upload

You can handle the success and failure actions using the [success](../api/uploader/#success) and [failure](../api/uploader/#failure) &nbsp;events. To handle these event, define the function and assign it to corresponding event as follows.

{% tab template="uploader/getting-started" %}

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :asyncSettings= "path" :success= "onUploadSuccess" :failure= "onUploadFailed" ></ejs-uploader>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(UploaderPlugin);

export default {
    data: function() {
        return {
            path:  {
                saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
                removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
            }
        }
    },
      methods:{
        onUploadSuccess: function (args) {
            console.log('Uploaded successfully');
        },
        onUploadFailed: function (args) {
            console.log('Upload fails');
        }
      }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
</style>
```

{% endtab %}

## See Also

* [How to add additional data on upload](./how-to/add-additional-data-on-upload)
* [Achieve file upload programmatically](./how-to/achieve-file-upload-programmatically)
* [Achieve invisible upload](./how-to/achieve-invisible-upload)
