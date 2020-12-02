---
title: "Special points customization"
component: "Sparkline"
description: "Explains how to customize the special points in sparkline"
---

# Special points customization

You can customize the points by initializing the point colors. The customization options allows to differentiate the [`start`], [`end`], [`positive`], [`negative`], and [`low`] points. This customization is only applicable for line, column, and area type sparklines.

<!-- markdownlint-disable MD036 -->

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div class="spark">
        <ejs-sparkline id="sparkline" align="center" :dataSource='dataSource':highPointColor ='highPointColor' :lowPointColor= 'lowPointColor' :startPointColor ='startPointColor' :endPointColor='endPointColor' :negativePointColor='negativePointColor' :type='type' :valueType='valueType' xName='xval' yName='yval' :height='height' :width='width'></ejs-sparkline>
    </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { SparklinePlugin } from "@syncfusion/ej2-vue-charts";
Vue.use(SparklinePlugin);

export default {
  data: function() {
    return {
    height: '150px',
    width: '130px',
    dataSource: [
            { x: 0, xval: 'AUDI', yval: 1 },
            { x: 1, xval: 'BMW', yval: 5 },
            { x: 2, xval: 'BUICK', yval: -1 },
            { x: 3, xval: 'CETROEN', yval: -6 },
            { x: 4, xval: 'CHEVROLET', yval: 0 },
            { x: 5, xval: 'FIAT', yval: 1 },
            { x: 6, xval: 'FORD', yval: -2 },
            { x: 7, xval: 'HONDA', yval: 7 },
            { x: 8, xval: 'HYUNDAI', yval: -9 },
            { x: 9, xval: 'JEEP', yval: 0 },
            { x: 10, xval: 'KIA', yval: -10 },
            { x: 11, xval: 'MAZDA', yval: 3 },
        ],
    type:'Column',
    valueType: 'Category',
    highPointColor:'blue',
    lowPointColor:'orange',
    startPointColor:'green',
    endPointColor:'green',
    negativePointColor:'red'
    }
  }
}
</script>
<style>
.spark {
    width: 100%;
    height: 100%;
}
</style>
```

{% endtab %}

## Tie point color

Tie point color is used to configure the win-loss series type sparkline's y-value point color. The following code sample shows the tie point color of sparkline series.

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div class="spark">
        <ejs-sparkline id="sparkline" align="center" :dataSource='dataSource' :tiePointColor='tiePointColor' :type='type' :valueType='valueType' :height='height' :width='width'></ejs-sparkline>
    </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { SparklinePlugin } from "@syncfusion/ej2-vue-charts";
Vue.use(SparklinePlugin);

export default {
  data: function() {
    return {
    height: '150px',
    width: '130px',
    dataSource: [12, 15, -10, 13, 15, 6, -12, 17, 13, 0, 8, -10],
    // Assign the 'WinLoss' as type of Sparkline
    type:'WinLoss',
    // Assign "Numeric" as the value type of the sparkline
    valueType: 'Numeric',
    tiePointColor:'blue'
    }
  }
}
</script>
<style>
.spark {
    width: 100%;
    height: 100%;
}
</style>
```

{% endtab %}
