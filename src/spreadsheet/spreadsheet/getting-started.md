---
title: "Getting Started"
component: "SpreadSheet"
description: "This section helps to learn how to create the Spreadsheet control in Vue application with its basic features like selection, editing, formatting, importing and exporting to Excel."
---

# Getting Started

This section explains the steps to create a simple Spreadsheet control with basic features in Vue environment.

## Dependencies

The following list of dependencies are required to use the Spreadsheet control in your application:

```js
|-- @syncfusion/ej2-vue-spreadsheet
    |-- @syncfusion/ej2-vue-base
        |-- @syncfusion/ej2-base
        |-- @syncfusion/ej2-dropdowns
        |-- @syncfusion/ej2-navigations
        |-- @syncfusion/ej2-grids
```

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

## Adding Syncfusion Spreadsheet package

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.

To install Spreadsheet control, use the following command

```bash
npm install @syncfusion/ej2-vue-spreadsheet --save
```

> The **--save** will instruct NPM to include the spreadsheet package inside of the **dependencies** section of the **package.json**.

## Registering Spreadsheet Control

You can register the Spreadsheet control in your application by using the **Vue.use()**.

Refer to the code example given below.

```typescript

import Vue from 'vue';
import { SpreadsheetPlugin } from '@syncfusion/ej2-vue-spreadsheet';

Vue.use(SpreadsheetPlugin);
export default {}
```

> Registering **SpreadsheetPlugin** in vue, will register the Spreadsheet component along with its required child directives globally.

## Adding CSS Reference

import components CSS as given below in **style** section of the **App.vue** file. Here Material theme is used for this sample.

```html
<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';  
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';  
  @import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';  
  @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';  
  @import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-grids/styles/material.css';
  @import "../node_modules/@syncfusion/ej2-vue-spreadsheet/styles/material.css";
</style>
```

## Adding Spreadsheet Control

Add the Vue Spreadsheet by using **ejs-spreadsheet** selector in **template** section of the **App.vue** file.

```html
<template>
  <ejs-spreadsheet> </ejs-spreadsheet>
</template>

<script>
import Vue from 'vue';
import { SpreadsheetPlugin } from '@syncfusion/ej2-vue-spreadsheet';

Vue.use(SpreadsheetPlugin);
export default { }
</script>
```

## Run the application

The Vue Spreadsheet application is configured to compile and run the application in a browser. Use the following command to run the application.

```bash
npm run dev
```

{% tab template="spreadsheet/getting-started", iframeHeight="450px" , isDefaultActive=true %}

```html
<template>
   <ejs-spreadsheet></ejs-spreadsheet>
</template>

<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";

Vue.use(SpreadsheetPlugin);
export default { }
</script>

<style>
 @import "../node_modules/@syncfusion/ej2-vue-spreadsheet/styles/material.css";
 @import '../node_modules/@syncfusion/ej2-base/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';  
 @import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
 @import '../node_modules/@syncfusion/ej2-grids/styles/material.css';
 @import "../node_modules/@syncfusion/ej2-spreadsheet/styles/material.css";
</style>
```

{% endtab %}

## See Also

* [Data Binding](./data-binding)
* [Open and Save](./open-save)