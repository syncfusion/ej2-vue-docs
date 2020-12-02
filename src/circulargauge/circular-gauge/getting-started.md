---
title: "Getting Started"
component: "CircularGauge"
description: "Getting started in circular gauge component"
---

# Getting Started

This section explains you the steps required to create a simple circular gauge and demonstrate the basic usage of the circular gauge control.

## Dependencies

Below is the list of minimum dependencies required to use the circular gauge.

```javascript
|-- @syncfusion/ej2-vue-circulargauge
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-popups
       |-- @syncfusion/ej2-splitbuttons
       |-- @syncfusion/ej2-vue-base
    |-- @syncfusion/ej2-svg-base
    |-- @syncfusion/ej2-circulargauge
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
You can choose the component that you want to install. For this application, we are going to use Circulargauge component.

To install Circulargauge component, use the following command

```bash
npm install @syncfusion/ej2-vue-circulargauge –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { CircularGaugePlugin } from '@syncfuion/ej2-vue-circulargauge';

Vue.use(CircularGaugePlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with name of Component from ComponentPlugin
and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { CircularGaugeComponent, CircularGaugePlugin } from '@syncfusion/ej2-vue-circulargauge';

Vue.component(CircularGaugePlugin.name, CircularGaugeComponent);
```

Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Run the application

Now use the `npm run dev` command to run the application in the browser.

```cmd
npm run dev
```

The below example shows a basic circular gauge component.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
         <ejs-circulargauge ></ejs-circulargauge>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from '@syncfusion/ej2-vue-circulargauge';

Vue.use(CircularGaugePlugin);
export default {}
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Set Pointer Value

You can change the pointer value in the above sample using [`value`](../api/circular-gauge/pointer/#value-number) property in [`pointers`](../api/circular-gauge/tooltipSettings/).

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
         <ejs-circulargauge >
          <e-axes>
            <e-axis>
              <e-pointers>
                <e-pointer :value='val'/>
              </e-pointers>
            </e-axis>
          </e-axes>
         </ejs-circulargauge>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from '@syncfusion/ej2-vue-circulargauge';

Vue.use(CircularGaugePlugin);
export default {
   data () {
    return {
      val : 35
    }
  }
}
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}
