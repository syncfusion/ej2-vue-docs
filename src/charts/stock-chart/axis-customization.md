---
title: " Stock Chart Axis Customization | Vue "

component: "Stock Chart"

description: " Stock Chart axis contains different customization and types like axis crossing, multiple axis, inversed axis, tick and grid, title customizations"
---

# Axis Customization

## Axis Crossing

An axis can be positioned in the Stock Chart area using `crossesAt` properties. The `crossesAt`  property specifies the values (datetime, numeric, or logarithmic) at which the axis line has to be intersected with the vertical axis or vice-versa, and the `crossesInAxis` property specifies the axis name with which the axis line has to be crossed.

{% tab template="stockchart/axis-customization", iframeHeight="500px" %}

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
            crossesAt : 15
        },
        primaryYAxis: {
            majorTickLines: { color: "transparent", width: 0 },
            crossesAt : 5
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

## Title

You can add a title to the axis using [`title`](../api/stock-chart/stockChartAxisModel/#title) property to provide quick
information to the user about the data plotted in the axis. Title style can be customized using [`titleStyle`](../api/stock-chart/stockChartAxisModel/#titlestyle) property of the axis.

{% tab template="stockchart/axis-customization", iframeHeight="500px" %}

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
           title: 'AAPL Historical'
        },
        primaryYAxis: {
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

## Tick Lines Customization

You can customize the  `width`, `color` and `size` of the minor and major tick lines, using
[`majorTickLines`](../api/stock-chart/stockChartAxisModel/#majorticklines) and
[`minorTickLines`](../api/stock-chart/stockChartAxisModel/#minorticklines) properties in the axis.

{% tab template="stockchart/axis-customization", iframeHeight="500px" %}

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
              majorTickLines : {
               color : 'green',
               width : 5
            },
            minorTickLines : {
               color : 'red',
               width : 0
            }
       },
        primaryYAxis: {
             majorTickLines : {
               color : 'blue',
               width : 5
            },
            minorTickLines : {
               color : 'red',
               width : 0
            }
        },
      title: 'AAPL Stock Price'
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries,HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,
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

## Grid Lines Customization

You can customize the `width`, `color` and `dashArray` of the minor and major grid lines,
using [`majorGridLines`](../api/stock-chart/stockChartAxisModel/#majorgridlines) and
[`minorGridLines`](../api/stock-chart/stockChartAxisModel/#minorgridlines) properties in the axis.

{% tab template="stockchart/axis-customization", iframeHeight="500px" %}

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
              majorGridLines : {
              color : 'blue',
              width : 1
           },
           minorGridLines : {
              color : 'red',
              width : 0
           }
       },
        primaryYAxis: {
            majorGridLines : {
              color : 'green',
              width : 1
           },
           minorGridLines : {
              color : 'red',
              width : 0
           }
        },
      title: 'AAPL Stock Price'
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,
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

## Multiple Axis

In addition to primary X and Y axis, we can add n number of axis to the stock chart. Series can be associated with
this [`axis`](../api/stock-chart/stockChartAxisModel), by mapping with axis's unique name.

{% tab template="stockchart/axis-customization", iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :axes='axes'
        :title="title">
        <e-stockchart-series-collection>
          <e-stockchart-series :dataSource="seriesData" type="Candle"  volume='volume' xName='date' low='low' high='high' open='open' close='close'></e-stockchart-series>
           <e-stockchart-series :dataSource="seriesData" type="Line" xName='date' yName='close' yAxisName='yAxis'></e-stockchart-series>
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
            majorGridLines: { color: "transparent" }
        },
        primaryYAxis: {
            majorTickLines: { color: "transparent", width: 0 }
        },
         axes:
          [
            {
            majorGridLines: { width: 0 },
            rowIndex: 1, opposedPosition: true,
            name: 'yAxis'
            }
        ],
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

## Inversed Axis

<!-- markdownlint-disable MD033 -->

When an axis is inversed, highest value of the axis comes closer to origin and vice versa. To place an axis in inversed manner set this property
 [`isInversed`](../api/stock-chart/stockChartAxisModel/#isinversed) to true.

 {% tab template="stockchart/axis-customization", iframeHeight="500px" %}

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
            isInversed: true
        },
        primaryYAxis: {
            majorTickLines: { color: "transparent", width: 0 },
            isInversed: true
        },
      title: 'AAPL Stock Price'
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries,HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,
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

## Opposed Position

<!-- markdownlint-disable MD012 -->
To place an axis opposite from its original position, set [`opposedPosition`](../api/stock-chart/stockChartAxisModel/#opposedposition)
property of the axis to true.
<!-- markdownlint-disable MD012 -->

 {% tab template="stockchart/axis-customization", iframeHeight="500px" %}

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
            majorGridLines: { color: "transparent" }
        },
        primaryYAxis: {
            majorTickLines: { color: "transparent", width: 0 },
            opposedPosition: true
        },
      title: 'AAPL Stock Price'
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries,HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,
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