# Getting Started with Vue 3

Vue CLI 3 is a complete rewrite of the previous version of the Vue command line interface tool and it comes with a set of new features that make Vue development and the management of Vue projects much easier.

## Prerequisites

To get started with Syncfusion Vue UI Components, ensure the compatible versions of Vue and Typescript.

* `vue` : 3+
* `Typescript` : 2.6+
* `node` : 10.15+
* `vue-class-component` : 8.0.0-rc.1

# Getting Started with Syncfusion Vue UI Components and Vue CLI

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your Vue applications.
At first, it is mostly recommended to uninstall the old Vue CLI package from your system. 

```bash
npm uninstall vue-cli -g
```
Then, install Vue CLI 3 using the following commands.

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

Then, you will be prompted with the option to pick a default preset or to manually select features. Using the arrow keys, we can highlight our selection. Now, you can select the `default`, then hit enter. If you wish to select manually, please use this [`vue-create`](https://cli.vuejs.org/guide/creating-a-project.html#vue-create) link for references. 

```bash
cd quickstart
npm install

```

## Adding Syncfusion packages

All the available Syncfusion Vue packages are published in the [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
Choose the component to be installed. In this application, the grid component is installed.

To install the grid component, use the following command.

```bash
npm install @syncfusion/ej2-vue-grids --save
```

## Registering Vue component

To register the Vue component, we must also register the component's directive.

Import the component from the EJ2 Vue package and register it under the components property.

Refer to the following code snippet.

```typescript
import { GridComponent, ColumnsDirective, ColumnDirective } from '@syncfusion/ej2-vue-grids';

export default {
  name: "App",
  components: {
    'ejs-grid' : GridComponent,
    'e-columns' : ColumnsDirective,
    'e-column' : ColumnDirective
  }
}
```

Note: In Vue 3, the child directives should be registered separately.

## Creating Vue sample

Add the EJ2 Vue Grid to the `<template>` section of the `App.vue` file or inside the components in the `src` directory using `<ejs-grids>`. The dataSource attribute of the grid component is provided as `data` in the data option of the `<script>` section.

```html
<template>
    <ejs-grid :dataSource='data'>
        <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' :isPrimaryKey='true' width=100></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='ShipCountry' headerText='Ship Country' width=150></e-column>
        </e-columns>
    </ejs-grid>
</template>
<script>
import { GridComponent, ColumnsDirective, ColumnDirective } from "@syncfusion/ej2-vue-grids";

export default {
  name: "Vue3-App",
  // Declaring component and its directives
  components: {
    "ejs-grid": GridComponent,
    "e-columns": ColumnsDirective,
    "e-column": ColumnDirective,
  },
  data() {
    return {
      data:  [
        {
           "OrderID":10248,
           "CustomerID":"VINET",
           "ShipCountry":"France"
        },
        {
           "OrderID":10249,
           "CustomerID":"TOMSP",
           "ShipCountry":"Germany"
        }]
    };
  },
  // module injection
  provide: {
    grid: [Edit, Toolbar],
  },
};
</script>
```

## Adding CSS reference

Add the styles of grid component to the `<style>` section of the `App.vue` file as follows.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-grids/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

## Running the application

Now, run the `npm run serve` command in the console to build your application and open it in the browser.

Note: In Vue3, we need to install `"vue-class-component@8.0.0-rc.1` and the node version must be 10+.

## Template Usage:
 
In Vue3 templates, the component name must be the same as the name used for property binding. For example, in the following sample the Grid column `template` property is assigned with the name `colTemplate` which should be the template component's name.

```html
<template>
  <ejs-grid ref='grid' :dataSource="data" height=310 >
    <e-columns>
      <e-column headerText='Employee Image' width='150' textAlign='Center' :template='colTemplate'></e-column>
      <e-column field='EmployeeID' width='125' textAlign='Right'></e-column>
    </e-columns>
  </ejs-grid>
<template>

<script>
import {
  GridComponent,
  ColumnsDirective,
  ColumnDirective,
  Edit,
  Toolbar,
} from "@syncfusion/ej2-vue-grids";

import { createApp } from "vue";

const app = createApp();

// Template declaration
var colVue = app.component('colTemplate', {
  data: () => ({}),
  template:`<span>value:{{data.EmployeeID}}</span>`});

export default {
  data() {
    return {
      data: employeeData,
      colTemplate: function() {
        return { template: colVue };
      }
    };
  }
};

</script>
```

## Component inside template property

For Rendering other EJ2 Components inside the template property, you need to register the EJ2 components tag inside the template as below:

In the following sample, we are using the EJ2 button component inside the grid component's template property.

```html
<template>
  <ejs-grid ref='grid' :dataSource="data" height=310 >
    <e-columns>
      <e-column headerText='Employee Image' width='150' textAlign='Center' :template='colTemplate'></e-column>
      <e-column field='EmployeeID' width='125' textAlign='Right'></e-column>
    </e-columns>
  </ejs-grid>
<template>

<script>
import { ButtonComponent } from "@syncfusion/ej2-vue-buttons";
import {
  GridComponent,
  ColumnsDirective,
  ColumnDirective,
  Edit,
  Toolbar,
} from "@syncfusion/ej2-vue-grids";

import { createApp } from "vue";

const app = createApp();

// Template declaration
var colVue = app.component('colTemplate', {
  data: () => ({}),
  template: `
  <span>value:{{data.EmployeeID}}</span>
  <ejs-Button cssClass="e-primary">Button</ejs-Button>`
  },
  // Declaring component which is used inside template property
  components: {
    "ejs-Button" : ButtonComponent
  });

export default {
  name: 'Vue3-App',
  components: {
    "ejs-grid": GridComponent,
    "e-columns": ColumnsDirective,
    "e-column": ColumnDirective,
  },
  data() {
    return {
      data: employeeData,
      colTemplate: function() {
        return { template: colVue };
      }
    };
  }
};

</script>
```

## Two-way binding

In Vue3, the default v-model property is renamed to modelValue instead of the old name of value.

The default v-model event is renamed to update:modelValue instead of the old name of input.

Please refer to the following syntax to use two-way binding in vue3.

```html
<CustomComponent v-model:probName="name" />
```
