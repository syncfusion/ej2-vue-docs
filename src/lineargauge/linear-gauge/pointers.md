---
title: "Pointers"
component: "LinearGauge"
description: "Pointers support in linear gauge"
---

# Pointers

Pointers are used to indicate values on the axis. Value of the pointer can be modified using the [`value`](../api/linear-gauge/pointer/#value-number) property.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="col-md-8 control-section">
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value=80 ></e-pointer>
    </e-pointers>
    </e-axis>
    </e-axes>
    </ejs-lineargauge>
   </div>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default { };
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

## Types of pointer

The Linear Gauge supports the following two types of pointers:

* Bar
* Marker

You can choose any one of the pointer by using [`type`](../api/linear-gauge/pointer/#type-string) property.

## Marker Pointer

A marker pointer is a shape, that can be placed to mark the pointer value in the linear gauge.

<b>Types of marker shapes</b>

The following marker types are available in linear gauge. You can change the marker shape using [`markerType`](../api/linear-gauge/pointer/#markertype-string) property in [`pointer`](../api/linear-gauge/pointer/#pointer-pointermodel) options. The available marker types are,

* Circle
* Rectangle
* Triangle
* InvertedTriangle
* Diamond

You can also use image instead of rendering shape as pointer. It can be achieved by using [`markerType`](../api/linear-gauge/pointer/#markertype-string) property as `Image` set image path to ['imageUrl'](../api/linear-gauge/pointer/#imageurl-string) in [`pointer`](../api/linear-gauge/pointer/#pointer-pointermodel).

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value=80 type= 'Marker'  markerType= 'Circle' ></e-pointer>
    </e-pointers>
    </e-axis>
    </e-axes>
    </ejs-lineargauge>
   </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default { };
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

<!-- markdownlint-disable MD036 -->

**Marker Pointer Customization**

The marker can be customized by using the following properties.

* [`height`](../api/linear-gauge/pointer/#height-number) - Specifies pointer height
* [`width`](../api/linear-gauge/pointer/#width-number) - Specifies pointer width
* [`color`](../api/linear-gauge/pointer/#color-string) - Specifies pointer color
* [`placement`](../api/linear-gauge/pointer/#placement-string) - Specifies pointer placement position, available placement options are 'Near', 'Far', 'Center' and 'None'
* [`offset`](../api/linear-gauge/pointer/#offset-number) - Specifies offset value from it default position.
* [`animationDuration`](../api/linear-gauge/pointer/#animationduration-number) - Specifies pointer animation duration
* [`border`](../api/linear-gauge/pointer/#pointer-bordermodel) - Specifies pointer border color and width

## Bar Pointer

Bar pointer is used to track the axis value and it will render depending upon the container type. Bar pointer starts from the beginning of the gauge and ends at the pointer value.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value=80 type= 'Bar'></e-pointer>
    </e-pointers>
    </e-axis>
    </e-axes>
    </ejs-lineargauge>
   </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default { };
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

<!-- markdownlint-disable MD036 -->

### Bar pointer customization

The bar pointer can be customized using following properties.

* [`width`](../api/linear-gauge/pointer/#width-number) - Specifies bar pointer width
* [`color`](../api/linear-gauge/pointer/#color-string) - Specifies bar pointer color
* [`offset`](../api/linear-gauge/pointer/#offset-number) - Helps to move the bar pointer from its default position.
* [`border`](../api/linear-gauge/pointer/#pointer-bordermodel) - Specifies bar pointer border width and color
* [`placement`](../api/linear-gauge/pointer/#placement-string) property is not supported for bar pointer.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value=80 type= 'Bar' color= '#f44141'></e-pointer>
    </e-pointers>
    </e-axis>
    </e-axes>
    </ejs-lineargauge>
   </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default { };
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

## Pointer placement

You can placement the marker pointer in any of the following locations using [`placement`] property.

* Far
* Near
* Center
* None

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value=60 markerType= 'Arrow' color= '#f44141' placement= 'Near'></e-pointer>
    </e-pointers>
    </e-axis>
    </e-axes>
    </ejs-lineargauge>
   </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default { };
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

## Multiple Pointers

In addition to the default pointer, you can add n number of pointer to an axis.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value=80 ></e-pointer>
           <e-pointer value=30 markerType= 'Diamond'></e-pointer>
           <e-pointer value=50 markerType= 'Circle'></e-pointer>
    </e-pointers>
    </e-axis>
    </e-axes>
    </ejs-lineargauge>
   </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default { };
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>

```

{% endtab %}

## Pointer Animation

Pointer will animate on loading the gauge. This can be handled by using [`animationDuration`](../api/linear-gauge/pointer/#animationduration-number) property. You need to specify the duration of the animation in milliseconds.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
   <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge >
    <e-axes>
      <e-axis >
        <e-pointers>
           <e-pointer value=80 animationDuration= 1000></e-pointer>
    </e-pointers>
    </e-axis>
    </e-axes>
    </ejs-lineargauge>
   </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from "@syncfusion/ej2-vue-lineargauge";

Vue.use(LinearGaugePlugin);
export default { };
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>

```

{% endtab %}

## Gradient Color

Gradient support allows to add multiple colors in the ranges and pointers of the linear gauge. The following gradient types are supported in the linear gauge.

* Linear Gradient
* Radial Gradient

### Linear Gradient

Using linear gradient, colors will be applied in a linear progression. The start value of the linear gradient can be set using the [`startValue`](../api/linear-gauge/linearGradient/#startvalue) property. The end value of the linear gradient will be set using the [`endValue`](../api/linear-gauge/linearGradient/#endvalue) property. The color stop values such as color, opacity and offset are set using [`colorStop`](../api/linear-gauge/linearGradient/#colorstop) property.

The linear gradient can be applied to all pointer types like marker and range bar. To do so, follow the below code sample.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
     <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge :orientation= 'orientation' :container= 'container'>
    <e-axes>
    <e-axis :ranges='ranges' :pointers= 'pointers' :line= 'line' :majorTicks= 'majorTicks' :minorTicks= 'minorTicks' :labelStyle= 'labelStyle'></e-axis>
    </e-axes>
    </ejs-lineargauge>
   </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin, Gradient } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
export default {
    data: function () {
        return {
        orientation: 'Horizontal',
        container: {
        width: 30, offset: 30
        },
        line: { width: 0 },
        majorTicks: { interval: 25, height: 0 },
        minorTicks: { height: 0 },
        labelStyle: {
            font: { color: '#424242',
            }, offset: 55
        },
        pointers: [{
            value: 80, height: 25,
            width: 35, placement: 'Near',
            offset: -44, markerType: 'Triangle',
            linearGradient: {
                startValue: '0%',
                endValue: '100%',
                colorStop: [
                    { color: '#fef3f9', offset: '0%', opacity: 1 },
                    { color: '#f54ea2', offset: '100%', opacity: 1 }]
            }
        }],
        ranges: [{
            start: 0, end: 80,
            startWidth: 30, endWidth: 30,
            color: '#f54ea2', offset: 30,
        }]
        }
    },
    provide: {
      lineargauge: [Gradient]
    }
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

### Radial Gradient

Using radial gradient, colors will be applied in circular progression. The inner circle position of the radial gradient will be set using the [`innerPosition`](../api/linear-gauge/radialGradient/#innerposition) property. The outer circle position of the radial gradient can be set using the [`outerPosition`](../api/linear-gauge/radialGradient/#outerposition) property. The color stop values such as color, opacity and offset are set using [`colorStop`](../api/linear-gauge/radialGradient/#colorstop) property.

The radial gradient can be applied to all pointer types like marker and range bar. To do so, follow the below code sample.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
     <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge :orientation= 'orientation' :container= 'container'>
    <e-axes>
    <e-axis :ranges='ranges' :pointers= 'pointers' :line= 'line' :majorTicks= 'majorTicks' :minorTicks= 'minorTicks' :labelStyle= 'labelStyle'></e-axis>
    </e-axes>
    </ejs-lineargauge>
   </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin, Gradient } from "@syncfusion/ej2-vue-lineargauge";
Vue.use(LinearGaugePlugin);
export default {
    data: function () {
        return {
        orientation: 'Horizontal',
        container: {
        width: 30, offset: 30
        },
        line: { width: 0 },
        majorTicks: { interval: 25, height: 0 },
        minorTicks: { height: 0 },
        labelStyle: {
            font: { color: '#424242',
            }, offset: 55
        },
        pointers: [{
            value: 80, height: 25,
            width: 35, placement: 'Near',
            offset: -44, markerType: 'Triangle',
            radialGradient: {
              radius: '60%',
              outerPosition: { x: '50%', y: '50%' },
              innerPosition: { x: '50%', y: '50%' },
              colorStop: [
                { color: '#fff5f5', offset: '0%', opacity: 0.9 },
                { color: '#f54ea2', offset: '100%', opacity: 0.8 }]
            }
        }],
        ranges: [{
            start: 0, end: 80,
            startWidth: 30, endWidth: 30,
            color: '#f54ea2', offset: 30,
        }]
        }
    },
    provide: {
      lineargauge: [Gradient]
    }
};
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}
