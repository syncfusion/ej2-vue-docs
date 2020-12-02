---
title: " StockChart Trendlines | Vue "

component: "StockChart"

description: "Trendlines are used to show the direction and speed of price. StockChart supports 6 types of trendlines and also provides trendlines customization."
---
<!-- markdownlint-disable MD036 -->

# Trendlines

Trendlines are used to show the direction and speed of price.

StockChart supports 6 types of trendlines namely `Linear`,`Exponential`,`Logarithmic`,`Polynomial`,`Power`,`Moving Average`. By using trendline dropdown button you can add or remove the required trendline type.

## Linear

A linear trendline is a best fit straight line that is used with simpler data sets. To render a linear trendline,
use trendline [`type`](../api/stock-chart/stockChartTrendlineModel/#type) as `Linear` and inject
`Trendlines` module using `provide`.

## Exponential

An exponential trendline is a curved line that is most useful when data values rise or fall at increasingly higher rates. You cannot create an exponential trendline, if your data contains zero or negative values.

To render a exponential trendline,
use trendline [`type`](../api/stock-chart/stockChartTrendlineModel/#type) as `Exponential` and inject
`Trendlines` module using `provide`.

## Logarithmic

A logarithmic trendline is a best-fit curved line that is most useful when the rate of change in the data increases or decreases quickly and then levels out. A logarithmic trendline can use negative and/or positive values.

To render a logarithmic trendline, use trendline [`type`](../api/stock-chart/stockChartTrendlineModel/#type) as `Logarithmic` and inject
`Trendlines` module using `provide`.

## Polynomial

A polynomial trendline is a curved line that is used when data fluctuates.

To render a polynomial trendline,
use trendline [`type`](../api/stock-chart/stockChartTrendlineModel/#type) as `Polynomial` and inject
`Trendlines` module using `provide`.

`polynomialOrder` used to define the polynomial value.

## Power

A power trendline is a curved line that is best used with data sets that compare measurements that increase at a specific rate.

To render a power trendline, use trendline [`type`](../api/stock-chart/stockChartTrendlineModel/#type) as `Power` and inject
`Trendlines` module using `provide`.

## Moving Average

A moving average trendline smoothen out fluctuations in data to show a pattern or trend more clearly.

To render a moving average trendline, use trendline [`type`](../api/stock-chart/stockChartTrendlineModel/#type) as `MovingAverage` and inject
`Trendlines` module using `provide`.

`period` property defines the period to find the moving average.

{% tab template="stockchart/trend-lines", iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :seriesType="seriesType"
        :indicatorType="indicatorType"
        :exportType="exportType"
        :title="title">
        <e-stockchart-series-collection>
          <e-stockchart-series :dataSource="seriesData" type="Candle"  volume='volume' xName='date' low='low' high='high' open='open' close='close'>
          <e-trendlines>
              <e-trendline :type='type'></e-trendline>
          </e-trendlines>
          </e-stockchart-series>
        </e-stockchart-series-collection>
      </ejs-stockchart>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { chartData } from "./datasource.js";
import {
  StockChartPlugin, DateTime, CandleSeries, RangeTooltip,Trendlines
} from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
        seriesData:chartData,
         seriesType:[],
        indicatorType:[],
        exportType: [],
        type: 'MovingAverage',
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
      DateTime, RangeTooltip,  CandleSeries, Trendlines
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

**Customization of Trendlines**

The [`fill`](../api/stock-chart/stockChartTrendlineModel/#fill-string) and [`width`](../api/stock-chart/stockChartTrendlineModel/#width-number)
properties are used to customize the appearance of the trendline.

{% tab template="stockchart/trend-lines", iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :seriesType="seriesType"
        :indicatorType="indicatorType"
        :exportType="exportType"
        :title="title">
        <e-stockchart-series-collection>
          <e-stockchart-series :dataSource="seriesData" type="Candle"  volume='volume' xName='date' low='low' high='high' open='open' close='close'>
          <e-trendlines>
              <e-trendline :type='type'></e-trendline>
          </e-trendlines>
          </e-stockchart-series>
        </e-stockchart-series-collection>
      </ejs-stockchart>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { chartData } from "./datasource.js";
import {
  StockChartPlugin, DateTime, CandleSeries, RangeTooltip,Trendlines
} from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
        seriesData:chartData,
         seriesType:[],
        indicatorType:[],
        exportType: [],
        type: 'MovingAverage',
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
      DateTime, RangeTooltip,  CandleSeries, Trendlines
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
