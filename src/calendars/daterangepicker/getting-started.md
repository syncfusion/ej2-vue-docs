---
title: "Getting Started"
component: "DateRangePicker"
description: "This getting started section briefly explains how to create a date range picker component in an application."
---

# Getting Started

This section explains how to create a simple DateRangePicker and how to configure the DateRangePicker component.

## Dependencies

The list of dependencies required to use the DateRangePicker component in your application is given below:

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
You can choose the component that you want to install. For this application, we are going to use DateRangePicker component.

To install DateRangePicker component, use the following command

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
import { DateRangePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(DateRangePickerPlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with name of Component from ComponentPlugin
and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { DateRangePickerComponent, DateRangePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.component(DateRangePickerPlugin.name, DateRangePickerComponent);
```

> By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the EJ2 Vue DateRangePicker using `<ejs-daterangepicker>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the DateRangePicker component is provided as name in data option in the `<script>` section.

```html
<template>
    <div id="app">
    <ejs-daterangepicker :placeholder="waterMark" ></ejs-daterangepicker>
  </div>
</template>
<script>
import Vue from 'vue';
import { DateRangePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(DateRangePickerPlugin);
export default {
  name: 'app',
  data () {
    return {
      waterMark : 'Select a Range'
    }
  }
}
</script>
```

## Adding CSS Reference

To render the DateRangePicker component, need to import DateRangePicker and its dependent component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
</style>
```

>Note: If you want to refer the combined component styles, please make use of our [`CRG`](https://crg.syncfusion.com/) (Custom Resource Generator) in your application.

## Running the Application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="daterangepicker/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
          <ejs-daterangepicker :placeholder="waterMark"></ejs-daterangepicker>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { DateRangePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(DateRangePickerPlugin);
export default {
    data () {
    return {
      waterMark : 'Select a Range'
    }
  }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrapper {
    max-width: 250px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Setting the start date and end date

The start and end date in a range can be defined with the help of startDate and endDate property.
The following example demonstrates to set the start and end date on initializing the
DateRangePicker. To know more about range restriction in DateRangePicker, please refer this [page](./range-restriction).

{% tab template="daterangepicker/min-max", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-daterangepicker :startDate="startVal" :endDate="endVal" :placeholder="waterMark"></ejs-daterangepicker>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { DateRangePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(DateRangePickerPlugin);
export default {
   data () {
        return {
           startVal : new Date("11/12/2019 12:00 PM"),
           endVal : new Date("11/25/2019 5:00 PM"),
           waterMark : 'Select a Range'
        }
    }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrapper {
    max-width: 250px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## See Also

* [Render DateRangePicker with pre-defined ranges](./customization#preset-ranges)
* [Render DateRangePicker with specific culture](./globalization)
