---
title: "Button Getting Started"
component: "Button"
description: "This section helps to learn how to create the button in Vue application with its basic features in step-by-step procedure."
---

# Getting Started

This section explains how to create a simple Button and to configure
the
 Button
component.

## Dependencies

The list of dependencies required to use the Button     component in your application is given      below :

```js
|-- @syncfusion/ej2-vue-buttons
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-vue-base
```

## Installation and   configuration

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

Install Syncfusion `Button` packages using below command.

```bash
npm install @syncfusion/ej2-vue-buttons --save
```

## Registering Button component using `Vue.use()`

Import the Button Plugin from the Essential JS 2 Vue package and register the same using `Vue.use()` with Component Plugin as its argument.

Refer to the code snippet given below.

```javascript
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ButtonPlugin);

export default {}
```

> By registering component plugin in Vue, all child directives are also globally registered.
We can also use `Vue.Component()` to register `Button`.
Refer [here](https://ej2.syncfusion.com/vue/documentation/base/getting-started/#registering-vue-component) to know more about component registration.

## Initialize Button

Add the EJ2 Vue Button using `<ejs-button>` to the `<template>` section of the `App.vue` file in `src` directory.

```html
<template>
<ejs-button>Button</ejs-button>
</template>

<script>
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
Vue.use(ButtonPlugin);

export default {}
</script>
```

## Adding CSS Reference

Add Button component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
</style>
```

## Run the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

The following example shows a basic Button.

{% tab template="button/default", isDefaultActive=true %}

```html
<template>
<ejs-button>Button</ejs-button>
</template>

<script>
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ButtonPlugin);

export default {}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

button {
  margin: 25px 5px 20px 20px;
}
</style>
```

{% endtab %}

## Change Button type

To change the default Button to flat Button, set the [`cssClass`](../api/button#cssclass) property to `e-flat` and text content of the Button is set using [`content`](../api/button#content) property.

{% tab template="button/default" %}

```html
<template>
<ejs-button cssClass='e-flat'>Button</ejs-button>
</template>

<script>
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ButtonPlugin);

export default {}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

button {
  margin: 25px 5px 20px 20px;
}
</style>
```

{% endtab %}

## See Also

* [Types of Button](./types-and-styles#button-types)