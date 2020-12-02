---
title: " Chart Selection | Vue "

component: "Chart"

description: "Strip Lines are vertical or horizontal lines used to highlight/mark a certain region on the plot area."
---

<!-- markdownlint-disable MD036 -->

# Selection

Chart provides selection support for the series and its data points on mouse click.

>When Mouse is clicked on the data points, the corresponding series legend will also be selected.

We have different type of selection mode for selecting the data. They are,

* None
* Point
* Series
* Cluster
* DragXY
* DragX
* DragY

## Point

 You can select a point, by setting `selectionMode` to point.

{% tab template="chart/user-interaction/selection" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' selectionMode='Point'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend, Selection  } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend, Selection  ]
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

>Note: To use select feature, we need to Inject `Selection` into the `provide`.

## Series

 You can select a series, by setting `selectionMode` to series.

{% tab template="chart/user-interaction/selection" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' selectionMode='Series'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend, Selection } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend, Selection]
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

## Cluster

You can select the points that corresponds to the same index in all the series, by setting `selectionMode` to
cluster.

{% tab template="chart/user-interaction/selection" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' selectionMode='Cluster'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend, Selection } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend, Selection]
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

## Rectangular selection

**DragXY, DragX and DragY**

To fetch the collection of data under a particular region, you have to set `selectionMode` as `DragXY`.

* DragXY - Allows us to select data with respect to horizontal and vertical axis.
* DragX - Allows us to select data with respect to horizontal axis.
* DragY - Allows us to select data with respect to vertical axis.

The selected data’s are returned as an array collection in the [`dragComplete`](../api/chart/iDragCompleteEventArgs/)
event.

{% tab template="chart/user-interaction/drag" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' selectionMode='DragXY'>
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Scatter' xName='x' yName='y' name='Male' opacity=0.7> </e-series>
                <e-series :dataSource='seriesData2' type='Scatter' xName='x' yName='y' name='Female' opacity=0.7> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ScatterSeries, Legend, Selection } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1: Object[] = [];
let series2: Object[] = [];
let point1: Object;
let value: number = 80;
let value1: number = 70;
let i: number;
for (i = 1; i < 50; i++) {
    if (Math.random() > 0.5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    value = value < 60 ? 60 : value > 90 ? 90 : value;
    point1 = { x: 120 + (i / 2), y: value.toFixed(1) };
    series1.push(point1);
}
for (i = 1; i < 50; i++) {
    if (Math.random() > 0.5) {
        value1 += Math.random();
    } else {
        value1 -= Math.random();
    }
    value1 = value1 < 60 ? 60 : value1 > 90 ? 90 : value1;
    point1 = { x: 120 + (i / 2), y: value1.toFixed(1) };
    series2.push(point1);
}

export default {
  data() {
    return {
      seriesData1: series1,
      seriesData2: series2,
      primaryXAxis: {
            title: 'Height (cm)',
            minimum: 120, maximum: 180,
            edgeLabelPlacement: 'Shift',
            labelFormat: '{value}cm'
        },
        primaryYAxis: {
            title: 'Weight (kg)',
            minimum: 60, maximum: 90,
            labelFormat: '{value}kg',
            rangePadding: 'None'
        },
        title: 'Height Vs Weight'
    };
  },
  provide: {
    chart: [ScatterSeries, Legend, Selection]
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

## Lasso selection

To select a region by drawing freehand shapes to fetch a collection of data use `selectionMode` as `Lasso`. You can also select multiple regions on the chart through this mode.

{% tab template="chart/user-interaction/drag" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' selectionMode='Lasso'>
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Scatter' xName='x' yName='y' name='Male' opacity=0.7> </e-series>
                <e-series :dataSource='seriesData2' type='Scatter' xName='x' yName='y' name='Female' opacity=0.7> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ScatterSeries, Legend, Selection } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1: Object[] = [];
let series2: Object[] = [];
let point1: Object;
let value: number = 80;
let value1: number = 70;
let i: number;
for (i = 1; i < 50; i++) {
    if (Math.random() > 0.5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    value = value < 60 ? 60 : value > 90 ? 90 : value;
    point1 = { x: 120 + (i / 2), y: value.toFixed(1) };
    series1.push(point1);
}
for (i = 1; i < 50; i++) {
    if (Math.random() > 0.5) {
        value1 += Math.random();
    } else {
        value1 -= Math.random();
    }
    value1 = value1 < 60 ? 60 : value1 > 90 ? 90 : value1;
    point1 = { x: 120 + (i / 2), y: value1.toFixed(1) };
    series2.push(point1);
}

export default {
  data() {
    return {
      seriesData1: series1,
      seriesData2: series2,
      primaryXAxis: {
            title: 'Height (cm)',
            minimum: 120, maximum: 180,
            edgeLabelPlacement: 'Shift',
            labelFormat: '{value}cm'
        },
        primaryYAxis: {
            title: 'Weight (kg)',
            minimum: 60, maximum: 90,
            labelFormat: '{value}kg',
            rangePadding: 'None'
        },
        title: 'Height Vs Weight'
    };
  },
  provide: {
    chart: [ScatterSeries, Legend, Selection]
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

## Multi-region selection

To select multiple region on the chart, set the `allowMultiSelection` property to true.

{% tab template="chart/user-interaction/drag" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' selectionMode='DragXY' allowMultiSelection='true'>
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Scatter' xName='x' yName='y' name='Male' opacity=0.7> </e-series>
                <e-series :dataSource='seriesData2' type='Scatter' xName='x' yName='y' name='Female' opacity=0.7> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ScatterSeries, Legend, Selection } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1: Object[] = [];
let series2: Object[] = [];
let point1: Object;
let value: number = 80;
let value1: number = 70;
let i: number;
for (i = 1; i < 50; i++) {
    if (Math.random() > 0.5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    value = value < 60 ? 60 : value > 90 ? 90 : value;
    point1 = { x: 120 + (i / 2), y: value.toFixed(1) };
    series1.push(point1);
}
for (i = 1; i < 50; i++) {
    if (Math.random() > 0.5) {
        value1 += Math.random();
    } else {
        value1 -= Math.random();
    }
    value1 = value1 < 60 ? 60 : value1 > 90 ? 90 : value1;
    point1 = { x: 120 + (i / 2), y: value1.toFixed(1) };
    series2.push(point1);
}

export default {
  data() {
    return {
      seriesData1: series1,
      seriesData2: series2,
      primaryXAxis: {
            title: 'Height (cm)',
            minimum: 120, maximum: 180,
            edgeLabelPlacement: 'Shift',
            labelFormat: '{value}cm'
        },
        primaryYAxis: {
            title: 'Weight (kg)',
            minimum: 60, maximum: 90,
            labelFormat: '{value}kg',
            rangePadding: 'None'
        },
        title: 'Height Vs Weight'
    };
  },
  provide: {
    chart: [ScatterSeries, Legend, Selection]
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

## Selection type

You can select multiple points or series, by enabling the [`isMultiSelect`](../api/chart/chartModel/#ismultiselect) property.

{% tab template="chart/user-interaction/selection" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' selectionMode='Point' isMultiSelect='true'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend, Selection } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend, Selection]
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

## Selection on load

You can able to select a point or series programmatically on a chart using
[`selectedDataIndexes`](../api/chart/chartModel/#selecteddataindexes) property.

{% tab template="chart/user-interaction/selection" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'  selectionMode='Point' isMultiSelect='true' :selectedDataIndexes='selectedData'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold'  :animation='animation' selectionStyle='chartSelection1'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver' :animation='animation' selectionStyle='chartSelection1'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze' :animation='animation' selectionStyle='chartSelection1'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend, Selection } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
        selectedData:[
        { series: 0, point: 1}, { series: 2, point: 3}
       ],
      animation:{ enable: false},
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend, Selection]
  }
};
</script>
<style>
 #container {
   height: 350px;
 }
  .chartSelection1 {
    fill: red
}

.chartSelection2 {

    fill: green

}

.chartSelection3 {
    fill: blue
}
</style>
```

{% endtab %}

## Selection through on legend

You can able to select a point or series through on legend using
[`toggleVisibility`](../api/chart/legendSettingsModel/#togglevisibility) property.

{% tab template="chart/user-interaction/selection" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'  :legendSettings='legendSettings' selectionMode='Point'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold' :animation='animation'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver'  :animation='animation'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze' :animation='animation'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend, Selection } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
      animation: { enable: false },
      legendSettings: { visible: true, toggleVisibility: false }
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend, Selection]
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

## Customization for selection

You can apply custom style to selected points or series with [`selectionStyle`](../api/chart/series/#selectionstyle) property.

{% tab template="chart/user-interaction/selection" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis'  selectionMode='Point' isMultiSelect='true'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='gold' name='Gold' selectionStyle='chartSelection1'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='silver' name='Silver' selectionStyle='chartSelection2'> </e-series>
                <e-series :dataSource='seriesData' type='Column' xName='country' yName='bronze' name='Bronze' selectionStyle='chartSelection3'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, Legend, Selection } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                { country: "USA", gold: 50, silver: 70, bronze: 45 },
                { country: "China", gold: 40, silver: 60, bronze: 55 },
                { country: "Japan", gold: 70, silver: 60, bronze: 50 },
                { country: "Australia", gold: 60, silver: 56, bronze: 40 },
                { country: "France", gold: 50, silver: 45, bronze: 35 },
                { country: "Germany", gold: 40, silver: 30, bronze: 22 },
                { country: "Italy", gold: 40, silver: 35, bronze: 37 },
                { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
              ],
        primaryXAxis: {
           valueType: 'Category',
           title: 'Countries'
        },
      animation: { enable: false },
      legendSettings: { visible: true, toggleVisibility: false }
      title: "Olympic Medals"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, Legend, Selection]
  }
};
</script>
<style>
 #container {
   height: 350px;
 }
 .chartSelection1 {
    fill: red
}

.chartSelection2 {

    fill: green

}

.chartSelection3 {
    fill: blue
}
</style>
```

{% endtab %}