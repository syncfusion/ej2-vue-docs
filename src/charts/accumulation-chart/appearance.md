---
title: "Accumulation Chart Appearance | TypeScript "

component: "Accumulation Chart"

description: "We can customize chart appearance by using color palette, point level customization, chart area cutomization,
 title and margin customizations."
---

# Appearance

## Custom Color Palette

You can customize the default color of series or points by providing a custom color palette of your choice by
using the [`palettes`](../api/accumulation-chart/accumulationSeries/#palettes) property.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container">
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' :palettes='palettes' xName='x' yName='y'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
           { x: 'Jan', y: 3, fill: '#498fff', text:'January' }, { x: 'Feb', y: 3.5, fill: '#ffa060', text: 'February' },
           { x: 'Mar', y: 7, fill: '#ff68b6', text: 'March' }, { x: 'Apr', y: 13.5, fill: '#81e2a1', text: 'April' }
            ],
         palettes: ["#E94649", "#F6B53F", "#6FAAB0", "#FF33F3","#228B22","#3399FF"],
    };
  },
  provide: {
     accumulationchart: [PieSeries]
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

### Fluid Animation

Fluid animation used to animate series with updated dataSource continues animation rather than animation whole series. You can customize animation for a particular series using [`animate`] method.

{% tab template="chart/series/pie" %}

```html
<template>
  <div id="app">
   <ejs-accumulationchart id="container" ref="pie" :title="title" :loaded="loaded">
        <e-accumulation-series-collection>
            <e-accumulation-series name="Revenue" :dataSource="data" xName="x" yName="y" :startAngle="startAngle"
                      :endAngle="endAngle" innerRadius="40%" :dataLabel="dataLabel">
             </e-accumulation-series>
        </e-accumulation-series-collection>
    </ejs-accumulationchart>
  </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries,AccumulationDataLabel } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);
let count = 0;
let datasource1 = [
  { x: "Net-tution and Fees", y: 10 },
  { x: "Self-supporting Operations", y: 10 },
  { x: "Private Gifts", y: 13 },
  { x: "All Other", y: 14 },
  { x: "Local Revenue", y: 9 },
  { x: "State Revenue", y: 13 },
  { x: "Federal Revenue", y: 8 }
];
let datasource2 = [
  { x: "Net-tution and Fees", y: 120 },
  { x: "Self-supporting Operations", y: 31 },
  { x: "Private Gifts", y: 6 },
  { x: "All Other", y: 12 },
  { x: "Local Revenue", y: 25 },
  { x: "State Revenue", y: 11 },
  { x: "Federal Revenue", y: 12 }
];
let datasource3 = [
  { x: "Net-tution and Fees", y: 6 },
  { x: "Self-supporting Operations", y: 22 },
  { x: "Private Gifts", y: 11 },
  { x: "All Other", y: 15 },
  { x: "Local Revenue", y: 13 },
  { x: "State Revenue", y: 10 },
  { x: "Federal Revenue", y: 8 }
];
let datasource4 = [
  { x: "Net-tution and Fees", y: 15 },
  { x: "Self-supporting Operations", y: 10 },
  { x: "Private Gifts", y: 18 },
  { x: "All Other", y: 20 },
  { x: "Local Revenue", y: 30 },
  { x: "State Revenue", y: 20 },
  { x: "Federal Revenue", y: 25 }
];
let datasource5 = [
  { x: "Net-tution and Fees", y: 21 },
  { x: "Self-supporting Operations", y: 10 },
  { x: "Private Gifts", y: 15 },
  { x: "All Other", y: 15 },
  { x: "Local Revenue", y: 11 },
  { x: "State Revenue", y: 20 },
  { x: "Federal Revenue", y: 60 }
];
export default {
  data() {
    return {
      data: [
        { x: "Net-tution and Fees", y: 21, text: "21%" },
        { x: "Self-supporting Operations", y: 21, text: "21%" },
        { x: "Private Gifts", y: 8, text: "8%" },
        { x: "All Other", y: 8, text: "8%" },
        { x: "Local Revenue", y: 4, text: "4%" },
        { x: "State Revenue", y: 21, text: "21%" },
        { x: "Federal Revenue", y: 16, text: "16%" }
      ],
        dataLabel: {
        visible: true,
        position: "Inside",
        font: {
          color: "white",
          fontWeight: "Bold",
          size: "14px"
        }
      },
      startAngle: 0,
      endAngle: 360,
      title: "Education Institutional Revenue"
    };
  },
    methods: {
    loaded: function(args) {
      this.$refs.pie.ej2Instances.loaded = null;
      setInterval(() => {
        if (count === 0) {
          this.$refs.pie.ej2Instances.series[0].dataSource = datasource1;
          this.$refs.pie.ej2Instances.animate();
          count++;
        } else if (count === 1) {
          this.$refs.pie.ej2Instances.series[0].dataSource = datasource2;
          this.$refs.pie.ej2Instances.animate();
          count++;
        } else if (count === 2) {
          this.$refs.pie.ej2Instances.series[0].dataSource = datasource3;
          this.$refs.pie.ej2Instances.animate();
          count++;
        } else if (count === 3) {
          this.$refs.pie.ej2Instances.series[0].dataSource = datasource4;
          this.$refs.pie.ej2Instances.animate();
          count++;
        } else if (count === 4) {
          this.$refs.pie.ej2Instances.series[0].dataSource = datasource5;
          this.$refs.pie.ej2Instances.animate();
          count = 0;
        }
      }, 3000);
    }
  },
  provide: {
      accumulationchart: [ PieSeries, AccumulationDataLabel]
  }
};
</script>
```