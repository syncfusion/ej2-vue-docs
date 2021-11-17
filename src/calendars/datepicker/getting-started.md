---
title: "Getting Started"
component: "DatePicker"
description: "This getting started section briefly explains how to create a date picker component in an application."
---

# Getting Started

This section explains how to create a simple DatePicker and how to configure the DatePicker component.

## Dependencies

The list of dependencies required to use the DatePicker component in your application is given below:

```javascript
|-- @syncfusion/ej2-vue-calendars
  |-- @syncfusion/ej2-base
  |-- @syncfusion/ej2-data
  |-- @syncfusion/ej2-vue-base
  |-- @syncfusion/ej2-calendars
    |-- @syncfusion/ej2-inputs
       |-- @syncfusion/ej2-splitbuttons
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-popups
        |-- @syncfusion/ej2-buttons
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
You can choose the component that you want to install. For this application, we are going to use DatePicker component.

To install DatePicker component, use the following command

```bash
npm install @syncfusion/ej2-vue-calendars --save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { DatePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(DatePickerPlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with name of Component from ComponentPlugin
and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { DatePickerComponent, DatePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.component(DatePickerPlugin.name, DatePickerComponent);
```

> By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the EJ2 Vue DatePicker using `<ejs-datepicker>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the DatePicker component is provided as name in data option in the `<script>` section.

```html
<template>
    <div id="app">
    <ejs-datepicker :placeholder="waterMark" ></ejs-datepicker>
  </div>
</template>
<script>
import Vue from 'vue';
import { DatePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(DatePickerPlugin);
export default {
   data () {
    return {
      waterMark : 'Select a date'
    }
  }
}
</script>
```

## Adding CSS Reference

To render the DatePicker component, need to import DatePicker and its dependent component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
</style>
```

>Note: If you want to refer the combined component styles, please make use of our [`CRG`](https://crg.syncfusion.com/) (Custom Resource Generator) in your application.

## Running the Application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="datepicker/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-datepicker :placeholder="waterMark"></ejs-datepicker>
      </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DatePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(DatePickerPlugin);
export default {
data () {
    return {
      waterMark : 'Select a date'
    }
  }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  .wrapper {
    max-width: 250px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Setting the value, min and max dates

The following example demonstrates how to set the value, min and max dates on initializing the
DatePicker. Here you can able to select a date within a range from 9th to 15th in a month of May 2017. To know more about range restriction in DatePicker, please refer this [page](./date-range).

{% tab template="datepicker/min-max", isDefaultActive=true %}

```html
<template>
  <div id="app">
   <div class='wrapper'>
    <ejs-datepicker :min="minDate" :max="maxDate" :value="dateVal" ></ejs-datepicker>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DatePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(DatePickerPlugin);
export default {
  data () {
    return {
       minDate : new Date("05/09/2017"),
       maxDate : new Date("05/15/2017"),
       dateVal : new Date("05/11/2017")
    }
  }
}
</script>
<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  .wrapper {
    max-width: 250px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

N> You can refer to our [Vue DatePicker](https://www.syncfusion.com/vue-ui-components/vue-datepicker) feature tour page for its groundbreaking feature representations. You can also explore our [Vue DatePicker example](https://ej2.syncfusion.com/vue/demos/#/material/datepicker/default.html) to know how to render and configure the datepicker.

## See Also

* [Change the format of selected date](./date-format)
* [Render DatePicker with specific culture](./globalization)
* [How to achieve validation with DatePicker](./how-to/client-side-validation)
