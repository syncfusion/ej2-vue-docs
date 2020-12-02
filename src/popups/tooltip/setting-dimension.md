---
title: "Setting Dimension for Tooltip"
component: "Tooltip"
description: "Vue tooltip component’s dimension can either be assigned auto height and width values or specific pixel values."
---

# Setting Dimension

## Height and width

The Tooltip can either be assigned auto height and width values or specific pixel values. The `width` and `height` properties are used to
 set the outer dimension of the Tooltip element. The default value for both the properties is `auto`.
  It also accepts string and number values in pixels.

The following sample explains how to set dimensions for the Tooltip.

{% tab template="tooltip/dimensions/height-width", isDefaultActive=true %}

```html
<template>
   <div id='app'>
      <div id='container'>
        <ejs-tooltip id="tooltip" content="This tooltip has 180px width and 40px height" width='180px' height='40px' target="#target">
          <div style="display: inline-block; position: relative; left: 50%;top: 100px;transform: translateX(-50%);">
              <ejs-button id='target'>Show Tooltip</ejs-button>
          </div>
        </ejs-tooltip>
      </div>
    </div>
</template>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
Vue.use(TooltipPlugin);
Vue.use(ButtonPlugin);

export default {
    data() {
    return {
    };
    }
}
</script>

<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
</style>

```

{% endtab %}

## Scroll mode

When `height` is specified with a certain pixel value and the Tooltip content overflows, the scrolling mode gets enabled.

{% tab template="tooltip/dimensions/scroll-mode", isDefaultActive=true %}

```html
<template>
  <div id='app'>
    <ejs-tooltip id='tooltip' :content='content' target='#target' width='300px' height='60px' isSticky='true'>
      <p>A green home is a type of house designed to be  <a id="target"><u>environmentally friendly</u></a>
        and sustainable. And also focuses on the efficient use of "energy, water, and building materials." As green homes
        have become more prevalent we have also seen the emergence of green affordable housing.
      </p>
    </ejs-tooltip>
  </div>
</template>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  #tooltipContent {
    padding: 0 10px;
    font-weight: 400;
    font-size: 12px;
    line-height: 22px;
  }
</style>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
Vue.use(TooltipPlugin);

var demoVue = Vue.component("demo", {
  template: `
    <div id="tooltipContent"><p><strong>Environmentally friendly</strong> or <strong>environment-friendly</strong>, <i>(also referred to as eco-friendly, nature-friendly, and green)</i> are marketing and sustainability terms referring to goods and services, laws, guidelines and policies that inflict reduced, minimal, or no harm upon ecosystems or the environment.</p></div>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data: function() {
    return {
      content: function () {
        return { template : demoVue}
      }
    };
  }
}
</script>

```

{% endtab %}

> The scrolling mode can best be seen when the sticky mode of the Tooltip is enabled. To enable sticky mode, set the `isSticky` property to true.
