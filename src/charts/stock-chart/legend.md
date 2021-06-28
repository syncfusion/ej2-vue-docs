---
title: " Stock Chart Legend | Vue "

component: "Stock Chart"

description: "Stock Chart legend provides information about the series rendered in the Stock Chart. It has different alignment, shapes and customization properties. "
---

# Legend

Legend provides information about the series rendered in the Stock Chart which can be customized using legend properties. Legend can be added to a Stock Chart by enabling the [`visible`](../api/stock-chart/legendSettings/#visible) option in the [`legendSettings`](../api/stock-chart/legendSettings/).

## Position and Alignment

By using the [`position`](../api/stock-chart/legendSettings/#position) property, legend can be placed at `Left`, `Right`, `Top`, `Bottom` or `Custom` of the Stock Chart. The legend is positioned at the bottom of the Stock Chart, by default.

{% tab template="stockchart/legend", iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :tooltip="tooltip"
        :legendSettings="legendSettings"
        :indicatorType="indicatorType"
        :trendlineType="trendlineType"
        :crosshair="crosshair"
        :title="title">
        <e-stockchart-series-collection>
          <e-stockchart-series :dataSource="seriesData" type="Candle"  volume='volume' xName='date' low='low' high='high' open='open' close='close' name='AAPL'></e-stockchart-series>
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
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,BollingerBands,  TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator,Tooltip,
  Crosshair,AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator, Export, StockLegend
} from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
        seriesData:chartData,
        trendlineType:[],
        indicatorType:[],
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
        tooltip: { enable: true },
        legendSettings: {
        visible: true,
        //Legend position as top
        position:'Top'
        },
        title: 'AAPL Stock Price',
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator, Tooltip,
  Crosshair,BollingerBands, TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator,Export, StockLegend
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

* [`Custom`](../api/stock-chart/legendSettings/#position) position is used to position the legend anywhere in the Stock Chart using x, y coordinates.

{% tab template="stockchart/legend", iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :tooltip="tooltip"
        :legendSettings="legendSettings"
        :indicatorType="indicatorType"
        :trendlineType="trendlineType"
        :crosshair="crosshair"
        :title="title">
        <e-stockchart-series-collection>
          <e-stockchart-series :dataSource="seriesData" type="Candle"  volume='volume' xName='date' low='low' high='high' open='open' close='close' name='AAPL'></e-stockchart-series>
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
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,BollingerBands,  TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator,Tooltip,
  Crosshair,AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator, Export, StockLegend
} from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
        seriesData:chartData,
        trendlineType:[],
        indicatorType:[],
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
        tooltip: { enable: true },
        legendSettings: {
        visible: true,
        //Legend position as custom
        position:'Custom',
        location: { x: 200, y: 20 } },
        title: 'AAPL Stock Price',
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator, Tooltip,
  Crosshair,BollingerBands, TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator,Export, StockLegend
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

<!-- markdownlint-disable MD036 -->

**Legend Alignment**

<!-- markdownlint-disable MD036 -->

The legend can be align as `Center`, `Far` or `Near` to the chart using [`alignment`](../api/stock-chart/legendSettings/#alignment) property.

{% tab template="stockchart/legend", iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :tooltip="tooltip"
        :legendSettings="legendSettings"
        :indicatorType="indicatorType"
        :trendlineType="trendlineType"
        :crosshair="crosshair"
        :title="title">
        <e-stockchart-series-collection>
          <e-stockchart-series :dataSource="seriesData" type="Candle"  volume='volume' xName='date' low='low' high='high' open='open' close='close' name='AAPL'></e-stockchart-series>
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
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,BollingerBands,  TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator,Tooltip,
  Crosshair,AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator, Export, StockLegend
} from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
        seriesData:chartData,
        trendlineType:[],
        indicatorType:[],
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
        tooltip: { enable: true },
        legendSettings: {
        visible: true,
        position:'Bottom',
        //Legend alignment as near
        alignment: 'Near'
        },
        title: 'AAPL Stock Price',
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator, Tooltip,
  Crosshair,BollingerBands, TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator,Export, StockLegend
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

To change the legend icon shape, [`legendShape`](../api/stock-chart/stockSeries/#legendshape) property in the [`series`](../api/stock-chart/stockSeries/) can be used. By default legend icon shape is `seriesType`.

{% tab template="stockchart/legend", iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :tooltip="tooltip"
        :legendSettings="legendSettings"
        :indicatorType="indicatorType"
        :trendlineType="trendlineType"
        :crosshair="crosshair"
        :title="title">
        <e-stockchart-series-collection>
          <e-stockchart-series :dataSource="seriesData" type="Candle"  volume='volume' xName='date' low='low' high='high' open='open' close='close' name='AAPL' legendShape='Pentagon'></e-stockchart-series>
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
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,BollingerBands,  TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator,Tooltip,
  Crosshair,AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator, Export, StockLegend
} from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
        seriesData:chartData,
        trendlineType:[],
        indicatorType:[],
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
        tooltip: { enable: true },
        legendSettings: { visible: true },
        title: 'AAPL Stock Price',
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator, Tooltip,
  Crosshair,BollingerBands, TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator,Export, StockLegend
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

**Legend Size**

By default, legend takes 20% - 25% of the Stock Chart's height horizontally, when it is placed on top or bottom position and 20% - 25% of the Stock Chart's width vertically, when placed on left or right position of the Stock Chart. The default legend size can be changed by using the [`width`](../api/stock-chart/legendSettings/#width) and [`height`](../api/stock-chart/legendSettings/#height) property of the `legendSettings`.

{% tab template="stockchart/legend", iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :tooltip="tooltip"
        :legendSettings="legendSettings"
        :indicatorType="indicatorType"
        :trendlineType="trendlineType"
        :crosshair="crosshair"
        :title="title">
        <e-stockchart-series-collection>
          <e-stockchart-series :dataSource="seriesData" type="Candle"  volume='volume' xName='date' low='low' high='high' open='open' close='close' name='AAPL'></e-stockchart-series>
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
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,BollingerBands,  TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator,Tooltip,
  Crosshair,AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator, Export, StockLegend
} from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
        seriesData:chartData,
        trendlineType:[],
        indicatorType:[],
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
        tooltip: { enable: true },
        legendSettings: {
        visible: true,
        //Legend size for chart
        width: '500', height: '50',
        border: { width: 1, color: 'pink'}
        },
        title: 'AAPL Stock Price',
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator, Tooltip,
  Crosshair,BollingerBands, TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator,Export, StockLegend
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

**Legend Item Size**

The size of the legend items can customized by using the [`shapeHeight`](../api/stock-chart/legendSettings/#shapeheight) and [`shapeWidth`](../api/stock-chart/legendSettings/#shapewidth) property.

{% tab template="stockchart/legend", iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :tooltip="tooltip"
        :legendSettings="legendSettings"
        :indicatorType="indicatorType"
        :trendlineType="trendlineType"
        :crosshair="crosshair"
        :title="title">
        <e-stockchart-series-collection>
          <e-stockchart-series :dataSource="seriesData" type="Candle"  volume='volume' xName='date' low='low' high='high' open='open' close='close' name='AAPL'></e-stockchart-series>
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
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,BollingerBands,  TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator,Tooltip,
  Crosshair,AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator, Export, StockLegend
} from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
        seriesData:chartData,
        trendlineType:[],
        indicatorType:[],
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
        tooltip: { enable: true },
        legendSettings: {
        visible: true,
        //Legend item size for chart
        shapeHeight: 15, shapeWidth: 15
        },
        title: 'AAPL Stock Price',
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator, Tooltip,
  Crosshair,BollingerBands, TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator,Export, StockLegend
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

## Collapsing Legend Item

By default, series name will be displayed as legend. To skip the legend for a particular series, empty string to the series name can be given.

{% tab template="stockchart/legend", iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :tooltip="tooltip"
        :legendSettings="legendSettings"
        :indicatorType="indicatorType"
        :trendlineType="trendlineType"
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
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,BollingerBands,  TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator,Tooltip,
  Crosshair,AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator, Export, StockLegend
} from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
        seriesData:chartData,
        trendlineType:[],
        indicatorType:[],
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
        tooltip: { enable: true },
        title: 'AAPL Stock Price',
        legendSettings: { visible: true }
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator, Tooltip,
  Crosshair,BollingerBands, TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator,Export, StockLegend
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

## Legend Title

The title for legend can be set using [`title`](../api/stock-chart/legendSettings/#title) property in `legendSettings`. Customize the [`fontStyle`](../api/stock-chart/stockChartFont/#fontstyle), [`size`](../api/stock-chart/stockChartFont/#size), [`fontWeight`](../api/stock-chart/stockChartFont/#fontweight), [`color`](../api/stock-chart/stockChartFont/#color), [`textAlignment`](../api/stock-chart/stockChartFont/#textalignment), [`fontFamily`](../api/stock-chart/stockChartFont/#fontfamily), [`opacity`](../api/stock-chart/stockChartFont/#opacity) and [`textOverflow`](../api/stock-chart/stockChartFont/#textoverflow) of legend title. [`titlePosition`](../api/stock-chart/legendSettings/#titleposition) is used to set the legend position in Top, Left and Right position. [`maximumTitleWidth`](../api/stock-chart/legendSettings/#maximumtitlewidth) is used to set the width of the legend title. By default, it will be `100px`.

{% tab template="stockchart/legend", iframeHeight="500px" %}

```html
<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        id="stockchartcontainer"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :tooltip="tooltip"
        :legendSettings="legendSettings"
        :indicatorType="indicatorType"
        :trendlineType="trendlineType"
        :crosshair="crosshair"
        :title="title">
        <e-stockchart-series-collection>
          <e-stockchart-series :dataSource="seriesData" type="Candle"  volume='volume' xName='date' low='low' high='high' open='open' close='close' name='AAPL'></e-stockchart-series>
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
  HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator,BollingerBands,  TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator,Tooltip,
  Crosshair,AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator, Export, StockLegend
} from "@syncfusion/ej2-vue-charts";

Vue.use(StockChartPlugin);

export default {
  data() {
    return {
        seriesData:chartData,
        trendlineType:[],
        indicatorType:[],
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
        tooltip: { enable: true },
        title: 'AAPL Stock Price',
        legendSettings: {
            visible: true,
            title: 'Countries',
            titlePosition: 'Top',
            titleStyle: {
                fontFamily: 'verdana',
                fontStyle: 'Normal',
                fontWeight: 'Normal',
                size: '15px',
                textAlignment: 'Center',
                color: 'blue',
                textOverflow: 'None'
            },
            maximumTitleWidth: 150
        }
    };
  },
  provide: {
    stockChart: [
      DateTime, RangeTooltip, LineSeries, SplineSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, RangeAreaSeries, Trendlines, EmaIndicator, RsiIndicator, Tooltip,
  Crosshair,BollingerBands, TmaIndicator, MomentumIndicator, SmaIndicator, AtrIndicator, AccumulationDistributionIndicator, MacdIndicator, StochasticIndicator,Export, StockLegend
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

>Note: To use legend feature, we need to inject `StockLegend` into the `Provide`.