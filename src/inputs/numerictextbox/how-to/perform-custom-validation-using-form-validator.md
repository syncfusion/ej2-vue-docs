# Perform custom validation using FormValidator

This section explains how to perform custom validation on the NumericTextBox using FormValidator. The NumericTextBox will be validated when the value changes or the user clicks the submit button.
Validation can be performed by adding custom validation in the rules collection of the FormValidator.

{% tab template="numeric-textbox/how-to/validation", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
    <div class='wrap'>
      <form id="form-element" class="form-horizontal">
        <div class="form-group">
          <ejs-numerictextbox id="numericRange" name="numericRange" class="form-control" floatLabelType='Always' :min='min' :max='max' :strictMode='strictMode'  :created='onCreate' :change='onChange'></ejs-numerictextbox>
          <button type="button" id="submit_btn" style="margin-top: 40px" v-on:click="onClick">Submit</button>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";
import { FormValidator, FormValidatorModel } from '@syncfusion/ej2-inputs';

Vue.use(NumericTextBoxPlugin);
export default {
  data () {
     // checks the value of NumericTextbox and returns the corresponding boolean value
      var customFn = function(args) {
         var numeric = document.getElementById('numericRange').ej2_instances[0];
          if(numeric.value>=10 && numeric.value<=100) {
              return true;
          }
          else {
              return false;
          }
      };

      // sets required property in the FormValidator rules collection
      var options = {
          rules: {
                  'numeric': { required: [true, "Number is required"] },
          },
      }
      // defines FormValidator to validate the NumericTextBox
      var formObject = new FormValidator('#form-element', options);

      // places error label outside the NumericTextBox using the customPlacement event of FormValidator
      formObject.customPlacement = function (element, errorElement) {
          element.parentNode.parentNode.parentNode.appendChild(errorElement);
      };
      //rules for validating the NumericTextbox
      formObject.addRules('numeric', { range: [customFn, "Please enter a number between 10 to 100"] })
     return {
       min : 10,
       max : 100,
       strictMode : false
     }
  },
  methods: {
    onCreate: function (event){
        document.getElementById("numericRange").setAttribute("name", "numeric");
    },
    onClick: function (event) {
       // checks the value of NumericTextbox and returns the corresponding boolean value
      var customFn = function(args) {
         var numeric = document.getElementById('numericRange').ej2_instances[0];
          if(numeric.value>=10 && numeric.value<=100) {
              return true;
          }
          else {
              return false;
          }
      };

      // sets required property in the FormValidator rules collection
      var options = {
          rules: {
                  'numeric': { required: [true, "Number is required"] },
          },
        }
      // defines FormValidator to validate the NumericTextBox
      var formObject = new FormValidator('#form-element', options);
      // places error label outside the NumericTextBox using the customPlacement event of FormValidator
      formObject.customPlacement = function (element, errorElement) {
          element.parentNode.parentNode.parentNode.appendChild(errorElement);
      };

      //rules for validating the NumericTextbox
      formObject.addRules('numeric', { range: [customFn, "Please enter a number between 10 to 100"] });
      formObject.validate("numeric");

       var ele = document.getElementById('numericRange').ej2_instances[0];
       // checks for incomplete value and alerts the formt submit
       if (ele.value >= 10 && ele.value <= 100) {
          alert("Submitted");
       }
    },
    onChange: function (args) {
        // checks the value of NumericTextbox and returns the corresponding boolean value
      var customFn = function(args) {
         var numeric = document.getElementById('numericRange').ej2_instances[0];
          if(numeric.value>=10 && numeric.value<=100) {
              return true;
          }
          else {
              return false;
          }
      };

      // sets required property in the FormValidator rules collection
      var options = {
          rules: {
                  'numeric': { required: [true, "Number is required"] },
          },
      }
      // defines FormValidator to validate the NumericTextBox
      var formObject = new FormValidator('#form-element', options);
      // places error label outside the NumericTextBox using the customPlacement event of FormValidator
      formObject.customPlacement = function (element, errorElement) {
          element.parentNode.parentNode.parentNode.appendChild(errorElement);
      };

      //rules for validating the NumericTextbox
      formObject.addRules('numeric', { range: [customFn, "Please enter a number between 10 to 100"] });
      var  numeric = document.getElementById('numericRange');
      if (numeric.value != null) {
        formObject.validate("numeric");
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
    padding-top: 100px;
}
   label.e-error {
      margin-top: -50px;
  }
</style>
```

{% endtab %}