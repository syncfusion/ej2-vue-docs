---
title: " Chart Trendlines | Vue "

component: "Chart"

description: "Trendlines are used to show the direction and speed of price. Chart supports 6 types of trendlines and also provides trendlines customization."
---

# Trendlines

Trendlines are used to show the direction and speed of price.

Trendlines can be generated for Cartesian type series (Line, Column, Scatter, Area, Candle, Hilo etc.)
except bar type series. You can add more than one trendline to a series.

Chart supports 6 types of trendlines.

## Linear

A linear trendline is a best fit straight line that is used with simpler data sets. To render a linear trendline,
use trendline [`type`](../api/chart/trendlineModel/#type) as `Linear` and inject
`TrendLines` module using `provide`.

{% tab template="chart/trendlines/linear" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Scatter' xName='x' yName='y'>
                 <e-trendlines>
                        <e-trendline :type='type'>
                        </e-trendline>
                    </e-trendlines>
                </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ScatterSeries, Trendlines, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1 = [];
let yValue = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95,
    13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point1; let i; let j = 0;
for (i = 1973; i <= 2013; i++) {
    point1 = { x: i, y: yValue[j] };
    series1.push(point1); j++;
}

export default {
  data() {
    return {
        seriesData: series1,
        primaryXAxis: {
        title: 'Months',
        },
        primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
        },
        type: 'Linear'
    };
  },
  provide: {
    chart: [ScatterSeries, Trendlines, LineSeries]
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

## Exponential

An exponential trendline is a curved line that is most useful when data values rise or fall
at increasingly higher rates. You cannot create an exponential trendline, if your data contains zero or negative values.

To render a exponential trendline,
use trendline [`type`](../api/chart/trendlineModel/#type) as `Exponential` and inject
`TrendLines` module using `provide`.

{% tab template= "chart/trendlines/exponential" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Scatter' xName='x' yName='y'>
                  <e-trendlines>
                        <e-trendline :type='type'>
                        </e-trendline>
                    </e-trendlines>
                 </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ScatterSeries, Trendlines, SplineSeries, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1 = [];
let yValue = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95,
    13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point1; let i; let j = 0;
for (i = 1973; i <= 2013; i++) {
    point1 = { x: i, y: yValue[j] };
    series1.push(point1); j++;
}

export default {
  data() {
    return {
        seriesData: series1,
        primaryXAxis: {
        title: 'Months',
        },
        primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
        },
        type: 'Exponential',
        title: 'Historical Indian Rupee Rate (INR USD)'
    };
  },
  provide: {
    chart: [ScatterSeries, Trendlines, SplineSeries, LineSeries]
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

## Logarithmic

A logarithmic trendline is a best-fit curved line that is most useful when the rate of change
in the data increases or decreases quickly and then levels out.

A logarithmic trendline can use negative and/or positive values.

To render a logarithmic trendline, use trendline [`type`](../api/chart/trendlineModel/#type) as `Logarithmic` and inject
`TrendLines` module using `provide`.

{% tab template= "chart/trendlines/logarithmic" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Scatter' xName='x' yName='y'>
                <e-trendlines>
                        <e-trendline :type='type'>
                        </e-trendline>
                    </e-trendlines>
                 </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ScatterSeries, SplineSeries, Trendlines, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1 = [];
let yValue = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95,
    13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point1; let i; let j = 0;
for (i = 1973; i <= 2013; i++) {
    point1 = { x: i, y: yValue[j] };
    series1.push(point1); j++;
}

export default {
  data() {
    return {
        seriesData: series1,
        primaryXAxis: {
        title: 'Months',
        },
        primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
        },
        type: 'Logarithmic',
        title: 'Historical Indian Rupee Rate (INR USD)'
    };
  },
  provide: {
    chart: [ScatterSeries, SplineSeries, Trendlines, LineSeries]
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

## Polynomial

A polynomial trendline is a curved line that is used when data fluctuates.

To render a polynomial trendline,
use trendline [`type`](../api/chart/trendlineModel/#type) as `Polynomial` and inject
`TrendLines` module using `provide`.

`polynomialOrder` used to define the polynomial value.

{% tab template= "chart/trendlines/polynomial" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Scatter' xName='x' yName='y'>
                <e-trendlines>
                        <e-trendline :type='type'>
                        </e-trendline>
                    </e-trendlines>
                </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ScatterSeries, SplineSeries, Trendlines, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1 = [];
let yValue = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95,
    13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point1; let i; let j = 0;
for (i = 1973; i <= 2013; i++) {
    point1 = { x: i, y: yValue[j] };
    series1.push(point1); j++;
}

export default {
  data() {
    return {
        seriesData: series1,
        primaryXAxis: {
        title: 'Months',
        },
        primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
        },
        type: 'Polynomial',
        title: 'Historical Indian Rupee Rate (INR USD)'
    };
  },
  provide: {
    chart: [ScatterSeries, Trendlines, SplineSeries, LineSeries]
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

## Power

A power trendline is a curved line that is best used with data sets that compare measurements that increase at a specific rate.

To render a power trendline, use trendline [`type`](../api/chart/trendlineModel/#type) as `Power` and inject
`TrendLines`.

{% tab template= "chart/trendlines/power" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Scatter' xName='x' yName='y'>
                  <e-trendlines>
                        <e-trendline :type='type'>
                        </e-trendline>
                    </e-trendlines>
                </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ScatterSeries, SplineSeries, Trendlines, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
        seriesData: [
        { x: 1, y: 10 }, { x: 2, y: 50 },{ x: 3, y: 80 }, { x: 4, y: 110 },
        { x: 5, y: 180 }, { x: 6, y: 220 }, { x: 7, y: 300 }, { x: 8, y: 370 }, { x: 9, y: 490 }, { x: 10, y: 500 }
        ],
        primaryXAxis: {
        title: 'Months',
        },
        primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 100
        },
        type: 'Power',
        title: 'Historical Indian Rupee Rate (INR USD)'
    };
  },
  provide: {
    chart: [ScatterSeries, SplineSeries, Trendlines, LineSeries]
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

## Moving Average

A moving average trendline smoothen out fluctuations in data to show a pattern or trend more clearly.

To render a moving average trendline, use trendline [`type`](../api/chart/trendlineModel/#type) as `MovingAverage` and inject
`TrendLines` module using `provide`.

`period` property defines the period to find the moving average.

{% tab template= "chart/trendlines/power" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Scatter' xName='x' yName='y'>
                  <e-trendlines>
                        <e-trendline :type='type'>
                        </e-trendline>
                    </e-trendlines>
                </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ScatterSeries, Trendlines, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1 = [];
let yValue = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95,
    13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point1; let i; let j = 0;
for (i = 1973; i <= 2013; i++) {
    point1 = { x: i, y: yValue[j] };
    series1.push(point1); j++;
}

export default {
  data() {
    return {
        seriesData: series1,
        primaryXAxis: {
        title: 'Months',
        },
        primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
        },
        type: 'MovingAverage',
        title: 'Historical Indian Rupee Rate (INR USD)'
    };
  },
  provide: {
    chart: [ScatterSeries, Trendlines, LineSeries]
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

* Customization of Trendlines

The [`fill`](../api/chart/trendlineModel/#fill) and [`width`](../api/chart/trendlineModel/#width)
properties are used to customize the appearance of the trendline.

{% tab template= "chart/trendlines/power" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Scatter' xName='x' yName='y' fill='#0066FF'>
                 <e-trendlines>
                        <e-trendline :type='type'>
                        </e-trendline>
                    </e-trendlines>
                </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ScatterSeries, Trendlines, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1 = [];
let yValue = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95,
    13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point1;
let i;
let j = 0;
for (i = 1973; i <= 2013; i++) {
    point1 = { x: i, y: yValue[j] };
    series1.push(point1); j++;
}

export default {
  data() {
    return {
        seriesData: series1,
        primaryXAxis: {
        title: 'Months',
        },
        primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
        },
        type: 'MovingAverage',
        title: 'Historical Indian Rupee Rate (INR USD)'
    };
  },
  provide: {
    chart: [ScatterSeries, Trendlines, LineSeries]
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

## Forecasting

Trendlines forecasting is the prediction of future/past situations.

Forecasting can be classified into two types as follows

Forward Forecasting
Backward Forecasting

* Forward Forecasting

The value set for forwardForecast is used to determine the distance moving towards the future trend.

{% tab template= "chart/trendlines/power" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Scatter' xName='x' yName='y'>
                   <e-trendlines>
                        <e-trendline :type='type' :forwardForecast='forwardForecast'>
                        </e-trendline>
                    </e-trendlines>
                </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ScatterSeries, Trendlines, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1 = [];
let yValue = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95,
    13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point1; let i; let j = 0;
for (i = 1973; i <= 2013; i++) {
    point1 = { x: i, y: yValue[j] };
    series1.push(point1); j++;
}

export default {
  data() {
    return {
        seriesData: series1,
        primaryXAxis: {
        title: 'Months'
        },
        primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
        },
        forwardForecast:5,
        type: 'MovingAverage',
        title: 'Historical Indian Rupee Rate (INR USD)'
    };
  },
  provide: {
    chart: [ScatterSeries, Trendlines, LineSeries]
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

* Backward Forecasting

The value set for the backwardForecast is used to determine the past trends.

{% tab template= "chart/trendlines/power" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Scatter' xName='x' yName='y'>
                 <e-trendlines>
                        <e-trendline :type='type' :backwardForecast='backwardForecast'>
                        </e-trendline>
                    </e-trendlines>
                </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ScatterSeries, Trendlines, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1 = [];
let yValue = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95,
    13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point1; let i; let j = 0;
for (i = 1973; i <= 2013; i++) {
    point1 = { x: i, y: yValue[j] };
    series1.push(point1); j++;
}

export default {
  data() {
    return {
        seriesData: series1,
        primaryXAxis: {
        title: 'Months',
        },
        primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
        },
        backwardForecast:5,
        type: 'MovingAverage',
        title: 'Historical Indian Rupee Rate (INR USD)'
    };
  },
  provide: {
    chart: [ScatterSeries, Trendlines, LineSeries]
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