---
title: " Stock Chart Working With Data | Vue "

component: "Stock Chart"

description: "Stock Chart can be rendered by using different types of data source. They are called local data, remote data and empty points. "
---
<!-- markdownlint-disable MD036 -->

# Working with Data

Stock Chart can visualise data bound from local or remote data.

## Local Data

You can bind a simple JSON data to the chart using
[`dataSource`](../api/stock-chart/stockSeriesModel/#datasource) property in series.

{% tab template="stockchart/working-with-data", iframeHeight="500px"%}

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
        seriesData:chartData,
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
<style>
#container {
   height: 350px;
 }
</style>
```

{% endtab %}

## See Also

* [Series Types](./series-types/)