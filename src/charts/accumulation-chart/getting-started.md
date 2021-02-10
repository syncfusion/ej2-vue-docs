---
title: " Accumulation Chart Getting Started | Vue "

component: "Accumulation Chart"

description: "Getting started file explains how configure and install chart packages and also how to create basic accumulation chart."
---

# Getting Started

In EJ2, Accumulation chart is implemented as a separate control to avoid axis related logics. Dependencies
for accumulation chart is same as chart control.

## Dependencies

The list of minimum dependencies required to use an accumulation chart are follows:

```javascript
|-- @syncfusion/ej2-vue-charts
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-pdf-export
    |-- @syncfusion/ej2-file-utils
    |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-charts
    |-- @syncfusion/ej2-vue-base
    |-- @syncfusion/ej2-svg-base
```

## Installation and Configuration

## Setup Vue Environment

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications.
To install Vue CLI use the following commands.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

## Create a Vue Application

Start a new Vue application using below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install
```

## Adding Syncfusion Chart package

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.

To install chart component, use the following command

```bash
npm install @syncfusion/ej2-vue-charts --save
```

> The **--save** will instruct NPM to include the chart package inside of the `dependencies` section of the `package.json`.

## Registering Chart Component

You can register the chart component in your application by using the `Vue.use()`.

Refer to the code example given below.

```typescript
import { AccumulationChartPlugin } from '@syncfusion/ej2-vue-charts';

Vue.use(AccumulationChartPlugin);
```

> Registering `ChartPlugin` in vue, will register the chart component along with its required child directives globally.

## Adding Chart Component

* Add the Vue Chart by using `<ejs-chart>` selector in `<template>` section of the `App.vue` file.

The below example shows a basic Charts,

* Pie Series

By default pie series will be rendered on assigning JSON data to the series by using
[`dataSource`](../api/accumulation-chart/accumulationSeries/#datasource) property. Map the field names
in the JSON data to the [`xName`](../api/accumulation-chart/accumulationSeries/#xname) and
[`yName`](../api/accumulation-chart/accumulationSeries/#yname) properties of the series.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container">
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries } from "@syncfusion/ej2-vue-charts";
import { data } from "data.ts";
Vue.use(AccumulationChartPlugin);
export default {
  data() {
    return {
      seriesData: data
    };
  },
  provide: {
     accumulationchart: [PieSeries]
  }
};
</script>
<style>
 #container {
     height: 350px;
 }
</style>
```

{% endtab %}

* Now run the application in the browser using the below command.

```cmd
npm run dev
```