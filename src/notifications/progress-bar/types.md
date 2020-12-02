---
title: "Types"
component: "ProgressBar"
description: "The ProgressBar Visualize the progress in different shapes"
---
# Types

Visualize progress in different shapes (rectangle, circle, and semi-circle) to give a unique appearance to your app design.

## Linear

Set **type** to Linear to get the linear progress bar. It also support secondary progress and different mode of progress.

`App.vue`

```html
<template>
     <div id='loader'>LOADING....</div>
      <div id='container'>
          <div class="row linear-parent">
              <div id="determinate" class="linear-progress">
              <ejs-progressbar
              id='determinate'
              type='Linear'
              height='60'
              :value='value1'
              :animation='animation'
              >
              </ejs-progressbar>
              </div>
              <div id="indeterminate" class="linear-progress">
              <ejs-progressbar
              id='indeterminate'
              type='Linear'
              height='60'
              :value='value2'
              :isIndeterminate='isIndeterminate'
             >
              </ejs-progressbar>
              </div>
              <div id="buffer" class="linear-progress">
              <ejs-progressbar
              id='buffer'
              type='Linear'
              height='60'
              :value='value3'
              :secondaryProgress='secondaryProgress'
              :animation=' animation'
              >
              </ejs-progressbar>
              </div>
              <div id="segment" class="linear-progress">
              <ejs-progressbar
              id='segment'
              type='Linear'
              height='60'
              :value='value4'
              :segmentCount='count'
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
    value1:100,
    value2:20,
    value3:40,
    value4:100,
    isIndeterminate:true,
    secondaryProgress:60,
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

## Circular

Set **type** to Circular to get the circular progress bar. It also support secondary progress and different mode of progress.

`App.vue`

```html
<template>
     <div id='loader'>LOADING....</div>
      <div id='container'>
          <div class="row linear-parent">
              <div id="determinate" class="linear-progress">
              <ejs-progressbar
              id='determinate'
              type='Circular'
              height='60'
              :value='value1'
              :animation='animation'
              >
              </ejs-progressbar>
              </div>
              <div id="indeterminate" class="linear-progress">
              <ejs-progressbar
              id='indeterminate'
              type='Circular'
              height='60'
              :value='value2'
              :isIndeterminate='isIndeterminate'
             >
              </ejs-progressbar>
              </div>
              <div id="buffer" class="linear-progress">
              <ejs-progressbar
              id='buffer'
              type='Circular'
              height='60'
              :value='value3'
              :secondaryProgress='secondaryProgress'
              :animation=' animation'
              >
              </ejs-progressbar>
              </div>
              <div id="segment" class="linear-progress">
              <ejs-progressbar
              id='segment'
              type='Circular'
              height='60'
              :value='value4'
              :segmentCount='count'
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
    value1:100,
    value2:20,
    value3:40,
    value4:100,
    isIndeterminate:true,
    secondaryProgress:60,
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
