---
title: " Bullet Chart Ranges | Vue "

component: "Bullet Chart"

description: "Bullet Chart scale can be rendered by using different types of end values. They are used to represnt the status of each data. "
---

# Ranges

`Ranges` are represents the quality of a specific range in bullet-chart scale like good, bad and satisfactory. The `end` property specifies the ending point of the qualitative range. `Minimum` value of quantitative scale is considered as the starting point of first range and previous end points are considered as starting point for other ranges.

{% tab template="bullet-chart/axis/custom" %}

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
        categoryField="category"
        :categoryLabelStyle="categoryStyle"
        height="400px"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="35" color="darkred" opacity= 0.5 ></e-bullet-range>
          <e-bullet-range end="50" color="red" opacity= 1 ></e-bullet-range>
          <e-bullet-range end="75" color="blue" opacity= 0.7 ></e-bullet-range>
          <e-bullet-range end="90" color="lightgreen" opacity= 1 ></e-bullet-range>
          <e-bullet-range end="100" color="green" opacity= 1 ></e-bullet-range>
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
      data: [{ value: 55, target: 75, category: "Year 1" },
            { value: 70, target: 70, category: "Year 2" },
            { value: 85, target: 75, category: "Year 3" }],
      minimum: 0, maximum: 100, interval: 10,
      categoryStyle: { color: "red", size: "13", fontWeight: "bold" }
    }
  }
}
</script>
```

{% endtab %}

## Color Customization

Color for each qualitative range is customized using `color` property based on end values. Also you can customize the opacity of the each range color.

{% tab template="bullet-chart/axis/custom" %}

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
        categoryField="category"
        :categoryLabelStyle="categoryStyle"
        height="400px"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="35" color="darkred" opacity= 0.5 ></e-bullet-range>
          <e-bullet-range end="50" color="red" opacity= 1 ></e-bullet-range>
          <e-bullet-range end="75" color="blue" opacity= 0.7 ></e-bullet-range>
          <e-bullet-range end="90" color="lightgreen" opacity= 1 ></e-bullet-range>
          <e-bullet-range end="100" color="green" opacity= 1 ></e-bullet-range>
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
      data: [{ value: 55, target: 75, category: "Year 1" },
            { value: 70, target: 70, category: "Year 2" },
            { value: 85, target: 75, category: "Year 3" }],
      minimum: 0, maximum: 100, interval: 10,
      categoryStyle: { color: "red", size: "13", fontWeight: "bold" }
    }
  }
}
</script>
```

{% endtab %}