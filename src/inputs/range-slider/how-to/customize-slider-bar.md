# Customize Slider Bar

Slider appearance can be customized through CSS. By overriding the slider CSS classes, you can customize the slider bar. The slider bar can be customized with different themes. By default, slider have class name `e-slider-track` for bar. The class can be overridden with our own color values like the following code snippet.

```css
.e-control.e-slider .e-slider-track .e-range {
    background: linear-gradient(left, #e1451d 0, #fdff47 17%, #86f9fe 50%, #2900f8 65%, #6e00f8 74%, #e33df9 83%, #e14423 100%);
}
```

You can also apply background color for a certain range depending upon slider values, using change event.

```typescript
  onChange(args){
           let sliderTrack = document.getElementById('dynamic_color_slider').querySelector('.e-range');
           let sliderHandle = document.getElementById('dynamic_color_slider').querySelector('.e-handle');
            if (args.value > 0 && args.value <= 25) {
                // Change handle and range bar color to green when
                (sliderHandle).style.backgroundColor = 'green';
                (sliderTrack).style.backgroundColor = 'green';
            } else if (args.value > 25 && args.value <= 50) {
                // Change handle and range bar color to royal blue
                (sliderHandle).style.backgroundColor = 'royalblue';
                (sliderTrack).style.backgroundColor = 'royalblue';
            } else if (args.value > 50 && args.value <= 75) {
                // Change handle and range bar color to dark orange
                (sliderHandle).style.backgroundColor = 'darkorange';
                (sliderTrack).style.backgroundColor = 'darkorange';
            } else if (args.value > 75 && args.value <= 100) {
                // Change handle and range bar color to red
                (sliderHandle).style.backgroundColor = 'red';
                (sliderTrack).style.backgroundColor = 'red';
            }
    }
```

{% tab template="range-slider/bar", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div class="col-lg-12 control-section">
      <div class="slider-content-wrapper">
        <div class="slider_container">
          <div class="slider-labeltext slider_userselect">Height</div>
          <!-- Square slider element -->
          <ejs-slider id="height_slider" value="30" min="0" max="100"></ejs-slider>
        </div>
        <div class="slider_container">
          <div class="slider-labeltext slider_userselect">Gradient color</div>
          <ejs-slider id="gradient_slider" min="0" max="100" value="30" type="MinRange"></ejs-slider>
        </div>
        <div class="slider_container">
          <div class="slider-labeltext slider_userselect">Dynamic thumb and selection bar color</div>
          <ejs-slider
            id="dynamic_color_slider"
            min="0"
            max="100"
            value="30"
            type="MinRange"
            v-on:created="onCreated"
            v-on:change="onChange"
          ></ejs-slider>
        </div>
      </div>
    </div>
  </div>
</template>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
#app {
  height: 40px;
  position: absolute;
  width: 98%;
}
.slider-content-wrapper {
  width: 40%;
  margin: 0 auto;
  min-width: 185px;
}

.slider-userselect {
  -webkit-user-select: none;
  /* Safari 3.1+ */
  -moz-user-select: none;
  /* Firefox 2+ */
  -ms-user-select: none;
  /* IE 10+ */
  user-select: none;
  /* Standard syntax */
}

.slider-labeltext {
  text-align: left;
  font-weight: 500;
  font-size: 13px;
  padding-bottom: 10px;
}

#height_slider .e-handle,
#gradient_slider .e-handle {
  height: 20px;
  width: 20px;
  margin-left: -10px;
  top: calc(50% - 10px);
}

.slider_container {
  margin-top: 40px;
}

#height_slider .e-tab-handle::after {
  background-color: #f9920b;
}

#height_slider .e-slider-track {
  height: 8px;
  top: calc(50% - 4px);
  border-radius: 0;
}

#gradient_slider .e-range {
  height: 6px;
  top: calc(50% - 3px);
  border-radius: 5px;
  background: -webkit-gradient(
    linear,
    left top,
    left bottom,
    color-stop(0%, #1e5799),
    color-stop(100%, #7db9e8)
  );
  background: -webkit-linear-gradient(
    left,
    #e1451d 0,
    #fdff47 17%,
    #86f9fe 50%,
    #2900f8 65%,
    #6e00f8 74%,
    #e33df9 83%,
    #e14423 100%
  );
  background: linear-gradient(
    left,
    #e1451d 0,
    #fdff47 17%,
    #86f9fe 50%,
    #2900f8 65%,
    #6e00f8 74%,
    #e33df9 83%,
    #e14423 100%
  );
  background: -moz-linear-gradient(
    left,
    #e1451d 0,
    #fdff47 17%,
    #86f9fe 50%,
    #2900f8 65%,
    #6e00f8 74%,
    #e33df9 83%,
    #e14423 100%
  );
}

#gradient_slider .e-slider-track {
  height: 8px;
  top: calc(50% - 4px);
  border-radius: 5px;
}
</style>
<script>
import Vue from "vue";
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(SliderPlugin);
import { enableRipple } from "@syncfusion/ej2-base";
enableRipple(true);
export default {
  data: function() {
    return {};
  },
  methods: {
    onCreated(args) {
      let sliderTrack = document
        .getElementById("dynamic_color_slider")
        .querySelector(".e-range");
      let sliderHandle = document
        .getElementById("dynamic_color_slider")
        .querySelector(".e-handle");
      sliderHandle.style.backgroundColor = "green";
      sliderTrack.style.backgroundColor = "green";
    },
    onChange(args) {
      let sliderTrack = document
        .getElementById("dynamic_color_slider")
        .querySelector(".e-range");
      let sliderHandle = document
        .getElementById("dynamic_color_slider")
        .querySelector(".e-handle");
      if (args.value > 0 && args.value <= 25) {
        // Change handle and range bar color to green when
        sliderHandle.style.backgroundColor = "green";
        sliderTrack.style.backgroundColor = "green";
      } else if (args.value > 25 && args.value <= 50) {
        // Change handle and range bar color to royal blue
        sliderHandle.style.backgroundColor = "royalblue";
        sliderTrack.style.backgroundColor = "royalblue";
      } else if (args.value > 50 && args.value <= 75) {
        // Change handle and range bar color to dark orange
        sliderHandle.style.backgroundColor = "darkorange";
        sliderTrack.style.backgroundColor = "darkorange";
      } else if (args.value > 75 && args.value <= 100) {
        // Change handle and range bar color to red
        sliderHandle.style.backgroundColor = "red";
        sliderTrack.style.backgroundColor = "red";
      }
    }
  }
};
</script>

```

{% endtab %}
