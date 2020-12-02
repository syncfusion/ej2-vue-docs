# Numeric Range Slider

The numeric values can be formatted into different decimal digits or fixed number of whole numbers or to represent units. The numeric processing is demonstrated as follows.

{% tab template="range-slider/numeric", isDefaultActive=true %}

```html
<template>
   <div id='app'>
     <div class='wrap'>
            <div class='label'>Slider formatted with unit representation</div>
            <ejs-slider id="slider"  min=0 max=100 step=1 value=30 :ticks='ticks' :tooltip='tooltip'>
            </ejs-slider>
        </div>

        <div class='wrap'>
            <div class='label'>Slider formatted with three decimal specifiers</div>
            <ejs-slider id="slider1" min=0.1 max=0.2 step=0.01 value=0.13 :tooltip='decimalTooltip' :ticks='decimalTicks'>
            </ejs-slider>
        </div>

        <div class='wrap'>
            <div class='label'>Slider formatted with two leading zeros</div>
            <ejs-slider id="slider2" min=0 max=100 step=1 value=30 :tooltip='formatTooltip' :ticks='formatTicks'>
            </ejs-slider>
        </div>
   </div>
</template>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
    #app {
        height: 40px;
        position: absolute;
        width: 98%;
    }
    .wrap {
    box-sizing: border-box;
    height: 100px;
    margin: 0 auto;
    padding: 30px 10px;
    width: 460px;
    }

    .wrap .label {
    text-align: center;
    }
</style>
<script>
import Vue from 'vue';
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(SliderPlugin);
export default {
  data: function() {
    return {
        tooltip: { isVisible: true, format: '##.## Km' },
        ticks: { placement: 'After', format: '##.## Km', largeStep: 20, smallStep: 10, showSmallTicks: true },
        decimalTooltip:{ isVisible: true, format: '##.#00' },
        decimalTicks:{ placement: 'After', format: '##.#00', largeStep: 0.02, smallStep: 0.01, showSmallTicks: true },
        formatTooltip:{ isVisible: true, format: '00##' },
        formatTicks:{ placement: 'After', format: '00##', largeStep: 20, smallStep: 10, showSmallTicks: true }
    };
  }
}
</script>

```

{% endtab %}
