---
title: "Localization"
component: "Sparkline"
description: "Localization support in sparkline component"
---

# Localization

The sparkline control supports localization. The default culture for localization is `en-US`. You can change the culture using the `setCulture` method.

## Tooltip format

Sparkline tooltip supports localization. The following code sample shows tooltip text with currency format based on culture.

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div class="spark">
        <ejs-sparkline id="sparkline" align="center" :dataSource='dataSource' :containerArea='containerArea' :border='border' fill= '#b2cfff' :padding='padding' lineWidth= 3 format= 'c0' useGroupingSeparator= 'true' :type='type' :tooltipSettings='tooltipSettings' :height='height' :width='width'></ejs-sparkline>
    </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { SparklinePlugin,SparklineTooltip } from "@syncfusion/ej2-vue-charts";
Vue.use(SparklinePlugin);

export default {
  data: function() {
    return {
   containerArea: {
        border: { color: '#033e96', width: 2 }
    },
    tooltipSettings: {
        visible: true
    },
    padding: { left: 20, right: 20, bottom: 20, top: 20},
    border: { color: '#033e96', width: 2 },
    height: '200px',
    width: '350px',
    type: 'Area',
    dataSource: [30000, 60000, 40000, 10000, 30000, 20000, 50000]
    }
  },
provide:{
    sparkline:[SparklineTooltip]
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

## Rtl

If you set the `enableRtl` property to true, then the sparkline will be rendered from rigt-to-left direction.

The following example shows the sparkline is render from "Right-to-left".

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div class="spark">
        <ejs-sparkline id="sparkline" align="center" :dataSource='dataSource' :enableRtl='enableRtl' :height='height' :width='width'></ejs-sparkline>
    </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { SparklinePlugin,SparklineTooltip } from "@syncfusion/ej2-vue-charts";
Vue.use(SparklinePlugin);

export default {
  data: function() {
    return {
    height: '150px',
    width: '150px',
    enableRtl: true
    dataSource: [30000, 60000, 40000, 10000, 30000, 20000, 50000]
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