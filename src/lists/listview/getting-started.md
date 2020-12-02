---
title: "ListView Getting Started"
component: "ListView"
description: "Getting started with ListView component."
---

# Getting Started

The following section explains the required steps to build the simple ListView component with its basic usage in step-by-step procedure.

## Installation and configuration

* You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications. To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
```

* To setup basic  sample use the following Vue CLI commands.

```bash
vue create quickstart
```

* Install Syncfusion `ListView` packages using below command.

```bash
npm install @syncfusion/ej2-vue-lists --save
```

## Registering ListView component using `Vue.use()`

Import the ListView Plugin from the Essential JS 2 Vue package and register the same using `Vue.use()` with Component Plugin as its argument.

Refer to the code snippet given below.

```typescript
import { ListViewPlugin } from '@syncfusion/ej2-vue-lists';

Vue.use(ListViewPlugin);
```

> By registering component plugin in Vue, all child directives are also globally registered.
We can also use `Vue.Component()` to register `ListView`.
Refer [here](../../getting-started/vue-sass/#registering-vue-component) to know more about component registration.

## Initialize ListView

Add the EJ2 Vue ListView using `<ejs-listview>` to the `<template>` section of the `App.vue` file in `src` directory.

```html
<template>
    <div id="app">
    <img src="./assets/logo.png">
    <ejs-listview id='flat-list'></ejs-listview>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListViewPlugin } from '@syncfusion/ej2-vue-lists';

Vue.use(ListViewPlugin);

export default {
  name: 'app'
}
</script>
```

## Bind data source

Populate the data in ListView by using the `dataSource` property.
Here, an array of JSON values are passed to the ListView component as `dataSource` in data option inside the `<script>` section.

```html
<template>
    <div id="app">
    <img src="./assets/logo.png">
    <ejs-listview id='flat-list' :dataSource='dataSource'></ejs-listview>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListViewPlugin } from '@syncfusion/ej2-vue-lists';

Vue.use(ListViewPlugin);

export default {
  name: 'app',
   data () {
    return {
       dataSource : [
        { text: 'Hennessey Venom', id: 'list-01' },
        { text: 'Bugatti Chiron', id: 'list-02' },
        { text: 'Bugatti Veyron Super Sport', id: 'list-03' },
        { text: 'SSC Ultimate Aero', id: 'list-04' },
        { text: 'Koenigsegg CCR', id: 'list-05' },
        { text: 'McLaren F1', id: 'list-06' },
        { text: 'Aston Martin One- 77', id: 'list-07' },
        { text: 'Jaguar XJ220', id: 'list-08' },
        { text: 'McLaren P1', id: 'list-09' },
        { text: 'Ferrari LaFerrari', id: 'list-10' },
      ]
    }
  }
}
</script>
```

## Adding CSS Reference

Add ListView component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-lists/styles/material.css";
</style>
```

## Run the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

The following example shows a basic ListView.

{% tab template="listview/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-listview id='flat-list' :dataSource='dataSource' width="330px"></ejs-listview>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListViewPlugin } from '@syncfusion/ej2-vue-lists';

Vue.use(ListViewPlugin);
export default {
  name: 'app',
   data () {
    return {
       dataSource : [
        { text: 'Hennessey Venom', id: 'list-01' },
        { text: 'Bugatti Chiron', id: 'list-02' },
        { text: 'Bugatti Veyron Super Sport', id: 'list-03' },
        { text: 'SSC Ultimate Aero', id: 'list-04' },
        { text: 'Koenigsegg CCR', id: 'list-05' },
        { text: 'McLaren F1', id: 'list-06' },
        { text: 'Aston Martin One- 77', id: 'list-07' },
        { text: 'Jaguar XJ220', id: 'list-08' },
        { text: 'McLaren P1', id: 'list-09' },
        { text: 'Ferrari LaFerrari', id: 'list-10' },
      ]
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-lists/styles/material.css";
  #flat-list {
        border: 1px solid #dddddd;
        border-radius: 3px;
    }
  #app {
    color: #008cff;
    height: 40px;
    left: 30%;
    position: absolute;
  }
</style>
```

{% endtab %}

## See Also

[Data Binding Types](./data-binding)

[ListView customization](./customizing-templates)

[Virtualization](./virtualization)
