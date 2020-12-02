---
title: " Chart Print and Export | Vue "

component: "Chart"

description: "The rendered chart can be printed or exported directly from the browser by calling the public method print and export."
---

# Print and Export

## Print

The rendered chart can be printed directly from the browser by calling the public method print.
You can pass array of ID of elements or element to this method. By default it take element of the chart.

{% tab template= "chart/series/polar" %}

```html
<template>
    <div id="app">
     <ejs-button id='print' @click.native='print'>Print</ejs-button>
         <ejs-chart ref="chart" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' style="float: left">
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Polar' xName='x' yName='y' drawType='Area'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, PolarSeries, Category, AreaSeries } from "@syncfusion/ej2-vue-charts";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(ChartPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
    seriesData:[
     { x: 'Jan', y: -1 }, { x: 'Feb', y: -1 }, { x: 'Mar', y: 2 },
    { x: 'Apr', y: 8 }, { x: 'May', y: 13 }, { x: 'Jun', y: 18 },
    { x: 'Jul', y: 21 }, { x: 'Aug', y: 20 }, { x: 'Sep', y: 16 },
    { x: 'Oct', y: 10 }, { x: 'Nov', y: 4 }, { x: 'Dec', y: 0 }
     ],
      primaryXAxis: {
          valueType: 'Category'
        },
         primaryYAxis: {
            minimum: -5, maximum: 35, interval: 10,
            title: 'Temperature in Celsius',
            labelFormat: '{value}C'
        },
      title: "Climate Graph-2012"
    };
  },
  provide: {
    chart: [PolarSeries, Category, AreaSeries]
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

## Export

The rendered chart can be exported to `JPEG`, `PNG`, `SVG`, or `PDF` format using the export method in chart. The input parameters for this method are `Export Type` for format and `fileName` for result.

The optional parameters for this method are,
* `orientation` - either portrait or landscape,
* `controls` - pass collections of controls for multiple export,
* `width` - width of chart export, and
* `height` - height of chart export.

{% tab template= "chart/series/polar" %}

```html
<template>
    <div id="app">
         <ejs-chart ref="chart" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :loaded='loaded'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Polar' xName='x' yName='y' drawType='Area'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, PolarSeries, Category, AreaSeries, Export } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
     { x: 'Jan', y: -1 }, { x: 'Feb', y: -1 }, { x: 'Mar', y: 2 },
    { x: 'Apr', y: 8 }, { x: 'May', y: 13 }, { x: 'Jun', y: 18 },
    { x: 'Jul', y: 21 }, { x: 'Aug', y: 20 }, { x: 'Sep', y: 16 },
    { x: 'Oct', y: 10 }, { x: 'Nov', y: 4 }, { x: 'Dec', y: 0 }
     ],
      primaryXAxis: {
          valueType: 'Category'
        },
         primaryYAxis: {
            minimum: -5, maximum: 35, interval: 10,
            title: 'Temperature in Celsius',
            labelFormat: '{value}C'
        },
      title: "Climate Graph-2012"
    };
  },
  provide: {
    chart: [PolarSeries, Category, AreaSeries, Export]
  },
  methods: {
    loaded: function(args) {
         args.chart.exportModule.export('PNG', 'export');
   }
  }
};
</script>
```

{% endtab %}

## Multiple Chart Export

You can export the multiple charts in single page by passing the multiple chart objects in the export
method of chart.

To export multiple charts in a single page, follow the given steps:

**Step 1**:

Initially, render more than one chart to export, and then add button to export the multiple charts. In
button click, call the export private method in charts, and then pass the multiple chart objects in the
export method.

{% tab template="chart/series/column" %}

```html
<template>
    <div id="app">
    <ejs-button cssClass="e-flat" iconCss='e-icons e-export-icon' isPrimary=true v-on:click.native='onClick' id="exportBtn">EXPORT</ejs-button>
         <ejs-chart ref="chart" id="container":title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold'> </e-series>
            </e-series-collection>
        </ejs-chart>
        <ejs-chart ref="chart1" id="container1":title='title' :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Export } from "@syncfusion/ej2-vue-charts";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(ChartPlugin);
Vue.use(ButtonPlugin);

export default {
  data: function() {
    return {
      seriesData: [
             { country: "USA", gold: 50 },
             { country: "China", gold: 40 },
             { country: "Japan", gold: 70 },
             { country: "Australia", gold: 60 },
             { country: "France", gold: 50 },
             { country: "Germany", gold: 40 },
             { country: "Italy", gold: 40 },
             { country: "Sweden", gold: 30 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Export]
  },
   methods: {
        onClick: function(args) {
      let chart1 = document.getElementById("container").ej2_instances[0];
      let chart2 = document.getElementById("container1").ej2_instances[0];
      chart1.exportModule.export('PNG', 'Chart', null, [chart1, chart2]);
    },
  }
};
</script>
<style>
 #container {
   height: 350px;
 }
  .e-export-icon::before {
   content: '\e728';
 }
</style>
```

{% endtab %}