# Customize Slider Limits

Slider appearance can be customized via CSS. By overriding the slider CSS classes, the slider limit bar can be customized. Here, the limit bar is customized with different background color. By default, the slider has class `e-limits` for limits bar. You can override the class with our own color values as given in the following code snippet.

```css
.e-slider-container.e-horizontal .e-limits {
     background-color: rgba(69, 100, 233, 0.46);
}
```

{% tab template="range-slider/limits", isDefaultActive=true %}

```html
<template>
   <div id='app'>
      <div class="col-lg-8 control-section">
            <div class="content-wrapper">
                <div class="sliderwrap">
                    <label class="userselect">MinRange Slider With Limits</label>
                    <ejs-slider id="minrange" min=0 max=100 value=30  step=1 type='MinRange' :ticks='ticks' :limits='limits' :tooltip='tooltip'></ejs-slider>
                </div>
                <div class="sliderwrap">
                    <label class="userselect">Range Slider With Limits</label>
                    <ejs-slider id="range" min=0 max=100 :value='value' step=1 type='Range' :ticks='rangeTicks' :tooltip='rangeTooltip' :limits='rangeLimits'></ejs-slider>
                </div>
            </div>
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
    .content-wrapper {
    width: 52%;
    margin: 0 auto;
    min-width: 185px;
    }

    .sliderwrap {
    margin-top: 45px;
    }

    .e-bigger .content-wrapper {
    width: 80%;
    }

    .sliderwrap label {
    padding-bottom: 50px;
    font-size: 13px;
    font-weight: 500;
    margin-top: 15px;
    display: block;
    }

    .userselect {
    -webkit-user-select: none;
    /* Safari 3.1+ */
    -moz-user-select: none;
    /* Firefox 2+ */
    -ms-user-select: none;
    /* IE 10+ */
    user-select: none;
    /* Standard syntax */
    }

    .property-custom td {
    padding: 5px;
    }

    #range .e-limits, #minrange .e-limits {
    background-color: #ccc;
    background-color: rgba(69, 100, 233, 0.46);
    }
</style>
<script>
import Vue from 'vue';
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(SliderPlugin);
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
export default {
  data: function() {
    return {
            ticks:{ placement: 'Before', largeStep: 20, smallStep: 5, showSmallTicks: true },
            limits: { enabled: true, minStart: 10, minEnd: 40 },
            tooltip:{ isVisible: true, placement: 'Before', showOn: 'Focus' },
            rangeTicks: { placement: 'Before', largeStep: 20, smallStep: 5, showSmallTicks: true },
            rangeLimits: { enabled: true, minStart: 10, minEnd: 40, maxStart: 60, maxEnd: 90 },
            rangeTooltip:{ isVisible: true, placement: 'Before', showOn: 'Focus' },
            value:[30,70]
    };
  }
}
</script>

```

{% endtab %}