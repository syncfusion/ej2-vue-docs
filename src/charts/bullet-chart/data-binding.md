---
title: " Bullet Chart DataBinding | Vue "

component: "Bullet Chart"

description: "Bullet Chart can be rendered by using different types of data source. They are called local data, remote data. "
---

# Working with Data

Bullet Chart can visualise data bound from local or remote data.

## Local Data

You can bind a simple JSON data to the chart using
[`dataSource`](../api/bullet-chart/) direct property of the bullet-chart. Now map the fields in
JSON to [`valueField`](../api/bullet-chart/#valueField-string) and [`targetField`](../api/bullet-chart/#targetField-string) properties.

{% tab template="bullet-chart/bullet-chart-dimensions/container" %}

```html
<template>
  <div>
      <ejs-bulletchart id="bulletChart"
        :dataSource="localData"
        valueField="value"
        targetField="comparativeMeasureValue"
        :minimum="minimum"
        :maximum="maximum"
        :interval="interval"
        title="Profit in %"
      >
      <e-bullet-range-collection>
          <e-bullet-range end="5" color="red"></e-bullet-range>
          <e-bullet-range end="15" color="blue"></e-bullet-range>
          <e-bullet-range end="20" color="green"></e-bullet-range>
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
        localData: [{ value: 5, comparativeMeasureValue: 7.5, category: '2001' },
               { value: 7, comparativeMeasureValue: 5, category: '2002' },
               { value: 10, comparativeMeasureValue: 6, category: '2003' },
               { value: 5, comparativeMeasureValue: 8, category: '2004' },
               { value: 12, comparativeMeasureValue: 5, category: '2005' },
               { value: 8, comparativeMeasureValue: 6, category: '2006' }
            ],
        minimum: 0, maximum: 20, interval: 5
    }
  }
}
</script>
```

{% endtab %}