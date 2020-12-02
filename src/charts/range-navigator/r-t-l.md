---
title: " RangeNavigator Selecting Range | Vue "

component: "RangeNavigator"

description: "The range navigator provides RTL (right-to-left) support. Axis labels, series types are rendered right to left when we enabled rtl property."
---

# RTL

The range navigator provides RTL (right-to-left) support. This can be enabled using the “enableRtl” property.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
        <ejs-rangenavigator :valueType='valueType' :value='value' :labelFormat='labelFormat' :enableRtl='enableRtl'>
            <e-rangenavigator-series-collection>
                <e-rangenavigator-series :dataSource='data' type='Area' xName='x' yName='y' width=2>
                </e-rangenavigator-series>
            </e-rangenavigator-series-collection>
        </ejs-rangenavigator>
    </div>
</template>
<script>
import Vue from "vue";
import { RangeNavigatorPlugin, AreaSeries, DateTime } from "@syncfusion/ej2-vue-charts";
import { bitCoinData } from "./default_data.js";

Vue.use(RangeNavigatorPlugin);

export default {
  data() {
    return {
     valueType: 'DateTime',
     value: [new Date('2017-09-01'), new Date('2018-02-01')],
     labelFormat: 'MMM-yy',
     enableRtl: true,
     data: bitCoinData
    };
  },
  provide: {
    rangeNavigator: [DateTime, AreaSeries]
  }
};
</script>
```

{% endtab %}