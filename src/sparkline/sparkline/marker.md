---
title: "Markers"
component: "Sparkline"
description: "Markers support in sparkline component"
---

# Markers

This section explains how to add markers to the sparklines.

## Adding marker to the sparkline

To add marker to the sparkline, specify the `visible` of `markerSettings` as following values. The `visible` will accept multiple values too.

* All - Enables markers for all points.
* Start - Enables marker for the start point.
* End - Enables marker for the end point.
* High - Enables marker for the high point.
* Low - Enables marker for the low point.
* Negative - Enables markers for the negative points.

The following code example shows enabling markers for all points.

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div class="spark">
        <ejs-sparkline id="sparkline" align="center" :dataSource='dataSource' :axisSettings='axisSettings' :markerSettings='markerSettings' :height='height' :width='width'></ejs-sparkline>
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
    height: '200px',
    width: '350px',
    axisSettings: {
        minX: -1, maxX: 7, maxY: 7, minY: -1
    }
    dataSource:   [0, 6, 4, 1, 3, 2, 5],
    // To enable markers for all points
    markerSettings: {
        visible: ['All']
    }
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

## Adding marker to special point

In sparkline, markers can be enabled for particular points such as the start, end, low, high, or negative. The following code examples shows enabling markers for the high and low points.

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div class="spark">
        <ejs-sparkline id="sparkline" align="center" :dataSource='dataSource' :lowPointColor='lowPointColor' :markerSettings='markerSettings' :highPointColor='highPointColor' :axisSettings='axisSettings' :height='height' :width='width'></ejs-sparkline>
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
    height: '200px',
    width: '350px',
    axisSettings: {
        minX: -1, maxX: 7, maxY: 7, minY: -1
    }
    dataSource:   [3, 6, 4, 1, 3, 2, 5],
    // To enable marker for high and low points with color customization
    highPointColor: 'blue',
    lowPointColor: 'red',
    markerSettings: {
        visible: ['High', 'Low']
    }
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

## Customizing markers

Sparkline markers can be customized in terms of fill color, border color, width, opacity, and size. The following code example shows customizing marker's fill, border, and size.

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div class="spark">
        <ejs-sparkline id="sparkline" align="center" :dataSource='dataSource' :markerSettings='markerSettings' fill= 'blue':axisSettings='axisSettings' :height='height' :width='width'></ejs-sparkline>
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
    height: '200px',
    width: '350px',
    axisSettings: {
        minX: -1, maxX: 7, maxY: 7, minY: -1
    }
    dataSource:   [3, 6, 4, 1, 3, 2, 5],
    // To enable marker for high and low points with color customization
    markerSettings: {
        visible: ['All'],
        size: 5, fill: 'white', border: { color: 'blue', width: 2}
    }
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
