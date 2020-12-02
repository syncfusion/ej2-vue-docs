---
title: " Chart Other Types | Vue "

component: "Chart"

description: "Chart contains box and wishker, errorbar, waterfall and histogram charts and also supports different customization"
---

<!-- markdownlint-disable MD036 -->

# Box and whisker

To render a box and whisker chart, use series[`type`](../api/chart/series/#type) as `BoxAndWhisker` and inject
`BoxAndWhiskerSeries` into the `provide`. The field y requires n number of data or it should
contains minimum of five values to plot a segment.
>
{% tab template="chart/series/box" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='BoxAndWhisker' xName='x' yName='y' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, BoxAndWhiskerSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                    { x: 'Development', y: [22, 22, 23, 25, 25, 25, 26, 27, 27, 28, 28, 29, 30, 32, 34, 32, 34, 36, 35, 38] },
                    { x: 'Testing', y: [22, 33, 23, 25, 26, 28, 29, 30, 34, 33, 32, 31, 50] },
                    { x: 'HR', y: [22, 24, 25, 30, 32, 34, 36, 38, 39, 41, 35, 36, 40, 56] },
                    { x: 'Finance', y: [26, 27, 28, 30, 32, 34, 35, 37, 35, 37, 45] },
                    { x: 'R&D', y: [26, 27, 29, 32, 34, 35, 36, 37, 38, 39, 41, 43, 58] },
                    { x: 'Sales', y: [27, 26, 28, 29, 29, 29, 32, 35, 32, 38, 53] },
                    { x: 'Inventory', y: [21, 23, 24, 25, 26, 27, 28, 30, 34, 36, 38] },
                    { x: 'Graphics', y: [26, 28, 29, 30, 32, 33, 35, 36, 52] },
                    { x: 'Training', y: [28, 29, 30, 31, 32, 34, 35, 36] }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
        marker: { visible: true },
      title: "Company Revenue and Profit"
    };
  },
  provide: {
    chart: [BoxAndWhiskerSeries, Category]
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

## Customization of Box and Whisker series

### boxPlotMode

You can change the rendering mode of the Box and Whisker series using the `boxPlotMode` property.
The default boxPlotMode is `exclusive`.The other boxPlotMode available are `inclusive` and `normal`.

To render a box and whisker chart, use series[`type`](../api/chart/series/#type) as `BoxAndWhisker` and
inject `BoxAndWhiskerSeries` into the `provide`. The field y requires n number of data or it
should contains minimum of five values to plot a segment.
>
{% tab template="chart/series/box" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='BoxAndWhisker' xName='x' yName='y' boxPlotMode='boxPlotMode' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, BoxAndWhiskerSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                    { x: 'Development', y: [22, 22, 23, 25, 25, 25, 26, 27, 27, 28, 28, 29, 30, 32, 34, 32, 34, 36, 35, 38] },
                    { x: 'Testing', y: [22, 33, 23, 25, 26, 28, 29, 30, 34, 33, 32, 31, 50] },
                    { x: 'HR', y: [22, 24, 25, 30, 32, 34, 36, 38, 39, 41, 35, 36, 40, 56] },
                    { x: 'Finance', y: [26, 27, 28, 30, 32, 34, 35, 37, 35, 37, 45] },
                    { x: 'R&D', y: [26, 27, 29, 32, 34, 35, 36, 37, 38, 39, 41, 43, 58] },
                    { x: 'Sales', y: [27, 26, 28, 29, 29, 29, 32, 35, 32, 38, 53] },
                    { x: 'Inventory', y: [21, 23, 24, 25, 26, 27, 28, 30, 34, 36, 38] },
                    { x: 'Graphics', y: [26, 28, 29, 30, 32, 33, 35, 36, 52] },
                    { x: 'Training', y: [28, 29, 30, 31, 32, 34, 35, 36] }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
      boxPlotMode: 'Normal',
      marker: { visible: true },
      title: "Company Revenue and Profit"
    };
  },
  provide: {
    chart: [BoxAndWhiskerSeries, Category]
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

### showMean

In Box and Whisker series `showMean` property is used to show the box and whisker average value. The default value of `showMean` is false.

{% tab template="chart/series/box" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='BoxAndWhisker' xName='x' yName='y' :showMean='showMean' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, BoxAndWhiskerSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                    { x: 'Development', y: [22, 22, 23, 25, 25, 25, 26, 27, 27, 28, 28, 29, 30, 32, 34, 32, 34, 36, 35, 38] },
                    { x: 'Testing', y: [22, 33, 23, 25, 26, 28, 29, 30, 34, 33, 32, 31, 50] },
                    { x: 'HR', y: [22, 24, 25, 30, 32, 34, 36, 38, 39, 41, 35, 36, 40, 56] },
                    { x: 'Finance', y: [26, 27, 28, 30, 32, 34, 35, 37, 35, 37, 45] },
                    { x: 'R&D', y: [26, 27, 29, 32, 34, 35, 36, 37, 38, 39, 41, 43, 58] },
                    { x: 'Sales', y: [27, 26, 28, 29, 29, 29, 32, 35, 32, 38, 53] },
                    { x: 'Inventory', y: [21, 23, 24, 25, 26, 27, 28, 30, 34, 36, 38] },
                    { x: 'Graphics', y: [26, 28, 29, 30, 32, 33, 35, 36, 52] },
                    { x: 'Training', y: [28, 29, 30, 31, 32, 34, 35, 36] }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
      showMean: false,
      marker: { visible: true },
      title: "Company Revenue and Profit"
    };
  },
  provide: {
    chart: [BoxAndWhiskerSeries, Category]
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

## Waterfall Chart

Waterfall chart helps to understand the cumulative effect of the sequentially introduced positive
and negative values. To render a Waterfall series, use series [`type`](../api/chart/series/#type) as
`Waterfall` and inject `WaterfallSeries` into the `provide`.
[`intermediateSumIndexes`](../api/chart/series/#intermediatesumindexes) property of waterfall is used
to represent the in between the sum values and [`sumIndexes`](../api/chart/series/#sumindexes)
is used to represent the cumulative sum values.

{% tab template="chart/series/waterfall" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Waterfall' xName='x' yName='y' name='Male'
                :intermediateSumIndexes:='intermediate' :sumIndexes='sum'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, WaterfallSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { x: 'Income', y: 4711 }, { x: 'Sales', y: -1015 },
            { x: 'Development', y: -688 },
            { x: 'Revenue', y: 1030 }, {x: 'Balance'},
            { x: 'Administrative', y: -780 },
            { x: 'Expense', y: -361 }, { x: 'Tax', y: -695 },
            { x: 'Net Profit'}
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
        sum: [7],
        intermediate: [4]
      title: "Company Revenue and Profit"
    };
  },
  provide: {
    chart: [WaterfallSeries, Category]
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

**Customization of Waterfall Series**

The negative changes of waterfall charts is
represented by using [`negativeFillColor`](../api/chart/series/#negativefillcolor) and the summary changes are
represented by using [`summaryFillColor`](../api/chart/series/#summaryfillcolor) properties.

By default, the negativeFillColor as ‘#E94649’ and the summaryFillColor as ‘#4E81BC’.

{% tab template="chart/series/waterfall" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Waterfall' xName='x' yName='y' name='Male' summaryFillColor='#e56590' negativeFillColor='#f8b883'
                :intermediateSumIndexes:='intermediate' :sumIndexes='sum'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, WaterfallSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { x: 'Income', y: 4711 }, { x: 'Sales', y: -1015 },
            { x: 'Development', y: -688 },
            { x: 'Revenue', y: 1030 }, {x: 'Balance'},
            { x: 'Administrative', y: -780 },
            { x: 'Expense', y: -361 }, { x: 'Tax', y: -695 },
            { x: 'Net Profit'}
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
        sum: [7],
        intermediate: [4]
      title: "Company Revenue and Profit"
    };
  },
  provide: {
    chart: [WaterfallSeries, Category]
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

## Histogram Series

Histogram type charts can provide a visual display of large amounts of data that are difficult to understand in a
tabular or spreadsheet form. To render histogram chart, use series[`type`](../api/chart/series/#type) as `Histogram`
and inject `HistogramSeries` module using `provide` method.

{% tab template="chart/series/waterfall" %}

```html
<template>
    <div id="app">
          <ejs-chart id="container" :legendSettings='legendSettings' :primaryYAxis='primaryYAxis'
        :title='title' :tooltip='tooltip'>
            <e-series-collection>
                <e-series type='Histogram' width=2 yName='y' name='Score' :dataSource='dataSource'
                :binInterval='binInterval' :marker='marker' :showNormalDistribution='showNormalDistribution' :columnWidth='columnWidth'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ChartTheme, HistogramSeries, DataLabel, Tooltip } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let chartData = [];
let points = [5.250, 7.750, 0, 8.275, 9.750, 7.750, 8.275, 6.250, 5.750,
        5.250, 23.000, 26.500, 27.750, 25.025, 26.500, 26.500, 28.025, 29.250, 26.750, 27.250,
        26.250, 25.250, 34.500, 25.625, 25.500, 26.625, 36.275, 36.250, 26.875, 40.000, 43.000,
        46.500, 47.750, 45.025, 56.500, 56.500, 58.025, 59.250, 56.750, 57.250,
        46.250, 55.250, 44.500, 45.525, 55.500, 46.625, 46.275, 56.250, 46.875, 43.000,
        46.250, 55.250, 44.500, 45.425, 55.500, 56.625, 46.275, 56.250, 46.875, 43.000,
        46.250, 55.250, 44.500, 45.425, 55.500, 46.625, 56.275, 46.250, 56.875, 41.000, 63.000,
        66.500, 67.750, 65.025, 66.500, 76.500, 78.025, 79.250, 76.750, 77.250,
        66.250, 75.250, 74.500, 65.625, 75.500, 76.625, 76.275, 66.250, 66.875, 80.000, 85.250,
        87.750, 89.000, 88.275, 89.750, 97.750, 98.275, 96.250, 95.750, 95.250
    ];
points.map((value) => {
    chartData.push({
        y: value
    });
});

export default {
  data() {
    return {
        legendSettings: { visible: false },
        primaryYAxis: {
            title: 'Number of Students',
            minimum: 0, maximum: 50, interval: 10,
            majorTickLines: { width: 0 }, lineStyle: { width: 0 }
        },
          marker: { dataLabel: { visible: true, position: 'Top', font: { fontWeight: '600', color: '#ffffff' } } },
        title: 'Examination Result', tooltip: { enable: true },
       dataSource: chartData,
       tooltip: {enable: true},
       binInterval: 20,
       columnWidth: 0.99,
       showNormalDistribution: true
    };
  },
  provide: {
    chart: [HistogramSeries, DataLabel, Tooltip]
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

## Error Bar Chart

Error bars are graphical representations of the variability of data and used on graphs to indicate the error or uncertainty in a reported
measurement. To render the error bar for the series, set [`visible`](../api/chart/series/#visible)
as `true` in error bar object and inject `ErrorBar` module into the `provide`.

{% tab template="chart/series/errorbar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='India' width=2 :marker='marker' :errorBar='errorBar'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category, ErrorBar } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { x: 2006, y: 7.8 }, { x: 2007, y: 7.2 },
            { x: 2008, y: 6.8 }, { x: 2009, y: 10.7 },
            { x: 2010, y: 10.8 }, { x: 2011, y: 9.8 }
              ],
        primaryXAxis: {
           minimum: 2005, maximum: 2012, interval: 1,
            title: 'Year'
        },
        errorBar: {
            visible: true
        },
        marker: {
            visible: true
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [LineSeries, Category, ErrorBar]
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

**Changing Error Bar Type**

To change the error bar rendering type using [`type`](../api/chart/series/#visible)
option of error bar. To change the error bar line length you can use [`verticalError`](../api/chart/errorBarSettings/)
property.

{% tab template="chart/series/errorbar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='India' width=2 :marker='marker' :errorBar='errorBar'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category, ErrorBar } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { x: 2006, y: 7.8 }, { x: 2007, y: 7.2 },
            { x: 2008, y: 6.8 }, { x: 2009, y: 10.7 },
            { x: 2010, y: 10.8 }, { x: 2011, y: 9.8 }
              ],
        primaryXAxis: {
           minimum: 2005, maximum: 2012, interval: 1,
            title: 'Year'
        },
        errorBar: {
            visible: true,  type: 'Percentage', verticalError:4
        },
        marker: {
            visible: true
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [LineSeries, Category, ErrorBar]
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

**Customizing Error Bar Type**

To customize the error bar type, set error bar [`type`](../api/chart/errorBarSettings/#type) as `Custom` and  then change the horizontal/vertical positive and negative error of error bar.

{% tab template="chart/series/errorbar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='India' width=2 :marker='marker' :errorBar='errorBar'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category, ErrorBar } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { x: 2006, y: 7.8 }, { x: 2007, y: 7.2 },
            { x: 2008, y: 6.8 }, { x: 2009, y: 10.7 },
            { x: 2010, y: 10.8 }, { x: 2011, y: 9.8 }
              ],
        primaryXAxis: {
           minimum: 2005, maximum: 2012, interval: 1,
            title: 'Year'
        },
        errorBar: {
            visible: true, type: 'Custom',
            mode:'Both'
            verticalPostiveError:3,
            horizontalPositiveError:2,
            verticalNegativeError:3,
            horizontalNegativeError:2
        },
        marker: {
            visible: true
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [LineSeries, Category, ErrorBar]
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

**Changing Error Bar Mode**

Error bar mode is used to define whether the error bar line has to be drawn horizontally, vertically or in both side.
To change the error bar mode use [`mode`](../api/chart/errorBarSettings/#mode) option.

{% tab template="chart/series/errorbar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='India' width=2 :marker='marker' :errorBar='errorBar'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category, ErrorBar } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { x: 2006, y: 7.8 }, { x: 2007, y: 7.2 },
            { x: 2008, y: 6.8 }, { x: 2009, y: 10.7 },
            { x: 2010, y: 10.8 }, { x: 2011, y: 9.8 }
              ],
        primaryXAxis: {
           minimum: 2005, maximum: 2012, interval: 1,
            title: 'Year'
        },
        errorBar: {
            visible: true, mode: 'Horizontal'
        },
        marker: {
            visible: true
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [LineSeries, Category, ErrorBar]
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

**Changing Error Bar Direction**

To change the error bar direction to plus, minus or both side using [`direction`](../api/chart/errorBarSettings/#direction) option.

{% tab template="chart/series/errorbar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='India' width=2 :marker='marker' :errorBar='errorBar'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category, ErrorBar } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { x: 2006, y: 7.8 }, { x: 2007, y: 7.2 },
            { x: 2008, y: 6.8 }, { x: 2009, y: 10.7 },
            { x: 2010, y: 10.8 }, { x: 2011, y: 9.8 }
              ],
        primaryXAxis: {
           minimum: 2005, maximum: 2012, interval: 1,
            title: 'Year'
        },
        errorBar: {
            visible: true,  mode:'Vertical', direction:'Minus'
        },
        marker: {
            visible: true
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [LineSeries, Category, ErrorBar]
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

**Customizing Error Bar Cap**

To customize the error bar cap length, width and fill color, you can use [`errorBarCap`](../api/chart/errorBarSettings/#errorbarcap) option.

{% tab template="chart/series/errorbar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='India' width=2 :marker='marker' :errorBar='errorBar'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category, ErrorBar } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { x: 2006, y: 7.8 }, { x: 2007, y: 7.2 },
            { x: 2008, y: 6.8 }, { x: 2009, y: 10.7 },
            { x: 2010, y: 10.8 }, { x: 2011, y: 9.8 }
              ],
        primaryXAxis: {
           minimum: 2005, maximum: 2012, interval: 1,
            title: 'Year'
        },
        errorBar: { visible: true, errorBarCap:{ length:10, width:10, color:'#0000ff' } },
        marker: {
            visible: true
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [LineSeries, Category, ErrorBar]
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

## Vertical Chart

In EJ2 chart, you can draw a chart in vertical manner by changing orientation of the axis. All series types support this feature.
You can use `isTransposed` property in chart to render a chart in vertical manner.

{% tab template="chart/series/line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'  isTransposed='true'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Spline' xName='x' yName='y' name='London'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, SplineSeries, Category, ScatterSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
     { x: 'Jan', y: -1 }, { x: 'Feb', y: -1 }, { x: 'Mar', y: 2 },
    { x: 'Apr', y: 8 }, { x: 'May', y: 13 }, { x: 'Jun', y: 18 },
    { x: 'Jul', y: 21 }, { x: 'Aug', y: 20 }, { x: 'Sep', y: 16 },
    { x: 'Oct', y: 10 }, { x: 'Nov', y: 4 }, { x: 'Dec', y: 0 }
     ],
      primaryXAxis: {
          valueType: 'Category'
        },
         primaryYAxis: {
            minimum: -5, maximum: 35, interval: 10,
            title: 'Temperature in Celsius',
            labelFormat: '{value}C'
        },
      title: "Climate Graph-2012"
    };
  },
  provide: {
    chart: [SplineSeries, Category, ScatterSeries]
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

## Pareto chart

Pareto charts are used to find the cumulative values of data in different categories. It is a combination of Column and Line series.The initial values are represented by column chart and the cumulative values are represented by Line chart. To render a pareto chart, use series [`type`](../api/chart/errorBarSettings/#type) as `Pareto` and inject `ParetoSeries` `ColumnSeries` and  `LineSeries` module.

{% tab template="chart/series/line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container":title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Pareto' xName='x' yName='y' name='Defect' width='2'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import {ChartPlugin, LineSeries, StackingColumnSeries, Tooltip, ColumnSeries, Category, Legend, ParetoSeries} from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data: function() {
    return {
      seriesData: [
                    { x: 'Traffic', y: 56 }, { x: 'Child Care', y: 44.8 },
                    { x: 'Transport', y: 27.2 }, { x: 'Weather', y: 19.6 },
                    { x: 'Emergency', y: 6.6 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Defects'
        },
        primaryYAxis:
        {
            title: 'Frequency',
            minimum: 0,
            maximum: 150,
            interval: 30,
        },

      title: 'Defect vs Frequency',
      tooltip: {
            enable: true,
            shared: true
        }

    };
  },
  provide: {
    chart: [StackingColumnSeries, LineSeries, Category, ColumnSeries, Legend, Tooltip, ParetoSeries]
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

* [Data label](./data-labels/)
* [Tooltip](./tool-tip/)
