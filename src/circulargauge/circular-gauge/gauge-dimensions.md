---
title: "Circular Gauge Dimensions"
component: "CircularGauge"
description: "Explains how to customize the dimenstions of circular gauge"
---

# Circular Gauge Dimensions

## Size for Container

Circular gauge can render to its container size. You can set the size via inline or CSS as demonstrated below.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript
<template>
    <div id="app">
      <div class='wrapper'>
         <ejs-circulargauge ></ejs-circulargauge>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from '@syncfusion/ej2-vue-circulargauge';

Vue.use(CircularGaugePlugin);
export default {}
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

## Size for Circular Gauge

<!-- markdownlint-disable MD036 -->

You can also set size for the gauge directly through [`width`](../api/circular-gauge/#width-string) and [`height`](../api/circular-gauge/#height-string) properties.

### In Pixel

You can set the size of the gauge in pixel as demonstrated below.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
      <div class='wrapper'>
         <ejs-circulargauge width='650' height='350' ></ejs-circulargauge>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from '@syncfusion/ej2-vue-circulargauge';

Vue.use(CircularGaugePlugin);
export default {}
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>

```

{% endtab %}

### In Percentage

By setting value in percentage, gauge gets its dimension with respect to its container. For example, when
the height is ‘50%’, gauge renders to half of the container height.

{% tab template= "circular-gauge/getting-started", isDefaultActive=true %}

```typescript

<template>
    <div id="app">
      <div class='wrapper'>
         <ejs-circulargauge width='80%' height='50%'></ejs-circulargauge>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { CircularGaugePlugin } from '@syncfusion/ej2-vue-circulargauge';

Vue.use(CircularGaugePlugin);
export default {}
</script>
<style>
  .wrapper {
    max-width: 300px;
    margin: 0 auto;
  }
</style>

```

{% endtab %}

>Note: When you do not specify the size, it takes `450px` as the height and window size as its width.