# Getting Started

This section explains how to create a simple Chip and to configure
the
 Chip
component.

## Dependencies

The list of dependencies required to use the Chip     component in your application is given      below :

```js
|-- @syncfusion/ej2-vue-buttons
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-vue-base
```

## Installation and   configuration

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

Install Syncfusion `Button` packages using below command.

```bash
npm install @syncfusion/ej2-vue-buttons --save
```

## Registering Chip component using `Vue.use()`

Import the Chip Plugin from the Essential JS 2 Vue package and register the same using `Vue.use()` with Component Plugin as its argument.

Refer to the code snippet given below.

```javascript
import Vue from 'vue';
import { ChipListPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ChipListPlugin);

export default {}
```

> By registering component plugin in Vue, all child directives are also globally registered.
We can also use `Vue.Component()` to register `Chip`.
Refer [here](../common/template#vuecomponent) to know more about component registration.

## Initialize Chip

Add the EJ2 Vue Chip using `<ejs-chiplist>` to the `<template>` section of the `App.vue` file in `src` directory.

```html
<template>
 <ejs-chiplist id="chip" text="Janet Leverling"></ejs-chiplist>
</template>

<script>
import Vue from 'vue';
import { ChipListPlugin } from '@syncfusion/ej2-vue-buttons';
Vue.use(ChipListPlugin);

export default {}
</script>
```

## Adding CSS Reference

Add Chip component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import '../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css';
</style>
```

## Run the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

The following example shows a basic Chip.

{% tab template="chips/default", isDefaultActive=true %}

```html
<template>
 <ejs-chiplist id="chip" text="Janet Leverling"></ejs-chiplist>
</template>

<script>
import Vue from 'vue';
import { ChipListPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ChipListPlugin);

export default {}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css';

</style>
```

{% endtab %}
