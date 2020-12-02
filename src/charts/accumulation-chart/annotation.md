---
title: " Accumulation Chart Annotation | Vue "

component: "Accumulation Chart"

description: "The annotations are used to mark the specific area of interest in the chart area with texts, shapes or images."
---

# Annotation

The annotations are used to mark the specific area of interest in the chart area with texts, shapes or images.

<!-- markdownlint-disable MD033 -->

By using the <code>content</code> option of annotation property, you can specify the Id of the element that needs
to be displayed in the chart area.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :annotations='annotations'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationAnnotation } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [{ x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 }, { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },{ x: 'May', y: 19 }, { x: 'Jun', y: 23.5 }, { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }],
        annotations:[{
        content:'<div style="border: 1px solid black;background-color:#f5f5f5; padding: 5px 5px 5px 5px">13.5</div>',
        region: 'Series',
        coordinateUnits: 'Point',
        x: 'Jan',
        y: 3
    }]
    };
  },
  provide: {
     accumulationchart: [AccumulationAnnotation, PieSeries]
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

>Note: To use annotation feature in accumulation chart, we need to inject `AccumulationAnnotation` using `provide`.

## Region

The annotation can be placed with respect to either `Series` or `Chart`.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :annotations='annotations'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationAnnotation } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [{ x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 }, { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },{ x: 'May', y: 19 }, { x: 'Jun', y: 23.5 }, { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }],
        annotations:[{
        content:'<div style="border: 1px solid black;background-color:#f5f5f5; padding: 5px 5px 5px 5px">13.5</div>',
        region: 'Chart',
        coordinateUnits: 'Pixel',
        x: 250,
        y: 150
    }]
    };
  },
  provide: {
     accumulationchart: [AccumulationAnnotation, PieSeries]
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

## Co-ordinate Units

Specifies the coordinate units of an annotation either in `Pixel` or `Point`.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :annotations='annotations'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationAnnotation } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [{ x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 }, { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },{ x: 'May', y: 19 }, { x: 'Jun', y: 23.5 }, { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }],
        annotations:[{
        content:'<div style="border: 1px solid black;background-color:#f5f5f5; padding: 5px 5px 5px 5px">Jan : 13.5</div>',
        region: 'Series',
        coordinateUnits: 'Point',
        x: 'Jan',
        y: 3
    }]
    };
  },
  provide: {
     accumulationchart: [AccumulationAnnotation, PieSeries]
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

## Alignment

The annotations provides the `verticalAlignment`or `horizontalAlignment` properties.
The `verticalAlignment` property can be customized via `Top`, `Bottom` or `Middle` and the `horizontalAlignment`
property can be customized via `Near`, `Far` or `Center`.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :annotations='annotations'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationAnnotation } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [{ x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 }, { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },{ x: 'May', y: 19 }, { x: 'Jun', y: 23.5 }, { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }],
        annotations:[{
        content:'<div style="border: 1px solid black;background-color:#f5f5f5; padding: 5px 5px 5px 5px">Jan : 13.5</div>',
        region: 'Series',
        coordinateUnits: 'Point',
        x: 'Jan',
        y: 3,
        verticalAlignment:'Top',
        horizontalAlignment:'Near'
    }]
    };
  },
  provide: {
     accumulationchart: [AccumulationAnnotation, PieSeries]
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