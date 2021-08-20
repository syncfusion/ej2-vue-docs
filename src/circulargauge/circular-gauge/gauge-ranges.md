---
title: "Ranges"
component: "CircularGauge"
description: "Ranges support in circular gauge"
---

# Ranges

You can categories certain interval on gauge axis using [`ranges`](../api/circular-gauge/range/#properties) property.

## Start and End

Start and end value of a range in an axis can be customized by using [`start`](../api/circular-gauge/range/#start-number) and [`end`](../api/circular-gauge/range/#end-number) properties.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
<div id="app">
    <div class='wrapper'>
    <ejs-circulargauge>
    <e-axes>
    <e-axis :ranges='ranges'></e-axis>
    </e-axes>
    </ejs-circulargauge>
   </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
            ranges: [{
             start: 40,
             end: 80
        }]
        }
    }
};
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Customization

Color and thickness of the range can be customized by using [`color`](../api/circular-gauge/range/#color-string),[`startWidth`](../api/circular-gauge/range/#startwidth-number) and [`endWidth`](../api/circular-gauge/range/#endwidth-number) property.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
    <div class='wrapper'>
    <ejs-circulargauge>
    <e-axes>
    <e-axis :ranges='ranges'></e-axis>
    </e-axes>
    </ejs-circulargauge>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
            ranges: [{
             start: 40,
            end: 80, endWidth: 15,
            startWidth: 15,
            color: '#ff5985'
        }]
        }
    }
};
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Rounded Corner Ranges

The corners of the ranges can be rounded by specifying desired values to the `roundedCornerRadius` property.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
<div id="app">
      <div class='wrapper'>
    <ejs-circulargauge >
    <e-axes>
      <e-axis minimum= 0 maximum= 120 :majorTicks= 'majorTicks' :ranges ='ranges'>
        <e-pointers>
           <e-pointer value=70 radius= '60%' :animation='animation' ></e-pointer>
    </e-pointers>
    </e-axis>
    </e-axes>
    </ejs-circulargauge>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
            animation: { enable: false },
            majorTicks: {
            height: 5
        },
        ranges: [{
            start: 0,
            end: 40,
            startWidth: 15,
            endWidth: 15,
            roundedCornerRadius: 10,
            radius: '110%'
        },{
            start: 40,
            end: 80,
            startWidth: 15,
            endWidth: 15,
            roundedCornerRadius: 10,
            radius: '110%'
        },{
            start: 80,
            end: 120,
            startWidth: 15,
            endWidth: 15,
            roundedCornerRadius: 10,
            radius: '110%'
        }]
        }
    }
};
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

<!-- markdownlint-disable MD036 -->

## Radius

You can place the range inside or outside of the axis by using [`radius`](../api/circular-gauge/range/#radius-string)
property. The radius of the range can takes value either in percentage or in pixels. By default, ranges
take 100% of the axis radius.

### In Pixel

You can set the radius of the range in pixel as demonstrated below,

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
    <div class='wrapper'>
    <ejs-circulargauge>
    <e-axes>
    <e-axis :ranges='ranges'></e-axis>
    </e-axes>
    </ejs-circulargauge>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
            ranges: [{
             start: 40,
             end: 80,
             radius: '100'
        }]
        }
    }
};
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

<!-- markdownlint-disable MD036 -->

### In Percentage

By setting value in percentage, range gets its dimension with respect to its axis radius.
For example, when the radius is ‘50%’, range renders to half of the axis radius.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
    <div class='wrapper'>
    <ejs-circulargauge>
    <e-axes>
    <e-axis  minimum= 0 maximum= 100 :ranges='ranges'></e-axis>
    </e-axes>
    </ejs-circulargauge>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
            ranges: [{
             start: 40,
             end: 80,
             radius: '50%'
        }]
        }
    }
};
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Dragging Range

The ranges can be dragged on the axis line by clicking and dragging the same. To enable or disable the range drag, use the [`enableRangeDrag`](../api/circular-gauge/circularGaugeModel/#enablerangedrag) property.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
   <div id="app">
      <div class='wrapper'>
    <ejs-circulargauge enableRangeDrag='true' height='250px' width='250px'>
    <e-axes>
      <e-axis :ranges='ranges'>
        <e-pointers>
           <e-pointer value=50></e-pointer>
    </e-pointers>
    </e-axis>
    </e-axes>
    </ejs-circulargauge>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
            ranges: [{
              start: 0,
              end: 100,
              startWidth: 8, endWidth: 8,
              radius: '108%',
              color: '#30B32D'
            }]
        }
    }
};
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Multiple Ranges

You can add multiple ranges to an axis with the above customization as demonstrated below.

>Note: You can set the range color to axis ticks and labels by enabling `useRangeColor` property in [`majorTicks`](../api/circular-gauge/tick/),
[`minorTicks`](../api/circular-gauge/tick/) and [`labelStyle`](../api/circular-gauge/label/) object.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
    <div class='wrapper'>
   <ejs-circulargauge >
    <e-axes>
    <e-axis  :majorTicks= 'majorTicks' :minorTicks= 'minorTicks' :labelStyle= 'labelStyle' :ranges='ranges'></e-axis>
    </e-axes>
    </ejs-circulargauge>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        return {
        majorTicks: {
          useRangeColor: true
        },
        minorTicks: {
            useRangeColor: true
        },
        labelStyle: {
            useRangeColor: true
        },
            ranges: [{
            start: 0,
            end: 25,
            radius: '108%'
        },{
            start: 25,
            end: 50,
            radius: '70%'
        },{
            start: 50,
            end: 75,
            radius: '70%'
        },{
            start: 75,
            end: 100,
            radius: '108%'
        }]
        }
    }
};
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Gradient Color

Gradient support allows to add multiple colors in the ranges and pointers of the circular gauge. The following gradient types are supported in the circular gauge.

* Linear Gradient
* Radial Gradient

### Linear Gradient

Using linear gradient, colors will be applied in a linear progression. The start value of the linear gradient can be set using the [`startValue`](../api/circular-gauge/linearGradient/#startvalue) property. The end value of the linear gradient will be set using the [`endValue`](../api/circular-gauge/linearGradient/#endvalue) property. The color stop values such as color, opacity and offset are set using [`colorStop`](../api/circular-gauge/linearGradient/#colorstop) property.

To apply linear gradient to the range, follow the below code sample.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
  <div id="app">
  <div class='wrapper'>
       <ejs-circulargauge style='display:block' align='center' id='range-container'>
        <e-axes>
            <e-axis :radius='gaugeRadius' :startAngle='startAngle' :endAngle='endAngle' :majorTicks='majorTicks' :lineStyle='lineStyle' :minorTicks='minorTicks' :labelStyle='labelStyle' :ranges='ranges'>
                <e-pointers>
                    <e-pointer :cap='cap' :pointerWidth=0></e-pointer>
                </e-pointers>
            </e-axis>
        </e-axes>
    </ejs-circulargauge>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin, Gradient } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        var rangeLinearGradient = {
          startValue: '0%', endValue: '100%',
          colorStop: [
          { color: '#9E40DC', offset: '0%', opacity: 0.9 },
          { color: '#E63B86', offset: '70%', opacity: 0.9 }]
        }
        return {
            gaugeRadius: '90%',
            startAngle: 200,
            endAngle: 160,
            majorTicks: {
                width: 0
            },
            lineStyle:  { width: 0 },
            minorTicks: {
                width: 0
            },
            labelStyle: {
                 position: 'Inside', useRangeColor: true,
                 font: { size: '0px', color: 'white', fontFamily: 'Roboto', fontStyle: 'Regular' }
            },
            ranges: [{
                start: 0, end: 100,
                radius: '90%',
                startWidth: 30, endWidth: 30,
                roundedCornerRadius: 20,
                linearGradient: rangeLinearGradient
            }],
            cap: {
                radius: 0
            },
    }
  },
  provide: {
        circulargauge: [Gradient]
    }
};
</script>
<style>
    .wrapper {
        max-width: 500px;
        margin: 0 auto;
    }
</style>
```

{% endtab %}

### Radial Gradient

Using radial gradient, colors will be applied in circular progression. The inner circle position of the radial gradient will be set using the [`innerPosition`](../api/circular-gauge/radialGradient/#innerposition) property. The outer circle position of the radial gradient can be set using the [`outerPosition`](../api/circular-gauge/radialGradient/#outerposition) property. The color stop values such as color, opacity and offset are set using [`colorStop`](../api/circular-gauge/radialGradient/#colorstop) property.

To apply radial gradient to the range, follow the below code sample.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
  <div id="app">
  <div class='wrapper'>
       <ejs-circulargauge style='display:block' align='center' id='range-container'>
        <e-axes>
            <e-axis :radius='gaugeRadius' :startAngle='startAngle' :endAngle='endAngle' :majorTicks='majorTicks' :lineStyle='lineStyle' :minorTicks='minorTicks' :labelStyle='labelStyle' :ranges='ranges'>
                <e-pointers>
                    <e-pointer :cap='cap' :pointerWidth=0></e-pointer>
                </e-pointers>
            </e-axis>
        </e-axes>
      </ejs-circulargauge>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin, Gradient } from "@syncfusion/ej2-vue-circulargauge";

Vue.use(CircularGaugePlugin);
export default {
    data: function () {
        var rangeRadialGradient = {
            radius: '50%', innerPosition: { x: '50%', y: '50%' },
            outerPosition: { x: '50%', y: '50%' },
            colorStop: [
            { color: '#9E40DC', offset: '90%', opacity: 0.9 },
            { color: '#E63B86', offset: '160%', opacity: 0.9 }]
        }
        return {
            gaugeRadius: '90%',
            startAngle: 200,
            endAngle: 160,
            majorTicks: {
                width: 0
            },
            lineStyle:  { width: 0 },
            minorTicks: {
                width: 0
            },
            labelStyle: {
                 position: 'Inside', useRangeColor: true,
                 font: { size: '0px', color: 'white', fontFamily: 'Roboto', fontStyle: 'Regular' }
            },
            ranges: [{
                start: 0, end: 100,
                radius: '90%',
                startWidth: 30, endWidth: 30,
                roundedCornerRadius: 20,
                radialGradient: rangeRadialGradient
            }],
            cap: {
                radius: 0
            },
    }
  },
  provide: {
      circulargauge: [Gradient]
    }
};
</script>
<style>
    .wrapper {
        max-width: 500px;
        margin: 0 auto;
    }
</style>
```

{% endtab %}

## See also

* [Tooltip for Ranges](https://ej2.syncfusion.com/documentation/circular-gauge/gauge-user-interaction/tooltip-for-ranges-and-annotations/)