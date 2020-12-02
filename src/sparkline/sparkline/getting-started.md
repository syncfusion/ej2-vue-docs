---
title: "Getting Started"
component: "Sparkline"
description: "Getting started in sparkline component"
---

# Getting Started

This section explains you the steps required to create a sparkline and demonstrate its basic usage.

## Dependencies

The following list of minimum dependencies are required to use the sparkline:

```js
|-- @syncfusion/ej2-vue-charts
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-pdf-export
    |-- @syncfusion/ej2-file-utils
    |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-svg-base
    |-- @syncfusion/ej2-sparkline
    |-- @syncfusion/ej2-vue-base
```

## Installation and configuration

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications. To install Vue CLI use the following command.

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

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry. You can choose the component that you want to install. For this application, we are going to use Sparkline component.

To install Sparkline component, use the following command

```bash
npm install @syncfusion/ej2-vue-charts –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.

* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { SparklinePlugin } from '@syncfuion/ej2-vue-charts';

Vue.use(SparklinePlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package, register the same using the Vue.component() with name of Component from ComponentPlugin and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { SparklineComponent, SparklinePlugin } from '@syncfusion/ej2-vue-charts';

Vue.component(SparklinePlugin.name, SparklineComponent);
```

Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Initialize Sparkline component

Add the EJ2 Vue Sparkline using `<ejs-sparkline>` to the `<template>` section of the `App.vue` file in src directory, the content attribute of the Sparkline component is provided as name in data option in the `<script>` section.

```html
<template>
    <div id="app">
    <ejs-sparkline></ejs-sparkline>
  </div>
</template>
<script>
import Vue from 'vue';
import { SparklinePlugin } from '@syncfusion/ej2-vue-charts';

Vue.use(SparklinePlugin);
export default Vue.extend ({});
</script>
```

## Run the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

The following example shows a basic Sparkline.

```html
<template>
<ejs-sparkline id="sparkline"></ejs-sparkline>
</template>

<script>
import Vue from 'vue';
import { SparklinePlugin } from '@syncfusion/ej2-vue-charts';

Vue.use(SparklinePlugin);

export default Vue.extend ({});
</script>
```

Since the data source has not been specified to the sparkline, no shape will be rendered. Only an empty SVG element is appended to the sparkline container.

## Module Injection

The sparkline component is segregated into individual feature-wise modules. To use a particular feature, inject its feature module using the `provide` option on component creation. The module available in sparkline and its descriptions is as follows.

* SparklineTooltip - Inject this provider to use tooltip series.

In the current application, the above basic sparkline is modified to visualize the types of sparkline.

In this application, tooltip feature of the sparkline is used. Now, import the SparklineTooltip module from the sparkline package, and inject it into the sparkline control using the `provide` option.

```html
<template>
    <div class="control_wrapper">
        <ejs-sparkline id="sparkline"></ejs-sparkline>
    </div>
</template>
<script>
import Vue from 'vue';
import { SparklinePlugin,SparklineTooltip } from "@syncfusion/ej2-vue-charts";
Vue.use(SparklinePlugin);

export default {
  data: function() {
    return {
    }
  },
provide:{
    sparkline:[SparklineTooltip]
}
}
</script>
```

## Bind data source to Sparkline

The [`dataSource`] property is used for binding data source to the sparkline. This property takes the collection value as input. For example, the list of objects can be provided as input.

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div>
        <ejs-sparkline id="sparkline" align="center" :dataSource='dataSource' xName='xval' yName='yval' :height='height' :width='width'></ejs-sparkline>
    </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { SparklinePlugin } from "@syncfusion/ej2-vue-charts";
Vue.use(SparklinePlugin);

export default {
  data: function() {
    return {
    height: '100px',
    width: '70%',
    dataSource: [
            { x: 0, xval: '2005', yval: 20090440 },
            { x: 1, xval: '2006', yval: 20264080 },
            { x: 2, xval: '2007', yval: 20434180 },
            { x: 3, xval: '2008', yval: 21007310 },
            { x: 4, xval: '2009', yval: 21262640 },
            { x: 5, xval: '2010', yval: 21515750 },
            { x: 6, xval: '2011', yval: 21766710 },
            { x: 7, xval: '2012', yval: 22015580 },
            { x: 8, xval: '2013', yval: 22262500 },
            { x: 9, xval: '2014', yval: 22507620 },
        ]
    }
  }
}
</script>
<style>
.spark {
    border: 1px solid rgb(209, 209, 209);
    border-radius: 2px;
    width: 100%;
    height: 100%;
}
</style>
```

{% endtab %}

## Change the type of Sparkline

You can change the sparkline type by setting the [`type`] property to [`Line`], [`Column`], [`WinLoss`], [`Pie`], or [`Area`]. Here, the sparkline type has been set to [`area`].

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div>
        <ejs-sparkline id="sparkline" align="center" :dataSource='dataSource' xName='xval' yName='yval' :type='type' :height='height' :width='width'></ejs-sparkline>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { SparklinePlugin } from "@syncfusion/ej2-vue-charts";
Vue.use(SparklinePlugin);

export default {
  data: function() {
    return {
    height: '100px',
    width: '70%',
    dataSource: [
            { x: 0, xval: '2005', yval: 20090440 },
            { x: 1, xval: '2006', yval: 20264080 },
            { x: 2, xval: '2007', yval: 20434180 },
            { x: 3, xval: '2008', yval: 21007310 },
            { x: 4, xval: '2009', yval: 21262640 },
            { x: 5, xval: '2010', yval: 21515750 },
            { x: 6, xval: '2011', yval: 21766710 },
            { x: 7, xval: '2012', yval: 22015580 },
            { x: 8, xval: '2013', yval: 22262500 },
            { x: 9, xval: '2014', yval: 22507620 },
        ],
    // Assign the 'area' as type of Sparkline
    type:'Area'
    }
  }
}
</script>
<style>
.spark {
    border: 1px solid rgb(209, 209, 209);
    border-radius: 2px;
    width: 100%;
    height: 100%;
}
</style>
```

{% endtab %}

## Enable tooltip for Sparkline

The sparkline displays additional information through tooltip when the mouse is hovered over the sparkline. You can enable tooltip by setting the [`visible`] property to true in [`tooltipSettings`] and injecting `SparklineTooltip` module using the `provide` option.

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div>
        <ejs-sparkline id="sparkline" align="center" :dataSource='dataSource' xName='xval' yName='yval' :type='type' :tooltipSettings='tooltipSettings' :height='height' :width='width'></ejs-sparkline>
    </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { SparklinePlugin,SparklineTooltip } from "@syncfusion/ej2-vue-charts";
Vue.use(SparklinePlugin);

export default {
  data: function() {
    return {
    height: '100px',
    width: '70%',
    dataSource: [
            { x: 0, xval: '2005', yval: 20090440 },
            { x: 1, xval: '2006', yval: 20264080 },
            { x: 2, xval: '2007', yval: 20434180 },
            { x: 3, xval: '2008', yval: 21007310 },
            { x: 4, xval: '2009', yval: 21262640 },
            { x: 5, xval: '2010', yval: 21515750 },
            { x: 6, xval: '2011', yval: 21766710 },
            { x: 7, xval: '2012', yval: 22015580 },
            { x: 8, xval: '2013', yval: 22262500 },
            { x: 9, xval: '2014', yval: 22507620 },
        ],
    // Assign the 'area' as type of Sparkline
    type:'Area',
     // To enable the tooltip for Sparkline
    tooltipSettings: {
        visible: true,
        format: '${xval} : ${yval}'
    }
    }
  },
provide:{
    sparkline:[SparklineTooltip]
}
}
</script>
<style>
.spark {
    border: 1px solid rgb(209, 209, 209);
    border-radius: 2px;
    width: 100%;
    height: 100%;
}
</style>
```

{% endtab %}
