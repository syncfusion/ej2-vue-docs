---
title: "Range band"
component: "Sparkline"
description: "Range band support in sparkline component"
---

# Range Band

This section explains how to customize the sparkline with multiple range bands.

## Range band customization

The range band feature is used to highlight a particular range along with the y-axis using the [`startRange`] and [`endRange`] properties. You can also customize the [`color`] and [`opacity`] of the range band.

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div class="spark">
        <ejs-sparkline id="sparkline" align="center" :dataSource='dataSource' :rangeBandSettings ='rangeBandSettings' fill= '#0d3c9b' :lineWidth='lineWidth' :height='height' :width='width'></ejs-sparkline>
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
    width: '150px',
    lineWidth: 2,
    dataSource:   [0, 6, 4, 1, 3, 2, 5],
    // To configure range band settings
    rangeBandSettings: [
            {
                startRange: 1,
                endRange: 3,
                color: '#bfd4fc',
                opacity:0.4
            }
    ]
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

## Multiple range band customization

You can define multiple range bands to a sparkline as shown in the following code sample.

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div class="spark">
        <ejs-sparkline id="sparkline" align="center" :dataSource='dataSource' fill= '#0d3c9b' :rangeBandSettings='rangeBandSettings' :lineWidth='lineWidth' :height='height' :width='width'></ejs-sparkline>
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
    width: '150px',
    lineWidth: 2,
    dataSource:   [0, 6, 4, 1, 3, 2, 5],
    rangeBandSettings: [
            {
                startRange: 1,
                endRange: 2,
                color: '#bfd4fc',
                opacity:0.4
            },
            {
                startRange: 4,
                endRange: 5,
                color: 'red',
                opacity:0.4
            }
        ]
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
