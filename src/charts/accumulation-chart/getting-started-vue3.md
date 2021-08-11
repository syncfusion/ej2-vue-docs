---
title: "Getting Stared with Vue Accumulation Chart | Syncfusion"
component: "Accumulation Chart"
description: "Learn here all about Getting Started with Syncfusion Accumulation Chart in Vue application using Vue CLI."
---

# Getting Started with Syncfusion Accumulation Chart component in Vue 3

This section explains how to use Accumulation Chart component in Vue 3 application.

## Prerequisites

* `vue` : `3+`
* `node` : `10.15+`
* `vue-class-component` : `8.0.0-rc.1`

## Creating Vue application using Vue CLI

The easiest way to create a Vue application is to use the [`Vue CLI`](https://github.com/vuejs/vue-cli). Vue CLI versions above [`4.5.0`](https://v3.vuejs.org/guide/migration/introduction.html#vue-cli) are mandatory for creating applications using Vue 3. Use the following command to uninstall older versions of the Vue CLI.

```bash
npm uninstall vue-cli -g
```

Use the following commands to install the latest version of Vue CLI.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

Create a new project using the command below.

```bash
vue create quickstart

```

Initiating a new project prompts us to choose the type of project to be used for the current application. Select the option `Default (Vue 3 Preview)` from the menu.

![Vue 3 Terminal](./images/vue3-terminal.png)

## Adding Syncfusion Accumulation Chart package in the application

Syncfusion Vue packages are maintained in the [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry. The Accumulation Chart component will be used in this example. To install it in the **quickstart** folder use the following command.

```bash
npm install @syncfusion/ej2-vue-charts --save
```

## Adding Syncfusion Accumulation Chart component in the application

You have completed all the necessary configurations needed for rendering the Syncfusion Vue component. Now, you are going to add the Accumulation Chart component using following steps.

**1.** Import the Accumulation Chart component in the `<script>` section of the `src/App.vue` file.

```html
<script>
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective, AccumulationLegend,
PieSeries, AccumulationTooltip } from "@syncfusion/ej2-vue-charts";
</script>
```

**2.** Register the Accumulation Chart component along with the required child directives which are used in this example. Find the list of child directives and the tag names that can be used in the Accumulation Chart component in the following table.
  
| Directive Name                          | Tag Name                           |
|-----------------------------------------|------------------------------------|
| `AccumulationSeriesCollectionDirective` | `e-accumulation-series-collection` |
| `AccumulationSeriesDirective`           | `e-accumulation-series`            |

```js
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective, AccumulationLegend,
PieSeries, AccumulationTooltip } from "@syncfusion/ej2-vue-charts";
//Component registeration.
export default {
    name: "App",
    components: {
    "ejs-accumulationchart": AccumulationChartComponent,
    "e-accumulation-series-collection": AccumulationSeriesCollectionDirective,
    "e-accumulation-series":  AccumulationSeriesDirective
  },
};

```

In the above code snippet, you have registered Accumulation Chart and the directives for series. Series directives are used to visualize the data with `Pie` series.

**3.** Add the component definition in template section.

```html
<template>
    <ejs-accumulationchart :legendSettings="legendSettings" :tooltip="tooltip">
        <e-accumulation-series-collection>
            <e-accumulation-series :dataSource='data' xName='x' yName='y' innerRadius="20%"> </e-accumulation-series>
        </e-accumulation-series-collection>
    </ejs-accumulationchart>
</template>

```

Above is the Accumulation Chart component with `dataSource` bound to series directives.

**4.** Define the collection `data` which is bound for the `dataSource`, `legendSettings` and `tooltip` properties in the `script` section.

```js
  data() {
    return {
      data: [
        { x: 'Argentina', y: 505370 },
        { x: 'Belgium', y: 551500 },
        { x: 'Cuba', y: 312685 },
        { x: 'Dominican Republic', y: 350000 },
        { x: 'Egypt', y: 301000 },
        { x: 'Kazakhstan', y: 300000 },
        { x: 'Somalia', y: 357022 }
     ],
     legendSettings: { visible: true },
     tooltip: {
        enable: true
     },
    };
  },

```

**5.** Summarizing the above steps, update the `src/App.vue` file with following code.

```html
<template>
    <ejs-accumulationchart :legendSettings="legendSettings" :tooltip="tooltip">
        <e-accumulation-series-collection>
            <e-accumulation-series :dataSource='data' xName='x' yName='y' innerRadius="20%"> </e-accumulation-series>
        </e-accumulation-series-collection>
    </ejs-accumulationchart>
</template>

<script>
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective, AccumulationLegend,
PieSeries, AccumulationTooltip } from "@syncfusion/ej2-vue-charts";

export default {
    name: "App",
    components: {
    "ejs-accumulationchart": AccumulationChartComponent,
    "e-accumulation-series-collection": AccumulationSeriesCollectionDirective,
    "e-accumulation-series":  AccumulationSeriesDirective
  },
  data() {
    return {
      data: [
        { x: 'Argentina', y: 505370 },
        { x: 'Belgium', y: 551500 },
        { x: 'Cuba', y: 312685 },
        { x: 'Dominican Republic', y: 350000 },
        { x: 'Egypt', y: 301000 },
        { x: 'Kazakhstan', y: 300000 },
        { x: 'Somalia', y: 357022 }
     ],
     legendSettings: { visible: true },
     tooltip: {
        enable: true
     },
    };
  },
  provide: {
    accumulationchart: [AccumulationLegend, PieSeries, AccumulationTooltip]
  },
};
</script>

```

**6.** Run the application using the following command.

```bash
npm run serve
```

The web server will be initiated and open the **quickstart** app in the browser at port [`localhost:8080`](http://localhost:8080/).

![Output](./images/vue3-accumulation-chart-demo.png)

Refer the following sample, [vue3-accumulation-chart-getting-started](https://github.com/SyncfusionExamples/vue3-accumulation-chart-getting-started).
