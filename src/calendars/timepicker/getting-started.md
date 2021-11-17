---
title: "Getting Started"
component: "TimePicker"
description: "This getting started section briefly explains how to create a time picker component in an application."
---

# Getting Started

This section explains how to create a simple TimePicker and how to configure the TimePicker component.

## Dependencies

The list of dependencies required to use the Vue TimePicker component in your application is given below:

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
You can choose the component that you want to install. For this application, we are going to use TimePicker component.

To install TimePicker component, use the following command

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
import { TimePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(TimePickerPlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with name of Component from ComponentPlugin
and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { TimePickerComponent, TimPickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.component(TimPickerPlugin.name, TimePickerComponent);
```

> By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the EJ2 Vue TimePicker using `<ejs-timepicker>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the TimePicker component is provided as name in data option in the `<script>` section.

```html
<template>
    <div id="app">
    <ejs-timepicker :placeholder="waterMark" ></ejs-timepicker>
  </div>
</template>
<script>
import Vue from 'vue';
import { TimePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(TimePickerPlugin);
export default {
   data () {
    return {
      waterMark : 'Select a time'
    }
  }
}
</script>
```

## Adding CSS Reference

To render the Vue TimePicker component, need to import TimePicker and its dependent component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
</style>
```

>Note: If you want to refer the combined component styles, please make use of our [`CRG`](https://crg.syncfusion.com/) (Custom Resource Generator) in your application.

## Running the Application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="timepicker/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-timepicker :placeholder="waterMark"></ejs-timepicker>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { TimePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(TimePickerPlugin);
export default {
  data () {
    return {
      waterMark : 'Select a time'
    }
  }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
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

## Setting the value, min, and max time

The following example demonstrates how to set the value, min, and max time on initializing
 the TimePicker. The Vue TimePicker allows you to select the time value within a range from `7:00 AM` to `4:00 PM`.

{% tab template="timepicker/min-max", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
       <ejs-timepicker :min="minDate" :max="maxDate" :value="timeVal"></ejs-timepicker>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { TimePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(TimePickerPlugin);
export default {
  data () {
        return {
           minDate : new Date("05/07/2017 7:00 AM"),
           maxDate : new Date("05/07/2017 4:00 PM"),
           timeVal : new Date("05/27/2017 1:00 PM")
        }
    }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
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

## Setting the time format

Time formats is a way of representing the time value in different string format in textbox and popup
list. By default, the TimePicker's format is based on the culture. You can also customize the format by using the
[`format`](../api/timepicker#format)
property. To know more about the time format standards, refer to the
[Date and Time Format](../common/internationalization#custom-formats) section.

The following example demonstrates the TimePicker component in 24 hours format with 60 minutes
interval. The time interval is set to
60 minutes by using the [`step`](../api/timepicker#step-number) property.

{% tab template="timepicker/format", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <div class='wrapper'>
    <ejs-timepicker :step="timeStep" :format="timeFormat" :value="timeVal"></ejs-timepicker>
  </div>
</template>
<script>
import Vue from 'vue';
import { TimePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(TimePickerPlugin);
export default {
  data () {
        return {
           timeStep : 60,
           timeFormat : 'HH:mm',
           timeVal : new Date()
        }
    }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
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

> Once the time format property is defined, it will be applicable to all the cultures.

## See Also

* [Render TimePicker with min and max time](./time-range)
* [How to achieve validation with TimePicker](./how-to/client-side-validation-using-form-validator)
* [Render TimePicker with specific culture](./globalization)