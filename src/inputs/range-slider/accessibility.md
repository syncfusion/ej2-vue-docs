---
title: "Slider Accessibility"
component: "Range Slider"
description: "Vue slider component has accessibility support to help access the features via keyboard, on-screen readers, or other assistive technology devices."
---

# Accessibility

The Slider is characterized with complete ARIA Accessibility support that helps to access
by on-screen readers and other assistive technology devices. This component is designed with the
reference of guidelines document given in the [WAI ARAI Accessibility Practices](https://www.w3.org/TR/wai-aria-practices/#slider).

The Slider component uses the `Slider` role and the following ARIA properties for its element based on the state.

| **Property** | **Functionalities** |
| --- | --- |
| aria-valuenow | It Indicates the current value of the slider. |
| aria-valuetext | Returns the current text of the slider. |
| aria-valuemin | It Indicates the Minimum value of the slider. |
| aria-valuemax | It Indicates the Maximum value of the slider. |
| aria-orientation | It Indicates the Slider Orientation. |
| aria-label | Slider left and right button label text (increment and decrement). |
| aria-labelledby | It indicates the name of the Slider. |

## Keyboard interaction

The Keyboard interaction of the Slider component is designed based on the
[WAI-ARIA Practices](https://www.w3.org/TR/wai-aria-practices/#slider ) described for Slider.
Users can use the following shortcut keys to interact with the Slider.

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Keyboard shortcuts</b></td><td>
<b>Actions</b></td></tr>
<tr>
<td>
<kbd>Right Arrow</kbd>&nbsp;&nbsp; &#124;&nbsp;&nbsp; <kbd>Up Arrow</kbd></td><td>
Increase the Slider value.
</td></tr>
<tr>
<td>
<kbd>Left Arrow</kbd>&nbsp;&nbsp; &#124;&nbsp;&nbsp; <kbd>Down Arrow</kbd></td><td>
Decrease the Slider value.</td></tr>
<tr>
<td>
<kbd>Home</kbd></td><td>
Moves to the start value (for Range Slider when the second thumb is focused and the Home key is pressed, it moves to the first thumb value).</td></tr>
<tr>
<td>
<kbd>End</kbd></td><td>
Moves to the end value (for Range Slider when the first thumb is focused and the End key is pressed, it moves to the second thumb value).</td></tr>
<tr>
<td>
<kbd>Page Up</kbd></td><td>
Increases the Slider by `largeStep` value.</td></tr>
<tr>
<td>
<kbd>Page Down</kbd></td><td>
Decreases the Slider by `largeStep` value.</td></tr>
</table>

{% tab template="range-slider/format", isDefaultActive=true %}

```html

<template>
    <div id="app">
    <div >
    <div class='label'>Slider without formatted values</div>
    <ejs-slider id='slider1' :value='value' :tooltip="tooltip" :ticks="ticks" :step="step" :type="type" :showButtons="showButtons"> </ejs-slider>
    </div>
    <div class="sliderwrapper">
    <div class='label'>Slider with formatted values</div>
    <ejs-slider id='slider2' :tooltip="wktooltip" :ticks="wkticks" :step="wkstep" :max="wkmax" :min="wkmin" :renderingTicks="renderingTicks" :tooltipChange="tooltipChange"> </ejs-slider>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(SliderPlugin);

export default {
  data() {
    return {
        ticks: { placement: 'After', largeStep: 20, smallStep: 10, showSmallTicks: true },
        tooltip: { placement: 'Before', isVisible: true, showOn: 'Always' },
        value: 30,
        step: 10,
        type: 'MinRange',
        showButtons: true,
        wkmin: 0, wkmax: 6, wkstep: 1,
        // Assigning ticks data
        wkticks: {  placement: 'After',  largeStep: 1 },
        // Assigning tooltip data
        wktooltip: {
            placement: 'Before',
            isVisible: true,
        }
    };
  },
  methods: {
        renderingTicks: function (args) {
            // Weekdays Array
            var daysArr = ['Sunday','Monday','Tuesday','Wednesday','Thrusday','Friday','Saturday'];
            // Customizing each ticks text into weeksdays
            args.text = daysArr[parseFloat(args.value)];
        },
         tooltipChange: function (args) {
                // Customizing tooltip to display the Day (in numeric) of the week
                args.text =  'Day ' + (Number(args.value) + 1).toString();
        }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
   #app {
    height: 40px;
    left: 30%;
    position: absolute;
    top: 40%;
    width: 50%;
  }
  .sliderwrapper{
      padding-top:50px;
  }
</style>
```

{% endtab %}