---
title: " RangeNavigator Tooltip | Vue "

component: "RangeNavigator"

description: "The range navigator supports tooltips for sliders.Tooltips  display the selected start and end values."
---

# Tooltip

<!-- markdownlint-disable MD036 -->

The range navigator supports tooltips for sliders. Sliders are used to select data at a range in the range navigator.
Tooltips  display the selected start and end values.

<!-- markdownlint-disable MD013 -->

## Customization

Tooltips can be customized using the following properties:

* tooltip: Customizes the text displayed in tooltip.
* enable: Customizes the visibility of the tooltip.
* fill: Customizes the background color of the tooltip.
* opacity: Customizes the opacity of the tooltip.
* textStyle: Customizes the font size, color, family, style, weight, alignment, and overflow of the tooltip.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
        <ejs-rangenavigator :valueType='valueType' :value='value' :labelFormat='labelFormat' :tooltip='tooltip'>
            <e-rangenavigator-series-collection>
                <e-rangenavigator-series :dataSource='data' type='Area' xName='x' yName='y' width=2>
                </e-rangenavigator-series>
            </e-rangenavigator-series-collection>
        </ejs-rangenavigator>
    </div>
</template>
<script>
import Vue from "vue";
import { RangeNavigatorPlugin, AreaSeries, DateTime, RangeTooltip } from "@syncfusion/ej2-vue-charts";
import { bitCoinData } from "./default_data.js";

Vue.use(RangeNavigatorPlugin);

export default {
  data() {
    return {
     valueType: 'DateTime',
     value: [new Date('2017-09-01'), new Date('2018-02-01')],
     tooltip: { enable: true, displayMode: 'Always', fill:'red', opacity: 0.6, textStyle:{ style: 'Italic', color:'blue', size:'12px'} },
     labelFormat: 'MMM-yy',
     data: bitCoinData
    };
  },
  provide: {
    rangeNavigator: [DateTime, AreaSeries, RangeTooltip]
  }
};
</script>
```

{% endtab %}

## Label Format

You can format and parse the date to all globalize format using [`labelFormat`](../api/range-navigator/rangeNavigatorAxis/) property in an axis.

{% tab template="rangenavigator/getting-started" %}

```html
<template>
    <div id="app">
        <ejs-rangenavigator :valueType='valueType' :value='value' :tooltip='tooltip'>
            <e-rangenavigator-series-collection>
                <e-rangenavigator-series :dataSource='data' type='Area' xName='x' yName='y' width=2>
                </e-rangenavigator-series>
            </e-rangenavigator-series-collection>
        </ejs-rangenavigator>
    </div>
</template>
<script>
import Vue from "vue";
import { RangeNavigatorPlugin, AreaSeries, DateTime, RangeTooltip } from "@syncfusion/ej2-vue-charts";
import { bitCoinData } from "./default_data.js";

Vue.use(RangeNavigatorPlugin);

export default {
  data() {
    return {
     valueType: 'DateTime',
     value: [new Date('2017-09-01'), new Date('2018-02-01')],
     tooltip: { enable: true, displayMode: 'Always', labelFormat: 'y/M/d' },
     data: bitCoinData
    };
  },
  provide: {
    rangeNavigator: [DateTime, AreaSeries, RangeTooltip]
  }
};
</script>
```

{% endtab %}

The following table describes the result of applying some common date time formats to the `labelFormat` property

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Label Value</b></td>
<td><b>Label Format Property Value</b></td>
<td><b>Result </b></td>
<td><b>Description </b></td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>EEEE</td>
<td>Monday</td>
<td>The Date is displayed in day format</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>yMd</td>
<td>04/10/2000</td>
<td>The Date is displayed in month/date/year format</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td> MMM </td>
<td>Apr</td>
<td>The Shorthand month for the date is displayed</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>hm</td>
<td>12:00 AM</td>
<td>Time of the date value is displayed as label</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>hms</td>
<td>12:00:00 AM</td>
<td>The Label is displayed in hours:minutes:seconds format</td>
</tr>
</table>