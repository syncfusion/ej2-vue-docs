---
title: "Getting Started"
component: "Calendar"
description: "This getting started section briefly explains how to create a calendar component in an application."
---

# Getting Started

This section explains how to create a simple Calendar and how to configure the Calendar component.

## Dependencies

The list of dependencies required to use the Calendar component in your application is given below:

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

Start a new project using the below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install

```

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.
You can choose the component that you want to install. For this application, we are going to use the Calendar component.

To install Calendar component, use the following command

```bash
npm install @syncfusion/ej2-vue-calendars --save
```

## Registering Vue Component

Two ways are available for registering the Vue Component. They are as follows.

* Vue.use()

* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { CalendarPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(CalendarPlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with the name of Component from ComponentPlugin
and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { CalendarComponent, CalendarPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.component(CalendarPlugin.name, CalendarComponent);
```

> By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the EJ2 Vue Calendar using `<ejs-calendar>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the Calendar component is provided as name in data option in the `<script>` section.

```html
<template>
    <div id="app">
    <ejs-calendar ></ejs-calendar>
  </div>
</template>
<script>
import Vue from 'vue';
import { CalendarPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(CalendarPlugin);
export default { }
</script>
```

## Adding CSS Reference

To render the Calendar component, need to import Calendar and its dependent component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
</style>
```

>Note: If you want to refer the combined component styles, please make use of our [`CRG`](https://crg.syncfusion.com/) (Custom Resource Generator) in your application.

## Running the Application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="calendar/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
         <ejs-calendar ></ejs-calendar>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { CalendarPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(CalendarPlugin);
export default {}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  .wrapper {
    max-width: 250px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Setting the value, min and max dates

The following example demonstrates how to set the value, min and max dates on initializing the Calendar.
Here the Calendar allows you to select a date within the range from 9th to 15th in the month of May 2017. To know more about range restriction in Calendar, please refer this [page](./date-range).

{% tab template="calendar/min-max", isDefaultActive=true %}

```html
<template>
  <div id="app">
   <div class='wrapper'>
    <ejs-calendar :min="minDate" :max="maxDate" :value="dateVal" ></ejs-calendar>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { CalendarPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(CalendarPlugin);
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
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  .wrapper {
    max-width: 250px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## See Also

* [Select multiple dates in the Calendar](./multi-select)
* [Render Calendar with specific culture](./globalization)
* [How to change the initial view of the Calendar](./calendar-views)
* [Render Calendar with week numbers](./how-to/render-the-calendar-with-week-numbers)
* [Show other month dates](./how-to/show-dates-of-other-months)
