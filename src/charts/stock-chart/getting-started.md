---
title: " Stock Chart Getting Started | Vue "

component: "Stock Chart"

---

# Getting Started

Getting started file explains how to create a simple Stock Chart and demonstrate the basic usage of the Stock Chart control.

## Dependencies

The list of minimum dependencies required to use stock chart are follows:

```javascript
|-- @syncfusion/ej2-charts
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-pdf-export
    |-- @syncfusion/ej2-file-utils
    |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-svg-base
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-calendars
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-splitbuttons
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

## Registering Stock Chart Component

You can register the Stock chart component in your application by using the `Vue.use()`.

Refer to the code example given below.

```typescript
import { StockChartPlugin } from '@syncfuion/ej2-vue-charts';

Vue.use(StockChartPlugin);
```

> Registering `StockChartPlugin` in vue, will register the stock chart component along with its required child directives globally.

## Adding Stock chart to the Project

* Add the Vue Stock Chart by using `<ejs-stockchart>` selector in `<template>` section of the `App.vue` file.
The below example shows a basic stock chart,

```html
<template>
  <div id="app">
      <ejs-stockchart></ejs-stockchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { StockChartPlugin } from '@syncfusion/ej2-vue-charts';

Vue.use(StockChartPlugin);
export default {
  data () {
    return {
    }
  }
}
</script>
```

## Run the application

The quickstart project is configured to compile and run the application in the browser. Use the following command to run the application.

* Now run the application in the browser using the below command.

```cmd
npm run dev
```

## Module Injection

To create stock chart with additional features, inject the required modules. The following modules are used to extend stock chart’s basic functionality.

•`CandleSeries` - Inject this module to use candle series.
•`DateTime` - Inject this module to use date time axis.
•`RangeTooltip` - Inject this module to show the tooltip.

These modules should be injected to the provide section as follows,

 ```javascript
import Vue from "vue";
import { StockChartPlugin, CandleSeries, DateTime, RangeTooltip } from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  provide: {
    stockChart: [CandleSeries, DateTime, RangeTooltip]
  }
};
</script>
 ```

## Populate Stock Chart with Data

 This section explains how to plot below JSON data to the  Stock Chart. Please find the below imported datasource.

```javascript
export default {
  data() {
    return {
     data: [{
   x: new Date( '2012-04-02' ),
    open : 85.9757,
    high : 90.6657,
    low : 85.7685,
    close : 90.5257,
    volume : 660187068
  },
  {
   x: new Date( '2012-04-09' ),
    open : 89.4471,
    high : 92,
    low : 86.2157,
    close : 86.4614,
    volume : 912634864
  },
  {
   x: new Date( '2012-04-16' ),
    open : 87.1514,
    high : 88.6071,
    low : 81.4885,
    close : 81.8543,
    volume : 1221746066
  },
  {
   x: new Date( '2012-04-23' ),
    open : 81.5157,
    high : 88.2857,
    low : 79.2857,
    close : 86.1428,
    volume : 965935749
  },
  {
   x: new Date( '2012-04-30' ),
    open : 85.4,
    high : 85.4857,
    low : 80.7385,
    close : 80.75,
    volume : 615249365
  }];
};
}
};
```

 Add a series object to the Stock chart by using [`series`](../api/stock-chart/stockSeries.html) property and then set the JSON data to [`dataSource`](../api/stock-chart/stockSeries.html#datasource-object---datamanager) property.

Since the JSON contains category data, set the [`valueType`](../api/stock-chart/stockChartAxis.html#valuetype-string) for
horizontal axis to Category. By default, the axis valueType is Numeric.

{% tab template="stockchart/getting-started",  iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :title="title">
        <e-stockchart-series-collection>
          <e-stockchart-series :dataSource="seriesData" type="Candle"  volume='volume' xName='date' low='low' high='high' open='open' close='close'></e-stockchart-series>
        </e-stockchart-series-collection>
      </ejs-stockchart>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { chartData } from "./datasource.js";
import {
  StockChartPlugin, DateTime, CandleSeries, RangeTooltip, LineSeries,SplineSeries,
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,BollingerBands,  TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator, Export
} from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
        seriesData: chartData,
        primaryXAxis: {
            valueType: "DateTime",
            majorGridLines: { color: "transparent" },
        },
        primaryYAxis: {
            majorTickLines: { color: "transparent", width: 0 }
        },
      title: 'AAPL Stock Price',
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,
      BollingerBands, TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator,Export
    ]
  }
};
</script>
```

{% endtab %}

## Add Stock Chart Title

 You can add a title using [`title`](../api/stock-chart/stockChartModel/#title-string) property to the Stock Chart to provide quick information to the user about the data plotted in the Chart.

 {% tab template="stockchart/getting-started",  iframeHeight="500px" %}

```html
<template>
    <div id="app">
        <ejs-stockchart :valueType='valueType' :labelFormat='labelFormat' :title='title'>
            <e-stockchart-series-collection>
                <e-stockchart-series :dataSource='seriesData' type='Candle' xName='date' low='low' high='high' open='open' close='close' width=2>
                </e-stockchart-series>
            </e-stockchart-series-collection>
        </ejs-stockchart>
    </div>
</template>
<script>
import Vue from "vue";
import { StockChartPlugin, DateTime, CandleSeries, RangeTooltip, LineSeries,SplineSeries,
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,BollingerBands,  TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator, Export} from "@syncfusion/ej2-vue-charts";
import { chartData } from "./datasource.js";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
     valueType: 'DateTime',
     seriesData: chartData,
     labelFormat: 'MMM-yy',
     title: 'Sales Analysis'
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries,HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,
      BollingerBands, TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator,      AccumulationDistributionIndicator,  MacdIndicator, StochasticIndicator, Export
    ]
  }
};
</script>
```

{% endtab %}

## Add Crosshair

Crosshair has a vertical and horizontal line to view the value of the axis at mouse or touch position.

Crosshair lines can be enabled by using [`enable`](../api/chart/crosshairTooltip.html#enable-boolean) property in the `crosshair`. Likewise tooltip label for an axis can be enabled by using [`enable`](../api/chart/crosshairTooltipModel.html#enable-boolean) property of `crosshairTooltip` in the corresponding axis.

{% tab template="stockchart/getting-started",  iframeHeight="500px" %}

```html
<template>
    <div id="app">
        <ejs-stockchart :title='title'  :crosshair="crosshair">
            <e-stockchart-series-collection>
                <e-stockchart-series :dataSource='seriesData' type='Candle'>
                </e-stockchart-series>
            </e-stockchart-series-collection>
        </ejs-stockchart>
    </div>
</template>
<script>
import Vue from "vue";
import { chartData } from "./datasource.js";
import {
  StockChartPlugin, DateTime, CandleSeries, RangeTooltip, LineSeries,SplineSeries,Crosshair,
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,BollingerBands,  TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator, Export
} from "@syncfusion/ej2-vue-charts";
Vue.use(StockChartPlugin);

export default {
  data() {
    return {
     title: 'Sales Analysis',
     seriesData: chartData,
       crosshair: {
        enable: true,
      }
    };
  },
   provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries,HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,Crosshair,
      BollingerBands, TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator,      AccumulationDistributionIndicator,  MacdIndicator, StochasticIndicator, Export
    ]
  }
};
</script>
```

{% endtab %}

## Add Trackball

Trackball is used to track a data point closest to the mouse or touch position. Trackball marker indicates the
closest point and trackball tooltip displays the information about the point. To use trackball feature,
we need to inject `Crosshair` and `Tooltip` into the `provide`.

Trackball can be enabled by setting the [`enable`](../api/chart/crosshairSettings.html#enable-boolean) property of the crosshair to true and
[`shared`](../api/chart/tooltipSettings.html#shared-boolean) property in `tooltip` to true in chart.

{% tab template="stockchart/getting-started",  iframeHeight="500px" %}

```html
<template>
    <div id="app">
         <ejs-stockchart id= "container" :title='title' :primaryXAxis='primaryXAxis' :crosshair='crosshair' :tooltip='tooltip'>
            <e-stockchart-series-collection>
                <e-stockchart-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='John' > </e-stockchart-series>
                <e-stockchart-series :dataSource='seriesData' type='Line' xName='x' yName='y1' name='Andrew' > </e-stockchart-series>
                <e-stockchart-series :dataSource='seriesData' type='Line' xName='x' yName='y2' name='Thomas' > </e-stockchart-series>
                <e-stockchart-series :dataSource='seriesData' type='Line' xName='x' yName='y3' name='Mark' > </e-stockchart-series>
                <e-stockchart-series :dataSource='seriesData' type='Line' xName='x' yName='y4' name='William' > </e-stockchart-series>
            </e-stockchart-series-collection>
        </ejs-stockchart>
    </div>
</template>
<script>
import Vue from "vue";
import {
  StockChartPlugin, DateTime, CandleSeries, RangeTooltip, LineSeries,SplineSeries,Crosshair,
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,BollingerBands,  TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, Tooltip,AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator, Export
} from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
        seriesData: [
            { x: new Date(2000, 2, 11), y: 15, y1: 39, y2: 60, y3: 75, y4: 85 },
            { x: new Date(2000, 9, 14), y: 20, y1: 30, y2: 55, y3: 75, y4: 83 },
            { x: new Date(2001, 2, 11), y: 25, y1: 28, y2: 48, y3: 68, y4: 85 },
            { x: new Date(2001, 9, 16), y: 21, y1: 35, y2: 57, y3: 75, y4: 87 },
            { x: new Date(2002, 2, 7), y: 13, y1: 39, y2: 62, y3: 71, y4: 82 },
            { x: new Date(2002, 9, 7), y: 18, y1: 41, y2: 64, y3: 69, y4: 74 },
            { x: new Date(2003, 2, 11), y: 24, y1: 45, y2: 57, y3: 81, y4: 73 },
            { x: new Date(2003, 9, 14), y: 23, y1: 48, y2: 53, y3: 84, y4: 75 },
            { x: new Date(2004, 2, 6), y: 19, y1: 54, y2: 63, y3: 85, y4: 73 },
            { x: new Date(2004, 9, 6), y: 31, y1: 55, y2: 50, y3: 87, y4: 60 },
            { x: new Date(2005, 2, 11), y: 39, y1: 57, y2: 66, y3: 75, y4: 48 },
            { x: new Date(2005, 9, 11), y: 50, y1: 60, y2: 65, y3: 70, y4: 55 },
            { x: new Date(2006, 2, 11), y: 24, y1: 60, y2: 79, y3: 85, y4: 40 }
              ],
      primaryXAxis: {
            title: 'Years',
            minimum: new Date(2000, 1, 1), maximum: new Date(2006, 2, 11),
            intervalType: 'Months',
            valueType: 'DateTime',
        },
        title: "Average Sales per Person",
        crosshair: {  enable: true, lineType: 'Vertical' },
        tooltip: { enable: true, shared: true, format: '${series.name} : ${point.x} : ${point.y}' }
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries,HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,Tooltip,Crosshair,
      BollingerBands, TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator,      AccumulationDistributionIndicator,  MacdIndicator, StochasticIndicator, Export
    ]
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