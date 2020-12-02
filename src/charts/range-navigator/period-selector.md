---
title: " RangeNavigator Period Selector | Vue "

component: "RangeNavigator"

description: "The period selector allows to select a range with specified periods."
---

# Period selector

The period selector allows to select a range with specified periods.

## Periods

Periods is an array of objects that allows users to specify the range of periods. The “interval” property specifies the count value of the button, and the “text” property specifies the text to be displayed on button. The “intervalType” property allows users to customize the intervals of the buttons. The “intervalType” property supports the following interval types:

* Auto
* Years
* Quarter
* Months
* Weeks
* Days
* Hours
* Minutes
* Seconds

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
        <ejs-rangenavigator :valueType='valueType' :value='value' :labelFormat='labelFormat'
        :periodSelectorSettings='periodSelectorSettingsTop' >
            <e-rangenavigator-series-collection>
                <e-rangenavigator-series :dataSource='data' type='Area' xName='x' yName='y' width=2>
                </e-rangenavigator-series>
            </e-rangenavigator-series-collection>
        </ejs-rangenavigator>
    </div>
</template>
<script>
import Vue from "vue";
import { RangeNavigatorPlugin, AreaSeries, DateTime, PeriodSelector } from "@syncfusion/ej2-vue-charts";
import { bitCoinData } from "./default_data.js";

Vue.use(RangeNavigatorPlugin);

export default {
  data() {
    return {
     valueType: 'DateTime',
      periodSelectorSettingsTop: {
        periods: [
          { text: "1M", interval: 1, intervalType: "Months" },
          { text: "3M", interval: 3, intervalType: "Months" },
          { text: "6M", interval: 6, intervalType: "Months" },
          { text: "1Y", interval: 1, intervalType: "Years" },
          { text: "2Y", interval: 2, intervalType: "Years", selected: true },
          { text: "ALL" }
        ],
        position: "Top"
      },
     value: [new Date('2017-09-01'), new Date('2018-02-01')],
     labelFormat: 'MMM-yy',
     data: bitCoinData
    };
  },
  provide: {
    rangeNavigator: [DateTime, AreaSeries, PeriodSelector]
  }
};
</script>
```

{% endtab %}

>Note: To use the period selector feature, inject the PeriodSelector module using the RangeNavigator.Inject(PeriodSelector)
method.

## Positioning period selector

The “position” property allows users to position the period selector either at the “top” or “bottom”.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
        <ejs-rangenavigator :valueType='valueType' :value='value' :labelFormat='labelFormat'
        :periodSelectorSettings='periodSelectorSettingsTop' >
            <e-rangenavigator-series-collection>
                <e-rangenavigator-series :dataSource='data' type='Area' xName='x' yName='y' width=2>
                </e-rangenavigator-series>
            </e-rangenavigator-series-collection>
        </ejs-rangenavigator>
    </div>
</template>
<script>
import Vue from "vue";
import { RangeNavigatorPlugin, AreaSeries, DateTime, PeriodSelector } from "@syncfusion/ej2-vue-charts";
import { bitCoinData } from "./default_data.js";

Vue.use(RangeNavigatorPlugin);

export default {
  data() {
    return {
     valueType: 'DateTime',
      periodSelectorSettingsTop: {
        periods: [
          { text: "1M", interval: 1, intervalType: "Months" },
          { text: "3M", interval: 3, intervalType: "Months" },
          { text: "6M", interval: 6, intervalType: "Months" },
          { text: "1Y", interval: 1, intervalType: "Years" },
          { text: "2Y", interval: 2, intervalType: "Years", selected: true },
          { text: "ALL" }
        ],
        position: "Bottom"
      },
     value: [new Date('2017-09-01'), new Date('2018-02-01')],
     labelFormat: 'MMM-yy',
     data: bitCoinData
    };
  },
  provide: {
    rangeNavigator: [DateTime, AreaSeries, PeriodSelector]
  }
};
</script>
```

{% endtab %}

## Height

The “height” property allows users to specify the height for period selector. The default value of the height property is 43.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
        <ejs-rangenavigator :valueType='valueType' :value='value' :labelFormat='labelFormat'
        :periodSelectorSettings='periodSelectorSettingsTop' >
            <e-rangenavigator-series-collection>
                <e-rangenavigator-series :dataSource='data' type='Area' xName='x' yName='y' width=2>
                </e-rangenavigator-series>
            </e-rangenavigator-series-collection>
        </ejs-rangenavigator>
    </div>
</template>
<script>
import Vue from "vue";
import { RangeNavigatorPlugin, AreaSeries, DateTime, PeriodSelector } from "@syncfusion/ej2-vue-charts";
import { bitCoinData } from "./default_data.js";

Vue.use(RangeNavigatorPlugin);

export default {
  data() {
    return {
     valueType: 'DateTime',
      periodSelectorSettingsTop: {
        periods: [
          { text: "1M", interval: 1, intervalType: "Months" },
          { text: "3M", interval: 3, intervalType: "Months" },
          { text: "6M", interval: 6, intervalType: "Months" },
          { text: "1Y", interval: 1, intervalType: "Years" },
          { text: "2Y", interval: 2, intervalType: "Years", selected: true },
          { text: "ALL" }
        ],
        position: "Top",
        height: 65
      },
     value: [new Date('2017-09-01'), new Date('2018-02-01')],
     labelFormat: 'MMM-yy',
     data: bitCoinData
    };
  },
  provide: {
    rangeNavigator: [DateTime, AreaSeries, PeriodSelector]
  }
};
</script>
```

{% endtab %}

## Visibility of range navigator

The “disableRangeSelector” property allows users to render the period selector without range navigator.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
    <ejs-rangenavigator valueType='DateTime'
        labelPosition='Outside' :dataSource='data' xName='x' yName='Close'
        :periodSelectorSettings='periodSelectorSettingsTop' disableRangeSelector=true>
       </ejs-rangenavigator>
    </div>
</template>
<script>
import Vue from "vue";
import { RangeNavigatorPlugin, AreaSeries, PeriodSelector, DateTime } from "@syncfusion/ej2-vue-charts";
import { chartData } from "./default_data.js";

Vue.use(RangeNavigatorPlugin);

export default {
  data() {
    return {
     valueType: 'DateTime',
      periodSelectorSettingsTop: {
        periods: [
          { text: "1M", interval: 1, intervalType: "Months" },
          { text: "3M", interval: 3, intervalType: "Months" },
          { text: "6M", interval: 6, intervalType: "Months" },
          { text: "1Y", interval: 1, intervalType: "Years" },
          { text: "2Y", interval: 2, intervalType: "Years", selected: true },
          { text: "ALL" }
        ],
        position: "Top"
      },
     data: chartData
    };
  },
  provide: {
    rangeNavigator: [DateTime, AreaSeries, PeriodSelector]
  }
};
</script>
```

{% endtab %}

## See Also

* [LightWeight](./lightweight/)