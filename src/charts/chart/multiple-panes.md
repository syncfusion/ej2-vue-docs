---
title: " Chart Multiple-panes | Vue "

component: "Chart"

description: "Chart can be divided multiple rows and columns. Axes are rendering based on row index or column index in pane."
---

# Multiple Panes

Chart area can be divided into multiple panes using [`rows`](../api/chart/row/) and [`columns`](../api/chart/column/).

## Rows

To split the chart area vertically into number of rows, use [`rows`](../api/chart/row/) property of the chart.

* You can allocate space for each row by using the [`height`](../api/chart/row/#height) property. The value can be either in
 percentage or in pixel.
* To associate a vertical axis to a particular row, specify its index to
[`rowIndex`](../api/chart/axis/#rowindex) property of the axis.
* To customize each row’s bottom line, use [`border`](../api/chart/axis/#border) property.

{% tab template="chart/axis/multiple-panes" %}

```html
<template>
    <div id="app">
         <ejs-chart  id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :axes='axes' :rows='rows'>
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
          title: 'Months',
          valueType: 'Category',
          interval: 1
        },
        primaryYAxis: {
        minimum: 0, maximum: 90, interval: 20,
        lineStyle: { width: 0 },
        title: 'Temperature (Fahrenheit)',
        labelFormat: '{value}°F'
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
        rows:[
        {
            height: '50%'
        },{
            height: '50%'
        }
    ],
      marker: { visible: true, width: 10, height: 10, border: { width: 2, color: '#F8AB1D' } },
      title: "Weather Condition"
    };
  },
  provide: {
    chart: [ColumnSeries,LineSeries, Category]
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

For spanning the vertical axis along multiple row, you can use [`span`](../api/chart/axis/#span) property of an axis.

{% tab template="chart/axis/multiple-panes" %}

```html
<template>
    <div id="app">
         <ejs-chart  id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :axes='axes' :rows='rows'>
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
          title: 'Months',
          valueType: 'Category',
          interval: 1
        },
        primaryYAxis: {
        minimum: 0, maximum: 90, interval: 10,
        lineStyle: { width: 0 },
        title: 'Temperature (Fahrenheit)',
        labelFormat: '{value}°F',
        //Span for chart axis
        span: 2
         },
         axes:
        [
            {
            majorGridLines: { width: 0 },
            rowIndex: 1, opposedPosition: true,
            lineStyle: { width: 0 },
            minimum: 24, maximum: 36, interval: 2,
            name: 'yAxis', title: 'Temperature (Celsius)',
            labelFormat: '{value}°C'
            }
        ],
        rows:[
        {
            height: '50%'
        },{
            height: '50%'
        }
    ],
      marker: { visible: true, width: 10, height: 10, border: { width: 2, color: '#F8AB1D' } },
      title: "Weather Condition"
    };
  },
  provide: {
    chart: [ColumnSeries,LineSeries, Category]
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

## Columns

To split the chart area horizontally into number of columns, use [`columns`](../api/chart/column/) property of the chart.

* You can allocate space for each column by using the [`width`](../api/chart/column/#width)

property. The given width can be either in percentage or in pixel.

* To associate a horizontal axis to a particular column, specify its index to

[`columnIndex`](../api/chart/axis/#columnindex) property of the axis.

* To customize each column’s bottom line, use [`border`](../api/chart/column/#border)

property.

{% tab template="chart/axis/multiple-panes" %}

```html
<template>
    <div id="app">
         <ejs-chart  id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :axes='axes' :columns='columns'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Germany'> </e-series>
                 <e-series :dataSource='seriesData' type='Line' xName='x' yName='y1' xAxisName='xAxis' name='Japan'
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
           title: 'Months',
           valueType: 'Category',
           interval: 1
        },
        primaryYAxis: {
            minimum: 0, maximum: 90, interval: 20,
            lineStyle: { width: 0 },
            title: 'Temperature (Fahrenheit)',
            labelFormat: '{value}°F'
        },
        columns:[
        {
            width: '50%'
        },{
            width: '50%'
        }
    ],
    axes:[
        {
            majorGridLines: { width: 0 },
            columnIndex: 1,
            valueType: 'Category',
            lineStyle: { width: 0 },
            name: 'xAxis'
        }
    ],
      marker: { visible: true, width: 10, height: 10, border: { width: 2, color: '#F8AB1D' } },
      title: "Weather Condition"
    };
  },
  provide: {
    chart: [ColumnSeries,LineSeries, Category]
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

For spanning the horizontal axis along multiple column, you can use [`span`](../api/chart/axis/#span) property of an axis.

{% tab template="chart/axis/multiple-panes" %}

```html
<template>
    <div id="app">
         <ejs-chart  id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :axes='axes' :columns='columns'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Germany'> </e-series>
                 <e-series :dataSource='seriesData' type='Line' xName='x' yName='y1' xAxisName='xAxis' name='Japan'
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
           title: 'Months',
           valueType: 'Category',
           interval: 1,
           span: 2
        },
        primaryYAxis: {
            minimum: 0, maximum: 90, interval: 20,
            lineStyle: { width: 0 },
            title: 'Temperature (Fahrenheit)',
            labelFormat: '{value}°F'
        },
        columns:[
        {
            width: '50%'
        },{
            width: '50%'
        }
    ],
    axes:[
        {
            majorGridLines: { width: 0 },
            columnIndex: 1,
            valueType: 'Category',
            lineStyle: { width: 0 },
            name: 'xAxis'
        }
    ],
      marker: { visible: true, width: 10, height: 10, border: { width: 2, color: '#F8AB1D' } },
      title: "Weather Condition"
    };
  },
  provide: {
    chart: [ColumnSeries,LineSeries, Category]
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
