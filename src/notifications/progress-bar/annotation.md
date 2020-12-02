---
title: "Annotation and Label"
component: "ProgressBar"
description: "ProgressBar component  supports the annotation and label"
---
# Annotation and Label

## Annotation

In the circular progress bar, you can add any view to the center using the **Content** property in annotation.

For example, you can include add, start, or pause button to control the progress. You can also add an image that indicates the actual task in progress or add custom text that conveys how far the task is completed.

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
               :trackThickness='trackThickness'
               :progressThickness='progressThickness'
              >
            <e-progressbar-annotations>
              <e-progressbar-annotation
                :content="content"
               ></e-progressbar-annotation>
            </e-progressbar-annotations>
           </ejs-progressbar>
          </div>
       </div>
    </div>
</template>
<script>
import Vue from "vue";
import { Browser } from "@syncfusion/ej2-base";
import { ProgressBarPlugin, ProgressAnnotation } from "@syncfusion/ej2-vue-progressbar";

Vue.use(ProgressBarPlugin);

export default Vue.extend({
  data: function() {
    return {
     trackThickness:10,
     progressThickness:10,
     content: '<div id="point1" style="font-size:20px;font-weight:bold;color:#ffffff;fill:#ffffff"><span>60%span><div>'
    };
  },
  provide: {
    progressbar: [ProgressAnnotation]
  },
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

## Label

You can show the progress value in both linear and cicular progress bar using **showProgressValue** property.

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
              :textRender='textRender'
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
     value:50,
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
     textRender: function(args) {
        args.text = '50';
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
