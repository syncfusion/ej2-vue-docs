---
title: "ColorPicker Getting Started"
component: "ColorPicker"
description: "This section helps to learn how to create the colorpicker in Vue application with its basic features in step-by-step procedure."
---

# Getting Started

This section explains how to create a default ColorPicker and to configure the ColorPicker component.

## Dependencies

The list of dependencies required to use the ColorPicker component in your application is given below:

```javascript
|-- @syncfusion/ej2-vue-inputs
    |-- @syncfusion/ej2-vue-base
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-splitbuttons
```

## Installation and configuration

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

Install Syncfusion `ColorPicker` packages using below command.

```bash
npm install @syncfusion/ej2-vue-inputs --save
```

## Registering ColorPicker component using `Vue.use()`

Import the ColorPicker Plugin from the Essential JS 2 Vue package and register the same using `Vue.use()` with Component Plugin as its argument.

Refer to the code snippet given below.

```javascript
import Vue from 'vue';
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';

Vue.use(ColorPickerPlugin);

export default {}
```

> By registering component plugin in Vue, all child directives are also globally registered.
We can also use `Vue.Component()` to register `ColorPicker`.
Refer [here](https://ej2.syncfusion.com/vue/documentation/base/getting-started/#registering-vue-component) to know more about component registration.

## Initialize ColorPicker

Add the EJ2 Vue ColorPicker using `<ejs-colorpicker>` to the `<template>` section of the `App.vue` file in `src` directory.

```html
<template>
<ejs-colorpicker></ejs-colorpicker>
</template>

<script>
import Vue from 'vue';
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(ColorPickerPlugin);

export default {}
</script>
```

## Adding CSS Reference

Add ColorPicker component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
</style>
```

## Run the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

The following example shows a default ColorPicker.

{% tab template="color-picker/default", isDefaultActive=true, iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <h4>Choose Color</h4>
    <ejs-colorpicker></ejs-colorpicker>
</div>
</template>

<script>
import Vue from 'vue';
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ColorPickerPlugin);

export default {}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';

.wrap {
  margin: 0 auto;
  width: 300px;
  text-align: center;
}
</style>
```

{% endtab %}

## Inline type

By default, the ColorPicker will be rendered using SplitButton and open the pop-up to access the ColorPicker. To
render the ColorPicker container alone and to access it directly, render it as inline. It can be achieved by setting the [`inline`](.../api/color-picker#inline) property to `true`.

The following sample shows the inline type rendering of ColorPicker.

{% tab template="color-picker/default", iframeHeight="500px" %}

```html
<template>
  <div class='wrap'>
    <h4>Choose Color</h4>
    <ejs-colorpicker :inline="true" :showButtons="false"></ejs-colorpicker>
  </div>
</template>

<script>
import Vue from 'vue';
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ColorPickerPlugin);

export default {}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';

.wrap {
  margin: 0 auto;
  width: 300px;
  text-align: center;
}
</style>
```

{% endtab %}

>> The `showButtons` property is disabled in this sample because the control buttons are not needed for inline type. To know about the control buttons functionality, refer to the [`showButtons`](./how-to/hide-control-buttons) sample.

## See Also

* [Set color value](./mode-and-value#color-value)
* [ColorPicker customization](./how-to/customize-colorpicker)