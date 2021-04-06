---
title: "ProgressButton Getting Started"
component: "ProgressButton"
description: "This section helps to learn how to create the progressbutton in Vue application with its basic features in step-by-step procedure."
---

# Getting started

This section explains how to create a simple ProgressButton and to configure the ProgressButton component.

## Dependencies

The list of dependencies required to use the ProgressButton component in your application is given as follows:

```js
|-- @syncfusion/ej2-vue-splitbuttons
    |-- @syncfusion/ej2-vue-base
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-splitbuttons
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

Install Syncfusion `ProgressButton` packages using below command.

```bash
npm install @syncfusion/ej2-vue-splitbuttons --save
```

## Registering ProgressButton component using `Vue.use()`

Import the ProgressButton Plugin from the Essential JS 2 Vue package and register the same using `Vue.use()` with Component Plugin as its argument.

Refer to the code snippet given below.

```javascript
import Vue from 'vue';
import { ProgressButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";

Vue.use(ProgressButtonPlugin);

export default {}
```

> By registering component plugin in Vue, all child directives are also globally registered.
We can also use `Vue.Component()` to register `ProgressButton`.
Refer [here](https://ej2.syncfusion.com/vue/documentation/base/getting-started/#registering-vue-component) to know more about component registration.

## Initialize ProgressButton

Add the EJ2 Vue ProgressButton using `<ejs-progressbutton>` to the `<template>` section of the `App.vue` file in `src` directory.

```html
<template>
<ejs-progressbutton  content="Spin Left"></ejs-progressbutton>
</template>

<script>
import Vue from 'vue';
import { ProgressButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";

Vue.use(ProgressButtonPlugin);

export default {}
</script>
```

## Adding CSS Reference

Add ProgressButton component's styles as given below in `<style>` section of the `App.vue` file.

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

The following example shows a basic ProgressButton component.

{% tab template="progress-button/default", isDefaultActive=true %}

```html
<template>
 <ejs-progressbutton content="Spin Left"></ejs-progressbutton>
</template>

<script>
import Vue from 'vue';
import { ProgressButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ProgressButtonPlugin);

export default {}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
</style>
```

{% endtab %}

> ProgressButton supports different styles, types and sizes like [`Button`](https://ej2.syncfusion.com/documentation/button/?lang=typescript). In addition, it also supports `top` and `bottom` icon positions.

## Enable progress in button

You can enable the background filler UI by setting the [`enableProgress`](../api/progress-button#enableProgress) property to `true`.

{% tab template="progress-button/default", isDefaultActive=true %}

```html
<template>
 <ejs-progressbutton content="Spin Left"  :enableProgress="true"></ejs-progressbutton>
</template>

<script>
import Vue from 'vue';
import { ProgressButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ProgressButtonPlugin);

export default {}

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

* [Spinner and Progress options](spinner-and-progress#spinner)