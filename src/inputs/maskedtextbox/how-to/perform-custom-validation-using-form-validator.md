# Perform custom validation using FormValidator

To perform custom validation on the MaskedTextBox use the FormValidator along with custom validation rules.

In the following example, the MaskedTextBox is validated for invalid mobile number by adding custom validation in the rules collection of the FormValidator.

{% tab template="masked-textbox/how-to/validation", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
    <div class='wrap'>
      <form id="form-element" class="form-horizontal">
        <div class="form-group">
          <ejs-maskedtextbox id="mask" type="text" name="mask" class="form-control" mask='000-000-0000' placeholder='Mobile Number' floatLabelType='Always'></ejs-maskedtextbox>
          <button type="button" id="submit_btn" style="margin-top: 10px" v-on:click="onClick">Submit</button>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { MaskedTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";
import { FormValidator, FormValidatorModel } from '@syncfusion/ej2-inputs';

Vue.use(MaskedTextBoxPlugin);
export default {
  data () {
    return {}
  },
  mounted: function() {
    var customFn = function (args) {
        if (args.element.ej2_instances[0].value.length !== 0) {
          return args.element.ej2_instances[0].value.length >= 10; }
          else {
            return true;
        }
      };
      var custom = function (args) {
        if (args.element.ej2_instances[0].value.length === 0) {
          return 0;
        }
        else {
          return args.element.ej2_instances[0].value.length;
        }
          //return args.element.ej2_instances[0].value.length === 0;
      };
      // sets required property in the FormValidator rules collection
      var options = {
          rules: {
              'mask': { numberValue: [customFn, 'Enter valid mobile number'] },
          },
      };
      // defines FormValidator to validate the MaskedTextBox
       this.formObject = new FormValidator('#form-element', options);
      this.formObject.addRules('mask', { maxLength: [custom, 'Enter mobile number'] });
      // places error label outside the MaskedTextBox using the customPlacement event of FormValidator
      this.formObject.customPlacement = function (element, errorElement) {
document.querySelector(".form-group").appendChild(errorElement);
};
  },
  methods: {
    onClick: function (event) {
      this.formObject.validate("mask");
      var ele = document.getElementById('mask');
      // checks for incomplete value and alerts the format submit
      if (ele.value !== "" && ele.value.indexOf(mask.ej2_instances[0].promptChar) === -1) {
            alert("Submitted");
      }
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
}

.e-mask.e-control-wrapper {
  margin-bottom: 20px;
}

label.e-error {
  margin-top: -42px;
}
</style>
```

{% endtab %}