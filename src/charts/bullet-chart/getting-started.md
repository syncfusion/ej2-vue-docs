---
title: "Bullet Chart Getting Started | Vue "

component: "Bullet Chart"

description: "Getting started file explains how to configure and install bullet chart packages and also how to create basic bullet chart, module injections."
---

# Getting Started

This section explains you the steps required to create a simple bullet chart and demonstrate the basic usage of the bullet chart control.

## Dependencies

Below is the list of minimum dependencies required to use the bullet chart component.

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

## Adding Syncfusion Bullet Chart package

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.

To install bullet chart component, use the following command

```bash
npm install @syncfusion/ej2-vue-charts --save
```

> The **--save** will instruct NPM to include the bullet chart package inside of the `dependencies` section of the `package.json`.

## Registering Bullet Chart Component

You can register the bullet chart component in your application by using the `Vue.use()`.

Refer to the code example given below.

```typescript
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';

Vue.use(BulletChartPlugin);
```

> Registering `BulletChartPlugin` in vue, will register the bullet chart component along with its required child directives globally.

## Adding Bullet Chart Component

* Add the Vue Bullet Chart by using `<ejs-bulletchart>` selector in `<template>` section of the `App.vue` file.
The below example shows a basic bullet chart,

{% tab template="bullet-chart/getting-started/initialize" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"> </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
    }
  }
}
</script>
```

{% endtab %}

* Now run the application in the browser using the below command.

```cmd
npm run dev
```

## Module Injection

Bullet Chart component are segregated into individual feature-wise modules. In order to use a particular feature, you need to inject its feature module using `provide` method. In the current application,we are going to use tooltip feature of the bullet chart.

* `BulletTooltip` - Inject this provider to use tooltip feature.

These modules should be injected to the provide method as follows,

 ```typescript
import Vue from "vue";
import { BulletChartPlugin, BulletTooltip } from "@syncfusion/ej2-vue-charts";

Vue.use(BulletChartPlugin);

export default {
  provide: {
    bulletChart: [BulletTooltip]
  }
};
 ```

## BulletChart With Data

This section explains how to plot local data to the bullet chart.

```typescript
let data: any[] = [
       { value: 100, target: 80 },
       { value: 200, target: 180 },
       { value: 300, target: 280 },
       { value: 400, target: 380 },
       { value: 500, target: 480 },
];
```

Now assign the local data to `dataSource` property. `value` and `target` values should be mapped with `valueField` and `targetField` respectively.

{% tab template="bullet-chart/getting-started/datasource" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        height="300"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
      > </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [
       { value: 100, target: 80 },
       { value: 200, target: 180 },
       { value: 300, target: 280 },
       { value: 400, target: 380 },
       { value: 500, target: 480 },
      ],
      minimum: 0, maximum: 300, interval: 50
    }
  }
}
</script>
```

{% endtab %}

## Add Bullet Chart Title

You can add a title using `title` property to the bullet chart to provide quick
information to the user about the data plotted in the bullet chart.

{% tab template="bullet-chart/getting-started/title" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Revenue"
      > </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 270, target: 250 }],
      minimum: 0, maximum: 300, interval: 50
    }
  }
}
</script>
```

{% endtab %}

## Ranges

You can add a range using `e-bullet-range` of the `e-bullet-range-collection`.

{% tab template="bullet-chart/getting-started/ranges" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Revenue"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="100" color="red"></e-bullet-range>
          <e-bullet-range end="200" color="blue"></e-bullet-range>
          <e-bullet-range end="300" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 270, target: 250 }],
      minimum: 0, maximum: 300, interval: 50
    }
  }
}
</script>
```

{% endtab %}

## Tooltip

You can use tooltip for the bullet chart by setting the `enable` property to true in `tooltip` object and by injecting the `BulletTooltip` module using `provide` method.

{% tab template="bullet-chart/getting-started/tooltip" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Revenue"
        :tooltip="tooltip"
      > </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin, BulletTooltip } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 270, target: 250 }],
      minimum: 0, maximum: 300, interval: 50,
      tooltip: { enable: true }
    }
  },
  provide: {
    bulletChart: [BulletTooltip]
  }
}
</script>
```

{% endtab %}
