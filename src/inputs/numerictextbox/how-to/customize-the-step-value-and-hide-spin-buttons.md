# Customize the step value and hide spin buttons

The spin buttons allow you to increase or decrease the value with the predefined [`step`](../../api/numerictextbox#step-number)
value. The visibility of spin buttons can be set using the[`showSpinButton`](../../api/numerictextbox#showspinbutton-boolean) property.

{% tab template="numeric-textbox/how-to/step-value", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-numerictextbox id="numeric" :showSpinButton='false' :value="value" :step="step" :min="min" :max="max"></ejs-numerictextbox>
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
        step: 2,
        min: 10,
        max: 100,
        value: 16
    }
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
 .wrap {
  margin: 0 auto;
  width: 240px;
  padding-top: 100px;
}
</style>
```

{% endtab %}