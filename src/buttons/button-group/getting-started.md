---
title: "ButtonGroup Getting Started"
component: "ButtonGroup"
description: "This section helps to learn how to create the buttongroup in Vue application with its basic features in step-by-step procedure."
---

# Getting Started

This section explains how to create a simple ButtonGroup, and configure its available functionalities in Vue using
Vue quickstart seed repository.

## Dependencies

The list of dependencies required to use the Button component in your application is given below:

```js
|-- @syncfusion/ej2-splitbuttons
```

## Installation and configuration

* You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your Vue applications. To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

* To setup basic sample use the following Vue CLI commands.

```bash
vue init webpack-simple quickstart

cd quickstart

npm install

```

* Install Syncfusion `ButtonGroup` packages using below command.

```bash
npm install @syncfusion/ej2-splitbuttons --save
```

## Creating Vue Sample

Add a div element with class name as `e-btn-group` and add the button elements that needs to be group inside the `div`
element in `App.vue` file.

To render button elements as EJ2 Vue Button, then add [`Button dependencies`](./../button/getting-started#dependencies) in
`systemjs.config.js` file. Then import `ButtonPlugin` from `ej2-vue-buttons`.

```html

<template>
  <div id='app'>
    <div class="e-btn-group">
        <ejs-button>HTML</ejs-button>
        <ejs-button>CSS</ejs-button>
        <ejs-button>Javascript</ejs-button>
    </div>
  </div>
</template>

```

## Adding CSS Reference

Add ButtonGroup component's styles as given below in `<style>` section of the `App.vue` file.

```html

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
</style>

```

## Running the Application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="button-group/getting-started", isDefaultActive=true %}

```html

<template>
  <div id='app'>
    <div class="e-btn-group">
        <ejs-button>HTML</ejs-button>
        <ejs-button>CSS</ejs-button>
        <ejs-button>Javascript</ejs-button>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ButtonPlugin);
export default {
  name: 'app'
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
  #app {
   margin: 20px;
  }
  .e-btn-group {
    margin: 25px 5px 20px 20px;
  }
</style>

```

{% endtab %}

## Orientation

ButtonGroup can be arranged in vertical and horizontal orientation. By default, it is horizontally aligned.

### Vertical Orientation

ButtonGroup can be aligned vertically using the built-in CSS class `e-vertical` to the target element.

The following example illustrates how to achieve vertical orientation in ButtonGroup,

{% tab template= "button-group/getting-started" %}

```html

<template>
  <div id='app'>
    <div class="e-btn-group e-vertical">
        <ejs-button >HTML</ejs-button>
        <ejs-button >CSS</ejs-button>
        <ejs-button >Javascript</ejs-button>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ButtonPlugin);

export default {
  name: 'app'
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
  #app {
   margin: 20px;
  }
  .e-btn-group {
    margin: 25px 5px 20px 20px;
  }
</style>

```

{% endtab %}

> ButtonGroup with SplitButton component nesting won't works in vertical orientation.

## See Also

* [Initialize ButtonGroup using util function](./how-to/initialize-buttongroup-using-util-function)