---
title: "Animation"
component: "ProgressBar"
description: "ProgressBar support to animate the track."
---
# Animation

<!-- markdownlint-disable MD033 -->

Progress Bar support to animate the progress by using `animation` property. Enable the animation by setting **enable** property and also you can control the speed by using **duration** property.

`App.vue`

```html
<template>
    <div id='loader'>LOADING....</div>
    <div id='container'>
        <div class="row linear-parent">
            <div id="percentage" class="linear-progress">
             <ejs-progressbar
               id="percentage"
               type='Circular'
               :value='value'
               :animation="animation"
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
      value : 100,
      animation: {
        enable: true,
        duration: 2000,
        delay: 0
      },
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
