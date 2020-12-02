---
title: "Axis"
component: "Smith Chart"
description: "Axis support in smith chart"
---

# Axis

Like chart, Smithchart is having support for two types of axis.
* Horizontal axis - axis drawn as straight line in the horizontal direction of the chart.
* Radial axis - axis is drawn as circular path.

## Labels Customization

Axis labels are used to denote what kind of data is bound for smithchart. Using axis labels, you can easily identify in which interval chart is rendered. Using following properties we can customize the axis labels for horizontal and radial axis.

* [`labelPosition`] - used to place the labels either inside or outside the axis line.
* [`labelIntersectAction`] - used to hide the labels when intersect with other one.
* [`labelStyle`] - used to customize the properties such as font size, family, weight, opacity.

{% tab template="smithchart/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-smithchart id="smithchart" :horizontalAxis='horizontalAxis' :radialAxis='radialAxis'>
                <e-seriesCollection>
                    <e-series :points='dataSource' :name='name' :reactance='reactance' :resistance='resistance' ></e-series>
                    <e-series :points='points' :name='name2'></e-series>
                </e-seriesCollection>
        </ejs-smithchart>
    </div>
</template>
<script>
import Vue from 'vue';
import { SmithchartPlugin,SmithchartLegend } from "@syncfusion/ej2-vue-charts";
Vue.use(SmithchartPlugin);

export default {
  data: function() {
    return {
        radialAxis : {
        labelPosition: 'Inside',
        labelIntersectAction: 'Hide',
        labelStyle: {
            fontFamily: 'Times New Roman',
            fontWeight: 'bold',
            fontStyle: 'Italic',
            opacity: 0.75,
            size: '14px'
        }
    },
    horizontalAxis: {
        labelPosition: 'Inside',
        labelIntersectAction: 'Hide',
        labelStyle: {
            fontFamily: 'Times New Roman',
            fontWeight: 'bold',
            fontStyle: 'Italic',
            opacity: 0.75,
            size: '14px'
        }
    },
        dataSource: [
                { resistance: 10, reactance: 25 }, { resistance: 8, reactance: 6 },
                { resistance: 6, reactance: 4.5 }, { resistance: 4.5, reactance: 2 },
                { resistance: 3.5, reactance: 1.6 }, { resistance: 2.5, reactance: 1.3 },
                { resistance: 2, reactance: 1.2 }, { resistance: 1.5, reactance: 1 },
                { resistance: 1, reactance: 0.8 }, { resistance: 0.5, reactance: 0.4 },
                { resistance: 0.3, reactance: 0.2 }, { resistance: 0, reactance: 0.15 },
            ],
        name: 'Transmission1',
        reactance: 'reactance', resistance: 'resistance',
        points: [{ resistance: 20, reactance: -50 }, { resistance: 10, reactance: -10 },
                { resistance: 9, reactance: -4.5 }, { resistance: 8, reactance: -3.5 },
                { resistance: 7, reactance: -2.5 }, { resistance: 6, reactance: -1.5 },
                { resistance: 5, reactance: -1 }, { resistance: 4.5, reactance: -0.5 },
                { resistance: 3.5, reactance: 0 }, { resistance: 2.5, reactance: 0.4 },
                { resistance: 2, reactance: 0.5 }, { resistance: 1.5, reactance: 0.5 },
                { resistance: 1, reactance: 0.4 }, { resistance: 0.5, reactance: 0.2 },
                { resistance: 0.3, reactance: 0.1 }, { resistance: 0, reactance: 0.05 },],
        name2: 'Transmission2'
    }
  },
provide:{
    smithchart:[SmithchartLegend]
}
}
</script>
```

{% endtab %}

## Gridlines

To make the data in a chart that displays axes easier to read, you can display horizontal and radial axis gridlines. Gridlines extend from any horizontal and radial axes across the plot area of the smithchart.
Both horizontal and radial axis are having support for major as well as minor gridlines. Major gridlines are drawn from the position in which labels are rendered. Minor gridlines are drawn between two major gridlines as per the count we set in settings.

We can customize following things, in major as well as minor gridlines.

* [`width`] - used to customize the width of gridlines.
* [`dashArray`] - used to customize whether gridline have to render as normal line or dashed line.
* [`visible`] - used to enable or disable the visibility of the gridlines.
* [`opacity`] - used to customize the opacity of the major gridlines.
* [`count`] - used to customize the count of the minor gridlines.

{% tab template="smithchart/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-smithchart id="smithchart"  :horizontalAxis= 'horizontalAxis'>
                <e-seriesCollection>
                    <e-series :points='dataSource' :name='name' :reactance='reactance' :resistance='resistance' ></e-series>
                    <e-series :points='points' :name='name2'></e-series>
                </e-seriesCollection>
        </ejs-smithchart>
    </div>
</template>
<script>
import Vue from 'vue';
import { SmithchartPlugin,SmithchartLegend } from "@syncfusion/ej2-vue-charts";
Vue.use(SmithchartPlugin);

export default {
  data: function() {
    return {
        horizontalAxis: {
        majorGridLines: {
            visible: true,
            opacity: 0.8,
            width: 10
        }
    },
        dataSource: [
                { resistance: 10, reactance: 25 }, { resistance: 8, reactance: 6 },
                { resistance: 6, reactance: 4.5 }, { resistance: 4.5, reactance: 2 },
                { resistance: 3.5, reactance: 1.6 }, { resistance: 2.5, reactance: 1.3 },
                { resistance: 2, reactance: 1.2 }, { resistance: 1.5, reactance: 1 },
                { resistance: 1, reactance: 0.8 }, { resistance: 0.5, reactance: 0.4 },
                { resistance: 0.3, reactance: 0.2 }, { resistance: 0, reactance: 0.15 },
            ],
        name: 'Transmission1',
        reactance: 'reactance', resistance: 'resistance',
        points: [{ resistance: 20, reactance: -50 }, { resistance: 10, reactance: -10 },
                { resistance: 9, reactance: -4.5 }, { resistance: 8, reactance: -3.5 },
                { resistance: 7, reactance: -2.5 }, { resistance: 6, reactance: -1.5 },
                { resistance: 5, reactance: -1 }, { resistance: 4.5, reactance: -0.5 },
                { resistance: 3.5, reactance: 0 }, { resistance: 2.5, reactance: 0.4 },
                { resistance: 2, reactance: 0.5 }, { resistance: 1.5, reactance: 0.5 },
                { resistance: 1, reactance: 0.4 }, { resistance: 0.5, reactance: 0.2 },
                { resistance: 0.3, reactance: 0.1 }, { resistance: 0, reactance: 0.05 },],
        name2: 'Transmission2'
    }
  },
}
</script>
```

{% endtab %}

## Axisline

As name suggests that, it is a line in smithchart that can be configured to denotes the axis. By default, visibility of the axis line is true. You can customize its visibility by using visible property in axis Line. Other than visibility of the axis line, you can customize the following properties of the axis line.

* [`width`] - used to customize the width of the axis line.
* [`dashArray`] - used to render the axis line as dashed line.
* [`visible`] - used to enable or disable the visibility of the axis line.

{% tab template="smithchart/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-smithchart id="smithchart"  :horizontalAxis= 'horizontalAxis'>
                <e-seriesCollection>
                    <e-series :points='dataSource' :name='name' :reactance='reactance' :resistance='resistance' ></e-series>
                    <e-series :points='points' :name='name2'></e-series>
                </e-seriesCollection>
        </ejs-smithchart>
    </div>
</template>
<script>
import Vue from 'vue';
import { SmithchartPlugin,SmithchartLegend } from "@syncfusion/ej2-vue-charts";
Vue.use(SmithchartPlugin);

export default {
  data: function() {
    return {
         horizontalAxis: {
        majorGridLines: {
            visible: true,
            opacity: 0.8,
            width: 10
        },
        axisLine: {
            width: 10,
            visible: false
        }
    },
        dataSource: [
                { resistance: 10, reactance: 25 }, { resistance: 8, reactance: 6 },
                { resistance: 6, reactance: 4.5 }, { resistance: 4.5, reactance: 2 },
                { resistance: 3.5, reactance: 1.6 }, { resistance: 2.5, reactance: 1.3 },
                { resistance: 2, reactance: 1.2 }, { resistance: 1.5, reactance: 1 },
                { resistance: 1, reactance: 0.8 }, { resistance: 0.5, reactance: 0.4 },
                { resistance: 0.3, reactance: 0.2 }, { resistance: 0, reactance: 0.15 },
            ],
        name: 'Transmission1',
        reactance: 'reactance', resistance: 'resistance',
        points: [{ resistance: 20, reactance: -50 }, { resistance: 10, reactance: -10 },
                { resistance: 9, reactance: -4.5 }, { resistance: 8, reactance: -3.5 },
                { resistance: 7, reactance: -2.5 }, { resistance: 6, reactance: -1.5 },
                { resistance: 5, reactance: -1 }, { resistance: 4.5, reactance: -0.5 },
                { resistance: 3.5, reactance: 0 }, { resistance: 2.5, reactance: 0.4 },
                { resistance: 2, reactance: 0.5 }, { resistance: 1.5, reactance: 0.5 },
                { resistance: 1, reactance: 0.4 }, { resistance: 0.5, reactance: 0.2 },
                { resistance: 0.3, reactance: 0.1 }, { resistance: 0, reactance: 0.05 },],
        name2: 'Transmission2'
    }
  },
}
</script>
```

{% endtab %}