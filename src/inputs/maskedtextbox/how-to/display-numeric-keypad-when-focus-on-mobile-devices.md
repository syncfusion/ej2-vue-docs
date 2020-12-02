# Display numeric keypad when focus on mobile devices

By default, on focusing the MaskedTextBox, alphanumeric keypad will be displayed on
mobile devices. Sometimes only numeric keypad for number
values is needed, and this can be achieved by setting "type" property to `tel`.
Refer to the following example to enable numeric keypad in MaskedTextBox.

{% tab template="masked-textbox/how-to/numeric", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
    <div class='wrap'>
        <ejs-maskedtextbox type='tel' class='form-control' mask='999-99999' value='342-45432'></ejs-maskedtextbox>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { MaskedTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";

Vue.use(MaskedTextBoxPlugin);
export default {
  data () {
    return {}
  },
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
 .wrap {
    margin: 0 auto;
    width: 240px;
}
</style>
```

{% endtab %}