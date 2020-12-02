---
title: " Chart Logarithmic Axis | Vue "

component: "Chart"

description: "Logarithmic axis uses logarithmic scale is defined as one where the units on an axis are powers, or logarithms, of a base number, usually 10."
---

# Logarithmic Axis

<!-- markdownlint-disable MD033 -->

Logarithmic axis uses logarithmic scale and it is very useful in visualizing data, when it has numeric values in
both lower order of magnitude (eg: 10<sup>-6</sup>) and higher order of magnitude (eg: 10<sup>6</sup>).

{% tab template="chart/axis/log" %}

```html
<template>
    <div id="app">
         <ejs-chart  id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Product X'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Logarithmic, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                { x: new Date(1995, 0, 1), y: 80 }, { x: new Date(1996, 0, 1), y: 200 },
                { x: new Date(1997, 0, 1), y: 400 }, { x: new Date(1998, 0, 1), y: 600 },
                { x: new Date(1999, 0, 1), y: 700 }, { x: new Date(2000, 0, 1), y: 1400 },
                { x: new Date(2001, 0, 1), y: 2000 }, { x: new Date(2002, 0, 1), y: 4000 },
                { x: new Date(2003, 0, 1), y: 6000 }, { x: new Date(2004, 0, 1), y: 8000 },
                { x: new Date(2005, 0, 1), y: 11000 }
        ],
      primaryXAxis: {
           valueType: 'DateTime',
            title: 'Years',
            labelFormat: 'y'
        },
         primaryYAxis: {
           valueType: 'Logarithmic',
           title: 'Profit'
        },
      title: "Product X Growth [1995-2005]"
    };
  },
  provide: {
    chart: [LineSeries, Logarithmic, DateTime]
  },
};
</script>
<style>
 #container {
     height: 350px;
 }
</style>
```

{% endtab %}

>Note: To use log axis, we need to inject `Logarithmic` into the `provide` and set
the [`valueType`](../api/chart/axis/#valuetype) of axis to `Logarithmic`.

## Range

Range of an axis, will be calculated automatically based on the provided data, you can also customize the range
of the axis using [`minimum`](../api/chart/axis/#minimum), [`maximum`](../api/chart/axis/#maximum)
and [`interval`](../api/chart/axis/#interval) property of the axis.

{% tab template="chart/axis/log" %}

```html
<template>
    <div id="app">
         <ejs-chart  id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Product X'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Logarithmic, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                { x: new Date(1995, 0, 1), y: 80 }, { x: new Date(1996, 0, 1), y: 200 },
                { x: new Date(1997, 0, 1), y: 400 }, { x: new Date(1998, 0, 1), y: 600 },
                { x: new Date(1999, 0, 1), y: 700 }, { x: new Date(2000, 0, 1), y: 1400 },
                { x: new Date(2001, 0, 1), y: 2000 }, { x: new Date(2002, 0, 1), y: 4000 },
                { x: new Date(2003, 0, 1), y: 6000 }, { x: new Date(2004, 0, 1), y: 8000 },
                { x: new Date(2005, 0, 1), y: 11000 }
        ],
      primaryXAxis: {
           valueType: 'DateTime',
            title: 'Years',
            labelFormat: 'y'
        },
         primaryYAxis: {
          valueType: 'Logarithmic',
           title: 'Profit',
           minimum: 100,
           maximum: 10000
        },
      title: "Product X Growth [1995-2005]"
    };
  }
  provide: {
    chart: [LineSeries, Logarithmic, DateTime]
  },
};
</script>
<style>
 #container {
     height: 350px;
 }
</style>
```

{% endtab %}

## Logarithmic Base

Logarithmic base can be customized by using the [`logBase`](../api/chart/axis/#logbase) property of the axis.
For example when the logBase is 5, the axis values follows 5<sup>-2</sup>, 5<sup>-1</sup>, 5<sup>0</sup>,
5<sup>1</sup>, 5<sup>2</sup> etc.

{% tab template="chart/axis/log"  %}

```html
<template>
    <div id="app">
         <ejs-chart  id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Product X'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Logarithmic, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                { x: new Date(1995, 0, 1), y: 80 }, { x: new Date(1996, 0, 1), y: 200 },
                { x: new Date(1997, 0, 1), y: 400 }, { x: new Date(1998, 0, 1), y: 600 },
                { x: new Date(1999, 0, 1), y: 700 }, { x: new Date(2000, 0, 1), y: 1400 },
                { x: new Date(2001, 0, 1), y: 2000 }, { x: new Date(2002, 0, 1), y: 4000 },
                { x: new Date(2003, 0, 1), y: 6000 }, { x: new Date(2004, 0, 1), y: 8000 },
                { x: new Date(2005, 0, 1), y: 11000 }
        ],
      primaryXAxis: {
           valueType: 'DateTime',
            title: 'Years',
            labelFormat: 'y'
        },
         primaryYAxis: {
          valueType: 'Logarithmic',
           title: 'Profit',
           logBase: 2
        },
      title: "Product X Growth [1995-2005]"
    };
  },
  provide: {
    chart: [LineSeries, Logarithmic, DateTime]
  }
};
</script>
<style>
 #container {
     height: 350px;
 }
</style>
```

{% endtab %}

## Logarithmic Interval

Logarithmic axis interval can be customized by using the [`interval`](../api/chart/axis/#interval)
property of the axis. When the logarithmic base is 10 and logarithmic interval is 2, then the axis labels are
placed at an interval of 10<sup>2</sup>. The default value of the interval is 1.

{% tab template="chart/axis/log" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Product X'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Logarithmic, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                { x: new Date(1995, 0, 1), y: 80 }, { x: new Date(1996, 0, 1), y: 200 },
                { x: new Date(1997, 0, 1), y: 400 }, { x: new Date(1998, 0, 1), y: 600 },
                { x: new Date(1999, 0, 1), y: 700 }, { x: new Date(2000, 0, 1), y: 1400 },
                { x: new Date(2001, 0, 1), y: 2000 }, { x: new Date(2002, 0, 1), y: 4000 },
                { x: new Date(2003, 0, 1), y: 6000 }, { x: new Date(2004, 0, 1), y: 8000 },
                { x: new Date(2005, 0, 1), y: 11000 }
        ],
      primaryXAxis: {
           valueType: 'DateTime',
            title: 'Years',
            labelFormat: 'y'
        },
         primaryYAxis: {
          valueType: 'Logarithmic',
           title: 'Profit',
           interval: 2
        },
      title: "Product X Growth [1995-2005]"
    };
  },
  provide: {
    chart: [LineSeries, Logarithmic, DateTime]
  }
};
</script>
<style>
 #container {
     height: 350px;
 }
</style>
```

{% endtab %}