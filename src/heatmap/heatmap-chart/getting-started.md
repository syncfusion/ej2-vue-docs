---
title: "Getting started"
component: "HeatMap Chart"
description: "This section describes on how to visualize a two-dimensional data by enabling the basic features in heatmap"
---

# Getting Started

This section explains the steps required to create a heat map and demonstrates the basic usage of the heat map control.

## Dependencies

For using heat map, the following minimum requirements are needed.

```javascript
|-- @syncfusion/ej2-vue-heatmap
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-heatmap
    |-- @syncfusion/ej2-vue-base
    |-- @syncfusion/ej2-svg-base
```

## Installation and configuration

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications. To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
```

Start a new project using below Vue CLI command.

```bash
vue create quickstart
```

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry. You can choose the component that you want to install. For this application, we are going to use HeatMap component.

To install HeatMap component, use the following command

```bash
npm install @syncfusion/ej2-vue-heatmap –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.

* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { HeatMapPlugin } from '@syncfusion/ej2-vue-heatmap';

Vue.use(HeatMapPlugin);
```

> By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package, register the same using the Vue.component() with name of Component from ComponentPlugin and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { HeatMapComponent, HeatMapPlugin } from '@syncfusion/ej2-vue-heatmap';

Vue.component(HeatMapPlugin.name, HeatMapComponent);
```

Note: By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Initialize HeatMap component

Add the EJ2 Vue HeatMap using `<ejs-heatmap>` to the `<template>` section of the `App.vue` file in src directory, the content attribute of the HeatMap component is provided as name in data option in the `<script>` section.

```html
<template>
    <div id="app">
    <ejs-heatmap></ejs-heatmap>
  </div>
</template>
<script>
import Vue from 'vue';
import { HeatMapPlugin } from '@syncfusion/ej2-vue-heatmap';

Vue.use(HeatMapPlugin);
export default Vue.extend ({});
</script>
```

## Run the application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

The following example shows a basic HeatMap.

```html
<template>
<ejs-heatmap id="heatmap"></ejs-heatmap>
</template>

<script>
import Vue from 'vue';
import { HeatMapPlugin } from '@syncfusion/ej2-vue-heatmap';

Vue.use(HeatMapPlugin);

export default {};
</script>
```

## Module injection

The heat map components are segregated into individual feature-wise modules. To use its feature, you need to inject its feature service in the AppModule. In the current application,the basic heat map is modified to visualize sales revenue data for week, and  the tooltip and legend features of the heat map are used. Find the relevant feature modules and descriptions as follows.

* Legend - Provides the legend feature by injecting it.
* Tooltip - Provides the tooltip feature by injecting it.

Now, import the above-mentioned modules from the heat map package and inject them into `provide`.

```javascript
import Vue from "vue";
import { HeatMapPlugin, Legend, Tooltip } from "@syncfusion/ej2-vue-heatmap";

Vue.use(HeatMapPlugin);

export default {
  provide: {
    heatmap: [Legend, Tooltip]
  }
};
 ```

## Populate heat map with data

This section explains how to populate the following two-dimensional array data to the heat map.

{% tab template="heatmap-chart/getting-started"%}

```html

<template>
    <div id="app">
        <ejs-heatmap id="heatmap" :dataSource='dataSource'></ejs-heatmap>
    </div>
</template>
<script>
import Vue from 'vue';
import { HeatMapPlugin } from '@syncfusion/ej2-vue-heatmap';
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
        ]
    }
  }
}
</script>

```

{% endtab %}

## Enable axis labels

You can add axis labels to the heat map and format those labels using the [`xAxis`](../api/heatmap/#xaxis) and [`yAxis`](../api/heatmap/#yaxis) properties. Axis labels provide additional information about the data points populated in the heat map.

{% tab template="heatmap-chart/getting-started"%}

```html

<template>
    <div class="control_wrapper">
        <ejs-heatmap id="heatmap" :dataSource='dataSource' :xAxis='xAxis' :yAxis='yAxis'></ejs-heatmap>
    </div>
</template>
<script>
import Vue from 'vue';
import { HeatMapPlugin, Tooltip, Legend } from '@syncfusion/ej2-vue-heatmap';
Vue.use(HeatMapPlugin);

export default {
  data: function() {
    return {
        xAxis: {
            labels: ['Nancy', 'Andrew','Janet', 'Margaret', 'Steven',
                        'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin', 'Mario'],
        },
        yAxis:{
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
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
        ]
    }
  },
  provide:{
    heatmap:[Tooltip, Legend]
},
}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-vue-heatmap/styles/material.css';
</style>

```

{% endtab %}

## Add heat map title

Add a title using the [`titleSettings`](../api/heatmap/#titlesettings) property to the heat map to provide quick information to the user about the data populated in the heat map.

{% tab template="heatmap-chart/getting-started"%}

```html

<template>
    <div class="control_wrapper">
        <ejs-heatmap id="heatmap" :dataSource='dataSource' :xAxis='xAxis' :yAxis='yAxis' :titleSettings='titleSettings'></ejs-heatmap>
    </div>
</template>
<script>
import Vue from 'vue';
import { HeatMapPlugin, Tooltip, Legend } from '@syncfusion/ej2-vue-heatmap';
Vue.use(HeatMapPlugin);

export default {
  data: function() {
    return {
        xAxis: {
            labels: ['Nancy', 'Andrew','Janet', 'Margaret', 'Steven',
                        'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin', 'Mario'],
         },
        yAxis:{
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
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
        ]
    }
  },
  provide:{
    heatmap:[Tooltip, Legend]
},
}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-vue-heatmap/styles/material.css';
</style>

```

{% endtab %}

## Enable legend

Use a legend for the heat map in the [`legendSettings`](../api/heatmap/#legendsettings) object by setting the [`visible`](../api/heatmap/legendSettings/#visible) property to true and injecting the `Legend` module into the `provide`.

{% tab template="heatmap-chart/getting-started"%}

```html

<template>
    <div class="control_wrapper">
        <ejs-heatmap id="heatmap" :dataSource='dataSource' :xAxis='xAxis' :yAxis='yAxis' :titleSettings='titleSettings' :legendSettings='legendSettings'></ejs-heatmap>
    </div>
</template>
<script>
import Vue from 'vue';
import { HeatMapPlugin, Tooltip, Legend } from '@syncfusion/ej2-vue-heatmap';
Vue.use(HeatMapPlugin);

export default {
  data: function() {
    return {
        xAxis: {
            labels: ['Nancy', 'Andrew','Janet', 'Margaret', 'Steven',
                        'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin', 'Mario'],
         },
        yAxis:{
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
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
        legendSettings: {
            visible:true,
            position: 'Right',
            showLabel: true,
            height: "150"
        }
    }
  },
  provide:{
    heatmap:[Tooltip, Legend]
},
}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-vue-heatmap/styles/material.css';
</style>

```

{% endtab %}

## Add data label

Add data labels to improve the readability of the heat map. This can be achieved by setting the [`showLabel`](../api/heatmap/cellSettings/#showlabel) property to true in the [`cellSettings`](../api/heatmap/#cellsettings) object.

{% tab template="heatmap-chart/getting-started"%}

```html

<template>
    <div class="control_wrapper">
       <ejs-heatmap id="heatmap" :dataSource='dataSource' :xAxis='xAxis' :yAxis='yAxis' :titleSettings='titleSettings' :legendSettings='legendSettings' :cellSettings='cellSettings'>
       </ejs-heatmap>
    </div>
</template>
<script>
import Vue from 'vue';
import { HeatMapPlugin, Tooltip, Legend } from '@syncfusion/ej2-vue-heatmap';
Vue.use(HeatMapPlugin);

export default {
  data: function() {
    return {
        xAxis: {
            labels: ['Nancy', 'Andrew','Janet', 'Margaret', 'Steven',
                        'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin', 'Mario'],
         },
        yAxis:{
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        cellSettings: {
            showLabel: true,
        },
        titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
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
        legendSettings: {
            visible:true,
            position: 'Right',
            showLabel: true,
            height: "150"
        }
    }
  },
  provide:{
    heatmap:[Tooltip, Legend]
},
}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-vue-heatmap/styles/material.css';
</style>

```

{% endtab %}

## Add custom cell palette

The default palette settings of the heat map cells can be customized by using the [`paletteSettings`](../api/heatmap/#palettesettings) property.
Using the [`palette`](../api/heatmap/paletteSettings/#palette) property in `paletteSettings` object, you can change the color set for the cells. You can change the color mode of the cells to fixed or gradient mode using the [`type`](../api/heatmap/paletteSettings/#type) property.

{% tab template="heatmap-chart/getting-started"%}

```html

<template>
    <ejs-heatmap id="heatmap" :dataSource='dataSource' :xAxis='xAxis' :yAxis='yAxis' :titleSettings='titleSettings' :legendSettings='legendSettings' :cellSettings='cellSettings' :paletteSettings='paletteSettings'></ejs-heatmap>
</template>
<script>
import Vue from 'vue';
import { HeatMapPlugin, Tooltip, Legend } from '@syncfusion/ej2-vue-heatmap';
Vue.use(HeatMapPlugin);

export default {
  data: function() {
    return {
        xAxis: {
            labels: ['Nancy', 'Andrew','Janet', 'Margaret', 'Steven',
                        'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin', 'Mario'],
         },
        yAxis:{
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        cellSettings: {
            showLabel: true,
        },
        titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
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
        legendSettings: {
            visible:true,
            position: 'Right',
            showLabel: true,
            height: "150"
        },
        paletteSettings: {
            palette: [
                { value: 0, color: '#C06C84' },
                { value: 50, color: '#6C5B7B' },
                { value: 100, color: '#355C7D' }
                ],
            type: "Gradient"
        }
    }
  },
  provide:{
    heatmap:[Tooltip, Legend]
},
}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-vue-heatmap/styles/material.css';
</style>

```

{% endtab %}

## Enable tooltip

The tooltip is used when you cannot display information by using the data labels due to space constraints. You can enable the tooltip by setting the [`showTooltip`](../api/heatmap/#showtooltip) property to `true` and injecting the `Tooltip` module into the `provide`.

{% tab template="heatmap-chart/getting-started"%}

```html

<template>
    <ejs-heatmap id="heatmap" :dataSource='dataSource' :xAxis='xAxis' :yAxis='yAxis' :titleSettings='titleSettings' :legendSettings='legendSettings' :cellSettings='cellSettings'  :showTooltip='showTooltip'></ejs-heatmap>
</template>
<script>
import Vue from 'vue';
import { HeatMapPlugin, Tooltip, Legend } from '@syncfusion/ej2-vue-heatmap';
Vue.use(HeatMapPlugin);

export default {
  data: function() {
    return {
        xAxis: {
            labels: ['Nancy', 'Andrew','Janet', 'Margaret', 'Steven',
                        'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin', 'Mario'],
         },
        yAxis:{
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        cellSettings: {
            showLabel: true,
        },
        titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
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
        legendSettings: {
            visible:true,
            position: 'Right',
            showLabel: true,
            height: "150"
        },
        showTooltip:true
    }
  },
  provide:{
    heatmap:[Tooltip, Legend]
},
}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-vue-heatmap/styles/material.css';
</style>

```

{% endtab %}
