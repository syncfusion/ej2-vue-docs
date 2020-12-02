# Customize the UI appearance of the control

You can change the appearance of the NumericTextBox by adding custom `cssClass` to the component and enabling styles. Refer to the following example to change the appearance of the NumericTextBox.
{% tab template="numeric-textbox/how-to/cssClass", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-numerictextbox id="numeric" :value="value" placeholder='Enter value' floatLabelType='Always' cssClass='e-style'></ejs-numerictextbox>
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
      value: 10
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
  .e-numeric.e-style .e-control.e-numerictextbox  {
    color: royalblue ;
    font-size: xx-large ;
    border: 0px ;
  }
  .e-input-group.e-control-wrapper:not(.e-success):not(.e-warning):not(.e-error):not(.e-float-icon-left), .e-float-input.e-control-wrapper:hover:not(.e-success):not(.e-warning):not(.e-error):not(.e-disabled):not(.e-float-icon-left) {
    border-color: royalblue;
  }
  .e-control-wrapper.e-numeric.e-float-input.e-style .e-spin-down  {
    color:royalblue;
  }
  .e-control-wrapper.e-numeric.e-float-input.e-style .e-float-line::before {
    background: royalblue ;
  }
  .e-control-wrapper.e-numeric.e-float-input.e-style .e-float-line::after {
    background: royalblue ;
   }
  .e-control-wrapper.e-numeric.e-float-input.e-style .e-spin-up {
    color:royalblue ;
  }
  .e-control-wrapper.e-numeric.e-float-input.e-style .e-float-text.e-label-top {
    color: royalblue ;
    font-size: medium ;
  }
</style>
```

{% endtab %}