# Get Started with Vue CLI

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

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
You can choose the component that you want to install. For this application, we are going to use Button component.

To install Button component, use the following command

```bash
npm install @syncfusion/ej2-vue-buttons –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { ButtonPlugin } from '@syncfuion/ej2-vue-buttons';

Vue.use(ButtonPlugin);
```

Note : By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with name of Component from ComponentPlugin
and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { ButtonComponent, ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.component(ButtonPlugin.name, ButtonComponent);
```

Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the EJ2 Vue Button using `<ejs-button>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the Button component is provided as name in data option in the `<script>` section.

```html
<template>
    <div id="app">
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <ejs-button content="name"></ejs-button>
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

## Adding CSS Reference

Add Button component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
</style>
```

## Running the Application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="base/default", isDefaultActive=true %}

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