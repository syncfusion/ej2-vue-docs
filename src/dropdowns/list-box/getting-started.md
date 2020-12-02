---
title: "list-box Getting started"
component: "ListBox"
description: "This section explains how to create a simple Syncfusion vue list box component and configure it's functionalities in vue."
---

# Getting Started

This section briefly explains how to create a simple **ListBox** component and configure its available
functionalities in Vue.

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
You can choose the component that you want to install. For this application, we are going to use ListBox component.

To install ListBox component, use the following command

```bash
npm install @syncfusion/ej2-vue-dropdowns –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { ListBoxPlugin } from '@syncfusion/ej2-vue-dropdowns';

Vue.use(ListBoxPlugin);
```

Note : By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with name of Component from ComponentPlugin
and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { ListBoxComponent, ListBoxPlugin } from '@syncfusion/ej2-vue-dropdowns';

Vue.component(ListBoxPlugin.name, ListBoxComponent);
```

Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the EJ2 Vue ListBox using `<ejs-listbox>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the ListBox component is provided as name in data option in the `<script>` section.

```html
<template>
    <div class="control_wrapper">
        <ejs-listbox id='listbox'></ejs-listbox>
    </div>
</template>
<script>
import Vue from 'vue';
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ListBoxPlugin);

export default Vue.extend({
  data: function() {
    return {

    };
  }
});

</script>
```

## Adding CSS Reference

Add ComboBox component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>
```

## Binding data source

After initialization, populate the ListBox with data using
the [dataSource](../api/list-box/#datasource) property.
Here, an array of object is passed to the ListBox component.

```html

<template>
    <div class="control_wrapper">
        <ejs-listbox :dataSource='data'></ejs-listbox>
    </div>
</template>
<script>
import Vue from 'vue';
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ListBoxPlugin);

export default Vue.extend({
  data: function() {
    return {
       data: { [key: string]: Object }[] = [
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
];
    };
  }
});

</script>
```

## Run the application

After completing the configuration required to render a basic ListBox, run the following command to
display the output in your default browser.

```cmd
npm run dev
```

{% tab template="list-box/getting-started/getting-started", isDefaultActive=true %}

```html

<template>
  <div id="app">
    <div id='container' style="margin:10px auto 0; width:250px;">
        <ejs-listbox :dataSource='data' ></ejs-listbox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(ListBoxPlugin);
export default {
  data (){
    return {
       data: [
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
];
    }
  }
}

</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>

```

{% endtab %}
