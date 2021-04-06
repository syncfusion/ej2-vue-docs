---
title: "RadioButton Getting Started"
component: "RadioButton"
description: "This section helps to learn how to create the radiobutton in Vue application with its basic features in step-by-step procedure."
---

# Getting Started

This section explains how to create a simple RadioButton, and to configure its available functionalities in Vue using Vue quickstart seed repository.

## Dependencies

The following list of dependencies are required to use the RadioButton component in your application.

```js
|-- @syncfusion/ej2-vue-buttons
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-vue-base
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

Install Syncfusion `RadioButton` packages using below command.

```bash
npm install @syncfusion/ej2-vue-buttons --save
```

## Registering RadioButton component using `Vue.use()`

Import the RadioButton Plugin from the Essential JS 2 Vue package and register the same using `Vue.use()` with Component Plugin as its argument.

Refer to the code snippet given below.

```javascript
import Vue from 'vue';
import { RadioButtonPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(RadioButtonPlugin);

export default {}
```

> By registering component plugin in Vue, all child directives are also globally registered.
We can also use `Vue.Component()` to register `RadioButton`.
Refer [here](https://ej2.syncfusion.com/vue/documentation/base/getting-started/#registering-vue-component) to know more about component registration.

## Initialize RadioButton

Add the EJ2 Vue RadioButton using `<ejs-radiobutton>` to the `<template>` section of the `App.vue` file in `src` directory.

```html
<template>
<ejs-radiobutton label='Default'></ejs-radiobutton>
</template>

<script>
import Vue from 'vue';
import { RadioButtonPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(RadioButtonPlugin);

export default {}
</script>
```

## Adding CSS Reference

Add RadioButton component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
</style>
```

## Run the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

The following example shows a basic RadioButton component.

{% tab template="radio-button/default", isDefaultActive=true %}

```html
<template>
<ul>
<li><ejs-radiobutton label='Option 1' name='default'></ejs-radiobutton></li>
<li><ejs-radiobutton label='Option 2' name='default' checked=true></ejs-radiobutton></li>
</ul>
</template>

<script>
import Vue from 'vue';
import { RadioButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(RadioButtonPlugin);

export default {}
</script>

<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";

.e-radio-wrapper {
  margin-top: 18px;
}

li {
  list-style: none;
}
</style>
```

{% endtab %}

## Change the RadioButton state

The Essential JS 2 RadioButton contains 2 states visually, they are as follows:
* Checked
* Unchecked

The RadioButton [`checked`](../api/radio-button#checked) property is used to handle the checked and unchecked state.
In the checked state an inner circle will be added to the visualization of RadioButton.

{% tab template="radio-button/default" %}

```html
<template>
<ul>
<li><ejs-radiobutton label='Option 1' name='default' checked=true></ejs-radiobutton></li>
<li><ejs-radiobutton label='Option 2' name='default'></ejs-radiobutton></li>
</ul>
</template>

<script>
import Vue from 'vue';
import { RadioButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(RadioButtonPlugin);

export default {}
</script>

<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";

.e-radio-wrapper {
  margin-top: 18px;
}

li {
  list-style: none;
}
</style>
```

{% endtab %}