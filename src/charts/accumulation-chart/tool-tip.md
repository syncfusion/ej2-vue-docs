---
title: "Accumulation Chart Tooltip | Vue "

component: "Accumulation Chart"

description: "Accumulation chart tooltip represents the x and y values of the current mouse pointer point."
---

# Tooltip

Tooltip for the accumulation chart can be enabled by using the `enable` property.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :tooltip='tooltip'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' radius='70%'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationTooltip } from "@syncfusion/ej2-vue-charts";

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
       tooltip:{enable: true}
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationTooltip]
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

>Note: To use tooltip feature, inject the `AccumulationTooltip` into the `provide`.

## Header

We can specify header for the tooltip using `header` property.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :tooltip='tooltip'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' radius='70%'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationTooltip } from "@syncfusion/ej2-vue-charts";

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
       tooltip:{enable: true, header:"Pie Chart"}
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationTooltip]
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

## Format

By default, tooltip shows information of x and y value in points. In addition to that, you can show more
information in tooltip. For example the format `${series.name} ${point.x}` shows series name and point x value.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :tooltip='tooltip'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' radius='70%'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationTooltip } from "@syncfusion/ej2-vue-charts";

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
       tooltip:{enable: true, format: '${point.x} : <b>${point.y}%</b>'}
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationTooltip]
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

## Tooltip Template

Any HTML element can be displayed in the tooltip by using the `template` property.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :tooltip='tooltip'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' radius='70%'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationTooltip } from "@syncfusion/ej2-vue-charts";

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
       tooltip:{
           enable: true,
           template:  "<div id='templateWrap' style='background-color:#bd18f9;border-radius: 3px; float: right;padding: 2px;line-height: 20px;text-align: center;'>"+
        "<img src='sun_annotation.png' />" +
        "<div style='color:white; font-family:Roboto; font-style: medium; fontp-size:14px;float: right;padding: 2px;line-height: 20px;text-align: center;padding-right:6px'><span>${y}</span></div></div>"
        }
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationTooltip]
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

## Customization

The [`fill`](../api/chart/tooltipSettingsModel/#fill) and
[`border`](../api/chart/tooltipSettingsModel/#border) properties are used to customize the background
color and border of the tooltip respectively. The [`textStyle`](../api/chart/tooltipSettingsModel/#textstyle)
property in the tooltip is used to customize the font of the tooltip text.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :tooltip='tooltip'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' radius='70%'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationTooltip } from "@syncfusion/ej2-vue-charts";

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
       tooltip:{
           enable: true,
             format: '${series.name} ${point.x} : ${point.y}',
            //fill for tooltip
            fill: '#7bb4eb',
            //border for tooltip
            border: {
                width: 2,
                color: 'grey'
        }
        }
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationTooltip]
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

## To customize individual tooltip

Using `tooltipRender` event, you can customize a tooltip for particular point. event, you can customize a
tooltip for particular point.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :tooltip='tooltip' :tooltipRender='tooltipRender'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' radius='70%'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationTooltip } from "@syncfusion/ej2-vue-charts";

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
       tooltip:{
           enable: true
        }
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationTooltip]
  },
  methods: {
      tooltipRender: function(args) {
     if (args.point.index === 3) {
              args.text = args.point.x + '' + ':' + args.point.y + '' + ' ' +'customtext';
              args.textStyle.color = '#f48042';
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

## Tooltip Mapping Name

By default, tooltip shows information of x and y value in points. You can show more information from datasource in tooltip by using the `tooltipMappingName` property of the tooltip. You can use the `${point.tooltip}` as place holders to display the specified tooltip content.

{% tab template="chart/series/pie" %}

```html
<template>
    <div id="app">
         <ejs-accumulationchart id="container" :tooltip='tooltip'>
            <e-accumulation-series-collection>
                <e-accumulation-series :dataSource='seriesData' xName='x' yName='y' tooltipMappingName='text' radius='70%'> </e-accumulation-series>
            </e-accumulation-series-collection>
        </ejs-accumulationchart>
    </div>
</template>
<script>
import Vue from "vue";
import { AccumulationChartPlugin, PieSeries, AccumulationTooltip } from "@syncfusion/ej2-vue-charts";

Vue.use(AccumulationChartPlugin);

export default {
  data() {
    return {
      seriesData: [
                    { x: 'Jan', y: 13, text: 'Jan: 13' }, { x: 'Feb', y: 13, text: 'Feb: 13' },
                    { x: 'Mar', y: 17, text: 'Mar: 17' }, { x: 'Apr', y: 13.5, text: 'Apr: 13.5' }
            ],
       tooltip:{
           enable: true, format: '${point.tooltip}'
        }
    };
  },
  provide: {
     accumulationchart: [PieSeries, AccumulationTooltip]
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