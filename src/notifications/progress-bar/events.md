---
title: "Events"
component: "ProgressBar"
description: "Visualize progress events"
---

# Events

## Value Change

<!-- markdownlint-disable MD033 -->

**valueChanged** event is triggered when the progress value is changed.

`App.vue`

```html
<template>
    <div id='loader'>LOADING....</div>
    <div id='container'>
        <div class="row linear-parent">
            <div id="percentage" class="linear-progress">
             <ejs-progressbar
              refs=event
              id='percentage'
              type='Linear'
              :trackThickness='trackThickness'
              :progressThickness='progressThickness'
              :value='value'
              :labelStyle='labelStyle'
              :valueChanged='valueChanged'
              :showProgressValue='showProgressValue'
              :animation='animation'
              >
            </ejs-progressbar>
          </div>
         <button id="reLoad" @click="onClick()">ValueChanged</button>
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
  methods: {
     valueChanged: function(args) {
        args.progressColor = '#2BB20E';
     },
     onClick: ()=> {
       this.refs.event.value = 50;
     }
  }
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

## ProgressCompleted

**ProgressCompleted** event is triggers when the ProgressBar attains the maximum value.

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
              :trackThickness='trackThickness'
              :progressThickness='progressThickness'
              :value='value'
              :labelStyle='labelStyle'
              :ProgressCompleted='ProgressCompleted'
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
  methods: {
     ProgressCompleted: function(args) {
        args.progressColor = '#2BB20E';
     }
   }
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
