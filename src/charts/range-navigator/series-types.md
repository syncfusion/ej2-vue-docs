---
title: " RangeNavigator Series Types | Vue "

component: "RangeNavigator"

description: "Essential JS 2 Range navigator supports 3 types of series, to render the data."
---

# Series Types

Essential JS 2 Range navigator supports 3 types of series, to render the data.

<!-- markdownlint-disable MD036 -->

## Line

<!-- markdownlint-disable MD036 -->

To render a line series, set the series[`type`](../api/chart/series/#type) to `Line`, and
inject the `LineSeries` module using the `RangeNavigator.Inject(LineSeries)` method.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
        <ejs-rangenavigator :valueType='valueType' :value='value' :labelFormat='labelFormat' :tooltip='tooltip'>
            <e-rangenavigator-series-collection>
                <e-rangenavigator-series :dataSource='data' type='Line' xName='x' yName='y' width=2>
                </e-rangenavigator-series>
            </e-rangenavigator-series-collection>
        </ejs-rangenavigator>
    </div>
</template>
<script>
import Vue from "vue";
import { RangeNavigatorPlugin, LineSeries, DateTime, RangeTooltip } from "@syncfusion/ej2-vue-charts";
import { bitCoinData } from "./default_data.js";

Vue.use(RangeNavigatorPlugin);

export default {
  data() {
    return {
     valueType: 'DateTime',
     value: [new Date('2017-09-01'), new Date('2018-02-01')],
     tooltip: { enable: true },
     labelFormat: 'MMM-yy',
     data: bitCoinData
    };
  },
  provide: {
    rangeNavigator: [DateTime, LineSeries, RangeTooltip]
  }
};
</script>
```

{% endtab %}

## Area

To render a step line series, use series [`type`](../api/chart/series/#type) as `Area` and
inject `AreaSeries` module using `RangeNavigator.Inject(AreaSeries)` method.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
        <ejs-rangenavigator :valueType='valueType' :value='value' :labelFormat='labelFormat' :tooltip='tooltip'>
            <e-rangenavigator-series-collection>
                <e-rangenavigator-series :dataSource='data' type='Area' xName='x' yName='y' width=2>
                </e-rangenavigator-series>
            </e-rangenavigator-series-collection>
        </ejs-rangenavigator>
    </div>
</template>
<script>
import Vue from "vue";
import { RangeNavigatorPlugin, AreaSeries, DateTime, RangeTooltip } from "@syncfusion/ej2-vue-charts";
import { bitCoinData } from "./default_data.js";

Vue.use(RangeNavigatorPlugin);

export default {
  data() {
    return {
     valueType: 'DateTime',
     value: [new Date('2017-09-01'), new Date('2018-02-01')],
     tooltip: { enable: true },
     labelFormat: 'MMM-yy',
     data: bitCoinData
    };
  },
  provide: {
    rangeNavigator: [DateTime, AreaSeries, RangeTooltip]
  }
};
</script>
```

{% endtab %}

## StepLine

To render a step line series, use series [`type`](../api/chart/series/#type) as `StepLine` and
inject `StepLineSeries` module using `RangeNavigator.Inject(StepLineSeries)` method.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
        <ejs-rangenavigator :valueType='valueType' :value='value' :labelFormat='labelFormat' :tooltip='tooltip'>
            <e-rangenavigator-series-collection>
                <e-rangenavigator-series :dataSource='data' type='StepLine' xName='x' yName='y' width=2>
                </e-rangenavigator-series>
            </e-rangenavigator-series-collection>
        </ejs-rangenavigator>
    </div>
</template>
<script>
import Vue from "vue";
import { RangeNavigatorPlugin, StepLineSeries, DateTime, RangeTooltip } from "@syncfusion/ej2-vue-charts";
import { bitCoinData } from "./default_data.js";

Vue.use(RangeNavigatorPlugin);

export default {
  data() {
    return {
     valueType: 'DateTime',
     value: [new Date('2017-09-01'), new Date('2018-02-01')],
     tooltip: { enable: true },
     labelFormat: 'MMM-yy',
     data: bitCoinData
    };
  },
  provide: {
    rangeNavigator: [DateTime, StepLineSeries, RangeTooltip]
  }
};
</script>
```

{% endtab %}