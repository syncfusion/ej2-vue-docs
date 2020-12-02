---
title: "Slider Ticks"
component: "Range Slider"
description: "Vue slider visually represents the slider values with small and large ticks placed before, after, or both, of the slider bar."
---

# Ticks

The Ticks in Slider supports you to easily identify the current value/values of the Slider.
It contains `smallStep` and `largeStep`. The value of the major ticks alone will be displayed in the slider.
In order to enable/disable the small ticks, use the `showSmallTicks` property.

{% tab template="range-slider/ticks", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-slider id='ticks' :value='value' :tooltip="tooltip" :ticks="ticks"></ejs-slider>
  </div>
</template>
<script>
import Vue from "vue";
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(SliderPlugin);

export default {
  data() {
    return {
       tooltip: { placement: 'Before', isVisible: true, showOn: 'Always' },
        value: 30,
        // Slider ticks customization
        ticks: { placement: 'After', largeStep: 20, smallStep: 10, showSmallTicks: true }
    };
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
   #app {
    height: 40px;
    left: 30%;
    position: absolute;
    top: 40%;
    width: 50%;
  }
</style>

```

{% endtab %}

## Step

When the Slider is moved, it increases/decreases the value
based on the step value. By default, the value is increased/decreased by 1. Use the `step` property to change the increment step value.

{% tab template="range-slider/ticks", isDefaultActive=true %}

```html

<template>
    <div id="app">
    <ejs-slider id='steps' :value='value' :tooltip="tooltip" :ticks="ticks" :step="step"></ejs-slider>
  </div>
</template>
<script>
import Vue from "vue";
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(SliderPlugin);

export default {
  data() {
    return {
      ticks: { placement: 'After', largeStep: 20, smallStep: 10, showSmallTicks: true },
        tooltip: { placement: 'Before', isVisible: true, showOn: 'Always' },
        value: 30,
        // Enables step
        step: 10
    };
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
   #app {
    height: 40px;
    left: 30%;
    position: absolute;
    top: 40%;
    width: 50%;
  }
</style>

```

{% endtab %}

## Min and Max

Enables the minimum/starting and maximum/ending value of the Slider, by using the `min` and `max`
property. By default, the minimum value is 1 and maximum value is 100.
In the following sample the slider is rendered with the min value as 100 and max value as 1000.

{% tab template="range-slider/ticks", isDefaultActive=true %}

```html

<template>
    <div id="app">
    <ejs-slider id='minmax' :value='value' :tooltip="tooltip" :ticks="ticks" :min="min" :max="max"></ejs-slider>
  </div>
</template>
<script>
import Vue from "vue";
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(SliderPlugin);

export default {
  data() {
    return {
      ticks: { placement: 'After', largeStep: 200, smallStep: 100, showSmallTicks: true },
        tooltip: { placement: 'Before', isVisible: true, showOn: 'Always' },
        // Minimum value
        min: 100,
        // Maximum value
        max: 1100,
        // Slider current value
        value: 400
    };
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
   #app {
    height: 40px;
    left: 30%;
    position: absolute;
    top: 40%;
    width: 50%;
  }
</style>

```

{% endtab %}