---
title: " Bullet Chart Value Bar | Vue "

component: "Bullet Chart"

description: "The main data value is encoded by a length of the main bar in the middle of the chart, known as the Feature Measure. "
---

# Feature Bar

The main data value is encoded by a length of the main bar in the middle of the chart, known as the `Feature Measure`. This is also called as `value Bar`. Also, if you want to display the target bar you should map the `valueField` name from the dataSource.

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
        categoryField="category"
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
      data: [{ value: 55, target: 75, category: "Year 1" }],
      minimum: 0, maximum: 100, interval: 20
    }
  }
}
</script>
```

{% endtab %}

## Feature Bar Types

You can customize the shape of the feature bar or value bar using the `type` property of the bullet chart. Feature bar contains `Rect` and `Dot` shapes. The default type of feature bar is `Rect`.

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
        categoryField="category"
        type="Dot"
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
      data: [{ value: 55, target: 75, category: "Year 1" }],
      minimum: 0, maximum: 100, interval: 20
    }
  }
}
</script>
```

{% endtab %}

## Customization

### Border Customization

Using the `valueBorder` property of the bullet chart, you can customize the border `color` and `width` of the feature bar.

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
        categoryField="category"
        :valueBorder="valueBorder"
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
      data: [{ value: 55, target: 75, category: "Year 1" }],
      minimum: 0, maximum: 100, interval: 20, valueBorder: {
          color: "red", width: 3
      }
    }
  }
}
</script>
```

{% endtab %}

### Fill color and height Customization

You can customize the fill color and height of the feature bar using the `valueFill` and `valueHeight` properties of the bullet chart.

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
        categoryField="category"
        valueFill="blue"
        valueHeight=15
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
      data: [{ value: 55, target: 75, category: "Year 1" }],
      minimum: 0, maximum: 100, interval: 20
    }
  }
}
</script>
```

{% endtab %}