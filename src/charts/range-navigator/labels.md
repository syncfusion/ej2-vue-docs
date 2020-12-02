---
title: " RangeNavigator Labels | Vue "

component: "RangeNavigator"

description: "RangeNavigator supports Multilevel label and enable grouping properties to customize axis labels."
---

# Labels

## Multilevel labels

The second level labels for the range navigator can be enabled by setting the “enableGrouping” property to true.
This is restricted to date-time axis alone.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
      <ejs-rangenavigator :valueType='valueType' :intervalType='intervalType' enableGrouping=true
        :value='value' :dataSource='dataSource'
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
    let points = [];
    let value = 0;
    let point = {};
    for (let j = 1; j < 1090; j++) {
      value += Math.random() * 10 - 5;
      value = value < 0 ? Math.abs(value) : value;
      point = { x: new Date(2000, 0, j), y: value, z: value + 10 };
      points.push(point);
    }
    return {
     valueType: "DateTime",
      intervalType: "Quarter",
      value: [new Date('2001-01-01'), new Date('2002-01-01')],
      dataSource: points,
    };
  },
  provide: {
    rangeNavigator: [DateTime, AreaSeries]
  }
};
</script>
```

{% endtab %}

## Grouping

The second level axis labels can be grouped using “groupBy” property with the following interval types:

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
      <ejs-rangenavigator :valueType='valueType' :intervalType='intervalType' enableGrouping=true groupBy='Years'
        :value='value' :dataSource='dataSource'
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
    let points = [];
    let value = 0;
    let point = {};
    for (let j = 1; j < 1090; j++) {
      value += Math.random() * 10 - 5;
      value = value < 0 ? Math.abs(value) : value;
      point = { x: new Date(2000, 0, j), y: value, z: value + 10 };
      points.push(point);
    }
    return {
     valueType: "DateTime",
      intervalType: "Quarter",
      value: [new Date('2001-01-01'), new Date('2002-01-01')],
      dataSource: points,
    };
  },
  provide: {
    rangeNavigator: [DateTime, AreaSeries]
  }
};
</script>
```

{% endtab %}

## Smart labels

The “labelIntersectAction” property is used to avoid overlapping of labels.

The following code sample shows setting the labelIntersectAction property to Hide.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
        <ejs-rangenavigator :valueType='valueType' :value='value' :labelFormat='labelFormat' labelIntersectAction='Hide'>
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
     labelFormat:'y/M/d',
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

## Label positioning

By default, the labels can be placed at outside of the range navigator. You can place the labels inside the range navigator
using the labelPosition property.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
        <ejs-rangenavigator :valueType='valueType' :value='value' :labelFormat='labelFormat' labelPosition='Inside'>
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
     labelFormat: 'MMM',
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

## Labels customization

The font size, color, family, etc. can be customized using the “labelStyle” property.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
      <ejs-rangenavigator :valueType='valueType' :intervalType='intervalType' :labelStyle='labelStyle'
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
      labelStyle: { color: 'red', size:'10px'}
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