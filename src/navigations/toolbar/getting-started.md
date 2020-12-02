---
title: "Toolbar Getting Started"
component: "Toolbar"
description: "This section explains how to create the Toolbar control in an Vue application with its basic features."
---

# Getting Started

This section explains briefly about how to create a simple Toolbar using Vue and, configuring the Toolbar items like button, separator and
input components.

## Dependencies

Install the below required dependency package in order to use the Toolbar component in your application.

```javascript
|-- @syncfusion/ej2-vue-navigations
  |-- @syncfusion/ej2-base
  |-- @syncfusion/ej2-vue-base
  |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-inputs
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
You can choose the component that you want to install. For this application, we are going to use Toolbar component.

To install Toolbar component, use the following command

```bash
npm install @syncfusion/ej2-vue-navigations –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { ToolbarPlugin } from '@syncfuion/ej2-vue-navigations';

Vue.use(ToolbarPlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with name of Component from ComponentPlugin
and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { ToolbarComponent, ToolbarPlugin } from '@syncfusion/ej2-vue-navigations';

Vue.component(ToolbarPlugin.name, ToolbarComponent);
```

Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the EJ2 Vue Toolbar using `<ejs-toolbar>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the Toolbar component is provided as name in data option in the `<script>` section.

```html
<template>
    <div id="app">
    <ejs-toolbar >
    <e-items>
             <e-item text='Cut'></e-item>
             <e-item text='Copy'></e-item>
             <e-item text='Paste'></e-item>
             <e-item type='Separator'></e-item>
             <e-item text='Bold'></e-item>
             <e-item text='Italic'></e-item>
             <e-item text='Underline'></e-item>
          </e-items>
    </ejs-toolbar>
  </div>
</template>
<script>
import Vue from 'vue';
import { ToolbarPlugin } from '@syncfusion/ej2-vue-navigations';

Vue.use(ToolbarPlugin);
export default {
  name: 'app',
}
</script>
```

## Adding CSS Reference

Add Toolbar component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
</style>
```

## Running the Application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="toolbar/getting-started", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:100%;">
        <br>
         <ejs-toolbar >
    <e-items>
             <e-item text='Cut'></e-item>
             <e-item text='Copy'></e-item>
             <e-item text='Paste'></e-item>
             <e-item type='Separator'></e-item>
             <e-item text='Bold'></e-item>
             <e-item text='Italic'></e-item>
             <e-item text='Underline'></e-item>
          </e-items>
    </ejs-toolbar>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ToolbarPlugin } from "@syncfusion/ej2-vue-navigations";
Vue.use(ToolbarPlugin);

export default {
  name: 'app',
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
</style>
```

{% endtab %}

## Initialize the Toolbar using HTML elements

The Toolbar component can be rendered based on the given HTML element using `<ejs-toolbar>`.
You need to follow the below structure of HTML elements to render the Toolbar inside the `<ejs-toolbar>` tag.

```html
   <ejs-toolbar>   --> Root Toolbar Element
    <div>      --> Toolbar Items Container
       <div>   --> Toolbar Item Element
       </div>
    </div>
  </ejs-toolbar>
```

{% tab template="toolbar/toolbar-container" %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:100%;">
        <br>
         <ejs-toolbar>
            <div>
                <div><button class="e-btn e-tbar-btn">Cut</button></div>
                <div><button class="e-btn e-tbar-btn">Copy</button></div>
                <div><button class="e-btn e-tbar-btn">Paste</button></div>
                <div class="e-separator"></div>
                <div><button class="e-btn e-tbar-btn">Bold</button></div>
                <div><button class="e-btn e-tbar-btn">Italic</button></div>
            </div>
          </ejs-toolbar>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ToolbarPlugin } from "@syncfusion/ej2-vue-navigations";
Vue.use(ToolbarPlugin);

export default {
  name: 'app',
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
</style>
```

{% endtab %}

## See Also

* [How to add Toggle Button](./how-to/add-toggle-button/)