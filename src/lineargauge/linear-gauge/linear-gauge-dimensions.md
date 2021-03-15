---
title: "Linear Gauge Dimensions"
component: "LinearGauge"
description: "Explains how to customize the dimension of linear gauge component"
---

# Linear Gauge Dimensions

## Size for Linear Gauge

You can also set size for linear gauge directly through [`width`](../api/linear-gauge/linearGaugeModel/#width-string) and [`height`](../api/linear-gauge/linearGaugeModel/#height-string) properties.

### In Pixel

You can set the size of linear gauge in pixel as demonstrated below.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```html
<template>
    <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge  width= '650px' height= '350px'></ejs-lineargauge>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from '@syncfusion/ej2-vue-lineargauge';

Vue.use(LinearGaugePlugin);
export default { }
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}

### In Percentage

By setting value in percentage, linear gauge gets its dimension with respect to its container. For example, when the height is ‘50%’, linear gauge renders to half of the container height.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```html
<template>
    <div>
    <div class="content-wrapper">
    <div align='center'>
    <ejs-lineargauge  width= '100%' height= '50%'></ejs-lineargauge>
  </div>
  </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { LinearGaugePlugin } from '@syncfusion/ej2-vue-lineargauge';

Vue.use(LinearGaugePlugin);
export default { }
</script>
<style>
#content-wrapper {
    padding: 0px !important;
}
</style>
```

{% endtab %}