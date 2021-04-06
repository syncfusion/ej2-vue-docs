---
title: "DropDownButton Getting Started"
component: "DropDownButton"
description: "This section helps to learn how to create the dropdownbutton in Vue application with its basic features in step-by-step procedure."
---

# Getting started

This section explains how to create a simple DropDownButton and to configure the DropDownButton component.

## Dependencies

The list of dependencies required to use the DropDownButton component in your application is given as follows:

```js
|-- @syncfusion/ej2-vue-splitbuttons
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-splitbuttons
    |-- @syncfusion/ej2-vue-base
    |-- @syncfusion/ej2-popups
        |-- @syncfusion/ej2-buttons
```

## Installation and configuration

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your Vue applications.
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

Install Syncfusion `DropDownButton` packages using below command.

```bash
npm install @syncfusion/ej2-vue-splitbuttons --save
```

## Registering DropDownButton component using `Vue.use()`

Import the DropDownButton Plugin from the Essential JS 2 Vue package and register the same using `Vue.use()` with Component Plugin as its argument.

Refer to the code snippet given below.

```javascript
import Vue from 'vue';
import { DropDownButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";

Vue.use(DropDownButtonPlugin);

export default {}
```

> By registering component plugin in Vue, all child directives are also globally registered.
We can also use `Vue.Component()` to register `DropDownButton`.
Refer [here](https://ej2.syncfusion.com/vue/documentation/base/getting-started/#registering-vue-component) to know more about component registration.

## Initialize DropDownButton

Add the EJ2 Vue DropDownButton using `<ejs-dropdownbutton>` to the `<template>` section of the `App.vue` file in `src` directory.

```html
<template>
<ejs-dropdownbutton :items='items'>Clipboard</ejs-dropdownbutton>
</template>

<script>
import Vue from 'vue';
import { DropDownButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";

Vue.use(DropDownButtonPlugin);

export default {
    data () {
        return {
            items:[
            {
                text: 'Cut'
            },
            {
                text: 'Copy'
            },
            {
                text: 'Paste'
            }]
        };
    }
}
</script>
```

## Adding CSS Reference

Add DropDownButton component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
</style>
```

## Run the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

The following example shows a basic DropDownButton component.

{% tab template="drop-down-button/default", isDefaultActive=true %}

```html
<template>
<ejs-dropdownbutton :items='items'>Clipboard</ejs-dropdownbutton>
</template>

<script>
import Vue from 'vue';
import { DropDownButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(DropDownButtonPlugin);

export default {
    data () {
        return {
            items:[
            {
                text: 'Cut'
            },
            {
                text: 'Copy'
            },
            {
                text: 'Paste'
            }]
        };
    }
}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
</style>
```

{% endtab %}

## See Also

* [DropDownButton with icons](./icons#dropdownbutton-icons)
* [How to hide dropdown arrow](./how-to/hide-dropdown-arrow)
* [Dropdown popup with separator](./popup-items#separator)