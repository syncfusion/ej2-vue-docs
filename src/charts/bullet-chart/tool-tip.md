---
title: "BulletChart Tooltip | Vue "

component: "BulletChart"

description: "Tooltip is used to show the data value when mouse hover on the chart.We can able to customize format,template and appearance."
---

# Tooltip

BulletChart will display details about the actual and target values through tooltip, when the mouse is moved over the target and feature bar.

## Default Tooltip

By setting [`enable`](https://ej2.syncfusion.com/documentation/api/bullet-chart/bulletTooltipSettings/#enable)property to true and by injecting `BulletTooltip` module
using `BulletChart.Inject(BulletTooltip)`. By default tooltip is visible in bullet-chart.

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
        height="400px"
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
        data: [{ value: 5, comparativeMeasureValue: 7.5, category: '2001' },
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

## Tooltip Template

Any HTML elements can be displayed in the tooltip by using the `template` property of the tooltip. You can use the ${target} and ${value} as place holders in the HTML element to display the value and target values of the corresponding data point.

## Customize the Appearance of Tooltip

The [`fill`](./https://ej2.syncfusion.com/documentation/api/bullet-chart/tooltipSettingsModel#fill-string) and [`border`](./https://ej2.syncfusion.com/documentation/api/bullet-chart/tooltipSettingsModel#border-bordermodel) properties are used to customize the background color and border of the tooltip respectively. The [`textStyle`](./https://ej2.syncfusion.com/documentation/api/bullet-chart/tooltipSettingsModel#textstyle-fontmodel) property in the tooltip is used to customize the font of the tooltip text.