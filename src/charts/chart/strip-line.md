---
title: " Chart Strip-lines | Vue "

component: "Chart"

description: "Strip Lines are vertical or horizontal lines used to highlight/mark a certain region on the plot area."
---

<!-- markdownlint-disable MD036 -->

# Strip lines

<!-- markdownlint-disable MD036 -->

EJ2 chart supports horizontal and vertical strip lines and customization of stripline in both orientation.
To use Stripline in axis, we need to inject `Stripline` into the `provide`

## Horizontal Strip lines

You can create Horizontal stripline by adding the `stripline` in the vertical axis and set `visible` option to true.
Striplines are rendered in the specified start to end range and you can add more than one stripline for an axis.

{% tab template= "chart/axis/strip-line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Run Rates'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, StripLine } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                 {x: 1, y: 20},{x: 2, y: 22},{x: 3, y: 0},{x: 4, y: 12},{x: 5, y: 5},
                 {x: 6, y: 15},{x: 7, y: 6},{x: 8, y: 12},{x: 9, y: 20},{x: 10, y: 7}
        ],
          primaryYAxis:
        {
           title: 'Runs',
            stripLines:[
            { start: 15, end: 22, text: 'Good', color: '#ff512f', visible: true, zIndex: 'Behind', opacity: 0.5 }
            { start: 8, end: 15, text: 'Medium', color: 'pink', opacity: 0.5, visible: true, zIndex: 'Behind' }
            { start: 0, end: 8, text:'Not enough', color: 'skyblue', opacity: 0.5, visible: true, zIndex: 'Behind' }]
        },
        primaryXAxis: {
            title: 'Overs'
        },
      title: "India Vs Australia 1st match"
    };
  },
  provide: {
    chart: [ColumnSeries, StripLine]
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

## Vertical Striplines

You can create vertical stripline by adding the`stripline` in the horizontal axis and set `visible` option to true.
Striplines are rendered in the specified start to end range and you can add more than one stripline for an axis.

{% tab template= "chart/axis/strip-line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Run Rates'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, StripLine } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                 {x: 1, y: 20},{x: 2, y: 22},{x: 3, y: 0},{x: 4, y: 12},{x: 5, y: 5},
                 {x: 6, y: 15},{x: 7, y: 6},{x: 8, y: 12},{x: 9, y: 20},{x: 10, y: 7}
        ],
          primaryYAxis:
        {
           title: 'Runs'
        },
        primaryXAxis: {
            title: 'Overs',
            stripLines:[
            {start: 0, end: 5, text: 'powerplay 1', color: 'red', visible: true, opacity: 0.5, rotation: 45, testStyle: { size: 20, color: 'black'}},
            {start: 5, end: 10, text: 'powerplay 2', color: 'blue', visible: true, opacity: 0.5, rotation: 45, testStyle: { size: 20, color: 'black'}},
        ]
        },
      title: "India Vs Australia 1st match"
    };
  },
  provide: {
    chart: [ColumnSeries, StripLine]
  },
}
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

## Customize the strip line

Starting value in specific strip line can be customized by `start` property in strip line. Similarly, ending value
is customized by `end`. It can be also set for starting from the corresponding origin of the axis by `startFromOrigin`.
Size of the strip line is customized by `size`. Border for the stripline is customized by `border`.
Order of the strip line such that whether it should be rendered in behind or over the series elements
is customized by `zIndex`.

{% tab template= "chart/axis/strip-line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Run Rates'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, StripLine } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data: function() {
    return {
      seriesData: [
                 {x: 1, y: 20},{x: 2, y: 22},{x: 3, y: 0},{x: 4, y: 12},{x: 5, y: 5},
                 {x: 6, y: 15},{x: 7, y: 6},{x: 8, y: 12},{x: 9, y: 20},{x: 10, y: 7}
        ],
          primaryYAxis:
        {
           title: 'Runs'
        },
        primaryXAxis: {
           stripLines:[
            { startFromOrigin: true, size: 4, zIndex: 'Behind', opacity: 0.5, border: { width: 2, color:'red'}}
        ],
            title: 'Overs'
        },
      title: "India Vs Australia 1st match"
    };
  },
  provide: {
    chart: [ColumnSeries, StripLine]
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

## Customize the stripline text

You can customize the text rendered in stripline by `textStyle` property. Rotation of the strip line text can be changed by `rotation` property.
Horizontal and Vertical alignment of stripline text can be changed by `horizontalAlignment` and `verticalAlignment` property.

{% tab template= "chart/axis/strip-line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Run Rates'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, StripLine } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                 {x: 1, y: 20},{x: 2, y: 22},{x: 3, y: 0},{x: 4, y: 12},{x: 5, y: 5},
                 {x: 6, y: 15},{x: 7, y: 6},{x: 8, y: 12},{x: 9, y: 20},{x: 10, y: 7}
        ],
          primaryYAxis:
        {
           title: 'Runs'
        },
        primaryXAxis: {
           stripLines:[
            { startFromOrigin: true, size: 4, zIndex: 'Behind', opacity: 0.5,  text: 'Good', verticalAlignment: 'Middle', horizontalAlignment: 'Middle', rotation: 90, textStyle: { size: 15}},
            { start: 5, end: 8, verticalAlignment: 'Start', horizontalAlignment: 'End', rotation: 45, text: 'Poor'}
        ],
            title: 'Overs'
        },
      title: "India Vs Australia 1st match"
    };
  },
  provide: {
    chart: [ColumnSeries, StripLine]
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

## Dash Array

You can create dash array stripline by using `dashArray` property. The Striplines are rendered with specified dash array values.

{% tab template= "chart/axis/strip-line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Run Rates'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, StripLine, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                {x: 1, y: 5},{x: 2, y: 39},{x: 3, y: 21},{x: 4, y: 51},{x: 5, y: 30},
                {x: 6, y: 25},{x: 7, y: 10},{x: 8, y: 40},{x: 9, y: 50},{x: 10, y: 20}
        ],
          primaryYAxis:
        {
          minimum: 0,
          maximum: 60,
          interval: 10,
          stripLines:[
                  { start: 30, size: 2, sizeType: 'Pixel', dashArray:"10,5", color: "red"}
        ],
        },
    };
  },
  provide: {
    chart: [ColumnSeries, StripLine, LineSeries]
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

## Recurrence Stripline

 The strip lines to be drawn repeatedly at the regular intervals – this will be useful when you want to mark an event that occurs recursively along the timeline of the chart. Following properties are used to configure this feature.

* `isRepeat`       - It is used for enable / disable the recurrence strip line.
* `repeatEvery`    - It is used for mention the stripline interval.
* `repeatUntil`    - It specifies the end value at which point strip line has to stop repeating.

{% tab template= "chart/axis/strip-line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :primaryXAxis='primaryXAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Run Rates'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, StripLine, LineSeries } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                {x: 1, y: 5},{x: 2, y: 39},{x: 3, y: 21},{x: 4, y: 51},{x: 5, y: 30},
                {x: 6, y: 25},{x: 7, y: 10},{x: 8, y: 40},{x: 9, y: 50},{x: 10, y: 20}

        ],
        primaryXAxis: {
           stripLines:[
                  {start: 1, size: 1, isRepeat: true, repeatEvery: 2, color: 'rgba(167,169,171, 0.3)'}
        ],
        },
    };
  },
  provide: {
    chart: [ColumnSeries, StripLine, LineSeries]
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

## Size Type

The `sizeType` property refers the size of the stripline. They are,

* `Auto`
* `Pixel`
* `Years`
* `Months`
* `Days`
* `Hours`
* `Minutes`
* `Seconds`

{% tab template= "chart/axis/strip-line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Run Rates'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, ColumnSeries, Category, LineSeries, DataLabel, StripLine, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              { x: new Date(2000, 0, 1), y: 10 }, { x: new Date(2002, 0, 1), y: 40 },
              { x: new Date(2004, 0, 1), y: 20 }, { x: new Date(2006, 0, 1), y: 50 },
              { x: new Date(2008, 0, 1), y: 15 }, { x: new Date(2010, 0, 1), y: 30 }
        ],
        primaryXAxis: {
           valueType: 'DateTime', intervalType: 'Years',
           stripLines:[
                {start:new Date(2002, 0, 1) , size: 2, sizeType: 'Years', color: 'rgba(167,169,171, 0.3)'}
        ],
        },
        primaryYAxis: {
          minimum: 0, maximum: 60, interval: 10
          },
    };
  },
  provide: {
    chart: [ColumnSeries, Category, LineSeries, DataLabel, StripLine, DateTime]
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

## Segment Stripline

You can create the stripline in a particular region with respect to the segment. You can enable the segment stripline using `isSegmented` property. The start and end value of this type of stripline can be defined using `segmentStart` and `segmentEnd` properties.

* `isSegmented`     - It is used for enable the segment stripline.
* `segmentStart`    - Used to change the segment start value. Value correspond to associated axis.
* `segmentEnd`      - Used to change the segment end value. Value correspond to associated axis.
* `segmentAxisName` - Used to specify the name of the associated axis.

{% tab template= "chart/axis/strip-line" %}

```html
<template>
    <div id="app">
         <ejs-chart id="container" :primaryYAxis='primaryYAxis'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='Run Rates'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, Chart, Category, ColumnSeries, LineSeries, DataLabel, StripLine } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
      seriesData: [
              {x: 1, y: 5},{x: 2, y: 39},{x: 3, y: 21},{x: 4, y: 51},{x: 5, y: 30},
              {x: 6, y: 25},{x: 7, y: 10},{x: 8, y: 40},{x: 9, y: 50},{x: 10, y: 20}
        ],
        primaryYAxis: {
           stripLines:[
              {start: 20, end: 40, isSegmented: true, segmentStart: 2, segmentEnd: 4,
            color: 'rgba(167,169,171, 0.3)'}

        ],
        },
    };
  },
  provide: {
    chart: [ColumnSeries, Category, LineSeries, DataLabel, StripLine]
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