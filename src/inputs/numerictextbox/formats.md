---
title: "Formats"
component: "NumericTextBox"
description: "Custom formats in numeric textbox"
---

# Number Formats

You can format the value of NumericTextBox using [`format`](../api/numerictextbox#format) property.
The value will be displayed in the specified format when the component is in focused out state. The format string
supports both the [standard numeric format](../common/internationalization#supported-format-string/)
and [custom numeric format](../common/internationalization#custom-number-formatting-and-parsing/).

## Standard formats

From the [standard numeric formats](../common/internationalization#supported-format-string/), you can use the numeric related
format specifiers such as `n`,`p` and `c` in the NumericTextBox component. By using these format specifiers, you can achieve the percentage
and currency textbox behavior also.

The below example demonstrates percentage and currency formats.

{% tab template="numeric-textbox/number-formats/standard", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-numerictextbox id="percent" format='p2' placeholder="Percentage format" floatLabelType="Auto" :value="value" :step="step" :min="min" :max="max"></ejs-numerictextbox>
        </div>
        <div class='wrap'>
           <ejs-numerictextbox id="currency" placeholder="Currency format" floatLabelType="Auto" format='c2' :value="currencyvalue"></ejs-numerictextbox>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";

Vue.use(NumericTextBoxPlugin);
export default {
  data () {
    return {
        value: 0.5,
        min: 0,
        max: 1,
        step: 0.01,

        // sets currency with 2 numbers of decimal places format
        format: 'c2'
        currencyvalue: 10,
    }
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
 .wrap {
    margin: 35px auto;
    width: 240px;
}
</style>
```

{% endtab %}

## Custom formats

From the [custom numeric format](../common/internationalization#custom-number-formatting-and-parsing/), you can provide any custom format by
combining one or more custom specifiers.

The below examples demonstrate format the value by using currency format string `#` and `0`.

{% tab template="numeric-textbox/number-formats/custom", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-numerictextbox id="numeric" format='###.##' placeholder="Custom format string #" floatLabelType="Auto" :value="value"></ejs-numerictextbox>
        </div>
        <div class='wrap'>
           <ejs-numerictextbox id="numeric1" placeholder="Custom format string 0" floatLabelType="Auto" format='000.00' :value="numvalue"></ejs-numerictextbox>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";

Vue.use(NumericTextBoxPlugin);
export default {
  data () {
    return {
        // sets the format using custom format string `#`
        value: 10,

        // sets the format using custom format string `0`
        numvalue: 10,
    }
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
 .wrap {
    margin: 35px auto;
    width: 240px;
}
</style>
```

{% endtab %}