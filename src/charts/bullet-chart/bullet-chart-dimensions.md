---
title: " Bullet Chart Appearance | Vue "

component: "Bullet Chart"

description: "We can set bullet-chart size manually by using width and height properties. We can set percentage or pixel size values to the bullet-chart."
---

# Bullet Chart Dimensions

## Size for Container

The bullet chart can be rendered to its container’s size. You can set the size using inline or CSS as shown below.

```html
<style>
  #bulletChart {
     width: 350px;
 }
</style>
<template>
  <div>
      <ejs-bulletchart id="bulletChart"> </ejs-bulletchart>
  </div>
</template>
<script>
import Vue from 'vue';
import { BulletChartPlugin } from '@syncfusion/ej2-vue-charts';
Vue.use(BulletChartPlugin);

export default {
       data() { /*
        */
       }
}
</script>
```

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
        title="Revenue"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="100" color="red"></e-bullet-range>
          <e-bullet-range end="200" color="blue"></e-bullet-range>
          <e-bullet-range end="300" color="green"></e-bullet-range>
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
      data: [{ value: 270, target: 250 }],
      minimum: 0, maximum: 300, interval: 50
    }
  }
}
</script>
<style>
  #bulletChart {
     width: 550px;
 }
</style>
```

{% endtab %}

## Size for Bullet Chart

You can also set the size for bullet chart directly using the [`width`](../api/bullet-chart/#width-string) and [`height`](../api/bullet-chart/#height-string) properties.

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
        title="Revenue"
        width="100%"
        height="100%"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="100" color="red"></e-bullet-range>
          <e-bullet-range end="200" color="blue"></e-bullet-range>
          <e-bullet-range end="300" color="green"></e-bullet-range>
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
      data: [{ value: 270, target: 250 }],
      minimum: 0, maximum: 300, interval: 50
    }
  }
}
</script>
```

{% endtab %}

### In Pixel

You can set the size of a chart in pixels as shown below.

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
        title="Revenue"
        width="600px"
        height="120px"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="100" color="red"></e-bullet-range>
          <e-bullet-range end="200" color="blue"></e-bullet-range>
          <e-bullet-range end="300" color="green"></e-bullet-range>
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
      data: [{ value: 270, target: 250 }],
      minimum: 0, maximum: 300, interval: 50
    }
  }
}
</script>
```

{% endtab %}

### In Percentage

By setting a value in percentage, the bullet chart gets its dimension with respect to its container. For example, when the height is ‘50%’, the bullet chart renders to half of the container’s height.

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
        title="Revenue"
        width="100%"
        height="100%"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="100" color="red"></e-bullet-range>
          <e-bullet-range end="200" color="blue"></e-bullet-range>
          <e-bullet-range end="300" color="green"></e-bullet-range>
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
      data: [{ value: 270, target: 250 }],
      minimum: 0, maximum: 300, interval: 50
    }
  }
}
</script>
```

{% endtab %}

>Note: When you do not specify the size, it takes `126px` as its height and window size as its width.