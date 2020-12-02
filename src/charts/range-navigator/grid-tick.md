---
title: " RangeNavigator Grid and Tick lines | Vue "

component: "RangeNavigator"

description: "RangeNavigator supports customization of width, color, and dashArray of the major grid lines using the majorGridLines property."
---

# Grid and Tick Lines

## Grid line customization

You can customize the width, color, and dashArray of the major grid lines using the majorGridLines property.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
    <ejs-rangenavigator :value='value' labelPosition ='Outside'  :tooltip='tooltip' :majorGridLines='majorGridLines' >
            <e-rangenavigator-series-collection >
                <e-rangenavigator-series :dataSource='data' xName='xData' type='Line' yName='yData' ></e-rangenavigator-series>
            </e-rangenavigator-series-collection>
        </ejs-rangenavigator>
    </div>
</template>
<script>
import Vue from "vue";
import { RangeNavigatorPlugin, AreaSeries, DateTime } from "@syncfusion/ej2-vue-charts";
import {  sl } from "./default_data.js";

Vue.use(RangeNavigatorPlugin);

export default {
  data() {
    return {
    majorGridLines:{
        width: 4,
        color: 'blue',
        dashArray: '5,5'
    },
     tooltip: { enable: true },
     value:[25,40],
     data:  [
      { xData: 10, yData: 35 }, { xData: 20, yData: 28 },
      { xData: 30, yData: 34 }, { xData: 40, yData: 32 },
      { xData: 50, yData: 40 }
     ]
    };
  },
  provide: {
    rangeNavigator: [DateTime, AreaSeries]
  }
};
</script>
```

{% endtab %}

## Tick line customization

You can customize the width, color, and height of the major tick lines using the majorTickLines property.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
    <ejs-rangenavigator :value='value' labelPosition ='Outside'  :tooltip='tooltip' :majorTickLines='majorTickLines' >
            <e-rangenavigator-series-collection >
                <e-rangenavigator-series :dataSource='data' xName='xData' type='Line' yName='yData' ></e-rangenavigator-series>
            </e-rangenavigator-series-collection>
        </ejs-rangenavigator>
    </div>
</template>
<script>
import Vue from "vue";
import { RangeNavigatorPlugin, AreaSeries, DateTime } from "@syncfusion/ej2-vue-charts";
import {  sl } from "./default_data.js";

Vue.use(RangeNavigatorPlugin);

export default {
  data() {
    return {
    majorTickLines:{
       width: 3,
       color: 'red'
   },
     tooltip: { enable: true },
     value:[25,40],
     data:  [
      { xData: 10, yData: 35 }, { xData: 20, yData: 28 },
      { xData: 30, yData: 34 }, { xData: 40, yData: 32 },
      { xData: 50, yData: 40 }
     ]
    };
  },
  provide: {
    rangeNavigator: [DateTime, AreaSeries]
  }
};
</script>
```

{% endtab %}