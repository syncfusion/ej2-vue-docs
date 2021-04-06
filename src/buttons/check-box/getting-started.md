---
title: "CheckBox Getting Started"
component: "CheckBox"
description: "This section helps to learn how to create the checkbox in Vue application with its basic features in step-by-step procedure."
---

# Getting Started

This section explains how to create a simple CheckBox, and configure its available functionalities in Vue, using Vue quickstart seed repository.

## Dependencies

The list of dependencies required to use the CheckBox component in your application is given below:

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

Install Syncfusion `CheckBox` packages using below command.

```bash
npm install @syncfusion/ej2-vue-buttons --save
```

## Registering CheckBox component using `Vue.use()`

Import the CheckBox Plugin from the Essential JS 2 Vue package and register the same using `Vue.use()` with Component Plugin as its argument.

Refer to the code snippet given below.

```javascript
import Vue from 'vue';
import { CheckBoxPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(CheckBoxPlugin);

export default {}
```

> By registering component plugin in Vue, all child directives are also globally registered.
We can also use `Vue.Component()` to register `CheckBox`.
Refer [here](https://ej2.syncfusion.com/vue/documentation/base/getting-started/#registering-vue-component) to know more about component registration.

## Initialize CheckBox

Add the EJ2 Vue CheckBox using `<ejs-checkbox>` to the `<template>` section of the `App.vue` file in `src` directory.

```html
<template>
<ejs-checkbox label='Default'></ejs-checkbox>
</template>

<script>
import Vue from 'vue';
import { CheckBoxPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(CheckBoxPlugin);

export default {}
</script>
```

## Adding CSS Reference

Add CheckBox component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
</style>
```

## Run the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

The following example shows a basic CheckBox.

{% tab template="check-box/default", isDefaultActive=true %}

```html
<template>
<ejs-checkbox label='Default'></ejs-checkbox>
</template>

<script>
import Vue from 'vue';
import { CheckBoxPlugin } from "@syncfusion/ej2-vue-buttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(CheckBoxPlugin);

export default {}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

.e-checkbox-wrapper {
  margin-top: 18px;
}
</style>
```

{% endtab %}

## Change the CheckBox state

The Essential JS 2 CheckBox contains 3 different states visually, they are:
* Checked
* Unchecked
* Indeterminate

The CheckBox [`checked`](../api/check-box#checked) property is used to handle the checked and unchecked state.
In checked state a tick mark will be added to the visualization of CheckBox.

### Indeterminate

The CheckBox indeterminate state can be set through [`indeterminate`](../api/check-box#indeterminate) property.
CheckBox indeterminate state masks the real value of CheckBox visually.
The Checkbox cannot be changed to indeterminate state through the user interface,
this state can be achieved only through the property.

{% tab template= "check-box/default" %}

```html
<template>
<ul>
<li><ejs-checkbox label='Checked State' checked=true></ejs-checkbox></li>
<li><ejs-checkbox label='Unchecked State'></ejs-checkbox></li>
<li><ejs-checkbox label='Indeterminate State' indeterminate=true></ejs-checkbox></li>
</ul>
</template>

<script>
import Vue from 'vue';
import { CheckBoxPlugin } from "@syncfusion/ej2-vue-buttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(CheckBoxPlugin);

export default {}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

.e-checkbox-wrapper {
  margin-top: 18px;
}

li {
  list-style: none;
}
</style>
```

{% endtab %}