---
title: "Getting Started"
component: "Card"
description: "This section explains how to create a Essential JS 2 Card control in the Vue application with its basic features."
---

# Getting Started

This section explains how to create a simple **Card** using styles by configuring the structure for the header, content, using Essential JS 2
[quickstart](https://github.com/syncfusion/ej2-quickstart.git) seed repository.

## Dependencies

The Card is pure CSS component so no other package dependencies are needed to render the Card.

```js
|-- @syncfusion/ej2-layouts
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
You can choose the component that you want to install. For this application, we are going to use Card component.

To install Card component, use the following command

```bash
npm install @syncfusion/ej2-vue-layouts –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

Since the Card is a pure CSS component there is no need to refer the scripts

## Creating Vue Sample

Add the HTML div element with **e-card** class into the `<template>` section of the `App.vue` file in src directory,
the content attribute of the Card component is provided as name in data option in the `<script>` section.

```html
<template>
    <div id="app">
     <div class = "e-card">
          Sample Card
        </div>
  </div>
</template>
<script>
import Vue from 'vue';
export default {
  name: 'app',
}
</script>
```

## Adding CSS Reference

Add Card component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css';
</style>
```

## Adding a header and content

You can create Card with a header in a specific structure. For adding header you need to create a `div` element with `e-card-header` class added.

* You can include heading inside the Card header by adding a `div` element with `e-card-header-caption` class, and also content will be added
 by adding element with `e-card-content`. For detailed information, refer to the [Header and Content](./header-content/).

```html
    <div class = "e-card">                    --> Root Element
        <div class="e-card-header">           --> Root Header Element
            <div class="e-card-header-caption">    --> Root Heading Element
                <div class="e-card-header-title"></div>   --> Heading Title Element
            </div>
            <div class="e-card-content"></div>         --> Card content Element
        </div>
    </div>
```

## Running the Application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="card/getting-started", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:100%;">
        <br>
          <div tabindex="0" class="e-card" id="basic">
            <div class="e-card-header">
                <div class="e-card-header-caption">
                    <div class="e-card-title">Advanced UWP</div>
                </div>
            </div>
            <div class="e-card-content">
                Communicating with Windows 10 and Other Apps, the second in a five-part series written by Succinctly series
                author Matteo Pagani. To download the complete white paper, and other papers in the series, visit
                the White Paper section of Syncfusion’s Technology Resource Portal.
            </div>
        </div>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';

export default {
  name: 'app',
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";
</style>
```

{% endtab %}

## See Also

* [How to add a header and content](header-content/)