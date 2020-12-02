---
title: "Slider Two-way Binding"
component: "Range Slider"
description: "Slider component V-model data binding."
---

# Two-way Binding

It can be achieved by using the `v-model` directive in vue. In the following sample, when you change a value in one slider will automatically change the value in the other slider. It updates the other slider using `value` property.

{% tab template="range-slider/two-way-binding", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div>Default Slider</div>
    <ejs-slider id='default' v-model='value'></ejs-slider>
      <div>Min Range Slider</div>
    <ejs-slider id='minRange' type='MinRange' v-model='value'></ejs-slider>
  </div>
</template>
<script>
import Vue from "vue";
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(SliderPlugin);

export default {
  data() {
    return {
        value: 30,
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