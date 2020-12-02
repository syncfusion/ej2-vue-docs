---
title: "Slider Formatting"
component: "Range Slider"
description: "Vue slider supports formatting to customize slider values like time, currency & km, values, also displayed in ticks & tooltip."
---

# Formatting

The `format` feature used to customize the units of Slider values to desired format.
The formatted values will also be applied to the ARIA attributes of the slider. There are two ways of achieving formatting in slider.

* Use the [format](../api/slider/tooltipDataModel/#format) API of slider which utilizes our [Internationalization](../common/internationalization/) to format values.

* Customize using the events namely `renderingTicks` and `tooltipChange`.

{% tab template="range-slider/format", isDefaultActive =true %}

```html
<template>
    <div id="app">
    <ejs-slider id='format' :value='value' :min="min" :max="max" :step="step"
    :tooltip="tooltip" :ticks="ticks" ></ejs-slider>
  </div>
</template>
<script>
import Vue from "vue";
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(SliderPlugin);

export default {
  data() {
    return {
      min: 0, max: 100, step: 1, value: 30,
    // Applying currency formatting for tooltip with two decimal specifiers
    tooltip: { isVisible: true, format: 'C2' },
    // Applying currency formatting for ticks with two decimal specifiers
    ticks: { placement: 'After', format: 'C2', largeStep: 20, smallStep: 10, showSmallTicks: true }
    };
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
</style>
```

{% endtab %}

## Using format API

In this method, we have different predefined formatting styles like Numeric (N), Percentage (P), Currency (C) and `#` specifiers.
In this below example, we have formatted the `ticks` and `tooltip` values into percentage.

{% tab template="range-slider/format", isDefaultActive =true %}

```html
<template>
    <div id="app">
    <ejs-slider id='api' :value='value' :min="min" :max="max" :step="step"
    :tooltip="tooltip" :ticks="ticks" ></ejs-slider>
  </div>
</template>
<script>
import Vue from "vue";
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(SliderPlugin);

export default {
  data() {
    return {
    min: 0, max: 1, value: 0.3, step: 0.01,
    // Assigning ticks values to percentage formatting
    ticks: { placement: 'After', largeStep: .2, smallStep: .1, showSmallTicks: true, format: 'P0' },
    // Assigning tooltip values to percentage formatting
    tooltip: { placement: 'Before', isVisible: true, showOn: 'Always', format: 'P0' }
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
</style>

```

{% endtab %}

## Using Events

In this method, we will be retrieving the values from the slider events then process them to desired formatted the values.
In this sample we have customized the `ticks` values into weekdays as one formatting and `tooltip` values into day of the week as another formatting.

{% tab template="range-slider/format", isDefaultActive =true %}

```html
<template>
    <div id="app">
    <ejs-slider id='events' :value='value' :tooltip="tooltip" :ticks="ticks" :min="min" :max="max" :renderingTicks="renderingTicks" :tooltipChange="tooltipChange"></ejs-slider>
  </div>
</template>
<script>
import Vue from "vue";
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(SliderPlugin);

export default {
  data() {
    return {
       // Minimum value
        min: 0,
        // Maximum value
        max: 6,
        // Slider current value
        value: 2,
        // Assigning ticks data
        ticks: {
            placement: 'After',
            largeStep: 1
        },
        // Assigning tooltip data
        tooltip: {
            placement: 'Before',
            isVisible: true
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
</style>
```

{% endtab %}
