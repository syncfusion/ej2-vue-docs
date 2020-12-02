---
title: "Series"
component: "Smith Chart"
description: "Series support in smith chart"
---

# Series

You can add any number of series to the smithchart as per your requirement. You can use series setting to either add or customize the data. For the points or datasource added in the series, line is drawn. You can customize the each series as per your requirement with marker, datalabel, animation, opacity and so on.

## points or datasource

For adding values in the smithchart, you can use either points or datasource in the series. Points and datasource both should be array of object which should contain the field names resistance and rectangle.

{% tab template="smithchart/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-smithchart id="smithchart"  >
                <e-seriesCollection>
                    <e-series :dataSource='dataSource' :name='name'  :reactance='reactance' :resistance='resistance'></e-series>
                </e-seriesCollection>
        </ejs-smithchart>
    </div>
</template>
<script>
import Vue from 'vue';
import { SmithchartPlugin } from "@syncfusion/ej2-vue-charts";
Vue.use(SmithchartPlugin);

export default {
  data: function() {
    return {
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
    }
  }
}
</script>
```

{% endtab %}

## Series customization

Using following options in series settings, you can customize each series in smithchart as per your requirement.

* [`fill`] - Used to customize the fill color for the series.
* [`enableSmartLabels`] - Used to place the data labels on the smithchart without overlapping with each other.
* [`visibility`] - Used to handle the visibility of the series.
* [`opacity`] - Used to control the opacity of the series line.
* [`width`] - Used to customize the width of the series line.

{% tab template="smithchart/getting-started", isDefaultActive=true %}

```html
<template>
    <div class="control_wrapper">
        <ejs-smithchart id="smithchart"  >
                <e-seriesCollection>
                    <e-series :dataSource='dataSource' :name='name' :fill='fill' :visibility='visibility':opacity='opacity' :width='width' :marker='marker' :reactance='reactance' :resistance='resistance'></e-series>
                </e-seriesCollection>
        </ejs-smithchart>
    </div>
</template>
<script>
import Vue from 'vue';
import { SmithchartPlugin } from "@syncfusion/ej2-vue-charts";
Vue.use(SmithchartPlugin);

export default {
  data: function() {
    return {
            fill: '#009933',
            visibility: 'visible',
            opacity: 0.75,
            width: 2.5,
            marker: {
                dataLabel: {
                    visible: true
                }
            }
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
    }
  }
}
</script>
```

{% endtab %}