---
title: "Modes"
component: "ProgressBar"
description: "Visualize progress in different modes."
---
# Modes

Visualize progress in different modes.

## Determinate

This is the default state. You can use it when the progress estimation is known.

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
            height='60'
            :value='value'
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
    value:100
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

## Indeterminate

By enabling the **IsIndeterminate** property, the state of the progress bar can be changed to indeterminate when the progress cannot be estimated or is not being calculated. It can be combined with determinate mode to know that the application is estimating progress before the actual progress starts.

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
            height='60'
            :value='value'
            :isIndeterminate='isIndeterminate'
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
    value:20,
    isIndeterminate:true
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

## Buffer

You can use a secondary progress indicator when the primary progress depends on the secondary progress. This will allow users to visualize both primary and secondary progress simultaneously.

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
            height='60'
            :value='value'
            :secondaryProgress='secondaryProgress'
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
    value:40,
    secondaryProgress:60
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
