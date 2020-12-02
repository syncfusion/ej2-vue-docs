---
title: " RangeNavigator Lightweight | Vue "

component: "RangeNavigator"

description: "Lightweight rangenavigator is getting intialized when the datasource for series property is empty."
---

# Lightweight range navigator

By default, when the dataSource for series property in RangeNavigator is empty, a light weight Range navigator will get
initialized without chart. The following code example shows the basic lightweight range navigator.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
      <ejs-rangenavigator :valueType='valueType' :intervalType='intervalType'
        :value='value' :labelFormat='labelFormat' :dataSource='dataSource'
        xName='x' yName='y'>
      </ejs-rangenavigator>
    </div>
</template>
<script>
import Vue from "vue";
import { RangeNavigatorPlugin, AreaSeries, DateTime } from "@syncfusion/ej2-vue-charts";
import { GetDateTimeData  } from "./default_data.js";

Vue.use(RangeNavigatorPlugin);

export default {
  data() {
    return {
     valueType: "DateTime",
      intervalType: "Months",
      labelFormat: "MMM",
      value: [new Date('2018-06-01'), new Date('2018-07-01')],
      dataSource: GetDateTimeData(new Date('2018-01-01'), new Date('2019-01-01')),
    };
  },
  provide: {
    rangeNavigator: [DateTime, AreaSeries]
  }
};
</script>
```

{% endtab %}

## See Also

* [Period Selector](./period-selector/)