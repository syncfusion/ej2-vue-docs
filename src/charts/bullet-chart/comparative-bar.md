---
title: " Bullet Chart Target Bar | Vue "

component: "Bullet Chart"

description: "The line marker that runs perpendicular to the orientation of the graph is known as the `Comparative Measure`. "
---

# Target Bar

The line marker that runs perpendicular to the orientation of the graph is known as the `Comparative Measure` and is used as a target marker to compare against the Feature Measure value. This is also called as `Target Bar` of the bullet chart. Also, if you want to display the target bar you should map the `targetField` name from the dataSource.

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
      data: [{ value: 55, target: 75 }],
      minimum: 0, maximum: 100, interval: 20
    }
  }
}
</script>
```

{% endtab %}

## Target Bar Types

You can customize the shape of the target bar or comparative bar using the `targetTypes` property of the bullet chart. Target bar contains `Circle`, `Cross`, and `Rect` shapes. The default type of target bar is `Rect`.

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
        :targetTypes="targetTypes"
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
      data: [{ value: 55, target: 75 }],
      minimum: 0, maximum: 100, interval: 20, targetTypes: ["Circle"]
    }
  }
}
</script>
```

{% endtab %}

## Customization

### Color Customization

Using the `targetColor` property of the bullet chart, you can customize the fill color of the target bar.

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
        targetColor="red"
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
      data: [{ value: 55, target: 75 }],
      minimum: 0, maximum: 100, interval: 20
    }
  }
}
</script>
```

{% endtab %}

### Width Customization

You can customize the width of the target bar using the `targetWidth` property of the bullet chart.

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
        targetWidth=15
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
      data: [{ value: 55, target: 75 }],
      minimum: 0, maximum: 100, interval: 20
    }
  }
}
</script>
```

{% endtab %}