---
title: "Pyramid | Vue "

component: "Accumulation Chart"

description: "The pyramid chart displays series value as progressively decreasing amount to hundred percent in total"
---

# Pyramid Chart

To render a pyramid series, use the series [`type`](../api/accumulation-chart/accumulationSeriesModel/#type) as `Pyramid` and
inject `PyramidSeries` module into the `provide`.

{% tab template="chart/series/pyramid" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container">
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' type='Pyramid' xName='x' yName='y'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PyramidSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: 'Australia', y: 20, text: 'Australia 20%' },
                { x: 'France', y: 22, text: 'France 22%' },
                { x: 'China', y: 23, text: 'China 23%' },
                { x: 'India', y: 24, text: 'India 24%' },
                { x: 'Japan', y: 25, text: 'Japan 25%' },
                { x: 'Germany', y: 27, text: 'Germany 27%' }
            ]
    };
  },
  provide: {
     accumulationchart: [PyramidSeries]
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

## Mode

The Pyramid chart supports linear and surface modes of rendering. The default type of the
`pyramidMode` is `linear`.

{% tab template="chart/series/pyramid" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container">
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' type='Pyramid' xName='x' yName='y' pyramidMode='Surface'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PyramidSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: 'Australia', y: 20, text: 'Australia 20%' },
                { x: 'France', y: 22, text: 'France 22%' },
                { x: 'China', y: 23, text: 'China 23%' },
                { x: 'India', y: 24, text: 'India 24%' },
                { x: 'Japan', y: 25, text: 'Japan 25%' },
                { x: 'Germany', y: 27, text: 'Germany 27%' }
            ]
    };
  },
  provide: {
     accumulationchart: [PyramidSeries]
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

The size of the pyramid chart can be customized by using the  `width` and `height` properties.

{% tab template="chart/series/pyramid" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container">
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' type='Pyramid' xName='x' yName='y' width='60%'  height='80%'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PyramidSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: 'Australia', y: 20, text: 'Australia 20%' },
                { x: 'France', y: 22, text: 'France 22%' },
                { x: 'China', y: 23, text: 'China 23%' },
                { x: 'India', y: 24, text: 'India 24%' },
                { x: 'Japan', y: 25, text: 'Japan 25%' },
                { x: 'Germany', y: 27, text: 'Germany 27%' }
            ]
    };
  },
  provide: {
     accumulationchart: [PyramidSeries]
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

## Gap Between the Segments

Pyramid chart provides options to customize the space between the segments by using the `gapRatio` property of the
series. It ranges from 0 to 1.

{% tab template="chart/series/pyramid" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container">
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' type='Pyramid' xName='x' yName='y' :gapRatio='gapRatio'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PyramidSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: 'Australia', y: 20, text: 'Australia 20%' },
                { x: 'France', y: 22, text: 'France 22%' },
                { x: 'China', y: 23, text: 'China 23%' },
                { x: 'India', y: 24, text: 'India 24%' },
                { x: 'Japan', y: 25, text: 'Japan 25%' },
                { x: 'Germany', y: 27, text: 'Germany 27%' }
            ],
            gapRatio: 0.08
    };
  },
  provide: {
     accumulationchart: [PyramidSeries]
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

{% tab template="chart/series/pyramid" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container">
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' type='Pyramid' xName='x' yName='y' explode=true
                 explodeOffset='10' :explodeIndex='explodeIndex'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PyramidSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: 'Australia', y: 20, text: 'Australia 20%' },
                { x: 'France', y: 22, text: 'France 22%' },
                { x: 'China', y: 23, text: 'China 23%' },
                { x: 'India', y: 24, text: 'India 24%' },
                { x: 'Japan', y: 25, text: 'Japan 25%' },
                { x: 'Germany', y: 27, text: 'Germany 27%' }
            ],
            explodeIndex:3
    };
  },
  provide: {
     accumulationchart: [PyramidSeries]
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

{% tab template="chart/series/pyramid" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :pointRender='onPointRender'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' type='Pyramid' xName='x' yName='y'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PyramidSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: 'Australia', y: 20, text: 'Australia 20%' },
                { x: 'France', y: 22, text: 'France 22%' },
                { x: 'China', y: 23, text: 'China 23%' },
                { x: 'India', y: 24, text: 'India 24%' },
                { x: 'Japan', y: 25, text: 'Japan 25%' },
                { x: 'Germany', y: 27, text: 'Germany 27%' }
            ]
    };
  },
  provide: {
     accumulationchart: [PyramidSeries]
  },
  methods: {
    onPointRender: function (args) {
        if ((args.point.x as string).indexOf('China') > -1) {
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