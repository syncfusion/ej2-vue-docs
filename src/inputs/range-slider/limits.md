---
title: "Slider Limits"
component: "Range Slider"
description: "Vue slider component supports limits feature that restricts thumb movement in min & max values and also supports interval dragging between range values."
---

# Movement Limits and Drag Interval

The slider limits restrict the slider thumb between a particular range. This is used if higher or lower value affects the process
or product where the slider is being used.

The following are the six options in the slider's limits object. Each API in the limits object is optional.

* ``enabled``: Enables the limits in the Slider.
* ``minStart``: Sets the minimum limit for the first handle.
* ``minEnd``: Sets the maximum limit for the first handle.
* ``maxStart``: Sets the minimum limit for the second handle.
* ``maxEnd``: Sets the maximum limit for the second handle.
* ``startHandleFixed``: Locks the first handle.
* ``endHandleFixed``: Locks the second handle.

## Default and MinRange Slider limits

There is only one handle in the Default and MinRange Slider, so ``minStart``, ``minEnd``, and ``startHandleFixed`` options can be used.
When the limits are enabled in the Slider, the limited area becomes darken. So you can differentiate the allowed and restricted area.
Refer to the following snippet to enable the limits in the Slider.

```typescript

    ......

    limits: { enabled: true, minStart: 10, minEnd: 40 }

    ......

```

{% tab template="range-slider/default-limit", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-slider id='default' :value='value' :limits='limits' :tooltip='tooltip' :type='type'></ejs-slider>
  </div>
</template>
<script>
import Vue from "vue";
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(SliderPlugin);

export default {
  data() {
    return {
        value: 30,
        tooltip: { isVisible: true },
        limits: { enabled: true, minStart: 10, minEnd: 40 },
        type: 'MinRange'
    };
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";;
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

## Range Slider limits

In the range slider, both handles can be restricted and locked from the limit's object. In this sample, the first handle is limited between
10 and 40, and the second handle is limited between 60 and 90.

```typescript
    ......

    limits: { enabled: true, minStart: 10, minEnd: 40, maxStart: 60, maxEnd: 90 }

    ......

```

{% tab template="range-slider/range-limit", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-slider id='default' :value='value' :limits='limits' :tooltip='tooltip' :type='type'></ejs-slider>
  </div>
</template>
<script>
import Vue from "vue";
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(SliderPlugin);

export default {
  data() {
    return {
        value: [30, 70],
        tooltip: { isVisible: true },
        limits: { enabled: true, minStart: 10, minEnd: 40, maxStart: 60, maxEnd: 90 },
        type: 'Range'
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

## Handle lock

The movement of slider handles can be locked by enabling the ``startHandleFixed`` and ``endHandleFixed`` properties in the limit's object.
In this sample, the movement of both slider handles has been locked.

```typescript

    ......

    limits: { enabled: true, startHandleFixed: true, endHandleFixed: true }

    ......

```

{% tab template="range-slider/handle-lock", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-slider id='default' :value='value' :limits='limits' :tooltip='tooltip' :type='type'></ejs-slider>
  </div>
</template>
<script>
import Vue from "vue";
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(SliderPlugin);

export default {
  data() {
    return {
        value: [30, 70],
        tooltip: { isVisible: true },
        limits: { enabled: true, startHandleFixed: true, endHandleFixed: true },
        type: 'Range'
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
