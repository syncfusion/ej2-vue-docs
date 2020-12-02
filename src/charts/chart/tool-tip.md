---
title: " Chart Tooltip | Vue "

component: "Chart"

description: "Tooltip is used to show the data value when mouse hover on the chart.We can able to customize format,template and appearance."
---

# Tooltip

<!-- markdownlint-disable MD036 -->

Chart will display details about the points through tooltip, when the mouse is moved over the point.

## Default Tooltip

By default, tooltip is not visible. Enable the tooltip by setting
[`enable`](../api/chart/tooltipSettingsModel/#enable) property to true and by injecting `Tooltip`
into the `provide`.

{% tab template="chart/user-interaction/tooltip" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :tooltip='tooltip'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StepLine' xName='x' yName='y' name='China' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StepLineSeries, DateTime, Tooltip } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                { x: new Date(1975, 0, 1), y: 16, y1: 10, y2: 4.5 },
                { x: new Date(1980, 0, 1), y: 12.5, y1: 7.5, y2: 5 },
                { x: new Date(1985, 0, 1), y: 19, y1: 11, y2: 6.5 },
                { x: new Date(1990, 0, 1), y: 14.4, y1: 7, y2: 4.4 },
                { x: new Date(1995, 0, 1), y: 11.5, y1: 8, y2: 5 },
                { x: new Date(2000, 0, 1), y: 14, y1: 6, y2: 1.5 },
                { x: new Date(2005, 0, 1), y: 10, y1: 3.5, y2: 2.5 },
                { x: new Date(2010, 0, 1), y: 16, y1: 7, y2: 3.7 }
        ],
      primaryXAxis: {
           valueType: 'DateTime'
        },
      marker: {
                    visible: true, width: 10, height: 10
        },
      tooltip: {enable: true},
      title: "Unemployment Rates 1975-2010"
    };
  },
  provide: {
    chart: [StepLineSeries, DateTime, Tooltip]
  },
};
</script>
<style>
 #container{
   height: 350px;
 }
</style>
```

{% endtab %}

<!-- markdownlint-disable MD013 -->

## Format the Tooltip

<!-- markdownlint-disable MD013 -->

By default, tooltip shows information of x and y value in points. In addition to that, you can show more
information in tooltip. For example the format '${series.name} ${point.x}' shows series name and point x
value.

{% tab template="chart/user-interaction/tooltip" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :tooltip='tooltip'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StepLine' xName='x' yName='y' name='China' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StepLineSeries, DateTime, Tooltip } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                { x: new Date(1975, 0, 1), y: 16, y1: 10, y2: 4.5 },
                { x: new Date(1980, 0, 1), y: 12.5, y1: 7.5, y2: 5 },
                { x: new Date(1985, 0, 1), y: 19, y1: 11, y2: 6.5 },
                { x: new Date(1990, 0, 1), y: 14.4, y1: 7, y2: 4.4 },
                { x: new Date(1995, 0, 1), y: 11.5, y1: 8, y2: 5 },
                { x: new Date(2000, 0, 1), y: 14, y1: 6, y2: 1.5 },
                { x: new Date(2005, 0, 1), y: 10, y1: 3.5, y2: 2.5 },
                { x: new Date(2010, 0, 1), y: 16, y1: 7, y2: 3.7 }
        ],
      primaryXAxis: {
           valueType: 'DateTime'
        },
      marker: {
          visible: true, width: 10, height: 10
        },
      tooltip: { enable: true, header: 'Unemployment', format: '<b>${point.x} : ${point.y}</b>'},
      title: "Unemployment Rates 1975-2010"
    };
  },
  provide: {
    chart: [StepLineSeries, DateTime, Tooltip]
  },
};
</script>
<style>
 #container{
   height: 350px;
 }
</style>
```

{% endtab %}

<!-- markdownlint-disable MD013 -->

## Individual Series Format

<!-- markdownlint-disable MD013 -->

 You can format the each series tooltip separately using series `tooltipFormat` property.

 >Note: If series `tooltipFormat` is given, it shows the tooltip for that series in that format, or else it will take tooltip format.

{% tab template="chart/user-interaction/tooltip" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :tooltip='tooltip'>
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Spline' xName='x' yName='y' name='Max Temp' :marker='marker' tooltipFormat='${point.x}'> </e-series>
                <e-series :dataSource='seriesData2' type='Spline' xName='x' yName='y' name='Avg Temp' :marker='marker' tooltipFormat='${point.y}'> </e-series>
                <e-series :dataSource='seriesData3' type='Spline' xName='x' yName='y' name='Min Temp' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, SplineSeries, DateTime, Tooltip } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData1:[
                { x: 'Sun', y: 15 }, { x: 'Mon', y: 22 },
                { x: 'Tue', y: 32 },
                { x: 'Wed', y: 31 },
                { x: 'Thu', y: 29 }, { x: 'Fri', y: 24 },
                { x: 'Sat', y: 18 },
            ],
    seriesData2:[
                { x: 'Sun', y: 10 }, { x: 'Mon', y: 18 },
                { x: 'Tue', y: 28 },
                { x: 'Wed', y: 28 },
                { x: 'Thu', y: 26 }, { x: 'Fri', y: 20 },
                { x: 'Sat', y: 15 }
            ],
    seriesData3:[
                { x: 'Sun', y: 2 }, { x: 'Mon', y: 12 },
                { x: 'Tue', y: 22 },
                { x: 'Wed', y: 23 },
                { x: 'Thu', y: 19 }, { x: 'Fri', y: 13 },
                { x: 'Sat', y: 8 },
            ],
      primaryXAxis: {
           valueType: 'Category'
        },
      marker: {
          visible: true, width: 10, height: 10
        },
      tooltip: { enable: true, header: 'Unemployment', format: '<b>${point.x} : ${point.y}</b>'},
      title: "NC Weather Report - 2016"
    };
  },
  provide: {
    chart: [SplineSeries, DateTime, Tooltip]
  },
};
</script>
<style>
 #container{
   height: 350px;
 }
</style>
```

{% endtab %}

<!-- markdownlint-disable MD013 -->

## Tooltip Template

Any HTML elements can be displayed in the tooltip by using the ‘template’ property of the tooltip. You can use the ${x} and ${y} as place holders in the HTML element to display the x and y values of the corresponding data point.

{% tab template="chart/user-interaction/tooltip" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :tooltip='tooltip'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StepLine' xName='x' yName='y' name='China' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StepLineSeries, DateTime, Tooltip } from "@syncfusion/ej2-vue-charts";

    var TemplateVue = Vue.component('contentTemplate', {
        template: `<div>
                   <table style="width:100%;  border: 1px solid black;">
                   <tr><th colspan="2" bgcolor="#00FFFF">Unemployment</th></tr>
                    <tr><td bgcolor="#00FFFF">{{data.x}}:</td><td bgcolor="#00FFFF">{{data.y}}</td></tr>
                   </table></div> `,
        data() {
            return {
                data: {}
            };
        }
    });

    let contentTemplate = function() {
  return { template: TemplateVue };
};

Vue.use(ChartPlugin);


export default {
  data() {
    return {
    seriesData:[
                { x: new Date(1975, 0, 1), y: 16, y1: 10, y2: 4.5 },
                { x: new Date(1980, 0, 1), y: 12.5, y1: 7.5, y2: 5 },
                { x: new Date(1985, 0, 1), y: 19, y1: 11, y2: 6.5 },
                { x: new Date(1990, 0, 1), y: 14.4, y1: 7, y2: 4.4 },
                { x: new Date(1995, 0, 1), y: 11.5, y1: 8, y2: 5 },
                { x: new Date(2000, 0, 1), y: 14, y1: 6, y2: 1.5 },
                { x: new Date(2005, 0, 1), y: 10, y1: 3.5, y2: 2.5 },
                { x: new Date(2010, 0, 1), y: 16, y1: 7, y2: 3.7 }
        ],
      primaryXAxis: {
           valueType: 'DateTime'
        },
      marker: {
          visible: true, width: 10, height: 10
        },
      tooltip: { enable: true,  template: contentTemplate },
      title: "Unemployment Rates 1975-2010"
    };
  },
  provide: {
    chart: [StepLineSeries, DateTime, Tooltip]
  },
};
</script>
<style>
 #container{
   height: 350px;
 }
</style>

```

{% endtab %}

## Customize the Appearance of Tooltip

The [`fill`](../api/chart/tooltipSettingsModel/#fill) and [`border`](../api/chart/tooltipSettingsModel/#border) properties are used to customize the background color and border of the tooltip respectively. The [`textStyle`](../api/chart/tooltipSettingsModel/#textstyle) property in the tooltip is used to customize the font of the tooltip text.

{% tab template="chart/user-interaction/tooltip" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :tooltip='tooltip'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='StepLine' xName='x' yName='y' name='China' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, StepLineSeries, DateTime, Tooltip } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                { x: new Date(1975, 0, 1), y: 16, y1: 10, y2: 4.5 },
                { x: new Date(1980, 0, 1), y: 12.5, y1: 7.5, y2: 5 },
                { x: new Date(1985, 0, 1), y: 19, y1: 11, y2: 6.5 },
                { x: new Date(1990, 0, 1), y: 14.4, y1: 7, y2: 4.4 },
                { x: new Date(1995, 0, 1), y: 11.5, y1: 8, y2: 5 },
                { x: new Date(2000, 0, 1), y: 14, y1: 6, y2: 1.5 },
                { x: new Date(2005, 0, 1), y: 10, y1: 3.5, y2: 2.5 },
                { x: new Date(2010, 0, 1), y: 16, y1: 7, y2: 3.7 }
        ],
      primaryXAxis: {
           valueType: 'DateTime'
        },
      marker: {
          visible: true, width: 10, height: 10
        },
      tooltip: { enable: true,
                format: '${series.name} ${point.x} : ${point.y}',
                fill: '#7bb4eb',
                border: {
                   width: 2,
                   color: 'grey'
                }},
      title: "Unemployment Rates 1975-2010"
    };
  },
  provide: {
    chart: [StepLineSeries, DateTime, Tooltip]
  },
};
</script>
<style>
 #container{
   height: 350px;
 }
</style>
```

{% endtab %}

## Tooltip Mapping Name

By default, tooltip shows information of x and y value in points. You can show more information from data source in tooltip by using the `tooltipMappingName` property of the tooltip. You can use the `${point.tooltip}` as place holders to display the specified tooltip content.

{% tab template="chart/user-interaction/tooltip" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :tooltip='tooltip'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' tooltipMappingName='text' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Tooltip } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
    seriesData:[
                    { x: 'Germany', y: 72, text: 'GER: 72'},
                    { x: 'Russia', y: 103.1, text: 'RUS: 103.1'},
                    { x: 'Brazil', y: 139.1, text: 'BRZ: 139.1'},
                    { x: 'India', y: 462.1, text: 'IND: 462.1'},
                    { x: 'China', y: 721.4, text: 'CHN: 721.4'},
                    { x: 'United States Of America', y: 286.9, text: 'USA: 286.9'},
                    { x: 'Great Britain', y: 115.1, text: 'GBR: 115.1'},
                    { x: 'Nigeria', y: 97.2, text: 'NGR: 97.2'},
        ],
      primaryXAxis: {
           valueType: 'Category'
        },
      marker: {
          visible: true, width: 10, height: 10
        },
      tooltip: {enable: true, format: '${point.tooltip}'},
      title: 'Internet Users in Million – 2016',
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Tooltip]
  },
};
</script>
<style>
#container{
   height: 350px;
 }
</style>
```

{% endtab %}