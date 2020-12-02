---
title: " Bullet Chart Customization | Vue "

component: "Bullet Chart"

description: "Bullet Chart have different customizable features like different orientation, flow directions and animation features"
---

# Orientation

Bullet Chart can be rendered in different mode as `Horizontal` or `vertical` by using `orientation` property of the bullet-chart. By default bullet-chart rendered in horizontal mode.

{% tab template="bullet-chart/bullet-chart-dimensions/container" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Sales Rate in dollars"
        labelFormat="${value}"
        subtitle="(in dollars $)"
        orientation="vertical"
        width="20%"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="35" color="red"></e-bullet-range>
          <e-bullet-range end="50" color="blue"></e-bullet-range>
          <e-bullet-range end="100" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 55, target: 45 }],
      minimum: 0, maximum: 100, interval: 20
    }
  }
}
</script>
```

{% endtab %}

## Flow Direction

Using `enableRtl` boolean property of the bullet-chart, you can render bullet-chart in right to left or left to right direction.

{% tab template="bullet-chart/bullet-chart-dimensions/container" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Sales Rate"
        enableRtl="true"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="500" color="red"></e-bullet-range>
          <e-bullet-range end="1500" color="blue"></e-bullet-range>
          <e-bullet-range end="2000" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 1500, target: 1000 }],
      minimum: 0, maximum: 2000, interval: 200
    }
  }
}
</script>
```

{% endtab %}

## Animation

By setting `animation` property value as `true`, you can enable the linear animation of the feature and target bars.

{% tab template="bullet-chart/bullet-chart-dimensions/container" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Sales Rate"
        :animation="animation"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="500" color="red"></e-bullet-range>
          <e-bullet-range end="1500" color="blue"></e-bullet-range>
          <e-bullet-range end="2000" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 1500, target: 1000 }],
      minimum: 0, maximum: 2000, interval: 200,
      animation: { enable: true }
    }
  }
}
</script>
```

{% endtab %}

## Theme

Bullet chart also support different types of themes. Using `theme` property of the bullet-chart, you can customize the theme styles.

{% tab template="bullet-chart/bullet-chart-dimensions/container" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="data"
        valueField="value"
        targetField="target"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Profit in %"
        :theme="theme"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="15" color="red"></e-bullet-range>
          <e-bullet-range end="50" color="blue"></e-bullet-range>
          <e-bullet-range end="100" color="green"></e-bullet-range>
        </e-bullet-range-collection>
      </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
  data () {
    return {
      data: [{ value: 50, target: 45 }],
      minimum: 0, maximum: 100, interval: 10, theme: "HighContrast"
    }
  }
}
</script>
```

{% endtab %}