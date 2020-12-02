---
title: " Stock Chart Axis Types | Vue "

component: "Stock Chart"

description: "Date time axis uses date time scale and displays the date time values as axis labels in the specified format. "
---

# DateTime,Numeric and Logarithmic Axis

## DateTime Axis

Date time axis uses date time scale and displays the date time values as axis labels in the specified format and set the [`valueType`](../api/stock-chart/stockChartAxisModel/#valuetype) of axis to DateTime.

{% tab template="stockchart/axis-types", iframeHeight="500px" %}

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
            lineStyle: { color: "transparent" },
            majorTickLines: { color: "transparent", width: 0 }
        },
      title: 'AAPL Stock Price'
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries,     HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,
      BollingerBands, TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator,      AccumulationDistributionIndicator,  MacdIndicator, StochasticIndicator,Export
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

>Note: To use datetime axis, we need to inject `DateTimeService` into the `provide` and set the [`valueType`](../api/stock-chart/stockChartAxisModel/#valuetype) of axis to `DateTime`.

## Logarithmic Axis

<!-- markdownlint-disable MD033 -->

Logarithmic axis uses logarithmic scale and it is very useful in visualizing data, when it has numerical values in
both lower order of magnitude (eg: 10<sup>-6</sup>) and higher order of magnitude (eg: 10<sup>6</sup>) and set the [`valueType`](../api/stock-chart/stockChartAxisModel/#valuetype) of axis to `Lograthmic`.

{% tab template="stockchart/axis-types", iframeHeight="500px" %}

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
          <e-stockchart-series :dataSource="seriesData" type="Candle"  volume='volume' xName='date' yName='volume' low='low' high='high' open='open' close='close'></e-stockchart-series>
        </e-stockchart-series-collection>
      </ejs-stockchart>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { chartData } from "./datasource.js";
import {
  StockChartPlugin, DateTime, CandleSeries, RangeTooltip, LineSeries,SplineSeries, Logarithmic,
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
             valueType: 'Logarithmic',
            majorTickLines: { color: "transparent", width: 0 }
        },
      title: 'AAPL Stock Price'
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,Logarithmic,
      BollingerBands, TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator,      AccumulationDistributionIndicator,  MacdIndicator, StochasticIndicator,Export
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

>Note: To use log axis, we need to inject `LogarithmicService` into the `provide` and set the [`valueType`](../api/stock-chart/stockChartAxisModel/#valuetype) of axis to `Logarithmic`.

## See Also

* [Axis Customization](./axis-customization/)