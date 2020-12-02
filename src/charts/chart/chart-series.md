---
title: " Chart Series | Vue "

component: "Chart"

description: "Chart supports to render collection of series like multiple series or combination series."
---

# Chart Series

## Multiple Series

You can add multiple series to the chart by using [`series`](../api/chart/seriesModel/) property.
The series are rendered in the order as it is added to the series array.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze'> </e-series>
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
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
      animation: { enable: false },
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

## Combination Series

Combination of different types like Line, column etc, can be rendered in a chart.

>Bar series cannot be combined with any other series as the axis orientation is different from other series.

{% tab template="chart/series/combination" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StackingColumn' xName='x' yName='y' name='USA'> </e-series>
                <e-series :dataSource='seriesData' type='StackingColumn' xName='x' yName='y1' name='UK'> </e-series>
                <e-series :dataSource='seriesData' type='StackingColumn' xName='x' yName='y2' name='Canada'> </e-series>
                <e-series :dataSource='seriesData' type='StackingColumn' xName='x' yName='y3' name='China'> </e-series>
                 <e-series :dataSource='seriesData' type='Line' xName='x' yName='y4' name='GDP' :marker='marker' opacity=0.6> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StackingColumnSeries, LineSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
              { x: '2005', y: 1.2, y1: 0.5, y2: 0.7, y3: -0.8, y4: 1.5 },
              { x: '2006', y: 1, y1: 0.5, y2: 1.4, y3: 0, y4: 2.3 },
              { x: '2007', y: 1, y1: 0.5, y2: 1.5, y3: -1, y4: 2 },
              { x: '2008', y: 0.25, y1: 0.35, y2: 0.35, y3: -.35, y4: 0.1 },
              { x: '2009', y: 0.1, y1: 0.9, y2: -2.7, y3: -0.3, y4: -2.7 },
              { x: '2010', y: 1, y1: 0.5, y2: 0.5, y3: -0.5, y4: 1.8 },
              { x: '2011', y: 0.1, y1: 0.25, y2: 0.25, y3: 0, y4: 2 },
              { x: '2012', y: -0.25, y1: -0.5, y2: -0.1, y3: -0.4, y4: 0.4 },
              { x: '2013', y: 0.25, y1: 0.5, y2: -0.3, y3: 0, y4: 0.9 },
              { x: '2014', y: 0.6, y1: 0.6, y2: -0.6, y3: -0.6, y4: 0.4 },
              { x: '2015', y: 0.9, y1: 0.5, y2: 0, y3: -0.3, y4: 1.3 }
        ],
        primaryXAxis: {
            title: 'Years',
            interval: 1,
            labelIntersectAction : 'Rotate45',
            valueType: 'Category'
        },
        marker: { visible: true, width: 10, opacity: 0.6, height: 10 },
         title: "Annual Growth GDP in France"
    };
  },
  provide: {
    chart: [StackingColumnSeries, LineSeries, Category]
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

## Enable Complex Property in Series

By setting `enableComplexProperty` value as `true` in series you can bind complex data to the chart.

{% tab template="chart/series/combination" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='group.x' yName='group.y' name='USA' enableComplexProperty="true"> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='group.x' yName='y' name='UK' enableComplexProperty="true"> </e-series>
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
       seriesData:[
  {group: { x: 'Aaa', y: 10}, y: 20},
  {group: { x: 'Baa', y: 30}, y: 10}
    ],
        primaryXAxis: {
            valueType: 'Category'
        },
        marker: { visible: true, width: 10, opacity: 0.6, height: 10 },
         title: "Annual Growth GDP in France"
    };
  },
  provide: {
    chart: [ColumnSeries, LineSeries, Category]
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