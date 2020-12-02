---
title: "Accumulation Chart Legend | Vue "

component: "Accumulation Chart"

description: "Accumulation chart legend is used to give additional information about the chart series."
---

# Legend

As like a chart, the legend is also available for accumulation charts, which gives information about the points.
By default, the legend will be placed on the right, if the width of the chart is high or will be placed on the bottom,
if the height of the chart is high. Other customization features regarding the legend element are same as the
[`chart legend`](http://ej2.syncfusion.com/vue/documentation/chart/legend.html#position-and-alignment).
Here, the legend for a point can be collapsed by giving the empty string to the x value of the point.

{% tab template="chart/series/legend" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :legendSettings='legendSettings'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' radius='70%'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationLegend } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
           { x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 },
           { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },
           { x: 'May', y: 19 }, { x: 'Jun', y: 23.5 },
           { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
           { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }
            ],
       legendSettings: {
        visible: true
       }
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationLegend]
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

## Position and Alignment

By using the position property, you can position the legend at the `left`, `right`, `top` or `bottom` of the chart.
You can also align the legend to `center`, `far` or `near` of the chart using the alignment property.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :legendSettings='legendSettings'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' radius='70%'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationLegend } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
           { x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 },
           { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },
           { x: 'May', y: 19 }, { x: 'Jun', y: 23.5 },
           { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }
            ],
       legendSettings:{ position:'Top' ,alignment:'Near'}
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationLegend]
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

## Legend Shape

To change the legend icon shape, use the `legendShape` property in the `series`. By default, legend icon shape
is `seriesType`.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :legendSettings='legendSettings'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' legendShape='Rectangle'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationLegend } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
           { x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 },
           { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },
           { x: 'May', y: 19 }, { x: 'Jun', y: 23.5 },
           { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }
            ],
       legendSettings:{ visible: true }
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationLegend]
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

## Legend Size

The legend size can be changed by using the `width` and `height` properties of the `legendSettings`.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :legendSettings='legendSettings'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationLegend } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
           { x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 },
           { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },
           { x: 'May', y: 19 }, { x: 'Jun', y: 23.5 },
           { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }
            ],
       legendSettings:{ width: '150', height: '100', border: { width: 1, color: 'pink'} }
    };
  },
  provide: {
    accumulationchart: [PieSeries, AccumulationLegend]
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

## Legend Item Size

You can customize the size of the legend items by using the `shapeHeight` and `shapeWidth` properties.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :legendSettings='legendSettings'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationLegend } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
           { x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 },
           { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },
           { x: 'May', y: 19 }, { x: 'Jun', y: 23.5 },
           { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }
            ],
       legendSettings:{ shapeHeight: 15, shapeWidth: 15 }
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationLegend]
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

## Paging for Legend

Paging will be enabled by default, when the legend items exceeds the legend bounds. You can view the each legend
item by navigating between the pages using the navigation buttons.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :legendSettings='legendSettings'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationLegend } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
           { x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 },
           { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },
           { x: 'May', y: 19 }, { x: 'Jun', y: 23.5 },
           { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }
            ],
       legendSettings:{ height: '150', width:'80' }
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationLegend]
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

## Enable Animation

You can customize the animation while clicking legend by setting enableAnimation as true or false using `enableAnimation` property in Accumulation Chart.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :legendSettings='legendSettings'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' legendShape='Rectangle'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationLegend } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
           { x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 },
           { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },
           { x: 'May', y: 19 }, { x: 'Jun', y: 23.5 },
           { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }
            ],
       legendSettings:{ visible: true },
       enableAnimation: true
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationLegend]
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

## Legend Title

You can set title for legend using `title` property in `legendSettings`. You can also customize the `fontStyle`, `size`, `fontWeight`,
`color`, `textAlignment`, `fontFamily`, `opacity` and `textOverflow` of legend title. `titlePosition` is used to set the legend position in `Top`, `Left` and `Right` position. `maximumTitleWidth` is used to set the width of the legend title. By default, it will be `100px`.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :legendSettings='legendSettings'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' radius='70%'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationLegend } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
           { x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 },
           { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },
           { x: 'May', y: 19 }, { x: 'Jun', y: 23.5 },
           { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
           { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }
            ],
       legendSettings:{ visible: true, title: 'Months', position: 'Bottom' }
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationLegend]
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

## Arrow Page Navigation

By default, the page number will be enabled while legend paging. Now, you can disable that page number and also you can get left and right arrows for page navigation. You have to set `false` value to `enablePages` to get this support.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :legendSettings='legendSettings'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' radius='70%'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationLegend } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
           { x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 },
           { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },
           { x: 'May', y: 19 }, { x: 'Jun', y: 23.5 },
           { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
           { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 },
           { x: 'Nov', y: 15 }, { x: 'Dec', y: 15 }
            ],
       legendSettings:{ width: '260px', height: '50px', enablePages: false, position: 'Bottom' }
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationLegend]
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