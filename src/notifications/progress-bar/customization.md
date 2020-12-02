---
title: "Customization"
component: "ProgressBar"
description: "The progressBar can  be customized in various ways "
---
# Customization

## Segments

We can divide a progress bar into multiple segments using a `segmentCount` to visualize the progress of multiple sequential tasks.

`App.vue`

```html
<template>
    <div id='loader'>LOADING....</div>
    <div id='container'>
        <div class="row linear-parent">
            <div id="percentage" class="linear-progress">
             <ejs-progressbar
             id='percentage'
             type='Circular'
             height='60'
             :segmentCount='segmentCount'
             :value='value'
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
     segmentCount:8,
     value:100,
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

## Thickness

You can customize the thickness of the track  using `trackThickness` and progress using `progressThickness` to render the ProgressBar with different appearances.

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
             width='90%'
             :trackThickness='trackThickness'
             :progressThickness='progressThickness'
             :value='value'
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
    animation: {
       enable: true,
       duration: 2000,
       delay: 0
       },
    trackThickness:24,
    progressThickness:24,
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

## Radius

The  radius of the progress bar can be customized using `radius` property and  corner can be customized by **cornerRadius** property.

`App.vue`

```html
<template>
    <div id='loader'>LOADING....</div>
    <div id='container'>
        <div class="row linear-parent">
            <div id="percentage" class="linear-progress">
             <ejs-progressbar
             id='percentage'
             type='Circular'
             height='160px'
             width='160px'
             trackColor='#FFD939'
             radius='100%'
             progressColor='white'
             cornerRadius='Round'
             :trackThickness='trackThickness'
             :progressThickness='progressThickness'
             :value='value'
             :animation='animation'>
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
    animation: {
       enable: true,
       duration: 2000,
       delay: 0
       },
    trackThickness:80,
    progressThickness:10,
    value:60
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

## InnerRadius

The inner radius of the progress bar can be customized using `innerRadius` property.

`App.vue`

```html
<template>
    <div id='loader'>LOADING....</div>
    <div id='container'>
        <div class="row linear-parent">
            <div id="percentage" class="linear-progress">
             <ejs-progressbar
             id='percentage'
             type='Circular'
             height='160px'
             width='160px'
             trackColor='#FFD939'
             radius='100%'
             innerRadius='80%'
             progressColor='white'
             cornerRadius='Round'
             :trackThickness='trackThickness'
             :progressThickness='progressThickness'
             :value='value'
             :animation='animation'>
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
    animation: {
       enable: true,
       duration: 2000,
       delay: 0
       },
    trackThickness:80,
    progressThickness:10,
    value:60
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

## Progress color and track color

We can customize the color of progress and track by using  **progressColor** and **trackColor** property.

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
             width='90%'
             :trackThickness='trackThickness'
             :progressThickness='progressThickness'
             :value='value'
             progressColor='#E3165B'
             trackColor='#F8C7D8'
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
    animation: {
       enable: true,
       duration: 2000,
       delay: 0
       },
    trackThickness:24,
    progressThickness:24,
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
