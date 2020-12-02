# Date Range Slider

The date formatting can be achieved in [ticks](../../api/slider#ticks) and [tooltip](../../api/slider#tooltip) using [`renderingTicks`](../../api/slider#renderingticks) and [`tooltipChange`](../../api/slider#tooltipchange) events, respectively. The process of formatting is explained in the following sample.

{% tab template="range-slider/how-to", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div class="wrap">
      <ejs-slider
        id="ticks"
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
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
#app {
  height: 40px;
  position: absolute;
  width: 98%;
}
.wrap {
  box-sizing: border-box;
  height: 260px;
  margin: 0 auto;
  padding: 30px 10px;
  width: 460px;
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
      minVal: new Date("2013-06-13").getTime(),
      maxVal: new Date("2013-06-21").getTime(),
      value: new Date("2013-06-15").getTime(),
      stepVal: 86400000,
      // Slider ticks customization
      ticks: { placement: "After", largeStep: 2 * 86400000 }
    };
  },
  methods: {
    onTooltipChange(args) {
      let totalMiliSeconds = Number(args.text);
      // Convert the current milliseconds to the respective date in desired format
      let custom = { year: "numeric", month: "short", day: "numeric" };
      args.text = new Date(totalMiliSeconds).toLocaleDateString(
        "en-us",
        custom
      );
    },
    onRenderingTicks(args) {
      let totalMiliSeconds = Number(args.value);
      // Convert the current milliseconds to the respective date in desired format
      let custom = { year: "numeric", month: "short", day: "numeric" };
      args.text = new Date(totalMiliSeconds).toLocaleDateString(
        "en-us",
        custom
      );
    }
  }
};
</script>

```

{% endtab %}
