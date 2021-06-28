---
title: " Chart Types | Vue "

component: "Chart"

description: "Essential JS 2 Chart supports 32 types of series and also supports different types customizations for each type of chart."
---

# Chart Types

Essential JS 2 Chart supports 32 types of series.

<!-- markdownlint-disable MD036 -->

## Line Charts

<!-- markdownlint-disable MD036 -->

* Line

To render a line series, use series [`type`](../api/chart/series/#type) as `Line` and
inject `LineSeries` into the `provide`.

{% tab template="chart/series/line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='India'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
             { x: 2005, y: 28 }, { x: 2006, y: 25 },{ x: 2007, y: 26 }, { x: 2008, y: 27 },
             { x: 2009, y: 32 }, { x: 2010, y: 35 }, { x: 2011, y: 30 }
              ],
      title: "Efficiency of oil-fired power production"
    };
  },
  provide: {
    chart: [LineSeries]
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

* Step Line

To render a step line series, use series [`type`](../api/chart/series/#type) as `StepLine` and inject `StepLineSeries` into
the `provide`.

{% tab template="chart/series/line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StepLine' xName='x' yName='y' name='USA'  width=2> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StepLineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
             { x: 2006, y: 378 }, { x: 2007, y: 416 },
             { x: 2008, y: 404 }, { x: 2009, y: 390 },
             { x: 2010, y: 376 }, { x: 2011, y: 365 }
        ],
      title: "CO2 - Intensity Analysis"
    };
  },
  provide: {
    chart: [StepLineSeries]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* Stacked Line

To render a stacked line series, use series [`type`](../api/chart/series/#type) as `StackingLine` and
inject `StackingLineSeries` into the `provide`.

{% tab template="chart/series/line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="chartcontainer"
        :title="title"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :tooltip="tooltip"
        :chartArea="chartArea">
            <e-series-collection>
               <e-series :dataSource="seriesData" type="StackingLine" xName="x"          yName="y" name="John" width="2" dashArray="5,1" :marker="marker" ></e-series>
            <e-series :dataSource="seriesData" type="StackingLine" xName="x" yName="y1"            name="Peter" width="2" dashArray="5,1" :marker="marker" ></e-series>
            <e-series :dataSource="seriesData" type="StackingLine" xName="x" yName="y2"
              name="Steve" width="2" dashArray="5,1" :marker="marker" ></e-series>
            <e-series :dataSource="seriesData" type="StackingLine" xName="x" yName="y3"
               name="Charle" width="2" dashArray="5,1" :marker="marker" ></e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import {   ChartPlugin,StackingLineSeries,Legend,Tooltip,Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: "Food", y: 90, y1: 40, y2: 70, y3: 120 },
              { x: "Transport", y: 80, y1: 90, y2: 110, y3: 70 },
              { x: "Medical", y: 50, y1: 80, y2: 120, y3: 50 },
              { x: "Clothes", y: 70, y1: 30, y2: 60, y3: 180 },
              { x: "Personal Care", y: 30, y1: 80, y2: 80, y3: 30 },
              { x: "Books", y: 10, y1: 40, y2: 30, y3: 270 },
              { x: "Fitness", y: 100, y1: 30, y2: 70, y3: 40 },
              { x: "Electricity", y: 55, y1: 95, y2: 55, y3: 75 },
              { x: "Tax", y: 20, y1: 50, y2: 40, y3: 65 },
              { x: "Pet Care", y: 40, y1: 20, y2: 80, y3: 95 },
              { x: "Education", y: 45, y1: 15, y2: 45, y3: 195 },
              { x: "Entertainment", y: 75, y1: 45, y2: 65, y3: 115 }
              ],
      primaryXAxis: {
          majorGridLines: { width: 0 },
          minorGridLines: { width: 0 },
          majorTickLines: { width: 0 },
          minorTickLines: { width: 0 },
          interval: 1,
          lineStyle: { width: 0 },
          valueType: "Category"
      },primaryYAxis: {
        title: "Expense",
        lineStyle: { width: 0 },
        minimum: 0,
        maximum: 400,
        interval: 100,
        majorTickLines: { width: 0 },
        majorGridLines: { width: 1 },
        minorGridLines: { width: 1 },
        minorTickLines: { width: 0 },
        labelFormat: "${value}"
      },
      chartArea: {
        border: {
          width: 0
        }
      },
      marker: {
        visible: true
      },
      tooltip: {
        enable: true
      },
      title: "Family Expense for Month"
    };
  },
  provide: {
    chart: [StackingLineSeries, Legend, Tooltip, Category]
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

* 100% Stacked Line

To render a 100% Stacked Line series, use series [`type`](../api/chart/series/#type) as `StackingLine100` and
inject `StackingLineSeries` into the `provide`.

{% tab template="chart/series/line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="chartcontainer"
        :title="title"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :tooltip="tooltip"
        :chartArea="chartArea">
            <e-series-collection>
               <e-series :dataSource="seriesData" type="StackingLine100" xName="x"          yName="y" name="John" width="2" dashArray="5,1" :marker="marker" ></e-series>
            <e-series :dataSource="seriesData" type="StackingLine100" xName="x" yName="y1"            name="Peter" width="2" dashArray="5,1" :marker="marker" ></e-series>
            <e-series :dataSource="seriesData" type="StackingLine100" xName="x" yName="y2"
              name="Steve" width="2" dashArray="5,1" :marker="marker" ></e-series>
            <e-series :dataSource="seriesData" type="StackingLine100" xName="x" yName="y3"
               name="Charle" width="2" dashArray="5,1" :marker="marker" ></e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import {   ChartPlugin,StackingLineSeries,Legend,Tooltip,Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: "Food", y: 90, y1: 40, y2: 70, y3: 120 },
              { x: "Transport", y: 80, y1: 90, y2: 110, y3: 70 },
              { x: "Medical", y: 50, y1: 80, y2: 120, y3: 50 },
              { x: "Clothes", y: 70, y1: 30, y2: 60, y3: 180 },
              { x: "Personal Care", y: 30, y1: 80, y2: 80, y3: 30 },
              { x: "Books", y: 10, y1: 40, y2: 30, y3: 270 },
              { x: "Fitness", y: 100, y1: 30, y2: 70, y3: 40 },
              { x: "Electricity", y: 55, y1: 95, y2: 55, y3: 75 },
              { x: "Tax", y: 20, y1: 50, y2: 40, y3: 65 },
              { x: "Pet Care", y: 40, y1: 20, y2: 80, y3: 95 },
              { x: "Education", y: 45, y1: 15, y2: 45, y3: 195 },
              { x: "Entertainment", y: 75, y1: 45, y2: 65, y3: 115 }
              ],
      primaryXAxis: {
         majorGridLines: { width: 0 },
        minorGridLines: { width: 0 },
        majorTickLines: { width: 0 },
        minorTickLines: { width: 0 },
        interval: 1,
        lineStyle: { width: 0 },
        valueType: "Category"
      },primaryYAxis: {
        title: "Expense",
        lineStyle: { width: 0 },
        interval: 20,
        minorTickLines: { width: 0 },
        majorTickLines: { width: 0 },
        majorGridLines: { width: 1 },
        minorGridLines: { width: 1 }
      },
      chartArea: {
        border: {
          width: 0
        }
      },
       marker: {
        visible: true
      },
      tooltip: {
        enable: true,
        format: "${point.x} : <b>${point.y} (${point.percentage}%)</b>"
      },
      title: "Family Expense for Month"
    };
  },
  provide: {
    chart: [StackingLineSeries, Legend, Tooltip, Category]
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

* Spline

To render a spline series, use series [`type`](../api/chart/series/#type) as `Spline` and inject `SplineSeries` into the `provide`.

{% tab template="chart/series/line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Spline' xName='x' yName='y' name='London'  width=2
                :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, SplineSeries, Category } from "@syncfusion/ej2-vue-charts";

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
           title: 'Month',
           valueType: 'Category'
        },
      marker: { visible: true, width: 10, height: 10 },
      title: "Climate Graph-2012"
    };
  },
  provide: {
    chart: [SplineSeries, Category]
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

* Spline Area

To render a spline series, use series [`type`](../api/chart/series/#type) as `Spline` and
inject `SplineAreaSeries` into the `provide`.

{% tab template="chart/series/line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='SplineArea' xName='x' yName='y' name='London'  width=2
                :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, SplineAreaSeries, Category } from "@syncfusion/ej2-vue-charts";

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
           title: 'Month',
           valueType: 'Category'
        },
      marker: { visible: true, width: 10, height: 10 },
      title: "Climate Graph-2012"
    };
  },
  provide: {
    chart: [SplineAreaSeries, Category]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* Multicolored Line

To render a multicolored line series, use the series type as `MultiColoredLine`, and inject the
`MultiColoredLineSeries` into the `provide`.
Here, the individual colors to the data can be mapped by using `pointColorMapping`.

{% tab template="chart/series/line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='MultiColoredLine' xName='x' yName='y' name='London'  width=2
                :marker='marker' pointColorMapping= 'color'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, MultiColoredLineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
        { x: 2005, y: 28 , color: 'red'}, { x: 2006, y: 25, color:'green'},
        { x: 2007, y: 26, color: '#ff0097' }, { x: 2008, y: 27, color: 'crimson' },
        { x: 2009, y: 32, color: 'blue' }, { x: 2010, y: 35 ,color: 'darkorange'}
        ],
      marker: { visible: true, width: 10, height: 10 },
      title: "Climate Graph-2012"
    };
  },
  provide: {
    chart: [MultiColoredLineSeries]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* Customization of Line Charts

`stroke`, `stroke-width` and `dashArray` of all line type series can be customized by using [`fill`](../api/chart/series/#fill),
[`width`](../api/chart/series/#width) and [`dashArray`](../api/chart/series/#dasharray) properties.

{% tab template="chart/series/line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='India'
                fill='green' width=3 dashArray='5,5' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
             { x: 2005, y: 28 }, { x: 2006, y: 25 },{ x: 2007, y: 26 }, { x: 2008, y: 27 },
             { x: 2009, y: 32 }, { x: 2010, y: 35 }, { x: 2011, y: 30 }
        ],
      title: "Efficiency of oil-fired power production",
      marker: { visible: true },
    };
  },
  provide: {
    chart: [LineSeries]
  },
};
</script>
<style>
#container {
   height: 350px;
 }
</style>
```

{% endtab %}

## Area Charts

* Area

To render a area series, use series [`type`](../api/chart/series/#type) as `Area` and inject `AreaSeries` into the `provide`.

{% tab template="chart/series/area" %}

```html
<template>
    <div id="app">
         <ejs-chart>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Area' xName='x' yName='y' name='India'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, AreaSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
             { x: 1900, y: 4 }, { x: 1920, y: 3.0 },{ x: 1940, y: 3.8 },
             { x: 1960, y: 3.4 }, { x: 1980, y: 3.2 }, { x: 2000, y: 3.9 }
        ]
    };
  },
  provide: {
    chart: [AreaSeries]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* Range Area

To render a range area series, use series [`type`](../api/chart/series/#type)
as `RangeArea` and inject `RangeAreaSeries`  into the `provide`.

{% tab template="chart/series/area" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='RangeArea' xName='x' high='high' low='low'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, RangeAreaSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
            { x: 'Jan', low: 0.7, high: 6.1 }, { x: 'Feb', low: 1.3, high: 6.3 },
            { x: 'Mar', low: 1.9, high: 8.5 }, { x: 'Apr', low: 3.1, high: 10.8 },
            { x: 'May', low: 5.7, high: 14.4 }, { x: 'June', low: 8.4, high: 16.9 },
            { x: 'July', low: 10.6, high: 19.2 }, { x: 'Aug', low: 10.5, high: 18.9 },
            { x: 'Sep', low: 8.5, high: 16.1 }, { x: 'Oct', low: 6.0, high: 12.5 },
            { x: 'Nov', low: 1.5, high: 6.9 }, { x: 'Dec', low: 5.1, high: 12.1 }
        ],
        primaryXAxis: {
           title: 'Month',valueType: 'Category',
           edgeLabelPlacement: 'Shift'
        },
        primaryYAxis: {
            title: 'Temperature(Celsius)',
            minimum: 0, maximum: 20
        },
         title: "Maximum and Minimum Temperature"
    };
  },
  provide: {
    chart: [RangeAreaSeries, Category]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* Spline Range Area

The Spline Range Area Chart is used to display continuous data points as a set of splines that vary between high and low values over intervals of time and across different categories.

To render a spline range area series, use series [`type`](../api/chart/series/#type) as `SplineRangeArea` and inject `SplineRangeAreaSeries`  into the `provide`.

{% tab template="chart/series/area" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='SplineRangeArea' xName='x' high='high' low='low' name='England'> </e-series>
                <e-series :dataSource='seriesData1' type='SplineRangeArea' xName='x' high='high' low='low' name='India'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, SplineRangeAreaSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
            { x: 'Jan', high: 14, low: 4 },
            { x: 'Feb', high: 17, low: 7 },
            { x: 'Mar', high: 20, low: 10 },
            { x: 'Apr', high: 22, low: 12 },
            { x: 'May', high: 20, low: 10 },
            { x: 'Jun', high: 17, low: 7 },
            { x: 'Jul', high: 15, low: 5 },
            { x: 'Aug', high: 17, low: 7 },
            { x: 'Sep', high: 20, low: 10 },
            { x: 'Oct', high: 22, low: 12 },
            { x: 'Nov', high: 20, low: 10 },
            { x: 'Dec', high: 17, low: 7 }
        ],
      seriesData1:[
            { x: 'Jan', high: 29, low: 19 },
            { x: 'Feb', high: 32, low: 22 },
            { x: 'Mar', high: 35, low: 25 },
            { x: 'Apr', high: 37, low: 27 },
            { x: 'May', high: 35, low: 25 },
            { x: 'Jun', high: 32, low: 22 },
            { x: 'Jul', high: 30, low: 20 },
            { x: 'Aug', high: 32, low: 22 },
            { x: 'Sep', high: 35, low: 25 },
            { x: 'Oct', high: 37, low: 27 },
            { x: 'Nov', high: 35, low: 25 },
            { x: 'Dec', high: 32, low: 22 }
        ],
        primaryXAxis: {
            valueType: 'Category',
            edgeLabelPlacement: 'Shift',
            majorGridLines: { width: 0 }
        },
        primaryYAxis: {
            labelFormat: '{value}˚C',
            lineStyle: { width: 0 },
            minimum: 0,
            maximum: 40,
            majorTickLines: { width: 0 }
        },
        title: 'Monthly Temperature Range'
    };
  },
  provide: {
    chart: [SplineRangeAreaSeries, Category]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* Stacked Area

To render a stacked area series, use series [`type`](../api/chart/series/#type) as `StackingArea` and inject `StackingAreaSeries`
into the `provide`.

{% tab template="chart/series/area" %}

```html
<template>
    <div id="app">
         <ejs-chart :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StackingArea' xName='x' yName='y' name='Organic'> </e-series>
                <e-series :dataSource='seriesData' type='StackingArea' xName='x' yName='y1' name='Fair-trade'> </e-series>
                <e-series :dataSource='seriesData' type='StackingArea' xName='x' yName='y2' name='Veg Alternatives'> </e-series>
                <e-series :dataSource='seriesData' type='StackingArea' xName='x' yName='y3' name='Others'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StackingAreaSeries, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
              { x: new Date(2000, 0, 1), y: 0.61, y1: 0.03, y2: 0.48, y3: 0.23 },
              { x: new Date(2001, 0, 1), y: 0.81, y1: 0.05, y2: 0.53, y3: 0.17 },
              { x: new Date(2002, 0, 1), y: 0.91, y1: 0.06, y2: 0.57, y3: 0.17 },
              { x: new Date(2003, 0, 1), y: 1, y1: 0.09, y2: 0.61, y3: 0.20 },
              { x: new Date(2004, 0, 1), y: 1.19, y1: 0.14, y2: 0.63, y3: 0.23 },
              { x: new Date(2005, 0, 1), y: 1.47, y1: 0.20, y2: 0.64, y3: 0.36 },
              { x: new Date(2006, 0, 1), y: 1.74, y1: 0.29, y2: 0.66, y3: 0.43 },
              { x: new Date(2007, 0, 1), y: 1.98, y1: 0.46, y2: 0.76, y3: 0.52 },
              { x: new Date(2008, 0, 1), y: 1.99, y1: 0.64, y2: 0.77, y3: 0.72 },
              { x: new Date(2009, 0, 1), y: 1.70, y1: 0.75, y2: 0.55, y3: 1.29 },
              { x: new Date(2010, 0, 1), y: 1.48, y1: 1.06, y2: 0.54, y3: 1.38 },
              { x: new Date(2011, 0, 1), y: 1.38, y1: 1.25, y2: 0.57, y3: 1.82 },
              { x: new Date(2012, 0, 1), y: 1.66, y1: 1.55, y2: 0.61, y3: 2.16 },
              { x: new Date(2013, 0, 1), y: 1.66, y1: 1.55, y2: 0.67, y3: 2.51 },
              { x: new Date(2014, 0, 1), y: 1.67, y1: 1.65, y2: 0.67, y3: 2.61 }
        ],
        primaryXAxis: {
            valueType: 'DateTime'
        },
         title: "Trend in Sales of Ethical Produce"
    };
  },
  provide: {
    chart: [StackingAreaSeries, DateTime]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* 100% Stacked Area

To render a 100% stacked area series, use series [`type`](../api/chart/series/#type) as `StackingArea100` and inject
`StackingAreaSeries` into the `provide`.

{% tab template="chart/series/area" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StackingArea100' xName='x' yName='y' name='USA'> </e-series>
                <e-series :dataSource='seriesData' type='StackingArea100' xName='x' yName='y1' name='UK'> </e-series>
                <e-series :dataSource='seriesData' type='StackingArea100' xName='x' yName='y2' name='Canada'> </e-series>
                <e-series :dataSource='seriesData' type='StackingArea100' xName='x' yName='y3' name='China'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StackingAreaSeries, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
             { x: new Date(2006, 0, 1), y: 34, y1: 51, y2: 14, y3: 37 },
             { x: new Date(2007, 0, 1), y: 20, y1: 26, y2: 34, y3: 15 },
             { x: new Date(2008, 0, 1), y: 40, y1: 37, y2: 73, y3: 53 },
             { x: new Date(2009, 0, 1), y: 51, y1: 51, y2: 51, y3: 51 },
             { x: new Date(2010, 0, 1), y: 26, y1: 26, y2: 26, y3: 26 },
             { x: new Date(2011, 0, 1), y: 37, y1: 37, y2: 37, y3: 37 },
             { x: new Date(2012, 0, 1), y: 54, y1: 43, y2: 12, y3: 54 },
             { x: new Date(2013, 0, 1), y: 44, y1: 23, y2: 16, y3: 44 },
             { x: new Date(2014, 0, 1), y: 48, y1: 55, y2: 34, y3: 23 }
        ],
        primaryXAxis: {
            valueType: 'DateTime'
        },
         title: "Annual Temperature Comparisone"
    };
  },
  provide: {
    chart: [StackingAreaSeries, DateTime]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* Step Area

To render a step area series, use series [`type`](../api/chart/series/#type) as `StepArea` and inject
`StepAreaSeries` into the `provide`.

{% tab template="chart/series/area" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StepArea' xName='x' yName='y' name='India'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StepAreaSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
    { x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 },
    { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 },
    { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 },
    { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }
        ],
    primaryXAxis: {
            valueType: 'Double',
            title: 'Overs'
        };
    primaryYAxis: {
            title: 'Runs'
        };
    title: 'England - Run Rate';
    };
  },
  provide: {
    chart: [StepAreaSeries]
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

* Stacked Step Area

To render a stacked step area series, use series `type` as `StackingStepArea` and inject
`StackingStepAreaSeries` into the `provide`.

{% tab template="chart/series/area" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container">
            <e-series-collection>
                <e-series :dataSource='dataSource1' type='StackingStepArea' xName='x' yName='y'> </e-series>
                <e-series :dataSource='dataSource2' type='StackingStepArea' xName='x' yName='y'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StackingStepAreaSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      dataSource1: [{ x: 2000, y: 416 }, { x: 2001, y: 490 }, { x: 2002, y: 470 }, { x: 2003, y: 500 },
                { x: 2004, y: 449 }, { x: 2005, y: 470 }, { x: 2006, y: 437 }, { x: 2007, y: 458 },
                { x: 2008, y: 500 }, { x: 2009, y: 473 }, { x: 2010, y: 520 }, { x: 2011, y: 509 }],
      dataSource2: [{ x: 2000, y: 180 }, { x: 2001, y: 240 }, { x: 2002, y: 370 }, { x: 2003, y: 200 },
                { x: 2004, y: 229 }, { x: 2005, y: 210 }, { x: 2006, y: 337 }, { x: 2007, y: 258 },
                { x: 2008, y: 300 }, { x: 2009, y: 173 }, { x: 2010, y: 220 }, { x: 2011, y: 309 }],
    };
  },
  provide: {
    chart: [StackingStepAreaSeries]
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

* Multicolored area

To render a multicolored area series, use the series type as `MultiColoredArea`, and
inject the `MultiColoredAreaSeries` into the `provide`.
The required `segments` of the series can be customized using the `value`, `color`, and `dashArray`.

{% tab template="chart/series/area" %}

```html
<template>
    <div id="app">
         <ejs-chart :title='title'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='MultiColoredArea' xName='x' yName='y' name='England'
                 segmentAxis='X' :segments='segments'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, MultiColoredAreaSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
          { x: 2005, y: 28 }, { x: 2006, y: 25},
          { x: 2007, y: 26 }, { x: 2008, y: 27 },
          { x: 2009, y: 32}, { x: 2010, y: 35 },
          { x: 2011, y: 25 }
          ],
    title: 'England - Run Rate',
    segments: [{
                    value: 2007,
                    color: 'blue'
                }, {
                    value: 2009,
                    color: 'lightgreen'
                }, {
                    color: 'orange'
        }],
    };
  },
  provide: {
    chart: [MultiColoredAreaSeries]
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

* Customization of Area Charts

`fill`, `border` and `dashArray` of all area type series can be customized
using [`fill`](../api/chart/series/#fill),
[`border`](../api/chart/series/#border)
and [`dashArray`](../api/chart/series/#dasharray) properties.

{% tab template="chart/series/area" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Area'xName='x' yName='y' name='Product A'
                fill='green' width=2 dashArray='5,5' :border='border' opacity=0.6> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, AreaSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
             { x: 1900, y: 4 }, { x: 1920, y: 3.0 },{ x: 1940, y: 3.8 },
             { x: 1960, y: 3.4 }, { x: 1980, y: 3.2 }, { x: 2000, y: 3.9 }
        ],
      border:{width:2, color:'Red'},
      title: "Average Sales Comparison"
    };
  },
  provide: {
    chart: [AreaSeries]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

## Column Charts

* Column

To render a column series, use series [`type`](../api/chart/series/#type) as `Column` and inject `ColumnSeries` into the `provide`.

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container":title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data: function() {
    return {
      seriesData: [
             { country: "USA", gold: 50 },
             { country: "China", gold: 40 },
             { country: "Japan", gold: 70 },
             { country: "Australia", gold: 60 },
             { country: "France", gold: 50 },
             { country: "Germany", gold: 40 },
             { country: "Italy", gold: 40 },
             { country: "Sweden", gold: 30 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category]
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

* Range Column

To render a range column series, use series [`type`](../api/chart/series/#type) as `RangeColumn` and inject `RangeColumnSeries`
into the `provide`.

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='RangeColumn'  xName='x' low='low' high='high'></e-series>
                <e-series :dataSource='seriesData2' type='RangeColumn'  xName='x' low='low' high='high'></e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, RangeColumnSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData1: [
             { x: 'Jan', low: 0.7, high: 6.1 }, { x: 'Feb', low: 1.3, high: 6.3 }, { x: 'Mar', low: 1.9, high: 8.5 },
             { x: 'Apr', low: 3.1, high: 10.8 }, { x: 'May', low: 5.7, high: 14.40 }, { x: 'Jun', low: 8.4, high: 16.90 },
             { x: 'Jul', low: 10.6,high: 19.20 }, { x: 'Aug', low: 10.5,high: 18.9 }, { x: 'Sep', low: 8.5, high: 16.1 },
             { x: 'Oct', low: 6.0, high: 12.5 }, { x: 'Nov', low: 1.5, high: 6.9  }, { x: 'Dec', low: 5.1, high: 12.1 }
              ],
         seriesData2: [
             { x: 'Jan', low: 1.7, high: 7.1 }, { x: 'Feb', low: 1.9, high: 7.7 }, { x: 'Mar', low: 1.2, high: 7.5 },
             { x: 'Apr', low: 2.5, high: 9.8 }, { x: 'May', low: 4.7, high: 11.4 }, { x: 'Jun', low: 6.4, high: 14.4 },
             { x: 'Jul', low: 9.6, high: 17.2 }, { x: 'Aug', low: 10.7, high: 17.9 }, { x: 'Sep', low: 7.5, high: 15.1 },
             { x: 'Oct', low: 3.0, high: 10.5 }, { x: 'Nov', low: 1.2, high: 7.9 }, { x: 'Dec', low: 4.1, high: 9.1 }
              ],
        primaryXAxis: {
            title: 'month',
            valueType: 'Category'
        },
      title: "Maximum and minimum Temperature"
    };
  },
  provide: {
    chart: [RangeColumnSeries, Category]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* Stacked Column

To render a stacked column series, use series [`type`](../api/chart/series/#type) as `StackingColumn` and inject
`StackingColumnSeries` into the `provide`.

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StackingColumn' xName='x' yName='y' name='USA'> </e-series>
                <e-series :dataSource='seriesData' type='StackingColumn' xName='x' yName='y1' name='UK'> </e-series>
                <e-series :dataSource='seriesData' type='StackingColumn' xName='x' yName='y2' name='Canada'> </e-series>
                <e-series :dataSource='seriesData' type='StackingColumn' xName='x' yName='y3' name='China'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StackingColumnSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
             { x: '2014', y: 111.1, y1: 76.9, y2: 66.1, y3: 34.1 },
              { x: '2015', y: 127.3, y1: 99.5, y2: 79.3, y3: 38.2 },
              { x: '2016', y: 143.4, y1: 121.7, y2: 91.3, y3: 44.0 },
              { x: '2017', y: 159.9, y1: 142.5, y2: 102.4, y3: 51.6 },
              { x: '2018', y: 175.4, y1: 166.7, y2: 112.9, y3: 61.9 },
              { x: '2019', y: 189.0, y1: 182.9, y2: 122.4, y3: 71.5 },
              { x: '2020', y: 202.7, y1: 197.3, y2: 120.9, y3: 82.0 }
        ],
        primaryXAxis: {
            title: 'Years',
            interval: 1,
            valueType: 'Category'
        },
         title: "Mobile Game Market by Country"
    };
  },
  provide: {
    chart: [StackingColumnSeries, Category]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* 100% Stacked Column

To render a 100% stacked column series, use series [`type`](../api/chart/series/#type) as `StackingColumn100` and
inject `StackingColumnSeries` into the `provide`.

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StackingColumn100' xName='x' yName='y' name='USA'> </e-series>
                <e-series :dataSource='seriesData' type='StackingColumn100' xName='x' yName='y1' name='UK'> </e-series>
                <e-series :dataSource='seriesData' type='StackingColumn100' xName='x' yName='y2' name='Canada'> </e-series>
                <e-series :dataSource='seriesData' type='StackingColumn100' xName='x' yName='y3' name='China'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StackingColumnSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
             { x: '2006', y: 900, y1: 190, y2: 250, y3: 150 },
             { x: '2007', y: 544, y1: 226, y2: 145, y3: 120 },
             { x: '2008', y: 880, y1: 194, y2: 190, y3: 115 },
             { x: '2009', y: 675, y1: 250, y2: 220, y3: 125 },
             { x: '2010', y: 765, y1: 222, y2: 225, y3: 132 },
             { x: '2011', y: 679, y1: 181, y2: 135, y3: 137 },
             { x: '2012', y: 770, y1: 128, y2: 152, y3: 110 },
        ],
        primaryXAxis: {
            title: 'Years',
            interval: 1,
            valueType: 'Category'
        },
         title: "Gross Domestic Product Growth"
    };
  },
  provide: {
    chart: [StackingColumnSeries, Category]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* Stacking Group

You can use the [`stackingGroup`](../api/chart/series/#stackinggroup) property to group the stacked columns and 100% stacked columns.
Columns with same group name are stacked on top of each other.

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StackingColumn' xName='x' yName='y' name='USA' stackingGroup='a'> </e-series>
                <e-series :dataSource='seriesData' type='StackingColumn' xName='x' yName='y1' name='UK' stackingGroup='a'> </e-series>
                <e-series :dataSource='seriesData' type='StackingColumn' xName='x' yName='y2' name='Canada' stackingGroup='b'> </e-series>
                <e-series :dataSource='seriesData' type='StackingColumn' xName='x' yName='y3' name='China' stackingGroup='b'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StackingColumnSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
              { x: '2014', y: 111.1, y1: 76.9, y2: 66.1, y3: 34.1 },
              { x: '2015', y: 127.3, y1: 99.5, y2: 79.3, y3: 38.2 },
              { x: '2016', y: 143.4, y1: 121.7, y2: 91.3, y3: 44.0 },
              { x: '2017', y: 159.9, y1: 142.5, y2: 102.4, y3: 51.6 },
              { x: '2018', y: 175.4, y1: 166.7, y2: 112.9, y3: 61.9 },
              { x: '2019', y: 189.0, y1: 182.9, y2: 122.4, y3: 71.5 },
              { x: '2020', y: 202.7, y1: 197.3, y2: 120.9, y3: 82.0 }
        ],
        primaryXAxis: {
            title: 'Years',
            interval: 1,
            valueType: 'Category'
        },
         title: "Mobile Game Market by Country"
    };
  },
  provide: {
    chart: [StackingColumnSeries, Category]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* Customization of Column Charts

<!-- markdownlint-disable MD013 -->
`fill` and `border` of all column type series can be
customized using [`fill`](../api/chart/series/#fill)) and [`border`](../api/chart/series/#border) properties.
For customizing a specify point, please refer the
[`pointRender`](../api/chart/#pointrender).

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold' fill='red' :border='border'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
             { country: "USA", gold: 50 },
             { country: "China", gold: 40 },
             { country: "Japan", gold: 70 },
             { country: "Australia", gold: 60 },
             { country: "France", gold: 50 },
             { country: "Germany", gold: 40 },
             { country: "Italy", gold: 40 },
             { country: "Sweden", gold: 30 }
              ],
        border: {
            color: 'green',
            width: 2
        },
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

## Bar Charts

* Bar

To render a bar series, use series [`type`](../api/chart/series/#type) as `Bar` and inject `BarSeries` into the `provide`.

{% tab template="chart/series/bar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Bar' xName='x' yName='y' name='India'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, BarSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
             { x: 2006, y: 7.8 }, { x: 2007, y: 7.2},
             { x: 2008, y: 6.8 }, { x: 2009, y: 10.7 },
             { x: 2010, y: 10.8}, { x: 2011, y: 9.8 }
              ],
      title: "Unemployment rate (%)"
    };
  },
  provide: {
    chart: [BarSeries]
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

* Stacked bar

To render a stacked bar series, use series [`type`](../api/chart/series/#type) as `StackingBar` and
inject `StackingBarSeries` into the `provide`.

{% tab template="chart/series/bar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StackingBar' xName='x' yName='y' name='Apple'> </e-series>
                <e-series :dataSource='seriesData' type='StackingBar' xName='x' yName='y1' name='Orange'> </e-series>
                <e-series :dataSource='seriesData' type='StackingBar' xName='x' yName='y2' name='Wastage'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StackingBarSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data: function() {
    return {
      seriesData:[
             { x: 'Jan', y: 6, y1: 6, y2: -1 }, { x: 'Feb', y: 8 , y1: 8, y2: -1.5 },
              { x: 'Mar', y: 12, y1: 11, y2: -2 }, { x: 'Apr', y: 15, y1: 16, y2: -2.5 },
              { x: 'May', y: 20, y1: 21, y2: -3 }, { x: 'Jun', y: 24, y1: 25, y2: -3.5 },
              { x: 'Jul', y: 28, y1: 27, y2: -4 }, { x: 'Aug', y: 32, y1: 31, y2: -4.5 },
              { x: 'Sep', y: 33, y1: 34, y2: -5 }, { x: 'Oct', y: 35, y1: 34, y2: -5.5 },
              { x: 'Nov', y: 40, y1: 41, y2: -6 }, { x: 'Dec', y: 42, y1: 42, y2: -6.5 }
        ],
        primaryXAxis: {
            valueType: 'Category',
            title: 'Months'
        },
         title: "Sales Comparison"
    };
  },
  provide: {
    chart: [StackingBarSeries, Category]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* 100% Stacked Bar

To render a 100% stacked bar series, use series [`type`](../api/chart/series/#type) as `StackingBar100` and
inject `StackingBarSeries` into the `provide`.

{% tab template="chart/series/bar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StackingBar100' xName='x' yName='y' name='Apple'> </e-series>
                <e-series :dataSource='seriesData' type='StackingBar100' xName='x' yName='y1' name='Orange'> </e-series>
                <e-series :dataSource='seriesData' type='StackingBar100' xName='x' yName='y2' name='Wastage'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StackingBarSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data: function() {
    return {
      seriesData:[
             { x: 'Jan', y: 6, y1: 6, y2: -1 }, { x: 'Feb', y: 8 , y1: 8, y2: -1.5 },
              { x: 'Mar', y: 12, y1: 11, y2: -2 }, { x: 'Apr', y: 15, y1: 16, y2: -2.5 },
              { x: 'May', y: 20, y1: 21, y2: -3 }, { x: 'Jun', y: 24, y1: 25, y2: -3.5 },
              { x: 'Jul', y: 28, y1: 27, y2: -4 }, { x: 'Aug', y: 32, y1: 31, y2: -4.5 },
              { x: 'Sep', y: 33, y1: 34, y2: -5 }, { x: 'Oct', y: 35, y1: 34, y2: -5.5 },
              { x: 'Nov', y: 40, y1: 41, y2: -6 }, { x: 'Dec', y: 42, y1: 42, y2: -6.5 }
        ],
        primaryXAxis: {
            valueType: 'Category',
            title: 'Months'
        },
         title: "Sales Comparison"
    };
  },
  provide: {
    chart: [StackingBarSeries, Category]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* Stacking Group

You can use the [`stackingGroup`](../api/chart/series/#stackinggroup) property to group the stacked
bar and 100% stacked bar. Columns with same group name are stacked on top of each other.

{% tab template="chart/series/bar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StackingBar' xName='x' yName='y' name='John' stackingGroup='JohnandAndrew'> </e-series>
                <e-series :dataSource='seriesData' type='StackingBar' xName='x' yName='y1' name='Andrew' stackingGroup='JohnandAndrew'> </e-series>
                <e-series :dataSource='seriesData' type='StackingBar' xName='x' yName='y2' name='Thomas' stackingGroup='ThomasandMichael'> </e-series>
                <e-series :dataSource='seriesData' type='StackingBar' xName='x' yName='y3' name='Thomas' stackingGroup='ThomasandMichael'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StackingBarSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
             { x: 2007, y: 453, y1: 876, y2: 356, y3: 122 }, { x: 2008, y: 354, y1: 564, y2: 876, y3: 444 },
             { x: 2009, y: 282, y1: 242, y2: 898, y3: 222 }, { x: 2010, y: 321, y1: 121, y2: 567, y3: 231 },
             { x: 2011, y: 333, y1: 343, y2: 456, y3: 122 }, { x: 2012, y: 351, y1: 451, y2: 345, y3: 333 },
             { x: 2013, y: 403, y1: 203, y2: 543, y3: 354 }, { x: 2014, y: 421, y1: 431, y2: 654, y3: 100 }
        ],
         title: "Sales by year"
    };
  },
  provide: {
    chart: [StackingBarSeries, Category]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* Customization of Bar Charts

`fill` and `border` of all bar type series can be
customized using [`fill`](../api/chart/series/#fill) and [`border`](../api/chart/series/#border).
For customizing a specify point, please refer the [`pointRender`](../api/chart/#pointrender).

{% tab template="chart/series/bar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Bar' xName='x' yName='y' name='India' fill='red' :border='border'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, BarSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
             { x: 2006, y: 7.8 }, { x: 2007, y: 7.2},
             { x: 2008, y: 6.8 }, { x: 2009, y: 10.7 },
             { x: 2010, y: 10.8}, { x: 2011, y: 9.8 }
              ],
       border: {
            width: 2,
            color: 'red'
        },
      title: "Unemployment rate (%)"
    };
  },
  provide: {
    chart: [BarSeries]
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

## Scatter Charts

To render a scatter series, use series [`type`](../api/chart/series/#type) as `Scatter` and inject `ScatterSeries` into the `provide`.

{% tab template="chart/series/scatter" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container">
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Scatter' xName='x' yName='y' name='Male' opacity=0.7> </e-series>
                <e-series :dataSource='seriesData2' type='Scatter' xName='x' yName='y' name='Female' opacity=0.7> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ScatterSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1: Object[] = [];
let series2: Object[] = [];
let point1: Object;
let value: number = 80;
let value1: number = 70;
let i: number;
for (i = 1; i < 50; i++) {
    if (Math.random() > 0.5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    value = value < 60 ? 60 : value > 90 ? 90 : value;
    point1 = { x: 120 + (i / 2), y: value.toFixed(1) };
    series1.push(point1);
}
for (i = 1; i < 50; i++) {
    if (Math.random() > 0.5) {
        value1 += Math.random();
    } else {
        value1 -= Math.random();
    }
    value1 = value1 < 60 ? 60 : value1 > 90 ? 90 : value1;
    point1 = { x: 120 + (i / 2), y: value1.toFixed(1) };
    series2.push(point1);
}

export default {
  data() {
    return {
      seriesData1: series1,
      seriesData2: series2
    };
  },
  provide: {
    chart: [ScatterSeries]
  },
};
</script>
<style>
  #container {
   height: 350px;
 }
</style>
```

{% endtab %}

<!-- markdownlint-disable MD018 -->

## Bubble Chart

To render a bubble series, use series [`type`](../api/chart/series/#type) as `Bubble` and inject `BubbleSeries` into the `provide`.

{% tab template="chart/series/bubble" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container">
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Bubble' size='size' xName='x' yName='y' name='pound'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, BubbleSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData1:  [
        { x: 92.2, y: 7.8, size: 1.347, text: 'China' },
        { x: 74, y: 6.5, size: 1.241, text: 'India' },
        { x: 90.4, y: 6.0, size: 0.238, text: 'Indonesia' },
        { x: 99.4, y: 2.2, size: 0.312, text: 'US' },
        { x: 88.6, y: 1.3, size: 0.197, text: 'Brazil' },
        { x: 99, y: 0.7, size: 0.0818, text: 'Germany' },
        { x: 72, y: 2.0, size: 0.0826, text: 'Egypt' },
        { x: 99.6, y: 3.4, size: 0.143, text: 'Russia' },
        { x: 99, y: 0.2, size: 0.128, text: 'Japan' },
        { x: 86.1, y: 4.0, size: 0.115, text: 'Mexico' },
        { x: 92.6, y: 6.6, size: 0.096, text: 'Philippines' },
        { x: 61.3, y: 14.5, size: 0.162, text: 'Nigeria' }]
    };
  },
  provide: {
    chart: [BubbleSeries]
  },
};
</script>
<style>
  #container {
   height: 350px;
 }
</style>
```

{% endtab %}

* Bubble Size Mapping

`size` property can be used to map the size value specified in data source.

{% tab template="chart/series/bubble" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container">
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Bubble' size='size' xName='x' yName='y' name='pound'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, BubbleSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData1:  [
        { x: 92.2, y: 7.8, size: 1.347, text: 'China' },
        { x: 74, y: 6.5, size: 1.241, text: 'India' },
        { x: 90.4, y: 6.0, size: 0.238, text: 'Indonesia' },
        { x: 99.4, y: 2.2, size: 0.312, text: 'US' },
        { x: 88.6, y: 1.3, size: 0.197, text: 'Brazil' },
        { x: 99, y: 0.7, size: 0.0818, text: 'Germany' },
        { x: 72, y: 2.0, size: 0.0826, text: 'Egypt' },
        { x: 99.6, y: 3.4, size: 0.143, text: 'Russia' },
        { x: 99, y: 0.2, size: 0.128, text: 'Japan' },
        { x: 86.1, y: 4.0, size: 0.115, text: 'Mexico' },
        { x: 92.6, y: 6.6, size: 0.096, text: 'Philippines' },
        { x: 61.3, y: 14.5, size: 0.162, text: 'Nigeria' }]
    };
  },
  provide: {
    chart: [BubbleSeries]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}