---
title: "Avatar Getting Started"
component: "Avatar"
description: "Vue getting started with Avatar, a pure CSS component."
---

# Getting Started

The following section explains the required steps to build the simple Avatar component with its basic usage in step-by-step procedure.

## Installation and configuration

* You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications. To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

* To setup basic  sample use the following Vue CLI commands.

```bash
vue init webpack-simple quickstart

cd quickstart

npm install

```

* Install Syncfusion `Avatar` packages using below command.

```bash
npm install @syncfusion/ej2-layouts --save
```

## Using Avatar in Vue Application

Add an HTML span element with `e-avatar` class into the `<template>` section of the `App.vue` file in `src` directory.

```html
<template>
    <div id="app">
        <span class="e-avatar">GR</span>
    </div>
</template>
<script>
import Vue from "vue";

export default {
  data() {
    return {};
  }
}
</script>
```

## Adding CSS Reference

Add Avatar component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-layouts/styles/material.css";
</style>
```

> We can also use [CRG](https://crg.syncfusion.com/) to generate combined component styles.

## Run the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

The following example shows a basic Avatar.

{% tab template="avatar/getting-started", isDefaultActive=true %}

```html
<template>
    <div id='element'>
        <span class="e-avatar e-avatar-xlarge"></span>
        <span class="e-avatar e-avatar-large"></span>
        <span class="e-avatar"></span>
        <span class="e-avatar e-avatar-small"></span>
        <span class="e-avatar e-avatar-xsmall"></span>
    </div>
</template>
<script>
import Vue from "vue";

export default {
  data() {
    return {};
  }
}
</script>
<style>
    @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-layouts/styles/material.css";
    #element {
        display: block;
        width: 300px;
        margin: 130px auto;
        border-radius: 3px;
        justify-content: center;
    }

    .e-avatar {
        background-image: url(./pic01.png);
        margin: 2px;
    }
</style>

```

{% endtab %}

## See Also

[Types of Avatar](./avatar/types)
