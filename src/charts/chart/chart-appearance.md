---
title: " Chart Appearance | Vue "

component: "Chart"

description: "We can customize chart appearance by using color palette, point level customization, chart area cutomization, title and margin customizations."
---

# Appearance

## Custom Color Palette

You can customize the default color of series or points by providing a custom color palette of your choice by
using the [`palettes`](../api/chart/chartModel/#palettes) property.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'
         :palettes='palettes'>
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
          primaryYAxis:
        {
            minimum: 0, maximum: 80,
           interval: 20, title: 'Medals',
           labelFormat: '${value}K'
        },
      palettes: ["#E94649", "#F6B53F", "#6FAAB0", "#C4C24A"],
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

## Point Level Customization

Marker, datalabel and fill color of each data point can be customized with
[`pointRender`](../api/chart/iPointRenderEventArgs/) and
[`textRender`](../api/chart/iTextRenderEventArgs/) event.

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :pointRender='pointRender'>
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
            interval: 20, title: 'Medals'
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category]
  },
   methods: {
      pointRender: function(args) {
      var seriesColor = ['#00bdae', '#404041', '#357cd2', '#e56590', '#f8b883',
                '#70ad47', '#dd8abd', '#7f84e8', '#7bb4eb', '#ea7a57'];
        args.fill = seriesColor[args.point.index];
    },
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

<!-- markdownlint-disable MD036 -->

## Chart Area Customization

<!-- markdownlint-disable MD036 -->

* Customize the Chart Background

<!-- markdownlint-disable MD013 -->
Using [`background`](../api/chart/chartModel/#background) and [`border`](../api/chart/chartModel/#border) properties, you can change the background color and border of the chart.

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container"  :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' background='skyblue' :border='border'>
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
          primaryYAxis: {
            minimum: 0, maximum: 80,
            interval: 20, title: 'Medals'
        },
      border: {color: "#FF0000", width: 2},
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

* Chart Margin

You can set margin for chart from its container through [`margin`](../api/chart/margin/) property.

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' background='skyblue' :border='border'
         :margin='margin'>
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
            interval: 20, title: 'Medals'
        },
      border: {color: "#FF0000", width: 2},
      margin: { left: 40, right: 40, top: 40, bottom: 40 },
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

* Chart Area Background

The chart area background can be customized by using the [`background`](../api/chart/chartArea/#background)
property in the [`chartArea`](../api/chart/chartArea/).

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' background='skyblue' :chartArea='chartArea'>
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
          primaryYAxis: {
            minimum: 0, maximum: 80,
            interval: 20, title: 'Medals'
        },
      chartArea: {
        //background for Chart area
        background: "skyblue"
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

## Animation

You can customize animation for a particular series using [`animation`](../api/chart/animationModel/) property. You can enable or disable animation of the series using `enable` property, `duration` specifies the duration of an animation and `delay` allows us to start the animation at desire time.

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' background='skyblue'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold'
                :border='border' :animation='animation'> </e-series>
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
          primaryYAxis: {
            minimum: 0, maximum: 80,
            interval: 20, title: 'Medals'
        },
        border:{ width: 2, color: 'grey'},
        //Animation for chart series
        animation:{
            enable: true,
            duration: 2000,
            delay: 200
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

### Fluid Animation

Fluid animation used to animate series with updated dataSource continues animation rather than animation whole series. You can customize animation for a particular series using [`animate`] method.

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :tooltip='tooltip' :chartArea='chartArea'
         :legendSettings='legendSettings' :loaded='loaded'>
            <e-series-collection>
                <e-series :dataSource='seriesData' :marker='marker' type='Column' xName='x' yName='y' name='Tiger' width='1' :cornerRadius="cornerRadius"> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import {  ChartPlugin,
  ColumnSeries,
  Category,
  DataLabel,
  Tooltip,
  Legend } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);
let count = 0;
let datasource1 = [
  { x: 'Egg', y: 206 },
  { x: 'Fish', y: 123 },
  { x: 'Misc', y: 48 },
  { x: 'Tea', y: 240 },
  { x: 'Fruit', y: 170 }
];
let datasource2 = [
 { x: 'Egg', y: 86 },
 { x: 'Fish', y: 173 },
 { x: 'Misc', y: 188 },
 { x: 'Tea', y: 109 },
 { x: 'Fruit', y: 100 }

];
let datasource3 = [
  { x: 'Egg', y: 156 },
  { x: 'Fish', y: 33 },
  { x: 'Misc', y: 260 },
  { x: 'Tea', y: 200 },
 { x: 'Fruit', y: 30 }

];
export default {
  data() {
    return {
      seriesData: [
                    { x: 'Egg', y: 106 },
                    { x: "Fish", y: 103 },
                    { x: "Misc", y: 198 },
                    { x: "Tea", y: 189 },
                    { x: "Fruit", y: 250 }
              ],
        primaryXAxis: {
              valueType: "Category",
              interval: 1,
              majorGridLines: { width: 0 },
              tickPosition: "Inside",
              labelPosition: "Inside",
              labelStyle: { color: "#ffffff" }
        },
          primaryYAxis: {
            minimum: 0,
            maximum: 300,
            interval: 50,
            majorGridLines: { width: 0 },
            majorTickLines: { width: 0 },
            lineStyle: { width: 0 },
            labelStyle: { color: "transparent" }
        },
          legendSettings: { visible: false },
          tooltip: {
            enable: false
        },
        cornerRadius: {
          bottomLeft: 10,
          bottomRight: 10,
          topLeft: 10,
          topRight: 10
        },
        marker: {
        dataLabel: {
          visible: true,
          position: "Top",
        }
        },
         chartArea: { border: { width: 0 } },
        title: "Trade in Food Groups"
    };
  },
  provide: {
    chart: [ColumnSeries, Legend, DataLabel, Category, Tooltip]
  }
  methods: {
     loaded: function(args) {
      this.$refs.chart.ej2Instances.loaded = null;
      let columninterval = setInterval(() => {
        if (document.getElementById('container')) {
        if (count === 0) {
          this.$refs.chart.ej2Instances.series[0].dataSource = datasource1;
          this.$refs.chart.ej2Instances.animate();
          count++;
        } else if (count === 1) {
          this.$refs.chart.ej2Instances.series[0].dataSource = datasource2;
          this.$refs.chart.ej2Instances.animate();
          count++;
        } else if (count === 2) {
          this.$refs.chart.ej2Instances.series[0].dataSource = datasource3;
          this.$refs.chart.ej2Instances.animate();
          count = 0;
        }
        } else {
          clearInterval(columninterval)
        }
      }, 2000);
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

## Chart Title

Chart can be given a title using [`title`](../api/chart/chartModel/#title) property, to show the information about the data plotted.

{% tab template="chart/chart-title" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :titleStyle='titleStyle'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StepLine' xName='x' yName='y' width=2 name='China' :marker='marker'> </e-series>
                <e-series :dataSource='seriesData'  type='StepLine' xName='x' yName='y1' width=2 name='Australia' :marker='marker'> </e-series>
                <e-series :dataSource='seriesData'  type='StepLine' xName='x' yName='y2' width=2 name='Japan' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StepLineSeries, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: new Date(1975, 0, 1), y: 16, y1: 10, y2: 4.5 },
                { x: new Date(1980, 0, 1), y: 12.5, y1: 7.5, y2: 5 },
                { x: new Date(1985, 0, 1), y: 19, y1: 11, y2: 6.5 },
                { x: new Date(1990, 0, 1), y: 14.4, y1: 7, y2: 4.4 },
                { x: new Date(1995, 0, 1), y: 11.5, y1: 8, y2: 5 },
                { x: new Date(2000, 0, 1), y: 14, y1: 6, y2: 1.5 },
                { x: new Date(2005, 0, 1), y: 10, y1: 3.5, y2: 2.5 },
                { x: new Date(2010, 0, 1), y: 16, y1: 7, y2: 3.7 }
              ],
        primaryXAxis: {
            title: 'Years',
            lineStyle: { width: 0 },
            labelFormat: 'y',
            intervalType: 'Years',
            valueType: 'DateTime',
            edgeLabelPlacement: 'Shift'
        },
          primaryYAxis: {
            title: 'Percentage (%)',
            minimum: 0, maximum: 20, interval: 2,
            labelFormat: '{value}%'
        },
       marker: {
                    visible: true, width: 10, height: 10
                },
      title: "Unemployment Rates 1975-2010",
      titleStyle:{
            fontFamily: "Arial",
            fontStyle: 'italic',
            fontWeight: 'regular',
            color: "#E27F2D",
            size: '23px'
        }
    };
  },
  provide: {
    chart: [StepLineSeries, DateTime]
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

## Chart SubTitle

Chart can be given a subtitle using [`subTitle`](../api/chart/chartModel/#subtitle) property, to show the information about the data plotted.

{% tab template="chart/chart-title" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :subTitle='subTitle' :subTitleStyle='subTitleStyle' :primaryXAxis='primaryXAxis' :axisLabelRender='axisLabelRender'>
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
      title: "Olympic Medals",
      subTitle:'In the year 2014',
      subTitleStyle:{
            fontFamily: "Arial",
            fontStyle: 'italic',
            fontWeight: 'regular',
            color: "#E27F2D"
        }
    };
  },
  provide: {
    chart: [ColumnSeries, Category]
  },
   methods: {
      axisLabelRender: function(args) {
           if(args.text === 'France') {
            args.labelStyle.color = 'Red';
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

* Title wrap

Chart can be given a title using [`title`](../api/chart/chartModel/#title) property, to show the information about the data plotted.

{% tab template="chart/chart-title" %}

```html
<template>
    <div id="app">
         <ejs-chart  id="container" :title='title' :primaryXAxis='primaryXAxis' :titleStyle='titleStyle'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='month' yName='sales' name='Gold'
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
      { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
      { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
      { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
      { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
      { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
      { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
              ],
        primaryXAxis: {
           valueType: 'Category',
        },
      title: "Unemployment Rates 1975-2010",
      marker: {
        visible: true, width: 10, height: 10
     },
     titleStyle:{
             size:'18px', color:'Red', textAlignment: 'Far', textOverflow: 'Wrap'
        }
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