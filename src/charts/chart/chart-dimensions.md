---
title: " Chart Appearance | Vue "

component: "Chart"

description: "We can set chart size manually by using width and height properties. We can set percentage or pixel size values to the chart."
---

# Chart Dimensions

## Size for Container

Chart can render to its container size. You can set the size via inline or CSS as demonstrated below.

{% tab template="chart/getting-started/datasource" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" width='650px' height='350px' :primaryXAxis='primaryXAxis'>
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

## Size for Chart

You can also set size for chart directly through [`width`](../api/chart/chartModel/#width) and
[`height`](../api/chart/chartModel/#height) properties.

<!-- markdownlint-disable MD036 -->
* In Pixel
<!-- markdownlint-disable MD036 -->

You can set the size of chart in pixel as demonstrated below.

{% tab template= "chart/getting-started/datasource" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" width='650px' height='350px' :primaryXAxis='primaryXAxis'>
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

* In Percentage

By setting value in percentage, chart gets its dimension with respect to its container. For example,
when the height is ‘50%’, chart renders to half of the container height.

{% tab template="chart/getting-started/datasource" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :primaryXAxis='primaryXAxis' width='80%' height='90%'>
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

> Note:  When you do not specify the size, it takes `450px` as the height and window size as its width.