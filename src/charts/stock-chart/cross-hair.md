---
title: " Stock Chart Crosshair | Vue "

component: "StockChart"

description: "Crosshair has a vertical and horizontal line to view the value of the axis at mouse position.The trackball used to display data collections"
---

# Crosshair

Crosshair has a vertical and horizontal line to view the value of the axis at mouse or touch position.

Crosshair lines can be enabled by using [`enable`](../api/chart/crosshairSettingsModel/#enable-boolean)property in the `crosshair`.

{% tab template="stockchart/cross-hair", iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        width='650px' height='350px'
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :crosshair="crosshair"
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
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,BollingerBands,  TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, Crosshair,AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator, Export
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
        crosshair: {
         enable: true,
        },
       title: 'AAPL Stock Price',
    };
  },
  provide: {
    stockChart: [
      DateTime, Crosshair, RangeTooltip, LineSeries, SplineSeries, CandleSeries,     HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,
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

## Tooltip for axis

Tooltip label for an axis can be enabled by using [`enable`](../api/chart/crosshairSettingsModel/#enable-boolean)
property of `crosshairTooltip` in the corresponding axis.

{% tab template="stockchart/cross-hair", iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :crosshair="crosshair"
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
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,BollingerBands,  TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, Crosshair,AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator, Export
} from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
        seriesData:chartData,
        primaryXAxis: {
            valueType: "DateTime",
            majorGridLines: { color: "transparent" },
            crosshairTooltip: { enable: true }
        },
        primaryYAxis: {
            majorTickLines: { color: "transparent", width: 0 },
            crosshairTooltip: { enable: true }
        },
        crosshair: {
         enable: true,
        },
       title: 'AAPL Stock Price',
    };
  },
  provide: {
    stockChart: [
      DateTime, Crosshair, RangeTooltip, LineSeries, SplineSeries, CandleSeries,     HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,
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

## Customization

The [`fill`](../api/chart/crosshairSettingsModel/#fill-string) and [`textStyle`](../api/chart/crosshairSettingsModel/#textstyle-fontmodel)
property of the `crosshairTooltip` is used to customize the background color and font style of the crosshair label
respectively. Color and width of the crosshair line can be customized by using the
[`line`](../api/chart/crosshairSettingsModel/#line-bordermodel) property in the crosshair.

{% tab template="stockchart/cross-hair", iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :crosshair="crosshair"
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
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,BollingerBands,  TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, Crosshair,AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator, Export
} from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
        seriesData:chartData,
        primaryXAxis: {
            valueType: "DateTime",
            majorGridLines: { color: "transparent" },
            crosshairTooltip: { enable: true,fill: 'green' }
        },
        primaryYAxis: {
            majorTickLines: { color: "transparent", width: 0 },
            crosshairTooltip: { enable: true ,fill: 'green'}
        },
        crosshair: {  enable: true, line: {width: 2, color: 'green'}, fill: 'green' }
       title: 'AAPL Stock Price',
    };
  },
  provide: {
    stockChart: [
      DateTime, Crosshair, RangeTooltip, LineSeries, SplineSeries, CandleSeries,     HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,
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

>Note: To use crosshair feature, we need to inject `Crosshair` into the `provide`.