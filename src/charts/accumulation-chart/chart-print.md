---
title: " Accumulation Chart Print and Export | Vue "

component: "Accumulation Chart"

description: "Accumultion chart have a public methods for print or export the rendered chart"
---

# Print and Export

## Print

The rendered chart can be printed directly from the browser by calling the public method print.

{% tab template="chart/series/radius" %}

```html
<template>
    <div id="app">
     <ejs-button id='print' @click.native='print'>Print</ejs-button>
         <ejs-accumulationchart ref="chart"  id="container">
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' radius='70%'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries } from "@syncfusion/ej2-vue-charts";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(AccumulationChartPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: 'Jan', y: 3, text: 'Jan: 3' }, { x: 'Feb', y: 3.5, text: 'Feb: 3.5' },
                { x: 'Mar', y: 7, text: 'Mar: 7' }, { x: 'Apr', y: 13.5, text: 'Apr: 13.5' },
                { x: 'May', y: 19, text: 'May: 19' }, { x: 'Jun', y: 23.5, text: 'Jun: 23.5' },
                { x: 'Jul', y: 26, text: 'Jul: 26' }, { x: 'Aug', y: 25, text: 'Aug: 25' },
                { x: 'Sep', y: 21, text: 'Sep: 21' }, { x: 'Oct', y: 15, text: 'Oct: 15' }],
    };
  },
  provide: {
    accumulationchart: [PieSeries]
  },
   methods: {
    print: function() {
        this.$refs.chart.print();
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

## Export

The rendered chart can be exported to `Image`(jpeg or png) or `SVG` or `PDF` format by using the export method.
Input parameters for this method are `Export` Type for `format` and `fileName` of result.

{% tab template="chart/series/radius" %}

```html
<template>
    <div id="app">
     <ejs-button  id='togglebtn' @click.native='exportIcon'>Export</ejs-button>
         <ejs-accumulationchart ref="chart" id="container">
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' radius='70%'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries } from "@syncfusion/ej2-vue-charts";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(AccumulationChartPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      seriesData: [
                { x: 'Jan', y: 3, text: 'Jan: 3' }, { x: 'Feb', y: 3.5, text: 'Feb: 3.5' },
                { x: 'Mar', y: 7, text: 'Mar: 7' }, { x: 'Apr', y: 13.5, text: 'Apr: 13.5' },
                { x: 'May', y: 19, text: 'May: 19' }, { x: 'Jun', y: 23.5, text: 'Jun: 23.5' },
                { x: 'Jul', y: 26, text: 'Jul: 26' }, { x: 'Aug', y: 25, text: 'Aug: 25' },
                { x: 'Sep', y: 21, text: 'Sep: 21' }, { x: 'Oct', y: 15, text: 'Oct: 15' }],
    };
  },
  provide: {
     accumulationchart: [PieSeries]
  },
   methods: {
    exportIcon: function() {
         this.$refs.chart.export('PNG', 'export');
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