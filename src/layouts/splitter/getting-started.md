---
title: "Getting Started"
component: "Splitter"
description: "Explains to get started with Splitter component with its key features such as resizable,validation and nested Splitter, etc."
---

# Getting Started

The following section explains the required steps to build the Splitter component with step-by-step procedure.

## Dependencies

The following list of dependencies required to use the Splitter component in your application:

```js
|-- @syncfusion/ej2-layouts
    |-- @syncfusion/ej2-base
|-- @syncfusion/ej2-vue-layouts
    |-- @syncfusion/ej2-vue-base

```

## Get Started with Vue CLI

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
You can choose the component that you want to install. For this application, we are going to use Splitter component.

To install Splitter component, use the following command

```bash
npm install @syncfusion/ej2-vue-layouts –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { SplitterComponent } from '@syncfusion/ej2-vue-layouts';

Vue.use(SplitterComponent);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Splitter Component from EJ2 Vue Package, register the same using the Vue.component() with name of Component from Component Plugin and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { SplitterComponent } from '@syncfusion/ej2-vue-layouts';

Vue.component(SplitterComponent);
```

Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the HTML div element into the `<template>` section of the `App.vue` file in src directory,
the content attribute of the Splitter component is provided as name in data option in the `<script>` section.

```html
<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='default-splitter' height='250px'>
        <e-panes>
            <e-pane></e-pane>
            <e-pane></e-pane>
        </e-panes>
    </ejs-splitter>
</div>
</template>
<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';

Vue.use(SplitterPlugin);

export default {
  name: 'app',
    data () {
    return { }
  }
}
</script>
```

## Adding CSS Reference

Add Splitter component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css';
</style>
```

## Load content to the pane

You can load the pane contents in either HTML element or string types using [content](../api/splitter/#content) property.

For detailed information, refer to the [Pane Content](./pane-content/) section

```html
<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='default-splitter' height='250px'>
        <e-panes>
            <e-pane content='Left Pane'></e-pane>
            <e-pane content='Middle Pane'></e-pane>
            <e-pane content='Right Pane'></e-pane>
        </e-panes>
    </ejs-splitter>
</div>
</template>
<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';

Vue.use(SplitterPlugin);

export default {
  name: 'app',
    data () {
    return { }
  }
}
</script>
```

## Running the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="splitter/getting-started" %}

```html
<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='default-splitter' height='250px'>
        <e-panes>
            <e-pane content='Left Pane'></e-pane>
            <e-pane content='Middle Pane'></e-pane>
            <e-pane content='Right Pane'></e-pane>
        </e-panes>
    </ejs-splitter>
</div>
</template>
<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';

Vue.use(SplitterPlugin);

export default {
  name: 'app',
    data () {
    return { }
  }
}
</script>

<style>
@import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css';

#app {
    margin: 60px auto;
    max-width: 700px;
}
.e-splitter {
    margin: 0 auto;
}
.e-pane {
  text-align: center;
  align-items: center;
  display: grid;
}
</style>
```

{% endtab %}

## See Also

* [Resizable split panes](./resizing/)
* [Collapsible panes](./expand-collapse/)
* [Construct different layouts using Splitter](./different-layouts/)