---
title: "Add floating label to read-only textbox"
component: "Textbox"
description: "Covers customization of the text box component such as a rounded corner, disabled, read-only state, background color, and font color."
---

# Add floating label to read-only TextBox

You can achieve floating label for read-only textboxes by adding/removing `e-label-top` and `e-label-bottom` classes to the label element

In this sample, click the update value button to fill the read-only textbox with value and float a label.

{% tab template="textbox/read-only", isDefaultActive=true %}

```html
<template>
    <div class ='wrap'>
        <div class="row">
          <div class="e-float-input">
            <input class="e-input myField" id="myText" name="readonlyAttr"  type="text" readOnly>
            <span class="e-float-line"></span>
            <label class="e-float-text">Enter value</label>
          </div>
          <div class="row">
            <button class="e-btn update_value" id='valuebtn' v-on:click="valuebtnClick">Set value</button>
            <button class="e-btn remove_value" id='removebtn' v-on:click="removebtnClick">Remove value</button>
          </div>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';

export default {
   data: function() {
        return { }
    },
    methods: {
        valuebtnClick: function(args){
            (document.getElementsByClassName('myField')[0]).value = '10';
            this.checkFloatingLabel('myText')
        },
        removebtnClick: function(args){
            (document.getElementsByClassName('myField')[0]).value = '';
            this.checkFloatingLabel('myText')
        },
        checkFloatingLabel: function(id) {
        var inputElement=  document.getElementById(id);
        var labelElement = inputElement.parentElement.querySelector('.e-float-text');
        if (inputElement.value !== '') {
            labelElement.classList.remove('e-label-bottom');
            labelElement.classList.add('e-label-top');
        } else {
            labelElement.classList.remove('e-label-top');
            labelElement.classList.add('e-label-bottom');
        }
        var inputField = document.getElementById('myText');
        }
    },
    mounted: function() {
        // To get the all input fields and its container.

        let inputElement = document.querySelectorAll('.e-input-group .e-input,.e-float-input.e-input-group input');

        // Add 'e-input-focus' class to the input for achive ripple effect when focus on the input field.

        for (let i = 0; i < inputElement.length; i++) {
            inputElement[i].addEventListener("focus", function () {
                this.parentNode.classList.add('e-input-focus');
            });
            inputElement[i].addEventListener("blur", function () {
                this.parentNode.classList.remove('e-input-focus');
            });
        }
    }
};
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
.wrap {
  box-sizing: border-box;
  margin: 0 auto;
  padding: 20px 10px;
  width: 260px;
}

.update_value, .remove_value {
    margin-top: 20px;
}

.remove_value {
    margin-left: 10px;
}
</style>

```

{% endtab %}
