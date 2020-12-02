---
title: " Chart Datetime Axis | Vue "

component: "Chart"

description: "Date time axis uses date time scale and displays the date time values as axis labels in the specified format."
---
<!-- markdownlint-disable MD036 -->

# DateTime and DateTimeCategory Axis

## DateTime Axis

 Date time axis uses date time scale and displays the date time values as axis labels in the specified format.

{% tab template="chart/axis/datetime" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Sales'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                 { x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
                 { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
                 { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }
        ],
      primaryXAxis: {
          valueType: 'DateTime',
          title: 'Sales Across Years',
          labelFormat: 'yMMM'
        },
         primaryYAxis: {
           title: 'Sales Amount in millions(USD)',
        },
      title: "Average Sales Comparison"
    };
  },
  provide: {
    chart: [LineSeries, DateTime]
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

>Note: To use datetime axis, we need to inject `DateTime` into the `provide` and
set the [`valueType`](../api/chart/axis/#valuetype) of axis to `DateTime`.

## DateTimeCategory Axis

Date-time category axis is used to display the date-time values with non-linear intervals. For example, the
business days alone have been depicted in a week here.

{% tab template="chart/axis/datetime" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container"  :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Sales'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, DateTimeCategory } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[{ x: new Date(2017, 11, 20), y: 21 }, { x: new Date(2017, 11, 21), y: 24 },
                { x: new Date(2017, 11, 22), y: 24 }, { x: new Date(2017, 11, 26), y: 70 },
                { x: new Date(2017, 11, 27), y: 75 }, { x: new Date(2018, 0, 2), y: 82 },
                { x: new Date(2018, 0, 3), y: 53 }, { x: new Date(2018, 0, 4), y: 54 },
                { x: new Date(2018, 0, 5), y: 53 }, { x: new Date(2018, 0, 8), y: 45 }
                ],
      primaryXAxis: {
           valueType: 'DateTimeCategory'
        },
         primaryYAxis: {
           title: 'Sales Amount in millions(USD)',
        },
      title: "Average Sales Comparison"
    };
  },
  provide: {
    chart: [LineSeries, DateTimeCategory]
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

>Note: To use datetime axis, we need to inject `DateTimeCategory` into the `provide` and
set the [`valueType`](../api/chart/axis/#valuetype) of axis to `DateTimeCategory`.

### Range

Range for an axis, will be calculated automatically based on the provided data, you can also customize the range
of the axis using [`minimum`](../api/chart/axis/#minimum), [`maximum`](../api/chart/axis/#maximum)
and [`interval`](../api/chart/axis/#interval) property of the axis.

{% tab template="chart/axis/datetime" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container"  :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Sales'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                 { x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
                 { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
                 { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }
        ],
      primaryXAxis: {
          valueType: 'DateTime',
            title: 'Sales Across Years',
            labelFormat: 'yMMM',
            minimum: new Date(2000, 6, 1),
            maximum: new Date(2010, 6, 1)
        },
      title: "Average Sales Comparison"
    };
  },
  provide: {
    chart: [LineSeries, DateTime]
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

### Interval Customization

Date time intervals can be customized by using the [`interval`](../api/chart/axis/#interval) and
[`intervalType`](../api/chart/axis/#intervaltype) properties of the axis.
For example, when you set interval as 2 and intervalType as years, it considers 2 years as interval.
DateTime axis supports following interval types,

* Auto
* Years
* Months
* Days
* Hours
* Minutes
* Seconds

{% tab template="chart/axis/datetime" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Sales'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                 { x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
                 { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
                 { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }
        ],
      primaryXAxis: {
           valueType: 'DateTime',
           intervalType: 'Years'
        },
      title: "Average Sales Comparison"
    };
  },
  provide: {
    chart: [LineSeries, DateTime]
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

**Applying Padding to the Range**

Padding can be applied to the minimum and maximum extremes of the range by using the
[`rangePadding`](../api/chart/axis/#rangepadding) property. Date time axis supports the following types
of padding,

* None
* Round
* Additional

**DateTime - None**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `None`, minimum and maximum of the axis is based on the data.

{% tab template="chart/axis/datetime" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Sales'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                 { x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
                 { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
                 { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }
        ],
      primaryXAxis: {
            valueType: 'DateTime',
            title: 'Sales Across Years',
            labelFormat: 'yMMM',
            rangePadding: 'None'
        },
      title: "Average Sales Comparison"
    };
  },
  provide: {
    chart: [LineSeries, DateTime]
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

**DateTime - Round**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `Round`, minimum and maximum will be
rounded to the nearest possible value divisible by interval. For example, when the minimum is 15th Jan, interval is
1 and the interval type is ‘month’, then the axis minimum will be Jan 1st.

{% tab template="chart/axis/datetime" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Sales'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                 { x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
                 { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
                 { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }
        ],
      primaryXAxis: {
            valueType: 'DateTime',
            title: 'Sales Across Years',
            labelFormat: 'yMMM',
            rangePadding: 'Round'
        },
      title: "Average Sales Comparison"
    };
  },
  provide: {
    chart: [LineSeries, DateTime]
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

**DateTime - Additional**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `Additional`, interval of an axis will
be padded to the minimum and maximum of the axis.

{% tab template="chart/axis/datetime" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Sales'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                 { x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
                 { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
                 { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }
        ],
      primaryXAxis: {
            valueType: 'DateTime',
            title: 'Sales Across Years',
            labelFormat: 'yMMM',
            rangePadding: 'Additional'
        },
      title: "Average Sales Comparison"
    };
  },
  provide: {
    chart: [LineSeries, DateTime]
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

## Label Format

You can format and parse the date to all globalize format using [`labelFormat`](../api/chart/axis/#labelformat) property in an axis.

{% tab template="chart/axis/datetime" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Sales'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                 { x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
                 { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
                 { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }
        ],
      primaryXAxis: {
            valueType: 'DateTime',
            title: 'Sales Across Years',
            labelFormat: 'yMd'
        },
      primaryYAxis: {
            title: 'Sales Amount in millions(USD)',
        },
      title: "Average Sales Comparison"
    };
  },
  provide: {
    chart: [LineSeries, DateTime]
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

The following table describes the result of applying some common date time formats to the labelFormat property

<!-- markdownlint-disable MD033 -->

<table>
<tr>
<td><b>Label Value</b></td>
<td><b>Label Format Property Value</b></td>
<td><b>Result </b></td>
<td><b>Description </b></td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>EEEE</td>
<td>Monday</td>
<td>The Date is displayed in day format</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>yMd</td>
<td>04/10/2000</td>
<td>The Date is displayed in month/date/year format</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td> MMM </td>
<td>Apr</td>
<td>The Shorthand month for the date is displayed</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>hm</td>
<td>12:00 AM</td>
<td>Time of the date value is displayed as label</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>hms</td>
<td>12:00:00 AM</td>
<td>The Label is displayed in hours:minutes:seconds format</td>
</tr>
</table>

<!-- markdownlint-disable MD033 -->