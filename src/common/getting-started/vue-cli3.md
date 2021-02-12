# Overview

Vue CLI 3 is a complete rewrite of the previous version of the Vue command line interface tool and comes with a set of new features which makes Vue development and the management of Vue projects a lot easier.

## Getting Started with Syncfusion Vue UI Components and Vue CLI

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your Vue applications.
At first it is mostly recommended to  uninstall the old Vue CLI package from your system.

```bash
npm uninstall vue-cli -g
```

Then install Vue CLI 3, use the following commands.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

Start a new project using the following Vue CLI command.

```bash
vue create quickstart

cd quickstart
npm install

```

Then we’ll be prompted with the option to pick a default preset or to manually select features. Using the arrow keys, we can highlight our selection. But now we can select the `default`, then hit enter. If you wish to select manually, please use this [`vue-create`](https://cli.vuejs.org/guide/creating-a-project.html#vue-create) link for references.

```bash
cd quickstart
npm install

```

## Adding Syncfusion packages

All the available Syncfusion Vue packages are published in the [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
Choose the component to be installed. In this application, the calendar component is installed.

To install the calendar component, use the following command.

```bash
npm install @syncfusion/ej2-vue-calendars --save
```

## Registering Vue component

The two ways to register the Vue component are:
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the component plugin from the EJ2 Vue package and register it using Vue.use() with component plugin as its argument.

Refer to the following code snippet.

```typescript
import { CalendarPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(CalendarPlugin);
```

Note : By registering the component plugin in Vue, all child directives can also be globally registered.

### Using Vue.component()

Import the component and component plugin from EJ2 Vue package and register it using the Vue.component() with name of component from component plugin and the EJ2 Vue component as its arguments.

Refer to the following the code snippet.

```typescript
import { CalendarComponent, CalendarPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.component(CalendarComponent, CalendarPlugin);
```

Note: By using the Vue.component(), only the EJ2 Vue component can be registered. The child directives should be registered separately.

## Creating Vue sample

Add the EJ2 Vue calendar to the `<template>` section of the `App.vue` file or inside components in src directory using `<ejs-calendar>`. The content attribute of the calendar component is provided as name in the data option of the `<script>` section.

```html
<template>
    <div id="app">
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <ejs-calendar ></ejs-calendar>
  </div>
</template>
<script>
import Vue from 'vue';
import { CalendarPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(CalendarPlugin);
export default {
  name: 'app',
  data () {
    return {
      msg: 'Hi EJ2 Components for Vue',
      name: 'Calendar'
    }
  }
}
</script>
```

## Adding CSS reference

Add the styles of calendar component to the `<style>` section of the `App.vue` file as follows.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
</style>
```

## Running the application

Now, run the `npm run serve` command in the console to build your application and open it in the browser.

{% tab template="common/cli3", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <ejs-calendar ></ejs-calendar>
  </div>
</template>
<script>
import Vue from 'vue';
import { CalendarPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(CalendarPlugin);
export default {
  name: 'app',
  data () {
    return {
      msg: 'Hi EJ2 Components for Vue',
      name: 'Calendar'
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
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