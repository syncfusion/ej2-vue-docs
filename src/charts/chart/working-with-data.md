---
title: " Chart Working With Data | Vue "

component: "Chart"

description: "Chart can be rendered by using different types of data source. They are called local data, remote data and empty points. "
---

# Working with Data

Chart can visualise data bound from local or remote data.

## Local Data

You can bind a simple JSON data to the chart using
[`dataSource`](../api/chart/series/#datasource) property in series. Now map the fields in JSON to
[`xName`](../api/chart/series/#xname) and [`yName`](../api/chart/series/#yname)
properties.

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='month' yName='sales' name='Sales'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
            { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
            { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
            { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
            { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
            { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category]
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

# Lazy loading

Lazy loading allows you to load data for chart on demand. Chart will fire the `scrollEnd` event, in that we can
get the minimum and maximum range of the axis, based on this, we can upload the data to chart.

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart ref='chart' :theme='theme' :chartArea='chartArea' width='80%' height='450' id='chartid' :scrollEnd='scrollEnd'
            :primaryXAxis='primaryXAxis' :legendSettings='legend' :title='title' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='series' xName= 'x' yName= 'y' type='Line' :animation='animation'>
                </e-series>
            </e-series-collection>
         </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin,LineSeries,Zoom, Legend,DateTime,ScrollBar} from "@syncfusion/ej2-vue-charts";
import { Browser, Internationalization } from "@syncfusion/ej2-base";
Vue.use(ChartPlugin);
let intl = new Internationalization();
export let GetDateTimeData = (start, end) => {
  let series = [];
  let point1;
  let date;
  let value = 80;
  let option = {
    skeleton: "full",
    type: "dateTime"
  };
  let dateParser = intl.getDateParser(option);
  let dateFormatter = intl.getDateFormat(option);
  for (let i = 1; start <= end; i++) {
    date = Date.parse(dateParser(dateFormatter(start)));
    if (Math.random() > 0.5) {
      value += Math.random() * 10 - 5;
    } else {
      value -= Math.random() * 10 - 5;
    }
    if (value < 0) {
      value = getRandomInt(20, 40);
    }
    let point1 = { x: new Date(date), y: Math.round(value) };
    new Date(start.setDate(start.getDate() + 1));
    series.push(point1);
  }
  return series;
};

export default {
  data() {
    return {
      primaryXAxis: {
        title: "Day",
        valueType: "DateTime",
        skeleton: "yMMM",
        skeletonType: "Date",
        edgeLabelPlacement: "Shift",
        scrollbarSettings: {
          range: {
            minimum: new Date(2009, 0, 1),
            maximum: new Date(2014, 0, 1)
          },
          enable: true,
          pointsLength: 1000
        }
      },
      //Initializing Primary Y Axis
      primaryYAxis: {
        title: "Server Load",
        labelFormat: "{value}MB"
      },
      legend: {
        visible: true
      },
      series: seriesData,
      animation: { enable: false },
      chartArea: {
        border: {
          width: 0
        }
      },
      title: "Network Load"
    };
  },
  provide: {
    chart: [ColumnSeries, Category]
  }
  methods: {
    scrollEnd: function(args) {
      if (lazymodeid.value === "Range") {
        this.$refs.chart.ej2Instances.series[0].dataSource = GetDateTimeData(
          args.currentRange.minimum,
          args.currentRange.maximum
        );
      }
      this.$refs.chart.dataBind();
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

## Common Datasource

You can also bind a JSON data common to all series using
[`dataSource`](../api/chart/series/#datasource) property in chart.

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :dataSource='seriesData'>
            <e-series-collection>
                <e-series type='Column' xName='month' yName='sales' > </e-series>
                <e-series type='Column' xName='month' yName='sales1' > </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
      { month: 'Jan', sales: 35, sales1: 28 }, { month: 'Feb', sales: 28, sales1: 35 },
      { month: 'Mar', sales: 34, sales1: 32 }, { month: 'Apr', sales: 32, sales1: 34 },
      { month: 'May', sales: 40, sales1: 32 }, { month: 'Jun', sales: 32, sales1: 40 },
      { month: 'Jul', sales: 35, sales1: 55 }, { month: 'Aug', sales: 55, sales1: 35 },
      { month: 'Sep', sales: 38, sales1: 30 }, { month: 'Oct', sales: 30, sales1: 38 },
      { month: 'Nov', sales: 25, sales1: 32 }, { month: 'Dec', sales: 32, sales1: 25 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category]
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

## Remote Data

You can also bind remote data to the chart using `DataManager`. The DataManager requires minimal information
like webservice URL, adaptor and crossDomain to interact with service endpoint properly. Assign the instance
 of DataManager to the [`dataSource`](../api/chart/series/#datasource) property in series and map
 the fields of data to [`xName`](../api/chart/series/#xname) and
[`yName`](../api/chart/series/#yname) properties. You can also use the
[`query`](../api/chart/series/#query) property of the series to filter the data.

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='Assignee' yName='Estimate' :query='queries' name='Story Point'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category } from "@syncfusion/ej2-vue-charts";
import { DataManager, Query } from '@syncfusion/ej2-data';

Vue.use(ChartPlugin);

let dataManager = new DataManager({
    url: 'https://mvc.syncfusion.com/Services/Northwnd.svc/Tasks/'
});
let query = new Query().take(5).where('Estimate', 'lessThan', 3, false);

export default {
  data() {
    return {
      seriesData: dataManager,
      queries: query,
        primaryXAxis: {
           rangePadding: 'Additional',
           valueType: 'Category',
           title: 'Assignee'
        },
        primaryYAxis: {
           title: 'Estimate',
            minimum: 0,
            maximum: 3,
            interval: 1
        }
    };
  },
  provide: {
    chart: [ColumnSeries, Category]
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

## Empty points

The Data points that uses the `null` or `undefined` as value are considered as empty points.
Empty data points are ignored and not plotted in the Chart.
When the data is provided by using the points property,
By using `emptyPointSettings` property in series, you can customize the empty point. Default `mode` of the empty point is `Gap`.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='month' yName='sales' name='Sales' :emptyPointSettings='emptyPointSettings1'></e-series>
                <e-series :dataSource='seriesData' type='Line' xName='month' yName='sales' name='Sales Compare' :emptyPointSettings='emptyPointSettings2'></e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, LineSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { month: 'Jan', sales: 35 }, { month: 'Feb', sales: null },
            { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
            { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
            { month: 'Jul', sales: undefined }, { month: 'Aug', sales: 55 },
            { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
            { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
      emptyPointSettings1: {
           mode: "Average",
           fill:'grey'
        },
         emptyPointSettings2: {
           mode: "Gap"
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, LineSeries, Category]
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

* Customizing empty point

Specific color for empty point can be set by `fill` property in `emptyPointSettings`. Border for a empty point can be set by
`border` property.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='month' yName='sales' name='Sales' :emptyPointSettings='emptyPointSettings'></e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, LineSeries, Category } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
            { month: 'Jan', sales: 35 }, { month: 'Feb', sales: null },
            { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
            { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
            { month: 'Jul', sales: undefined }, { month: 'Aug', sales: 55 },
            { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
            { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
              ],
        primaryXAxis: {
           valueType: 'Category'
        },
      emptyPointSettings: {
           mode: "Average",
            fill: 'red',
            border: { width: 2, color: 'violet'}
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, LineSeries, Category]
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