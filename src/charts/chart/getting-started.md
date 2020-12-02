---
title: " Chart Getting Started | Vue "

component: "Chart"

description: "Getting started file explains how to configure and install chart packages and also how to create basic chart, module injections."
---

# Getting Started

This section explains you the steps required to create a simple chart and demonstrate the basic usage of the chart control.

## Dependencies

Below is the list of minimum dependencies required to use the chart component.

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
import { ChartPlugin } from '@syncfusion/ej2-vue-charts';

Vue.use(ChartPlugin);
```

> Registering `ChartPlugin` in vue, will register the chart component along with its required child directives globally.

## Adding Chart Component

* Add the Vue Chart by using `<ejs-chart>` selector in `<template>` section of the `App.vue` file.
The below example shows a basic Charts,

{% tab template="chart/getting-started/initialize" %}

```html
<template>
  <div id="app">
      <ejs-chart id="container"> </ejs-chart>
  </div>
</template>
<script>
import Vue from 'vue';
import { ChartPlugin } from '@syncfusion/ej2-vue-charts';

Vue.use(ChartPlugin);
export default {
  data () {
    return {
    }
  }
}
</script>
<style>
 #container{
   height: 350px;
 }
</style>
```

{% endtab %}

* Now run the application in the browser using the below command.

```cmd
npm run dev
```

## Module Injection

Chart component are segregated into individual feature-wise modules. In order to use a particular feature,
you need to inject its feature service in the AppModule. In the current application, we are
going to modify the above basic chart to visualize sales data for a particular year.
For this application we are going to use  line series, tooltip, data label, category axis and legend
feature of the chart. Please find relevant
feature service name and description as follows.

* `LineSeries` - Inject this provider to use line series.
* `Legend` - Inject this provider to use legend feature.
* `Tooltip` - Inject this provider to use tooltip feature.
* `DataLabel` - Inject this provider to use datalabel feature.
* `Category`  - Inject this provider to use category feature.

These modules should be injected to the provide section as follows,

 ```javascript
import Vue from "vue";
import { ChartPlugin, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  provide: {
    chart: [LineSeries]
  }
};
</script>
 ```

## Populate Chart with Data

This section explains how to plot below JSON data to the chart.

```javascript
export default {
  data() {
    return {
      seriesData: [
            { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
            { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
            { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
            { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
            { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
            { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
              ]
    };
  }
};
```

* Add a series object to the chart by using [`series`](../api/chart/series/) property. Now map the field names `month` and `sales` in the JSON data to the [`xName`](../api/chart/series/#xname) and
[`yName`](../api/chart/series/#yname) properties of the series, then set the JSON data to [`dataSource`](../api/chart/series/#datasource) property.

Since the JSON contains category data, set the [`valueType`](../api/chart/valueType/#valuetype)for horizontal axis to `Category`. By default, the axis valueType is `Numeric`.

{% tab template="chart/getting-started/datasource" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='month' yName='sales' name='Sales'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
            { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
            { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
            { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
            { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
            { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        }
    };
  },
  provide: {
    chart: [LineSeries, Category]
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

* The sales data are in thousands, so format the vertical axis label by adding
`$` as a prefix and `K` as a suffix to each label. This can be achieved by setting the
`${value}K` to the [`labelFormat`](../api/chart/axis/#labelformat) property of axis. Here, `{value}` act as a placeholder
for each axis label.

{% tab template="chart/getting-started/datasource" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='month' yName='sales' name='Sales'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
            { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
            { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
            { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
            { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
            { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
        primaryYAxis:{
            labelFormat: '${value}K'
        }
    };
  },
  provide: {
    chart: [LineSeries, Category]
  }
};
</script>
<style>
 #container{
   height: 350px;
 }
</style>
```

{% endtab %}

## Add Chart Title

You can add a title using [`title`](../api/chart/chartModel/#title) property to the chart to provide
quick information to the user about the data plotted in the chart.

{% tab template="chart/getting-started/tooltip" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='month' yName='sales' name='Sales'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
            { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
            { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
            { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
            { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
            { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
        primaryYAxis:{
            labelFormat: '${value}K'
        },
      title: "Sales Analysis"
    };
  },
  provide: {
    chart: [LineSeries, Category]
  }
};
</script>
<style>
 #container{
   height: 350px;
 }
</style>
```

{% endtab %}

## Enable Legend

You can use legend for the chart by setting the `visible` property to true in [`legendSettings`](../api/chart/legendSettings/) object and by injecting the `LegendService` into the `@NgModule.providers`.

{% tab template="chart/getting-started/legend" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :legendSettings='legendSettings'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='month' yName='sales' name='Sales'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category, Legend } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
            { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
            { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
            { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
            { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
            { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
        primaryYAxis:{
            labelFormat: '${value}K'
        },
        legendSettings: {
            visible: true
        },
      title: "Sales Analysis"
    };
  },
  provide: {
    chart: [LineSeries, Category, Legend]
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

## Add Data Label

You can add data labels to improve the readability of the chart.
This can be achieved by setting the visible property to true in the `dataLabel` object  and by injecting `DataLabel` into the `provide`.

{% tab template="chart/getting-started/datalabel" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :legendSettings='legendSettings'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='month' yName='sales' name='Sales':marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category, DataLabel, Legend } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
            { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
            { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
            { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
            { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
            { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
        primaryYAxis:{
            labelFormat: '${value}K'
        },
        legendSettings: {
            visible: true
        },
        marker: {
        dataLabel:{
                visible: true
            }
        },
      title: "Sales Analysis"
    };
  },
  provide: {
    chart: [LineSeries, Category, DataLabel, Legend]
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

## Enable Tooltip

The tooltip is useful when you cannot display information by using the data labels
due to space constraints. You can enable tooltip by setting the enable property as true in [`tooltip`](../api/chart/tooltipSettingsModel/) object and by injecting `TooltipService` into the `@NgModule.providers`.

{% tab template="chart/getting-started/tooltip" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :tooltip='tooltip'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='month' yName='sales' name='Sales':marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category, DataLabel, Tooltip } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
            { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
            { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
            { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
            { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
            { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
        primaryYAxis:{
            labelFormat: '${value}K'
        },
        legendSettings: {
            visible: true
        },
        marker: {
        dataLabel:{
                visible: true
            }
        },
        tooltip:{ enable: true },
      title: "Sales Analysis"
    };
  },
  provide: {
    chart: [LineSeries, Category, DataLabel, Tooltip]
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