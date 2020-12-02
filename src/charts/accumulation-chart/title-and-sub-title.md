---
title: "Accumulation Chart Title and subtitle | Vue "

component: "Accumulation Chart"

description: "Accumulation chart title and subtitle represents the title and subtitle for the chart."
---

# Title and Subtitle

## Title

Accumulation Chart can be given a title using [`title`](../api/accumulation-chart/accumulationChartModel/#title) property, to show the information
about the data plotted.

{% tab template="chart/chart-title" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
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

## Title customization

Accumulation Chart can be customizing a title using [`titleStyle`](../api/accumulation-chart/accumulationChartModel/#titlestyle) property, to show the information
about the data plotted.

{% tab template="chart/chart-title" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :titleStyle='titleStyle' :primaryXAxis='primaryXAxis'>
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

## SubTitle

Accumulation Chart can be given a subtitle using [`subTitle`](../api/accumulation-chart/accumulationChartModel/#subtitle) property, to show the information
about the data plotted.

{% tab template="chart/chart-title" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :subTitle='subTitle' :primaryXAxis='primaryXAxis'>
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
      subTitle:'In the year of 2014'
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

## SubTitle Customization

Accumulation Chart can be customizing a subtitle using [`subTitleStyle`](../api/accumulation-chart/accumulationChartModel/#subtitlestyle) property.

{% tab template="chart/chart-title" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :subTitle='subTitle' :subTitleStyle='subTitleStyle' :primaryXAxis='primaryXAxis'>
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
      subTitle:'In the year of 2014',
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
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}
