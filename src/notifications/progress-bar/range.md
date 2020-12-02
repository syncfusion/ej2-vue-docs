---
title: "Range"
component: "ProgressBar"
description: "The ProgressBar Visualize the ProgressBar range"
---

# Range

<!-- markdownlint-disable MD033 -->
Range represents the entire span of the ProgressBar and can be defined using the `minimum` and `maximum` properties.

`App.vue`

```html
<template>
    <div id='loader'>LOADING....</div>
    <div id='container'>
        <div class="row linear-parent">
            <div id="percentage" class="linear-progress">
             <ejs-progressbar
              id='percentage'
              type='Linear'
              :minimum='minimum'
              :maximum='maximum'
              :trackThickness='trackThickness'
              :progressThickness='progressThickness'
              :value='value'
              :labelStyle='labelStyle'
              :showProgressValue='showProgressValue'
              :animation='animation'
              >
            </ejs-progressbar>
          </div>
         </div>
    </div>
</template>
<script>
import Vue from "vue";
import { Browser } from "@syncfusion/ej2-base";
import { ProgressBarPlugin } from "@syncfusion/ej2-vue-progressbar";

Vue.use(ProgressBarPlugin);

export default Vue.extend({
  data: function() {
    return {
     trackThickness:24,
     progressThickness:24,
     minimum:10,
     maximum:90,
     value:90,
     animation: {
       enable: true,
       duration: 2000,
       delay: 0
       },
     labelStyle: {
       color: '#FFFFFF'
       },
     showProgressValue: true
    };
  },
  provide: {},
  methods: {}
});
</script>
<style>
  #loader {
    color: #008cff;
    height: 40px;
    left: 45%;
    position: absolute;
    top: 45%;
    width: 30%;
}
  #container {
    display: -webkit-box;
}
</style>

```
