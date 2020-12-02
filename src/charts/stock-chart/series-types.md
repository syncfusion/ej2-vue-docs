---
title: " Series Types | Vue "

component: "StockChart"

description: "Essential JS 2 StockChart supports 32 types of series and also supports different tpes customizations for each type of StockChart."
---

# StockChart Series Types

Essential JS 2 StockChart supports 6 major types of series namely `Line`, `Spline`, `Hilo`, `HiloOpenClose`, `Hollow Candle` and `Candle` . By using the series dropdown button you can navigate between the above listed series types.

<!-- markdownlint-disable MD036 -->

## Line

To render a line series, use series [`type`](../api/stock-chart/stockSeriesModel/#type-string) as `Line` and
inject `LineSeries` into the `provide`.

## Spline

To render a spline series, use series [`type`](../api/stock-chart/stockSeriesModel/#type-string) as `Spline` and
inject `SplineSeries` into the `provide`.

## Hilo

To render a hilo series, use series [`type`](../api/stock-chart/stockSeriesModel/#type-string) as `Hilo` and
inject `HiloSeries` into the `provide`.

## HiloOpenClose

To render a hiloOpenClose series, use series [`type`](../api/stock-chart/stockSeriesModel/#type-string) as `HiloOpenClose` and
inject `HiloOpenCloseSeries` into the `provide`.

## HollowCandle

To render a hollowcandle series, use series [`type`](../api/stock-chart/stockSeriesModel/#type-string) as `Candle` and set `enableSolidCandle` as false. Now inject `CandleSeries` into the `provide`.

## Candle

To render a candle series, use series [`type`](../api/stock-chart/stockSeriesModel/#type-string) as `Candle` and
inject `CandleSeries` into the `provide`.

{% tab template="stockchart/series-types", iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :indicatorType="indicatorType"
        :trendlineType="trendlineType"
        :exportType="exportType"
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
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries
} from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
        seriesData:chartData,
        primaryXAxis: {
            valueType: "DateTime",
            majorGridLines: { color: "transparent" },
        },
        primaryYAxis: {
            majorTickLines: { color: "transparent", width: 0 }
        },
      indicatorType:[],
      trendlineType: [],
      exportType: [],
      title: 'AAPL Stock Price',
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, RangeAreaSeries ]
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