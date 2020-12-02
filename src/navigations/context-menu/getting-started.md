# Getting Started

This section explains how to create a simple ContextMenu, and configure its available
functionalities in Vue using Vue quickstart seed repository.

## Dependencies

The following list of dependencies are required to use the ContextMenu component in your application.

```js
|-- @syncfusion/ej2-vue-navigations
    |-- @syncfusion/ej2-vue-base
    |-- @syncfusion/ej2-navigations
        |-- @syncfusion/ej2-base
        |-- @syncfusion/ej2-data
        |-- @syncfusion/ej2-lists
        |-- @syncfusion/ej2-inputs
        |-- @syncfusion/ej2-popups
            |-- @syncfusion/ej2-buttons
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

Install Syncfusion `ContextMenu` packages using below command.

```bash
npm install @syncfusion/ej2-vue-navigations --save
```

## Registering ContextMenu component using `Vue.use()`

Import the ContextMenu Plugin from the Essential JS 2 Vue package and register the same using `Vue.use()` with Component Plugin as its argument.

Refer to the code snippet given below.

```javascript
import Vue from 'vue';
import { ContextMenuPlugin } from "@syncfusion/ej2-vue-navigations";

Vue.use(ContextMenuPlugin);

export default {}
```

> By registering component plugin in Vue, all child directives are also globally registered.
We can also use `Vue.Component()` to register `ContextMenu`.
Refer [here](https://ej2.syncfusion.com/vue/documentation/base/getting-started/#registering-vue-component) to know more about component registration.

## Initialize ContextMenu

Add the EJ2 Vue ContextMenu using `<ejs-contextmenu>` to the `<template>` section of the `App.vue` file in `src` directory.

```html
<template>
<div>
<div id="target">Right click / Touch hold to open the ContextMenu</div>
<ejs-contextmenu target='#target' :items='menuItems'></ejs-contextmenu>
</div>
</template>

<script>
import Vue from 'vue';
import { ContextMenuPlugin } from "@syncfusion/ej2-vue-navigations";

Vue.use(ContextMenuPlugin);

export default {
    data () {
        return {
            menuItems:[
            {
                text: 'Cut'
            },
            {
                text: 'Copy'
            },
            {
                text: 'Paste'
            }]
        };
    }
}
</script>
```

## Adding CSS Reference

Add ContextMenu component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";

/* Context Menu target */
#target {
    border: 1px dashed;
    height: 150px;
    padding: 10px;
    position: relative;
    text-align: justify;
    color: gray;
    user-select: none;
}
</style>
```

## Run the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

The following example shows a basic ContextMenu component.

{% tab template="context-menu/default", isDefaultActive=true %}

```html
<template>
<div>
<div id="target">Right click / Touch hold to open the ContextMenu</div>
<ejs-contextmenu target='#target' :items='menuItems'></ejs-contextmenu>
</div>
</template>

<script>
import Vue from 'vue';
import { ContextMenuPlugin } from "@syncfusion/ej2-vue-navigations";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ContextMenuPlugin);

export default {
    data () {
        return {
            menuItems:[
            {
                text: 'Cut'
            },
            {
                text: 'Copy'
            },
            {
                text: 'Paste'
            }]
        };
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";

#target {
    border: 1px dashed;
    height: 150px;
    padding: 10px;
    position: relative;
    text-align: justify;
    color: gray;
    user-select: none;
}
</style>
```

{% endtab %}

## Rendering items with Separator

The Separators are the horizontal lines that are used to separate the menu items. You cannot select the separators. You
can enable separators to group the menu items using the [`separator`](../api/context-menu/menuItemModel#separator) property.
Cut, Copy, and Paste menu items are grouped using the `separator` property in the following sample.

{% tab template="context-menu/default" %}

```html
<template>
<div>
<div id="target">Right click / Touch hold to open the ContextMenu</div>
<ejs-contextmenu target='#target' :items='menuItems'></ejs-contextmenu>
</div>
</template>

<script>
import Vue from 'vue';
import { ContextMenuPlugin } from "@syncfusion/ej2-vue-navigations";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ContextMenuPlugin);

export default {
    data () {
        return {
            menuItems:[
            {
                text: 'Cut'
            },
            {
                text: 'Copy'
            },
            {
                text: 'Paste'
            },
            {
                separator: true
            },
            {
                text: 'Font'
            },
            {
                text: 'Paragraph'
            }]
        };
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";

#target {
  border: 1px dashed;
  height: 150px;
  padding: 10px;
  position: relative;
  text-align: justify;
  color: gray;
  user-select: none;
}
</style>
```

{% endtab %}

> The [`separator`](../api/context-menu/menuItemModel#separator) property `should not` be given along with
the other fields in the [`MenuItem`](../api/context-menu/menuItemModel).

## See Also

* [ContextMenu with icons](./icons-and-navigation#icons)
* [Multi-level nesting](./template-and-multilevel-nesting#multilevel-nesting)