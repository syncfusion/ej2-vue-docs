---
title: "Appearance"
component: "Sparkline"
description: "Explains how to customize the appearance of sparkline"
---

# Appearance

The appearance of the sparkline can be customized using margin, container Area border, and container Area background.

## Sparkline border

The `container Area border` of the sparkline is used to render border to cover sparkline area.

The following code example shows the sparkline with overall border.

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div class="spark">
        <ejs-sparkline id="sparkline" align="center" :dataSource='dataSource' :border='border' fill= '#b2cfff' :containerArea='containerArea' :type='type' :height='height' :width='width'></ejs-sparkline>
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
    // To render border around the sparkline
    containerArea: {
        border: { color: '#033e96', width: 2 }
    },
    border: { color: '#033e96', width: 1 },
    height: '200px',
    width: '350px',
    type: 'Area',
    fill: '#b2cfff'
    dataSource: [3, 6, 4, 1, 3, 2, 5]
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

## Sparkline padding

Padding is used to specify padding value between container and sparkline. By default, padding value of the sparkline is 5. Sparkline `padding` values are specified by the left, right, top, and bottom.

The following code example shows the sparkline with overall padding is set to 20.

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div class="spark">
        <ejs-sparkline id="sparkline" align="center" :dataSource='dataSource' :border='border' :containerArea='containerArea' :padding='padding' fill= '#b2cfff' :type='type' :height='height' :width='width'></ejs-sparkline>
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
    containerArea: {
        border: { color: '#033e96', width: 2 }
    },
    // To render sparkline with padding
    padding: { left: 20, right: 20, bottom: 20, top: 20},
    border: { color: '#033e96', width: 1 },
    height: '200px',
    width: '350px',
    type: 'Area',
    dataSource: [3, 6, 4, 1, 3, 2, 5]
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

## Sparkline area customization

The background color of the sparkline area can be customized using the `containerArea background` color. By default, the sparkline background color is `transparent`.

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div class="spark">
        <ejs-sparkline id="sparkline" align="center" :padding='padding' :border='border' fill= '#b2cfff' :containerArea='containerArea' :dataSource='dataSource' :type='type' :height='height' :width='width'></ejs-sparkline>
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
    containerArea: {
        border: { color: '#033e96', width: 2 },
        // To render sparkline with background
        background: '#eff1f4',
    },
    padding: { left: 20, right: 20, bottom: 20, top: 20},
    border: { color: '#033e96', width: 2 },
    height: '200px',
    width: '350px',
    type: 'Area',
    dataSource: [3, 6, 4, 1, 3, 2, 5]
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

## Sparkline theme

Datalabel and track line colors of the sparkline will be changed based on theme. For example, for dark theme, the color of datalabel and track line should be white; for light theme, their value should be black. The possible values for sparkline theme are `Material`, `Fabric`, `Bootstrap`, and `Highcontrast`.

The following code example shows the color for datalabel and track line is set to white for dark theme.

{% tab template="sparkline/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
    <div class="spark">
        <ejs-sparkline id="sparkline" align="center" :dataSource='dataSource' :border='border' fill= '#007dd1' lineWidth= 3 :axisSettings='axisSettings' :dataLabelSettings='dataLabelSettings' theme= 'Highcontrast' :type='type' :tooltipSettings='tooltipSettings' :height='height' :width='width'></ejs-sparkline>
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
    dataLabelSettings: { visible: ['All']},
    tooltipSettings: {
        trackLineSettings: { visible: true }
    },
    axisSettings: {
        minX: -1, maxX: 7
    },
    border: { color: 'transparent', width: 2 },
    height: '200px',
    width: '350px',
    type: 'Line',
    dataSource: [3, 6, 4, 1, 3, 2, 5]
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
