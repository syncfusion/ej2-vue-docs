# Show Slider from Hidden state

This section demonstrates how-to render the Slider component in hidden state and make it visible in button click. We can initialize Slider in hidden state by setting the display as none.

In the sample, by clicking on the button, we can make the Slider visible from hidden state, and we must also call the [`refresh`](https://ej2.syncfusion.com/javascript/documentation/api/base/component/#refresh) method of the Slider to render it properly based on its original dimensions.

{% tab template="range-slider/hidden-slider", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <button type="button" id="btn" class="e-control e-btn" v-on:click="onClick">Button</button>
      <div id="wrap">
        <ejs-slider
          id="slider"
          :min="minVal"
          :max="maxVal"
          :value="value"
          :tooltip="tooltip"
          :ticks="ticks"
          showButtons="true"
          :step="stepVal"
          v-on:renderingTicks="onRenderingTicks"
          v-on:tooltipChange="onTooltipChange"
        ></ejs-slider>
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
  #wrap {
    box-sizing: border-box;
    height: 260px;
    margin: 0 auto;
    padding: 30px 10px;
    width: 460px;
    display: none;
  }
  </style>
  <script>
  import Vue from "vue";
  import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
  Vue.use(SliderPlugin);
  export default {
    data: function() {
      return {
        tooltip: { placement: "Before", isVisible: true },
        minVal: new Date(2013, 6, 13, 11).getTime(),
        maxVal: new Date(2013, 6, 13, 17).getTime(),
        value: new Date(2013, 6, 13, 13).getTime(),
        stepVal: 3600000,
        // Slider ticks customization
        ticks: { placement: "After", largeStep: 2 * 3600000 }
      };
    },
    methods: {
      onTooltipChange(args) {
        let totalMiliSeconds = Number(args.text);
        let custom = { hour: "2-digit", minute: "2-digit" };
        args.text = new Date(totalMiliSeconds).toLocaleTimeString(
          "en-us",
          custom
        );
      },
      onRenderingTicks(args) {
        let totalMiliSeconds = Number(args.value);
        let custom = { hour: "2-digit", minute: "2-digit" };
        args.text = new Date(totalMiliSeconds).toLocaleTimeString(
          "en-us",
          custom
        );
      },
      onClick: function (event){
        let slider = document.getElementById("wrap");
        let ticks = document.getElementById("slider");
        slider.style.display = "block";
        ticks.ej2_instances[0].refresh();
      }
    }
  };
  </script>

```

{% endtab %}
