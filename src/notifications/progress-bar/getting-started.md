---
title: "ProgressBar Getting Started"
component: "ProgressBar"
description: "This section explains how to create ProgressBar component in Vue with its basic features."
---

# Getting Started

This section explains you the steps required to create a progressbar and demonstrate the basic usage of the progressbar control.

## Dependencies

Below is the list of minimum dependencies required to use the progressbar component.

```javascript
    |-- @syncfusion/ej2-vue-progressbar
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data: "*"
    |-- @syncfusion/ej2-svg-base
```

## Installation and Configuration

## Setup Vue Environment

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications.
To install Vue CLI use the following commands.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

## Create a Vue Application

Start a new Vue application using below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install
```

## Adding Syncfusion ProgressBar package

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.

To install progressbar component, use the following command

```bash
npm install @syncfusion/ej2-vue-progressbar --save
```

> The **--save** will instruct NPM to include the chart package inside of the `dependencies` section of the `package.json`.

## Registering ProgressBar Component

You can register the progressbar component in your application by using the `Vue.use()`.

Refer to the code example given below.

```typescript
import { ProgressBarPlugin } from '@syncfusion/ej2-vue-charts';

Vue.use(ProgressBarPlugin);
```

> Registering `ProgressBarPlugin` in vue, will register the chart component along with its required child directives globally.

## Add CSS Reference

The progressbar has different themes. They are:
* Material
* Fabric
* Bootstrap
* High Contrast

import chart component CSS as given below in `<style>` section of the `App.vue` file.

```html
<style>
<!-- Material theme used for this sample -->
@import "../node_modules/@syncfusion/ej2-vue-progressbar/styles/material.css";
</style>
```

* Syncfusion `ej2-vue-progressbar`
packages needs to be mapped in `systemjs.config.js` configuration file.

```javascript
/**
 * System configuration for vue samples
 * Adjust as necessary for your application needs.
 */
(function (global) {
  System.config({
    transpiler: "typescript",
    typescriptOptions: {
        compilerOptions: {
            target: "umd",
            module: "commonjs",
            moduleResolution: "node",
            emitDecoratorMetadata: true,
            experimentalDecorators: true
        }
    },
    paths: {
      // paths serve as alias
      'npm:': 'node_modules/',
      "syncfusion:": "node_modules/@syncfusion/", // syncfusion alias

    },
    // map tells the System loader where to look for things
    map: {
     typescript: "https://unpkg.com/typescript@2.2.2/lib/typescript.js",
        vue: "https://unpkg.com/vue/dist/vue.min.js",
        "@syncfusion/ej2-base": "syncfusion:ej2-base/dist/ej2-base.umd.min.js",
        "@syncfusion/ej2-data": "syncfusion:ej2-data/dist/ej2-data.umd.min.js",
        "@syncfusion/ej2-splitbuttons": "syncfusion:ej2-splitbuttons/dist/ej2-splitbuttons.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
        "@syncfusion/ej2-inputs": "syncfusion:ej2-inputs/dist/ej2-inputs.umd.min.js",
        "@syncfusion/ej2-vue-base": "syncfusion:ej2-vue-base/dist/ej2-vue-base.umd.min.js",
        "@syncfusion/ej2-vue-buttons": "syncfusion:ej2-vue-buttons/dist/ej2-vue-buttons.umd.min.js",
        "@syncfusion/ej2-vue-inputs": "syncfusion:ej2-vue-inputs/dist/ej2-vue-inputs.umd.min.js",
        "@syncfusion/ej2-vue-charts": "syncfusion:ej2-vue-charts/dist/ej2-vue-charts.umd.min.js",
        "@syncfusion/ej2-charts": "syncfusion:ej2-charts/dist/ej2-charts.umd.min.js",
        "@syncfusion/ej2-svg-base": "syncfusion:ej2-svg-base/dist/ej2-svg-base.umd.min.js",
        "@syncfusion/ej2-data": "syncfusion:ej2-data/dist/ej2-data.umd.min.js",
        "@syncfusion/ej2-pdf-export": "syncfusion:ej2-pdf-export/dist/ej2-pdf-export.umd.min.js",
        "@syncfusion/ej2-file-utils": "syncfusion:ej2-file-utils/dist/ej2-file-utils.umd.min.js",
        "@syncfusion/ej2-compression": "syncfusion:ej2-compression/dist/ej2-compression.umd.min.js",
        "@syncfusion/ej2-navigations": "syncfusion:ej2-navigations/dist/ej2-navigations.umd.min.js",
        "@syncfusion/ej2-calendars": "syncfusion:ej2-calendars/dist/ej2-calendars.umd.min.js",
        "@syncfusion/ej2-lists": "syncfusion:ej2-lists/dist/ej2-lists.umd.min.js",
        "@syncfusion/ej2-vue-progressbar": "syncfusion:ej2-vue-progressbar/dist/ej2-vue-progressbar.umd.min.js",
        "@syncfusion/ej2-progressbar": "syncfusion:ej2-progressbar/dist/ej2-progressbar.umd.min.js",
    },
  });
   System.import('index.js');
```

## Adding ProgressBar Component

* Add the Vue Chart by using `<ejs-progressbar>` selector in `<template>` section of the `App.vue` file.
The below example shows a basic progressbar,

```html
<template>
  <div id="app">
      <ejs-progressbar id="container"> </ejs-progressbar>
  </div>
</template>
<script>
import Vue from 'vue';
import { ProgressBarPlugin } from '@syncfusion/ej2-vue-progressbar';

Vue.use(ProgressBarPlugin);
export default {
  data () {
    return {
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-charts/styles/material.css";
 #container{
   height: 350px;
 }
</style>
```

* Now run the application in the browser using the below command.

```cmd
npm run dev
```

## Module Injection

Progressbar component are segregated into individual feature-wise modules. In order to use a particular feature,
you need to inject its feature service in the AppModule.
feature service name and description as follows.

* `ProgressAnnotation` - Inject this provider to use Annotation.

This module should be injected to the provide section as follows,

 ```javascript
import Vue from "vue";
import { ProgressBarPlugin, ProgressAnnotationService } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  provide: {
    progressbar: [ProgressAnnotationService]
  }
};
 ```

The below example shows a basic Progressbar.

`App.vue`

```html
<template>
    <div id='loader'>LOADING....</div>
    <div id='container'>
        <div class="row linear-parent">
            <div id="percentage" class="linear-progress">
             <ejs-progressbar
               id="percentage"
               type='Circular'
               :value='value'
               :animation="animation"
              >
             </ejs-progressbar>
          </div>
       </div>
    </div>
</template>
<script>
import Vue from "vue";
import { Browser } from "@syncfusion/ej2-base";
import { ProgressBarPlugin } from "@syncfusion/ej2-vue-progressbar";

Vue.use(ProgressBarPlugin);

export default Vue.extend({
  data: function() {
    return {
      value : 100,
      animation: {
        enable: true,
        duration: 2000,
        delay: 0
      },
    };
  },
  provide: {},
  methods: {}
});
</script>
<style>
  #loader {
    color: #008cff;
    height: 40px;
    left: 45%;
    position: absolute;
    top: 45%;
    width: 30%;
}
  #container {
    display: -webkit-box;
}
</style>

```
