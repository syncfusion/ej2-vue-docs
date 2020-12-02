---
title: " Chart Zooming | Vue "

component: "Chart"

description: "Chart have zooming and panning properties. Chart contains different  zoom modes, zoom toolbar items, scrollbar and auto interval zooming. "
---

# Zooming  and Panning

## Enable Zooming

Chart can be zoomed in three ways.

* Selection - By setting [`enableSelectionZooming`](../api/chart/zoomSettingsModel/#enableselectionzooming) property to true
  in `zoomSettings`, you can zoom the chart by using the rubber band selection.
* Mousewheel - By setting [`enableMouseWheelZooming`](../api/chart/zoomSettingsModel/#enablemousewheelzooming) property to true
  in `zoomSettings`, you can zoomin and zoomout the chart by scrolling the mouse wheel.
* Pinch - By setting  [`enablePinchZooming`](../api/chart/zoomSettingsModel/#enablepinchzooming) property to true in `zoomSettings`,
  you can zoom the chart through pinch gesture in touch enabled devices.

 >Pinch zooming is supported only in browsers that support multi-touch gestures. Currently IE11, Chrome and Opera

 browsers support multi-touch in desktop devices.

{% tab template="chart/user-interaction/zoom" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :zoomSettings='zoom' :legendSettings='legend'>
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Area' xName='x' yName='y' name='Product X' :border='border' :animation='animation'
                opacity=0.3> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, AreaSeries, DateTime, Zoom } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1: Object[] = [];
let point1: Object;
let value: number = 40;
let i: number;
for (i = 1; i < 500; i++) {
    if (Math.random() > .5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    point1 = { x: new Date(1950, i + 2, i), y: value.toFixed(1) };
    series1.push(point1);
}

export default {
  data() {
    return {
      seriesData1: series1,
      primaryXAxis: {
           valueType: 'DateTime',
           labelFormat: 'yMMM'
        },
        zoom:
        {
            enableMouseWheelZooming: true,
            enablePinchZooming: true,
            enableSelectionZooming: true
        },
        title: 'Sales History of Product X',
        legend: { visible: false },
        border: { width: 0.5, color: '#00bdae' },
        animation: { enable: false }
    };
  },
  provide: {
    chart: [AreaSeries,  DateTime, Zoom]
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

>Note: To use zooming feature, we need to inject `Zoom` into the `provide`.

After zooming the chart, a zooming toolbar will appear with `zoom`,`zoomin`, `zoomout`, `pan` and `reset` buttons.
Selecting the Pan option will allow to pan the chart and selecting the Reset option will reset the zoomed chart.

## Modes

The [`mode`](../api/chart/zoomSettings/#mode) property in zoomSettings specifies whether the chart is
allowed to scale along the horizontal axis or vertical axis. The default value of the mode is XY (both axis).

There are three types of mode.

* X - Allows us to zoom the chart horizontally.
* Y - Allows us to zoom the chart vertically.
* XY - Allows us to zoom the chart both vertically and horizontally.

{% tab template="chart/user-interaction/zoom" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :zoomSettings='zoom' :legendSettings='legend'>
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Area' xName='x' yName='y' name='Product X' :border='border' :animation='animation'
                opacity=0.3> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, AreaSeries, DateTime, Zoom } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1: Object[] = [];
let point1: Object;
let value: number = 40;
let i: number;
for (i = 1; i < 500; i++) {
    if (Math.random() > .5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    point1 = { x: new Date(1950, i + 2, i), y: value.toFixed(1) };
    series1.push(point1);
}

export default {
  data() {
    return {
      seriesData1: series1,
      primaryXAxis: {
           valueType: 'DateTime',
           labelFormat: 'yMMM'
        },
        zoom:
        {
             enableSelectionZooming: true,
              mode: 'X'
        },
        title: 'Sales History of Product X',
        legend: { visible: false },
        border: { width: 0.5, color: '#00bdae' },
        animation: { enable: false }
    };
  },
  provide: {
    chart: [AreaSeries,  DateTime, Zoom]
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

## Toolbar

By default, zoomin, zoomout, pan and reset buttons will be displayed for zoomed chart. You can customize
to show your desire tools in the toolbar using [`toolbarItems`](../api/chart/zoomSettings/#toolbaritems)
property.

{% tab template="chart/user-interaction/zoom" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :zoomSettings='zoom'>
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Area' xName='x' yName='y' name='Product X' opacity=0.3> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, AreaSeries, DateTime, Zoom } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1: Object[] = [];
let point1: Object;
let value: number = 40;
let i: number;
for (i = 1; i < 500; i++) {
    if (Math.random() > .5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    point1 = { x: new Date(1950, i + 2, i), y: value.toFixed(1) };
    series1.push(point1);
}

export default {
  data() {
    return {
      seriesData1: series1,
      primaryXAxis: {
           valueType: 'DateTime',
           labelFormat: 'yMMM'
        },
        zoom:
        {
            enableSelectionZooming: true,
            toolbarItems: ['Zoom', 'Pan', 'Reset']
        },
        title: 'Sales History of Product X'
    };
  },
  provide: {
    chart: [AreaSeries,  DateTime, Zoom]
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

## Enable pan

Using [`enablePan`](../api/chart/zoomSettings/#enablepan)
property you can able to pan the zoomed chart without help of toolbar items.

{% tab template="chart/user-interaction/zoom" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :zoomSettings='zoom'>
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Area' xName='x' yName='y' name='Product X' opacity=0.3> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, AreaSeries, DateTime, Zoom } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1: Object[] = [];
let point1: Object;
let value: number = 40;
let i: number;
for (i = 1; i < 500; i++) {
    if (Math.random() > .5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    point1 = { x: new Date(1950, i + 2, i), y: value.toFixed(1) };
    series1.push(point1);
}

export default {
  data() {
    return {
      seriesData1: series1,
      primaryXAxis: {
            valueType: 'DateTime',
            labelFormat: 'yMMM',
            zoomFactor: 0.2, zoomPosition: 0.6
        },
        zoom:
        {
            enableSelectionZooming: true,
            enablePan: true
        },
        title: 'Sales History of Product X'
    };
  },
  provide: {
    chart: [AreaSeries,  DateTime, Zoom]
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

## Eanble Scrollbar

Using [`enableScrollbar`](../api/chart/zoomSettings/#enablescrollbar) property, you can able to add scrollbar for zoomed chart.
Using this scrollbar, you can pan or zoom the chart.

{% tab template="chart/user-interaction/zoom" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :zoomSettings='zoom'>
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Area' xName='x' yName='y' name='Product X' opacity=0.3> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, AreaSeries, DateTime, Zoom, ScrollBar } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1: Object[] = [];
let point1: Object;
let value: number = 40;
let i: number;
for (i = 1; i < 500; i++) {
    if (Math.random() > .5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    point1 = { x: new Date(1950, i + 2, i), y: value.toFixed(1) };
    series1.push(point1);
}

export default {
  data() {
    return {
      seriesData1: series1,
      primaryXAxis: {
            valueType: 'DateTime',
            labelFormat: 'yMMM',
            zoomFactor: 0.2, zoomPosition: 0.6
        },
        zoom:
        {
            enableSelectionZooming: true,
            enableScrollbar: true
        },
        title: 'Sales History of Product X'
    };
  },
  provide: {
    chart: [AreaSeries, DateTime, Zoom, ScrollBar]
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

## Auto interval on zooming

By using [`enableAutoIntervalOnZooming`](../api/chart/axis/?no-cache=1#enableautointervalonzooming) property,
the axis interval will get calculated automatically with respect to the zoomed range.

{% tab template="chart/user-interaction/zoom" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :zoomSettings='zoom'>
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Area' xName='x' yName='y' name='Product X' opacity=0.3> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, AreaSeries, DateTime, Zoom } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1: Object[] = [];
let point1: Object;
let value: number = 40;
let i: number;
for (i = 1; i < 500; i++) {
    if (Math.random() > .5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    point1 = { x: new Date(1950, i + 2, i), y: value.toFixed(1) };
    series1.push(point1);
}

export default {
  data() {
    return {
      seriesData1: series1,
      primaryXAxis: {
            valueType: 'DateTime',
            labelFormat: 'yMMM',
            enableAutoIntervalOnZooming: true
        },
        zoom:
        {
             enableSelectionZooming: true,
        },
        title: 'Sales History of Product X'
    };
  },
  provide: {
    chart: [AreaSeries,  DateTime, Zoom]
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