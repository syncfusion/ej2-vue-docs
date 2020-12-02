---
title: "Palette"
component: "HeatMap Chart"
description: "This section describes the gradient and solid cell coloring options available in heatmap and also defining the custom color stops for data value"
---

# Palette

In heat map, each data point is displayed as a cell with applied color based on the data value. The palette in the heat map is used to define the color range for cells and gradient type for colors. You can define the colors either in RGB or hex codes using the [`color`](../api/heatmap/paletteCollection/#color) property in the `palette`. The defined colors are applied to the cell background based on the palette type and cell value.

## Palette types

You can display the heat map cells either in gradient colors or fixed colors.

### Gradient

The smooth transition between the given palette colors can be applied for the heat map cells based on value. The heat map calculates all the gradient colors between the start and end colors for all distinct data values. Default start color and end color will be considered for gradient calculation, if the colors are not defined. The palette type must be defined as `Gradient` for the [`type`](../api/heatmap/paletteSettings/#type) property in the `paletteSettings` property.

{% tab template="heatmap-chart/palette"%}

```html

<template>
    <div id="app">
        <ejs-heatmap id="heatmap" :titleSettings='titleSettings' :xAxis='xAxis' :yAxis='yAxis' :dataSource='dataSource' :paletteSettings='paletteSettings' :legendSettings='legendSettings'></ejs-heatmap>
    </div>
</template>
<script>
import Vue from 'vue';
import { HeatMapPlugin, Tooltip, Legend } from '@syncfusion/ej2-vue-heatmap';
Vue.use(HeatMapPlugin);

export default {
  data: function() {
    return {
     dataSource: [
            [73, 39, 26, 39, 94, 0],
            [93, 58, 53, 38, 26, 68],
            [99, 28, 22, 4, 66, 90],
            [14, 26, 97, 69, 69, 3],
            [7, 46, 47, 47, 88, 6],
            [41, 55, 73, 23, 3, 79],
            [56, 69, 21, 86, 3, 33],
            [45, 7, 53, 81, 95, 79],
            [60, 77, 74, 68, 88, 51],
            [25, 25, 10, 12, 78, 14],
            [25, 56, 55, 58, 12, 82],
            [74, 33, 88, 23, 86, 59]
        ],
        titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
        xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
        yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        paletteSettings: {
            palette: [
                { color: '#C06C84'},
                { color: '#6C5B7B'},
                { color: '#355C7D'}
            ],
            type: "Gradient"
        },
        legendSettings: {
            visible: true,
        }
    }
  },
 provide:{
    heatmap:[Tooltip, Legend]
}
}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-vue-heatmap/styles/material.css';
</style>

```

{% endtab %}

### Fixed

In fixed palette type, solid colors are applied to the heat map cells. The data values can be grouped based on the number of colors defined for the heat map. The palette type should be defined as Fixed `Fixed` for the [`type`](../api/heatmap/paletteSettings/#type) property in the `paletteSettings` property.

{% tab template="heatmap-chart/palette"%}

```html

<template>
    <div id="app">
        <ejs-heatmap id="heatmap" :titleSettings='titleSettings' :xAxis='xAxis' :yAxis='yAxis' :dataSource='dataSource' :paletteSettings='paletteSettings' :legendSettings='legendSettings'></ejs-heatmap>
    </div>
</template>
<script>
import Vue from 'vue';
import { HeatMapPlugin, Tooltip, Legend } from '@syncfusion/ej2-vue-heatmap';
Vue.use(HeatMapPlugin);

export default {
  data: function() {
    return {
     dataSource: [
            [73, 39, 26, 39, 94, 0],
            [93, 58, 53, 38, 26, 68],
            [99, 28, 22, 4, 66, 90],
            [14, 26, 97, 69, 69, 3],
            [7, 46, 47, 47, 88, 6],
            [41, 55, 73, 23, 3, 79],
            [56, 69, 21, 86, 3, 33],
            [45, 7, 53, 81, 95, 79],
            [60, 77, 74, 68, 88, 51],
            [25, 25, 10, 12, 78, 14],
            [25, 56, 55, 58, 12, 82],
            [74, 33, 88, 23, 86, 59]
        ],
        titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
        xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
        yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        paletteSettings: {
            palette: [
                { color: '#C06C84'},
                { color: '#6C5B7B'},
                { color: '#355C7D'}
            ],
            type: "Fixed"
        },
        legendSettings: {
            visible: true,
        }
    }
  },
 provide:{
    heatmap:[Tooltip, Legend]
}
}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-vue-heatmap/styles/material.css';
</style>

```

{% endtab %}

## Defining color stops

You can define the colors ranges or color stops for data values in both gradient and fixed palette types. You need to define the data value in the [`value`](../api/heatmap/paletteCollection/#value)property for `palette` property to calculate the color stops. The heat map automatically calculates the color stops if the [`value`](../api/heatmap/paletteCollection/#value) property is not defined. The [`label`](../api/heatmap/paletteCollection/#label) property is used to provide the additional information about the color that is to be displayed in the legend. If the label is not provided, the value is displayed in the legend. The labels can be automatically calculated based on data values, if both the values and labels are not defined.

{% tab template="heatmap-chart/palette"%}

```html

<template>
    <div id="app">
        <ejs-heatmap id="heatmap" :titleSettings='titleSettings' :xAxis='xAxis' :yAxis='yAxis' :dataSource='dataSource' :paletteSettings='paletteSettings' :legendSettings='legendSettings'></ejs-heatmap>
    </div>
</template>
<script>
import Vue from 'vue';
import { HeatMapPlugin, Tooltip, Legend } from '@syncfusion/ej2-vue-heatmap';
Vue.use(HeatMapPlugin);

export default {
  data: function() {
    return {
        dataSource: [
            [73, 39, 26, 39, 94, 0],
            [93, 58, 53, 38, 26, 68],
            [99, 28, 22, 4, 66, 90],
            [14, 26, 97, 69, 69, 3],
            [7, 46, 47, 47, 88, 6],
            [41, 55, 73, 23, 3, 79],
            [56, 69, 21, 86, 3, 33],
            [45, 7, 53, 81, 95, 79],
            [60, 77, 74, 68, 88, 51],
            [25, 25, 10, 12, 78, 14],
            [25, 56, 55, 58, 12, 82],
            [74, 33, 88, 23, 86, 59]
        ],
        titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
        xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
        yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        paletteSettings: {
            palette: [
                { color: '#C06C84', label:'Low', value:50 },
                { color: '#6C5B7B', label:'Moderate', value:80 },
                { color: '#355C7D', label:'High', value: 100 }
            ],
            type: "Gradient"
        },
        legendSettings: {
            visible: true,
        }
    }
  },
 provide:{
    heatmap:[Tooltip, Legend]
}
}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-vue-heatmap/styles/material.css';
</style>

```

{% endtab %}

## Color range

The color range support is used to provide a specific color for specific range in heat map. The `startValue` and `endValue` properties are used to define the range start and end value. The `minColor` and `maxColor` properties represent the colors of given range. It's possible to set the cell color for the value not in the given range using the `fillColor` property.

> In Fixed type, the `minColor` value is used for cell color.

{% tab template="heatmap-chart/palette"%}

```html

<template>
    <div id="app">
        <ejs-heatmap id="heatmap" :titleSettings='titleSettings' :xAxis='xAxis' :yAxis='yAxis' :dataSource='dataSource' :paletteSettings='paletteSettings' :legendSettings='legendSettings'></ejs-heatmap>
    </div>
</template>
<script>
import Vue from 'vue';
import { HeatMapPlugin, Tooltip, Legend } from '@syncfusion/ej2-vue-heatmap';
Vue.use(HeatMapPlugin);

export default {
  data: function() {
    return {
        dataSource: [
            [73, 39, 26, 39, 94, 1],
            [93, 58, 53, 38, 26, 68],
            [99, 28, 22, 4, 66, 90],
            [14, 26, 97, 69, 69, 3],
            [7, 46, 47, 47, 88, 6],
            [41, 55, 73, 23, 3, 79],
            [56, 69, 21, 86, 3, 33],
            [45, 7, 53, 81, 95, 79],
            [60, 77, 74, 68, 88, 51],
            [25, 25, 10, 12, 78, 14],
            [25, 56, 55, 58, 12, 82],
            [74, 33, 88, 23, 86, 59]
        ],
        titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
        xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
        yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        paletteSettings: {
            palette: [
                { startValue:1, endValue:30, minColor: '#C2E7EC', maxColor: '#AEDFE6' },
                { startValue:30, endValue:60, minColor: '#9AD7E0', maxColor: '#72C7D4' },
                { startValue:60, endValue:90, minColor: '#5EBFCE', maxColor: '#4AB7C8' }
            ],
            type: "Gradient"
        },
        legendSettings: {
            visible: true,
        }
    }
  },
 provide:{
    heatmap:[Tooltip, Legend]
}
}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-vue-heatmap/styles/material.css';
</style>

```

{% endtab %}

## See Also

* [How to enable smart legend](./legend/#smart-legend)