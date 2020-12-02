---
title: " Chart Axis Customization | Vue "

component: "Chart"

description: "Chart axis contains different customization and types like axis crossing, multiple axis, inversed axis, tick and grid, title customizations"
---

# Axis Customization

## Axis Crossing

An axis can be positioned in the chart area using `crossesAt` and `crossesInAxis` properties. The `crossesAt`
property specifies the values (datetime, numeric, or logarithmic) at which the axis line has to be intersected
with the vertical axis or vice-versa, and the `crossesInAxis` property specifies the axis name with which the
axis line has to be crossed.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
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
           crossesAt : 15
        },
          primaryYAxis:
        {
            crossesAt : 5
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

## Title

You can add a title to the axis using [`title`](../api/chart/axis/#title) property to provide quick
information to the user about the data plotted in the axis.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
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
          primaryYAxis:
        {
           minimum: 0, maximum: 80,
           interval: 20, title: 'Medals',
           labelFormat: '${value}K',
           titleStyle: {
            size: '16px', color: 'grey',
            fontFamily : 'Segoe UI', fontWeight : 'bold'
           }
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

## Tick Lines Customization

You can customize the  `width`, `color` and `size` of the minor and major tick lines, using
[`majorTickLines`](../api/chart/majorTickLines/) and
[`minorTickLines`](../api/chart/minorTickLines/) properties in the axis.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Temperature'> </e-series>
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
                { x: 'Jan', y: 60 }, { x: 'Feb', y: 50 }, { x: 'Mar', y: 64 },
                { x: 'Apr', y: 63 }, { x: 'May', y: 81 }, { x: 'Jun', y: 64 },
                { x: 'Jul', y: 82 }, { x: 'Aug', y: 96 }, { x: 'Sep', y: 78 },
                { x: 'Oct', y: 60 }, { x: 'Nov', y: 58 }, { x: 'Dec', y: 56 }
              ],
        primaryXAxis: {
           valueType: 'Category',
            majorTickLines : {
               color : 'blue',
               width : 5
            },
            minorTickLines : {
               color : 'red',
               width : 0
            }
        },
          primaryYAxis:
        {
           title: 'Temperature (Fahrenheit)',
           majorTickLines : {
              color : 'blue',
              width : 5
           },
           minorTickLines : {
              color : 'red',
              width : 0
           }
        },
      title: "Temperature flow over months"
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

## Grid Lines Customization

You can customize the `width`, `color` and `dashArray` of the minor and major grid lines,
using [`majorGridLines`](../api/chart/minorGridLines/) and
[`minorGridLines`](../api/chart/minorGridLines/) properties in the axis.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Temperature'> </e-series>
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
                { x: 'Jan', y: 60 }, { x: 'Feb', y: 50 }, { x: 'Mar', y: 64 },
                { x: 'Apr', y: 63 }, { x: 'May', y: 81 }, { x: 'Jun', y: 64 },
                { x: 'Jul', y: 82 }, { x: 'Aug', y: 96 }, { x: 'Sep', y: 78 },
                { x: 'Oct', y: 60 }, { x: 'Nov', y: 58 }, { x: 'Dec', y: 56 }
              ],
        primaryXAxis: {
           valueType: 'Category',
            majorTickLines : {
               color : 'blue',
               width : 5
            },
            minorTickLines : {
               color : 'red',
               width : 0
            }
        },
          primaryYAxis:
        {
            majorGridLines : {
              color : 'blue',
              width : 1
           },
           minorGridLines : {
              color : 'red',
              width : 0
           }
        },
      title: "Temperature flow over months"
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

## Multiple Axis

In addition to primary X and Y axis, we can add n number of axis to the chart. Series can be associated with
this axis, by mapping with axis's unique name.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :axes='axes'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Germany'> </e-series>
                 <e-series :dataSource='seriesData' type='Line' xName='x' yName='y1' yAxisName='yAxis' name='Japan'
                 :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, LineSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: 'Jan', y: 15, y1: 33 }, { x: 'Feb', y: 20, y1: 31 }, { x: 'Mar', y: 35, y1: 30 },
                { x: 'Apr', y: 40, y1: 28 }, { x: 'May', y: 80, y1: 29 }, { x: 'Jun', y: 70, y1: 30 },
                { x: 'Jul', y: 65, y1: 33 }, { x: 'Aug', y: 55, y1: 32 }, { x: 'Sep', y: 50, y1: 34 },
                { x: 'Oct', y: 30, y1: 32 }, { x: 'Nov', y: 35, y1: 32 }, { x: 'Dec', y: 35, y1: 31 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
         axes:
        [
            {
            majorGridLines: { width: 0 },
            rowIndex: 1, opposedPosition: true,
            lineStyle: { width: 0 },
            minimum: 24, maximum: 36, interval: 4,
            name: 'yAxis', title: 'Temperature (Celsius)',
            labelFormat: '{value}°C'
            }
        ],
         marker: { visible: true, width: 10, height: 10, border: { width: 2, color: '#F8AB1D' } },
      title: "Weather Condition"
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

## Inversed Axis

<!-- markdownlint-disable MD033 -->

When an axis is inversed, highest value of the axis comes closer to origin and vice versa. To place an axis in inversed manner set this property
 [`isInversed`](../api/chart/axis/#isinversed) to true.

 {% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Years'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
        { x: 2008, y: 15.1 }, { x: 2009, y: 16 }, { x: 2010, y: 21.4 },
        { x: 2011, y: 18 }, { x: 2012, y: 16.2 }, { x: 2013, y: 11 },
        { x: 2014, y: 7.6 }, { x: 2015, y: 1.5 }
              ],
          primaryYAxis:
        {
            isInversed: true
        },
      title: "Exchange Rate"
    };
  },
  provide: {
    chart: [ColumnSeries]
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

## Opposed Position

<!-- markdownlint-disable MD012 -->
To place an axis opposite from its original position, set [`opposedPosition`](../api/chart/axis/#opposedposition)
property of the axis to true.
<!-- markdownlint-disable MD012 -->

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Temperature'> </e-series>
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
                { x: 'Jan', y: 60 }, { x: 'Feb', y: 50 }, { x: 'Mar', y: 64 },
                { x: 'Apr', y: 63 }, { x: 'May', y: 81 }, { x: 'Jun', y: 64 },
                { x: 'Jul', y: 82 }, { x: 'Aug', y: 96 }, { x: 'Sep', y: 78 },
                { x: 'Oct', y: 60 }, { x: 'Nov', y: 58 }, { x: 'Dec', y: 56 }
              ],
        primaryXAxis: {
             valueType: 'Category'
        },
          primaryYAxis: {
           title: 'Temperature (Fahrenheit)',
           opposedPosition: true
        },
      title: "Temperature flow over months"
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


