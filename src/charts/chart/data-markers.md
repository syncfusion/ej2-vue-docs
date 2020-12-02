---
title: " Chart Marker | Vue "

component: "Chart"

description: "Data markers are used to provide information about the data points in the series. You can add a shape to adorn each data point."
---

# Data Markers

Data markers are used to provide information about the data points in the series. You can add a shape to adorn
each data point.

<!-- markdownlint-disable MD036 -->

## Marker

<!-- markdownlint-disable MD036 -->

Markers can be added to the points by enabling the [`visible`](../api/chart/markerSettings/#visible)
option of the marker property.

{% tab template="chart/data-marker/marker" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='December 2007'
                :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: 'WW', y: 12, y1: 22, y2: 38.3, y3: 50 },
              { x: 'EU', y: 9.9, y1: 26, y2: 45.2, y3: 63.6 },
              { x: 'APAC', y: 4.4, y1: 9.3, y2: 18.2, y3: 20.9 },
              { x: 'LATAM', y: 6.4, y1: 28, y2: 46.7, y3: 65.1 },
              { x: 'MEA', y: 30, y1: 45.7, y2: 61.5, y3: 73 },
              { x: 'NA', y: 25.3, y1: 35.9, y2: 64, y3: 81.4 }
              ],
        primaryXAxis: {
            valueType: 'Category', interval: 1
        },
       marker: {
            visible: true,
                },
      title: "FB Penetration of Internet Audience"
    };
  },
  provide: {
    chart: [LineSeries, Category]
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

## Shape

Markers can be assigned with different shapes such as Rectangle, Circle, Diamond etc using the `shape`property.

{% tab template="chart/data-marker/marker" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='December 2007'
                :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: 'WW', y: 12, y1: 22, y2: 38.3, y3: 50 },
              { x: 'EU', y: 9.9, y1: 26, y2: 45.2, y3: 63.6 },
              { x: 'APAC', y: 4.4, y1: 9.3, y2: 18.2, y3: 20.9 },
              { x: 'LATAM', y: 6.4, y1: 28, y2: 46.7, y3: 65.1 },
              { x: 'MEA', y: 30, y1: 45.7, y2: 61.5, y3: 73 },
              { x: 'NA', y: 25.3, y1: 35.9, y2: 64, y3: 81.4 }
              ],
        primaryXAxis: {
            valueType: 'Category', interval: 1
        },
       marker: {
           visible: true, width: 10, height: 10, shape: 'Diamond'
                },
      title: "FB Penetration of Internet Audience"
    };
  },
  provide: {
    chart: [LineSeries, Category]
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

>Note : To know more about the marker shape type refer the [`shape`](../api/chart/markerSettings/#shape).

## Images

Apart from the shapes, you can also add custom images to mark the data point using the
[`imageUrl`](../api/chart/markerSettings/#imageurl) property.

{% tab template="chart/data-marker/marker" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='December 2007'
                :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: 'WW', y: 12, y1: 22, y2: 38.3, y3: 50 },
              { x: 'EU', y: 9.9, y1: 26, y2: 45.2, y3: 63.6 },
              { x: 'APAC', y: 4.4, y1: 9.3, y2: 18.2, y3: 20.9 },
              { x: 'LATAM', y: 6.4, y1: 28, y2: 46.7, y3: 65.1 },
              { x: 'MEA', y: 30, y1: 45.7, y2: 61.5, y3: 73 },
              { x: 'NA', y: 25.3, y1: 35.9, y2: 64, y3: 81.4 }
              ],
        primaryXAxis: {
            valueType: 'Category', interval: 1
        },
       marker: {
           visible: true,
           width: 10, height: 10, shape: 'Image',
           imageUrl:'./sun_annotation.png'
                },
      title: "FB Penetration of Internet Audience"
    };
  },
  provide: {
    chart: [LineSeries, Category]
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

Marker's color and border can be customized using `fill` and `border` properties.

{% tab template="chart/data-marker/marker" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='December 2007'
                :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: 'WW', y: 12, y1: 22, y2: 38.3, y3: 50 },
              { x: 'EU', y: 9.9, y1: 26, y2: 45.2, y3: 63.6 },
              { x: 'APAC', y: 4.4, y1: 9.3, y2: 18.2, y3: 20.9 },
              { x: 'LATAM', y: 6.4, y1: 28, y2: 46.7, y3: 65.1 },
              { x: 'MEA', y: 30, y1: 45.7, y2: 61.5, y3: 73 },
              { x: 'NA', y: 25.3, y1: 35.9, y2: 64, y3: 81.4 }
              ],
        primaryXAxis: {
            valueType: 'Category', interval: 1
        },
       marker: { visible: true,  fill: 'Red', height: 10, width: 10,
                    border:{width: 2, color: 'blue'} },
      title: "FB Penetration of Internet Audience"
    };
  },
  provide: {
    chart: [LineSeries, Category]
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

## Customizing Specific Point

You can also customize the specific marker and label using
[`pointRender`](../api/chart/iPointRenderEventArgs/) event.
`pointRender` event allows you to change the shape, color and border for a point.

{% tab template="chart/data-marker/marker" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :pointRender='pointRender'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='December 2007'
                :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: 'WW', y: 12, y1: 22, y2: 38.3, y3: 50 },
              { x: 'EU', y: 9.9, y1: 26, y2: 45.2, y3: 63.6 },
              { x: 'APAC', y: 4.4, y1: 9.3, y2: 18.2, y3: 20.9 },
              { x: 'LATAM', y: 6.4, y1: 28, y2: 46.7, y3: 65.1 },
              { x: 'MEA', y: 30, y1: 45.7, y2: 61.5, y3: 73 },
              { x: 'NA', y: 25.3, y1: 35.9, y2: 64, y3: 81.4 }
              ],
        primaryXAxis: {
            valueType: 'Category', interval: 1
        },
       marker: { visible: true, height: 10, width: 10 },
      title: "FB Penetration of Internet Audience"
    };
  },
  provide: {
    chart: [LineSeries, Category]
  },
   methods: {
      pointRender: function(args) {
      if(args.point.index === 3) {
         args.fill = 'red'
        }
  }
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