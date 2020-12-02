---
title: "Funnel | Vue "

component: "Accumulation Chart"

description: "The funnel chart displays series value as progressively decreasing amount to hundred percent in total"
---

# Funnel Chart

To render a funnel series, use the series [`type`](../api/accumulation-chart/accumulationSeriesModel/#type) as `Funnel` and
inject, the `FunnelSeries` module  into the `provide`.

{% tab template="chart/series/funnel" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container">
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' type='Funnel' xName='x' yName='y'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, FunnelSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: 'Renewed', y: 18.20, text: 'Renewed 18.20%' },
                { x: 'Subscribe', y: 27.3, text: 'Subscribe 27.3%' },
                { x: 'Support', y: 55.9, text: 'Support 55.9%' },
                { x: 'Downloaded', y: 76.8, text: 'Downloaded 76.8%' },
                { x: 'Visited', y: 100, text: 'Visited 100%' }
            ]
    };
  },
  provide: {
     accumulationchart: [FunnelSeries]
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

## Size

The size of the funnel chart can be customized by using the  `width` and `height` properties.

{% tab template="chart/series/funnel" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container">
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' type='Funnel' xName='x' yName='y' width='60%'  height='80%'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, FunnelSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: 'Renewed', y: 18.20, text: 'Renewed 18.20%' },
                { x: 'Subscribe', y: 27.3, text: 'Subscribe 27.3%' },
                { x: 'Support', y: 55.9, text: 'Support 55.9%' },
                { x: 'Downloaded', y: 76.8, text: 'Downloaded 76.8%' },
                { x: 'Visited', y: 100, text: 'Visited 100%' }
            ]
    };
  },
  provide: {
     accumulationchart: [FunnelSeries]
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

## Neck Size

The funnel's neck size can be customized by using the `neckWidth` and `neckHeight` properties.

{% tab template="chart/series/funnel" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container">
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' type='Funnel' xName='x' yName='y' :neckWidth='neckWidth'
             :neckHeight='neckHeight'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, FunnelSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: 'Renewed', y: 18.20, text: 'Renewed 18.20%' },
                { x: 'Subscribe', y: 27.3, text: 'Subscribe 27.3%' },
                { x: 'Support', y: 55.9, text: 'Support 55.9%' },
                { x: 'Downloaded', y: 76.8, text: 'Downloaded 76.8%' },
                { x: 'Visited', y: 100, text: 'Visited 100%' }
            ],
            neckWidth: '25%', neckHeight:'5%'
    };
  },
  provide: {
     accumulationchart: [FunnelSeries]
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

## Gap between the segments

Funnel chart provides options to customize the space between the segments by using the `gapRatio` property of the
series. It ranges from 0 to 1.

{% tab template="chart/series/funnel" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container">
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' type='Funnel' xName='x' yName='y' :gapRatio='gapRatio'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, FunnelSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: 'Renewed', y: 18.20, text: 'Renewed 18.20%' },
                { x: 'Subscribe', y: 27.3, text: 'Subscribe 27.3%' },
                { x: 'Support', y: 55.9, text: 'Support 55.9%' },
                { x: 'Downloaded', y: 76.8, text: 'Downloaded 76.8%' },
                { x: 'Visited', y: 100, text: 'Visited 100%' }
            ],
            gapRatio: 0.08
    };
  },
  provide: {
     accumulationchart: [FunnelSeries]
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

## Explode

Points can be exploded on mouse click by setting the `explode` property to true. You can also explode the point
on load using `explodeIndex`. Explode distance can be set by using `explodeOffset` property.

{% tab template="chart/series/funnel" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container">
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' type='Funnel' xName='x' yName='y' explode=true
                 explodeOffset='10' :explodeIndex='explodeIndex'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, FunnelSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: 'Renewed', y: 18.20, text: 'Renewed 18.20%' },
                { x: 'Subscribe', y: 27.3, text: 'Subscribe 27.3%' },
                { x: 'Support', y: 55.9, text: 'Support 55.9%' },
                { x: 'Downloaded', y: 76.8, text: 'Downloaded 76.8%' },
                { x: 'Visited', y: 100, text: 'Visited 100%' }
            ],
            explodeIndex:3
    };
  },
  provide: {
     accumulationchart: [FunnelSeries]
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

## Smart Data Label

It provides the data label smart arrangement of the funnel and pyramid series. The overlap data label will be placed on left side of the funnel/pyramid series.

{% tab template="chart/series/funnel" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :legendSettings="legendSettings" :title="title" :tooltip="tooltip" :load="load" :resized="resized" >
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' type='Funnel' xName='x' yName='y' neckWidth='15%'
            neckHeight='18%' name='2017 Population' explode="false" :dataLabel="dataLabel"> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, AccumulationLegend, FunnelSeries, AccumulationTooltip, AccumulationDataLabel,
IAccLoadedEventArgs, IAccResizeEventArgs } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
        { 'x': 'China', y: 1409517397, text: 'China' },
        { 'x': 'India', y: 1339180127, text: 'India' },
        { 'x': 'United States', y: 324459463, text: 'United States' },
        { 'x': 'Indonesia', y: 263991379, text: 'Indonesia' },
        { 'x': 'Brazil', y: 209288278, text: 'Brazil' },
        { 'x': 'Pakistan', y: 197015955, text: 'Pakistan' },
        { 'x': 'Nigeria', y: 190886311, text: 'Nigeria' },
        { 'x': 'Bangladesh', y: 164669751, text: 'Bangladesh' },
        { 'x': 'Russia', y: 143989754, text: 'Russia' },
        { 'x': 'Mexico', y: 129163276, text: 'Mexico' },
        { 'x': 'Japan', y: 127484450, text: ' Japan' },
        { 'x': 'Ethiopia', y: 104957438, text: 'Ethiopia' },
        { 'x': 'Philippines', y: 104918090, text: 'Philippines' },
        { 'x': 'Egypt', y: 97553151, text: 'Egypt' },
        { 'x': 'Vietnam', y: 95540800, text: 'Vietnam' },
        { 'x': 'Germany', y: 82114224, text: 'Germany' }],

        legendSettings: {visible: false},
        title: 'Top population countries in the world 2017',
        tooltip: { enable: true, format: '${point.x} : <b>${point.y}</b>' },
        dataLabel: {
                visible: true, position: 'Outside',
                connectorStyle: { length: '6%' }, name: 'text',
        },
    };
  },
  provide: {
     accumulationchart: [FunnelSeries, AccumulationTooltip, AccumulationDataLabel, AccumulationLegend]
  },
  methods: {
    load: function(args) {
            if (args.accumulation.availableSize.width < args.accumulation.availableSize.height) {
                args.accumulation.series[0].width = '80%';
                args.accumulation.series[0].height = '70%';
            }
        },
        resized: function(args) {
            let bounds: ClientRect = document.getElementById('container').getBoundingClientRect();
            if (bounds.width < bounds.height) {
                args.accumulation.series[0].width = '80%';
                args.accumulation.series[0].height = '70%';
            } else {
                args.accumulation.series[0].width = '60%';
                args.accumulation.series[0].height = '80%';
            }
        },
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

Individual points can be customized using the `pointRender` event.

{% tab template="chart/series/funnel" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :pointRender='onPointRender'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' type='Funnel' xName='x' yName='y'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, FunnelSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: 'Renewed', y: 18.20, text: 'Renewed 18.20%' },
                { x: 'Subscribe', y: 27.3, text: 'Subscribe 27.3%' },
                { x: 'Support', y: 55.9, text: 'Support 55.9%' },
                { x: 'Downloaded', y: 76.8, text: 'Downloaded 76.8%' },
                { x: 'Visited', y: 100, text: 'Visited 100%' }
            ]
    };
  },
  provide: {
     accumulationchart: [FunnelSeries]
  },
  methods: {
    onPointRender: function (args) {
        if ((args.point.x as string).indexOf('Downloaded') > -1) {
            args.fill = '#f4bc42';
        }
        else {
            args.fill = '#597cf9';
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

## See Also

* [Data label](./data-label/)
* [Grouping](./grouping/)