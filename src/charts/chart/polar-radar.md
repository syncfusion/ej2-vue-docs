---
title: " Chart Polar and Radar | Vue "

component: "Chart"

description: "Polar and Radar chart supports different draw types and customization to display the data."
---

# Polar Chart and Radar Chart

## Polar Chart

To render a polar series, use series[`type`](../api/chart/seriesModel/#type) as `Polar` and
inject `PolarSeries`  into the `provide`.

### Draw Types

Polar drawType property is used to change the series plotting type to line, column, area, range column, spline,
scatter, stacking area and stacking column. The default value of drawType is `Line`.

* Line

To render a line draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype) as `Line` and inject
`LineSeries` inject `LineSeries`  into the `provide`.
[`isClosed`](../api/chart/seriesModel/#isclosed) property specifies whether to join start and end point of
 a line series used in polar chart to form a closed path. Default value of isClosed is true.

{% tab template= "chart/series/polar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Polar' xName='x' yName='y' drawType='Line'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, Tooltip, Legend, PolarSeries, Category, LineSeries, RadarSeries} from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
     { x: 2005, y: 28 }, { x: 2006, y: 25 },{ x: 2007, y: 26 },
     { x: 2008, y: 27 }, { x: 2009, y: 32 }, { x: 2010, y: 35 },
     { x: 2011, y: 30 }],
      primaryXAxis: {
          title: 'Year',
          minimum: 2004, maximum: 2012, interval: 1
        },
         primaryYAxis: {
            minimum: 20, maximum: 40, interval: 5,
            title: 'Efficiency',
            labelFormat: '{value}%'
        },
      title: "Efficiency of oil-fired power production"
    };
  },
  provide: {
    chart: [Tooltip, Legend, PolarSeries, Category, LineSeries, RadarSeries]
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

* Spline

To render a spline line draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype) as `Spline`
and inject `SplineSeries` inject `SplineSeries`  into the `provide`.

{% tab template= "chart/series/polar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Polar' xName='x' yName='y' drawType='Spline'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { Tooltip, Legend, PolarSeries, Category, SplineSeries, RadarSeries, ChartPlugin } from "@syncfusion/ej2-vue-charts";

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
    chart: [Tooltip, Legend, PolarSeries, Category, SplineSeries, RadarSeries]
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

* Area

To render a area line draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype) as `Area` and
inject `AreaSeries`  into the `provide`.

{% tab template= "chart/series/polar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Polar' xName='x' yName='y' drawType='Area'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, PolarSeries, Category, AreaSeries } from "@syncfusion/ej2-vue-charts";

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
    chart: [PolarSeries, Category, AreaSeries]
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

* Stacked Area

To render a stacked area draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype) as `StackingArea` and inject `StackingAreaSeries`
into the `provide`.

{% tab template= "chart/series/polar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Polar' xName='x' yName='y' drawType='StackingArea' name='Organic'></e-series>
                <e-series :dataSource='seriesData' type='Polar' xName='x' yName='y1' drawType='StackingArea' name='Fair-trade'></e-series>
                <e-series :dataSource='seriesData' type='Polar' xName='x' yName='y' drawType='StackingArea' name='veg-Alternatives'></e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, PolarSeries, Category, StackingAreaSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
     { x: '2000', y: 0.61, y1: 0.03, y2: 0.48},
    { x: '2001', y: 0.81, y1: 0.05, y2: 0.53 },
    { x: '2002', y: 0.91, y1: 0.06, y2: 0.57 },
    { x: '2003', y: 1, y1: 0.09, y2: 0.61 },
    { x: '2004', y: 1.19, y1: 0.14, y2: 0.63 },
    { x: '2005', y: 1.47, y1: 0.20, y2: 0.64 },
    { x: '2006', y: 1.74, y1: 0.29, y2: 0.66 },
    { x: '2007', y: 1.98, y1: 0.46, y2: 0.76 },
    { x: '2008', y: 1.99, y1: 0.64, y2: 0.77 },
    { x: '2009', y: 1.70, y1: 0.75, y2: 0.55 }
     ],
      primaryXAxis: {
          valueType: 'Category'
        },
      title: "Trend in Sales of Ethical Produce"
    };
  },
  provide: {
    chart: [PolarSeries, Category, StackingAreaSeries]
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

* Column

To render a column draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype) as `Column` and inject `ColumnSeries`
into the `provide`.

{% tab template= "chart/series/polar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Polar' xName='country' yName='gold' drawType='Column' name='Gold'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, PolarSeries, ColumnSeries, Category } from "@syncfusion/ej2-vue-charts";

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
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, PolarSeries]
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

* Stacked Column

To render a stacked column draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype) as `StackingColumn` and inject `StackingColumnSeries`
into the `provide`.

{% tab template= "chart/series/polar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Polar' xName='x' yName='y' drawType='StackingColumn' name='Organic'></e-series>
                <e-series :dataSource='seriesData' type='Polar' xName='x' yName='y1' drawType='StackingColumn' name='Fair-trade'></e-series>
                <e-series :dataSource='seriesData' type='Polar' xName='x' yName='y' drawType='StackingColumn' name='veg-Alternatives'></e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, PolarSeries, Category, StackingColumnSeries } from "@syncfusion/ej2-vue-charts";

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
          valueType: 'Category'
        },
      title: "Trend in Sales of Ethical Produce"
    };
  },
  provide: {
    chart: [PolarSeries, Category, StackingColumnSeries]
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

To render a range column draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype) as `RangeColumn` and inject `RangeColumnSeries`
into the `provide`.

{% tab template= "chart/series/polar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Polar' xName='x' high='high' low='low' drawType='RangeColumn' name='Gold'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, PolarSeries, RangeColumnSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
        { x: 'Jan', low: 0.7, high: 6.1 }, { x: 'Feb', low: 1.3, high: 6.3 }, { x: 'Mar', low: 1.9, high: 8.5 },
        { x: 'Apr', low: 3.1, high: 10.8 }, { x: 'May', low: 5.7, high: 14.40 }, { x: 'Jun', low: 8.4, high: 16.90 },
        { x: 'Jul', low: 10.6,high: 19.20 }, { x: 'Aug', low: 10.5,high: 18.9 }, { x: 'Sep', low: 8.5, high: 16.1 },
        { x: 'Oct', low: 6.0, high: 12.5 }, { x: 'Nov', low: 1.5, high: 6.9  }, { x: 'Dec', low: 5.1, high: 12.1 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Months'
        },
      title: "Maximum and Minimum Temperature"
    };
  },
  provide: {
    chart: [RangeColumnSeries, Category, PolarSeries]
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

* Scatter

To render a scatter draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype) as `Scatter` and
inject `ScatterSeries`  into the `provide`.

{% tab template= "chart/series/polar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Polar' xName='x' yName='y' drawType='Scatter' name='London'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, PolarSeries, Category, ScatterSeries } from "@syncfusion/ej2-vue-charts";

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
    chart: [PolarSeries, Category, ScatterSeries]
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

## Radar Chart

To render a radar series, use series [`type`](../api/chart/seriesModel/#drawtype) as `Radar` and
inject `RadarSeries` into the `provide`.

### Draw Type

* Line

To render a line draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype) as `Line` and inject
`LineSeries` inject `LineSeries`  into the `provide`.
[`isClosed`](../api/chart/seriesModel/#isclosed) property specifies whether to join start and end point of a line series used in polar chart to form a closed path. Default value of isClosed is true.

{% tab template= "chart/series/polar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Radar' xName='x' yName='y' drawType='Line'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, RadarSeries, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
     { x: 2005, y: 28 }, { x: 2006, y: 25 },{ x: 2007, y: 26 },
     { x: 2008, y: 27 }, { x: 2009, y: 32 }, { x: 2010, y: 35 },
     { x: 2011, y: 30 }],
      primaryXAxis: {
          title: 'Year',
          minimum: 2004, maximum: 2012, interval: 1
        },
         primaryYAxis: {
            minimum: 20, maximum: 40, interval: 5,
            title: 'Efficiency',
            labelFormat: '{value}%'
        },
      title: "Efficiency of oil-fired power production"
    };
  },
  provide: {
    chart: [RadarSeries, LineSeries]
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

### Customization

* Start Angle

You can customize the start angle of the polar series using
[`startAngle`](../api/chart/axis/#startangle-number) property. By default, `startAngle` is 0 degree.

{% tab template= "chart/series/polar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Radar' xName='x' yName='y' drawType='Line'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, RadarSeries, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
     { x: 2005, y: 28 }, { x: 2006, y: 25 },{ x: 2007, y: 26 },
     { x: 2008, y: 27 }, { x: 2009, y: 32 }, { x: 2010, y: 35 },
     { x: 2011, y: 30 }],
      primaryXAxis: {
          title: 'Year',
          minimum: 2004, maximum: 2012, interval: 1
        },
         primaryYAxis: {
            minimum: 20, maximum: 40, interval: 5,
            title: 'Efficiency',
            labelFormat: '{value}%'
        },
      title: "Efficiency of oil-fired power production"
    };
  },
  provide: {
    chart: [RadarSeries, LineSeries]
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

* Coefficient in axis

You can customize the radius of the polar series and radar series using
[`coefficient`](../api/chart/axisModel/#coefficient) property. By default, `coefficient` is 100.

{% tab template= "chart/series/polar" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Radar' xName='x' yName='y' drawType='Line'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, RadarSeries, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
     { x: 2005, y: 28 }, { x: 2006, y: 25 },{ x: 2007, y: 26 },
     { x: 2008, y: 27 }, { x: 2009, y: 32 }, { x: 2010, y: 35 },
     { x: 2011, y: 30 }],
      primaryXAxis: {
          title: 'Year',
          minimum: 2004, maximum: 2012, interval: 1
        },
         primaryYAxis: {
            minimum: 20, maximum: 40, interval: 5,
            title: 'Efficiency',
            labelFormat: '{value}%'
        },
      title: "Efficiency of oil-fired power production"
    };
  },
  provide: {
    chart: [RadarSeries, LineSeries]
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

## See Also

* [Data label](./data-labels/)
* [Tooltip](./tool-tip/)
