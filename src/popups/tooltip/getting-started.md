---
title: "Getting Started For Tooltip"
component: "Tooltip"
description: "Getting started with Tooltip component."
---

# Getting Started

The following section explains the required steps to build the simple Tooltip component with its basic usage in step-by-step procedure.

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

* Install Syncfusion `Tooltip` packages using below command.

```bash
npm install @syncfusion/ej2-vue-popups --save
```

## Registering Tooltip component using `Vue.use()`

Import the Tooltip Plugin from the Essential JS 2 Vue package and register the same using `Vue.use()` with Component Plugin as its argument.

Refer to the code snippet given below.

```typescript
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";

Vue.use(TooltipPlugin);
```

> By registering component plugin in Vue, all child directives are also globally registered.
We can also use `Vue.Component()` to register `Tooltip`.
Refer [here](https://ej2.syncfusion.com/vue/documentation/getting-started/vue-cli/#registering-vue-component) to know more about component registration.

## Initialize Tooltip

Add the EJ2 Vue Tooltip using `<ejs-tooltip>` to the `<template>` section of the `App.vue` file in `src` directory.

```html
<template>
    <div id="app">
    <ejs-tooltip ref="tooltip" content='Tooltip content' >
            <span>Show Tooltip</span>
        </ejs-tooltip>
  </div>
</template>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
Vue.use(TooltipPlugin);

export default {
  data() {
    return { };
  }
}
</script>
```

## Adding CSS Reference

Add Tooltip component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
</style>
```

> We can also use [CRG](https://crg.syncfusion.com/) to generate combined component styles.

## Run the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

The following example shows a basic Tooltip.

{% tab template="tooltip/getting-started", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container'>
      <ejs-tooltip class="tooltipcontainer" content='Tooltip content' target="#target">
        <div style="display: inline-block; position: relative; left: 50%;top: 100px;transform: translateX(-50%);">
          <ejs-button id='target'>Show Tooltip</ejs-button>
        </div>
      </ejs-tooltip>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
Vue.use(TooltipPlugin);
Vue.use(ButtonPlugin);

export default {
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
</style>
```

{% endtab %}

## See Also

[Positioning Tooltip](./position)

[Tooltip Open Mode](./open-mode)

[Customize the Tooltip](./customization)
