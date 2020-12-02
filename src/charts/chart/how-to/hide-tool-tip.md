# Hide the tooltip for unselected series

By using the [`tooltipRender`](../../api/chart/#tooltiprender) event,
you can cancel the tooltip for unselected series in the chart.

To hide the tooltip value in unselected series, follow the given steps:

**Step 1**:

By using the [`tooltipRender`](../../api/chart/#tooltiprender) event,
you can get the series elements in the arguments. By using this argument we can compare whether seriesElementclasslist is deselected container or not.
If it is true then we cancel the tooltip by setting the value for `args.cancel` as `true`.

{% tab template="chart/axis/category" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' selectionMode='Series'
         :tooltipRender='tooltipRender' :tooltip='tooltip'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Selection, Series, Tooltip } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
             { country: "USA", gold: 50, silver: 60 },
             { country: "China", gold: 40, silver: 50 },
             { country: "Japan", gold: 70, silver: 80 },
             { country: "Australia", gold: 60, silver: 70 },
             { country: "France", gold: 50, silver: 60 },
             { country: "Germany", gold: 40, silver: 50 },
             { country: "Italy", gold: 40, silver: 50 },
             { country: "Sweden", gold: 30, silver: 70 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
          primaryYAxis:
        {
            minimum: 0, maximum: 80,
            interval: 20, title: 'Medals'
        },
      title: "Olympic Medals",
      tooltip: { enable: true }
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Selection, Tooltip]
  },
   methods: {
        tooltipRender: function(args) {
       var series = (args.series);
       if (series.seriesElement.classList[0] === 'container_ej2_deselected') {
          args.cancel = true;
       }
        }
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