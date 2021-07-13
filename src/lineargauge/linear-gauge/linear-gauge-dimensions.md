---
title: "Dimensions in Vue Linear Gauge component | Syncfusiion"

component: "Linear Gauge"

description: "Learn here all about the Dimensions of Syncfusion Vue Linear Gauge component and more."
---

# Dimensions in Vue Linear Gauge

## Size for Linear Gauge

The height and width of the Linear Gauge can be set using the [`width`](../api/linear-gauge/#width) and [`height`](../api/linear-gauge/#height) properties in [`ejs-lineargauge`](../api/linear-gauge/).

### In Pixel

The size of the Linear Gauge can be set in pixel as demonstrated below.

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```html
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge  width= '650px' height= '200px'></ejs-lineargauge>
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

By setting value in percentage, Linear Gauge receives its dimension matching to its parent. For example, when the height is set as "**50%**", Linear Gauge renders to half of the parent height. The Linear Gauge will be responsive when the width is set as "**100%**".

{% tab template="linear-gauge/getting-started", isDefaultActive=true %}

```html
<template>
  <div class="content-wrapper">
    <div align='center'>
      <ejs-lineargauge  width= '100%' height= '50%'></ejs-lineargauge>
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

> Note: When the component's size is not specified, the height will be "**450px**" and the width will be the same as the parent element's width.