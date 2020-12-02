---
title: " Chart Numeric Axis | Vue "

component: "Chart"

description: "Numeric axis used to represent numeric values data in chart. we can customize the range, label format and ranga padding in numeric axis. "
---

<!-- markdownlint-disable MD036 -->

# Numeric Axis

You can use numeric axis to represent numeric values of data in chart. By default, the `valueType` of an axis is `Double`.

{% tab template="chart/axis/double" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Area' xName='x' yName='y' name='England'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, AreaSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData:[
    { x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 }, { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 }, { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 }, { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }],
      title: "England - Run Rate"
    };
  },
  provide: {
    chart: [AreaSeries]
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

## Range

Range for an axis, will be calculated automatically based on the provided data, you can also customize the range
of the axis using [`minimum`](../api/chart/axis/#minimum), [`maximum`](../api/chart/axis/#maximum)
and [`interval`](../api/chart/axis/#interval) property of the axis.

{% tab template="chart/axis/double" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Area' xName='x' yName='y' name='England'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, AreaSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
    { x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 }, { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 }, { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 }, { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }],
      primaryXAxis: {
          valueType: 'Double',
            minimum: 1,
            maximum: 20,
            interval: 5,
            title: 'Overs'
        },
      title: "England - Run Rate"
    };
  },
  provide: {
    chart: [AreaSeries]
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

## Range Padding

Padding can be applied to the minimum and maximum extremes of the axis range by using the
[`rangePadding`](../api/chart/axis/#rangepadding) property. Numeric axis supports following types of padding.

* None
* Round
* Additional
* Normal
* Auto

**Numeric - None**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `None`, minimum and maximum of an axis is based on the data.

{% tab template="chart/axis/double" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Area' xName='x' yName='y' name='England'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, AreaSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
    { x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 }, { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 }, { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 }, { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }],
      primaryXAxis: {
          valueType: 'Double',
            title: 'Overs'
        },
         primaryYAxis: {
           title: 'Runs',
           valueType: 'Double',
           rangePadding: 'None'
        },
      title: "England - Run Rate"
    };
  },
  provide: {
    chart: [AreaSeries]
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

**Numeric - Round**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `Round`, minimum and maximum will be
rounded to the nearest possible value divisible by interval. For example, when the minimum is 3.5 and the interval
is 1, then the minimum will be rounded to 3.

{% tab template="chart/axis/double" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Area' xName='x' yName='y' name='England'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, AreaSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
    { x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 }, { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 }, { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 }, { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }],
      primaryXAxis: {
          valueType: 'Double',
            title: 'Overs'
        },
         primaryYAxis: {
           title: 'Runs',
           valueType: 'Double',
           rangePadding: 'Round'
        },
      title: "England - Run Rate"
    };
  },
  provide: {
    chart: [AreaSeries]
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

**Numeric - Additional**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `Additional`, interval of an axis will
be padded to the minimum and maximum of the axis.

{% tab template="chart/axis/double" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Area' xName='x' yName='y' name='England'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, AreaSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
    { x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 }, { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 }, { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 }, { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }],
      primaryXAxis: {
          valueType: 'Double',
            title: 'Overs'
        },
         primaryYAxis: {
           title: 'Runs',
           valueType: 'Double',
           rangePadding: 'Additional'
        },
      title: "England - Run Rate"
    };
  },
  provide: {
    chart: [AreaSeries]
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

**Numeric - Normal**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `Normal`, padding is applied to the axis
based on default range calculation.

{% tab template="chart/axis/double" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Area' xName='x' yName='y' name='England'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, AreaSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
    { x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 }, { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 }, { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 }, { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }],
      primaryXAxis: {
          valueType: 'Double',
            title: 'Overs'
        },
         primaryYAxis: {
           title: 'Runs',
           valueType: 'Double',
            rangePadding: 'Normal'
        },
      title: "England - Run Rate"
    };
  },
  provide: {
    chart: [AreaSeries]
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

**Numeric - Auto**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `Auto`,horizontal numeric axis takes
None as padding calculation, while the vertical numeric axis takes Normal as padding calculation.

{% tab template="chart/axis/double" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Area' xName='x' yName='y' name='England'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, AreaSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
    { x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 }, { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 }, { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 }, { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }],
      primaryXAxis: {
          valueType: 'Double',
            title: 'Overs'
        },
         primaryYAxis: {
           title: 'Runs',
           valueType: 'Double',
            rangePadding: 'Auto'
        },
      title: "England - Run Rate"
    };
  },
  provide: {
    chart: [AreaSeries]
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

## Label Format

**Numeric Label Format**

Numeric labels can be formatted by using the [`labelFormat`](../api/chart/axis/#labelformat) property.
Numeric labels supports all globalize format.

{% tab template="chart/axis/double" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Product X' opacity=0.6> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                { x: 1900, y: 4, y1: 2.6, y2: 2.8 }, { x: 1920, y: 3.0, y1: 2.8, y2: 2.5 },
                { x: 1940, y: 3.8, y1: 2.6, y2: 2.8 }, { x: 1960, y: 3.4, y1: 3, y2: 3.2 },
                { x: 1980, y: 3.2, y1: 3.6, y2: 2.9 }, { x: 2000, y: 3.9, y1: 3, y2: 2 }
        ],
      primaryXAxis: {
          title: 'Year',
          edgeLabelPlacement: 'Shift'
        },
         primaryYAxis: {
           title: 'Sales Amount in Millions',
           labelFormat: 'c'
        },
      title: "Average Sales Comparison"
    };
  },
  provide: {
    chart: [LineSeries]
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

The following table describes the result of applying some commonly used label formats on numeric values.

<!-- markdownlint-disable MD033 -->

<table>
<tr>
<td><b>Label Value</b></td>
<td><b>Label Format property value</b></td>
<td><b>Result </b></td>
<td><b>Description </b></td>
</tr>
<tr>
<td>1000</td>
<td>n1</td>
<td>1000.0</td>
<td>The Number is rounded to 1 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>n2</td>
<td>1000.00</td>
<td>The Number is rounded to 2 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>n3</td>
<td>1000.000</td>
<td>The Number is rounded to 3 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p1</td>
<td>1.0%</td>
<td>The Number is converted to percentage with 1 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p2</td>
<td>1.00%</td>
<td>The Number is converted to percentage with 2 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p3</td>
<td>1.000%</td>
<td>The Number is converted to percentage with 3 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>c1</td>
<td>$1000.0</td>
<td>The Currency symbol is appended to number and number is rounded to 1 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>c2</td>
<td>$1000.00</td>
<td>The Currency symbol is appended to number and number is rounded to 2 decimal place</td>
</tr>
</table>

## GroupingSeperator

To separate groups of thousands, use [`useGroupingSeparator`](../api/chart/chartModel/#usegroupingseparator)
property in chart.

{% tab template="chart/axis/double" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' useGroupingSeparator='true'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Product X' opacity=0.6> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
     { x: 10, y: 7000 }, { x: 20, y: 1000 }, { x: 30, y: 12000 }, { x: 40, y: 14000 }, { x: 50, y: 11000 }, { x: 60, y: 5000 },
     { x: 70, y: 7300 }, { x: 80, y: 9000 }, { x: 90, y: 12000 }, { x: 100, y: 14000 }, { x: 110, y: 11000 }, { x: 120, y: 5000 },
        ],
      primaryXAxis: {
          title: 'Rate',
          edgeLabelPlacement: 'Shift'
        },
         primaryYAxis: {
           title: 'Sales Amount in Millions',
        },
      title: "Average Sales Comparison"
    };
  },
  provide: {
    chart: [ColumnSeries]
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

## Custom Label Format

Axis also supports custom label format using placeholder like {value}°C, in which the value represent the axis
label e.g 20°C.

{% tab template="chart/axis/double" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Product X' opacity=0.6> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                { x: 1900, y: 4, y1: 2.6, y2: 2.8 }, { x: 1920, y: 3.0, y1: 2.8, y2: 2.5 },
                { x: 1940, y: 3.8, y1: 2.6, y2: 2.8 }, { x: 1960, y: 3.4, y1: 3, y2: 3.2 },
                { x: 1980, y: 3.2, y1: 3.6, y2: 2.9 }, { x: 2000, y: 3.9, y1: 3, y2: 2 }
        ],
      primaryXAxis: {
          title: 'Year',
          edgeLabelPlacement: 'Shift'
        },
         primaryYAxis: {
           title: 'Sales Amount in Millions',
           labelFormat: '${value}k'
        },
      title: "Average Sales Comparison"
    };
  },
  provide: {
    chart: [LineSeries]
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