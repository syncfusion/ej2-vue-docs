---
title: " RangeNavigator Export and Print | Vue "

component: "RangeNavigator"

description: "The rendered rangenavigator can be printed or exported directly from the browser by calling the public method print and export."
---

# Export and print

## Export

The rendered range navigator can be exported to JPEG, PNG, SVG, or PDF format using the export method in the range navigator. The input parameters for this method are Export Type for format and fileName for result.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
     <ejs-button id='export' @click.native='exportIcon'>Export</ejs-button>
        <ejs-rangenavigator ref="chart" :valueType='valueType' :value='value' :labelFormat='labelFormat'>
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
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { bitCoinData } from "./default_data.js";

Vue.use(RangeNavigatorPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
     valueType: 'DateTime',
     value: [new Date('2017-09-01'), new Date('2018-02-01')],
     labelFormat: 'MMM-yy',
     data: bitCoinData
    };
  },
  provide: {
    rangeNavigator: [DateTime, AreaSeries]
  },
  methods: {
    exportIcon: function() {
        this.$refs.chart.export('PNG', 'export');
    }
  }
};
</script>
```

{% endtab %}

## Print

The rendered range navigator can be printed directly from the browser by calling the public method print. The ID of the range navigator div element must be passed as argument to that method.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
      <ejs-button id='print' @click.native='print'>Print</ejs-button>
        <ejs-rangenavigator ref="chart" :valueType='valueType' :value='value' :labelFormat='labelFormat'>
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
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { bitCoinData } from "./default_data.js";

Vue.use(RangeNavigatorPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
     valueType: 'DateTime',
     value: [new Date('2017-09-01'), new Date('2018-02-01')],
     labelFormat: 'MMM-yy',
     data: bitCoinData
    };
  },
  provide: {
    rangeNavigator: [DateTime, AreaSeries]
  },
  methods: {
    print: function() {
        this.$refs.chart.print();
    }
  }
};
</script>
```

{% endtab %}
