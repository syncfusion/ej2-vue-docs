# Getting Started with Syncfusion Vue UI Components and Vue CLI

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your Vue applications.
To install Vue CLI, use the following command.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

Start a new project using the following Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install

```

## Adding Syncfusion packages

All the available Syncfusion Vue packages are published in the [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
Choose the component to be installed. In this application, the button component is installed.

To install the button component, use the following command.

```bash
npm install @syncfusion/ej2-vue-buttons --save
```

## Registering Vue component

The two ways to register the Vue component are:
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the component plugin from the EJ2 Vue package and register it using Vue.use() with component plugin as its argument.

Refer to the following code snippet.

```typescript
import { ButtonPlugin } from '@syncfuion/ej2-vue-buttons';

Vue.use(ButtonPlugin);
```

Note : By registering the component plugin in Vue, all child directives can also be globally registered.

### Using Vue.component()

Import the component and component plugin from EJ2 Vue package and register it using the Vue.component() with name of component from component plugin and the EJ2 Vue component as its arguments.

Refer to the following the code snippet.

```typescript
import { ButtonComponent, ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.component(ButtonPlugin.name, ButtonComponent);
```

Note: By using the Vue.component(), only the EJ2 Vue component can be registered. The child directives should be registered separately.

## Creating Vue sample

Add the EJ2 Vue button to the `<template>` section of the `App.vue` file in src directory using `<ejs-button>`. The content attribute of the button component is provided as name in the data option of the `<script>` section.

```html
<template>
    <div id="app">
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <ejs-button :content="name"></ejs-button>
  </div>
</template>
<script>
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ButtonPlugin);
export default {
  name: 'app',
  data () {
    return {
      msg: 'Hi EJ2 Components for Vue',
      name: 'Button'
    }
  }
}
</script>
```

## Adding CSS reference

Add the styles of the button component to the `<style>` section of the `App.vue` file as follows.

```html
<style>
@import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
</style>
```

## Running the application

Now, run the `npm run dev` command in the console to build your application and open it in the browser.

{% tab template="common/default", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <ejs-button :content="name"></ejs-button>
  </div>
</template>
<script>
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ButtonPlugin);
export default {
  data () {
    return {
      msg: 'Hi EJ2 Components for Vue',
      name: 'Button'
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  #app {
    color: #008cff;
    height: 40px;
    left: 45%;
    position: absolute;
    top: 45%;
    width: 30%;
  }
</style>
```

{% endtab %}