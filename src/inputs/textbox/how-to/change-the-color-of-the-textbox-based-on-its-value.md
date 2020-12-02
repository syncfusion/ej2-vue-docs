---
title: "Change the color of the TextBox based on its value"
component: "Textbox"
description: "Covers customization of the text box component such as a rounded corner, disabled, read-only state, background color, and font color."
---

# Change the color of the TextBox based on its value

You can change the color of the TextBox by validating its value using regular expression in the `keyup` event for predicting the numeric values as demonstrated in the following code sample.

{% tab template="textbox/text-color", isDefaultActive=true %}

```html
<template>
    <div class ='wrap'>
        <div id ='input-container'>
            <label>Normal Input</label>
            <div class="e-input-group">
                <input class="e-input" type="text" placeholder="Enter numeric values" @keyup="onKeyup" />
            </div>
                <label> Floating Input </label>
            <div class="e-float-input">
                <input type="text" @keyup="onKeyup" required />
                <span class="e-float-line"> </span>
                <label class="e-float-text">Enter numeric values</label>
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
        // To Configure RegExp for predicting Numeric values on keyUp event function

        onKeyup(e) {
            let str = e.target.value.match(/^[0-9]+$/);
            if (!((str && str.length > 0)) && e.target.value.length) {
            e.target.parentElement.classList.add('e-error');
            } else {
            e.target.parentElement.classList.remove('e-error');
            }
        }
    }
    mounted: function() {
        // To get the all input fields and its container.

        let inputElement = document.querySelectorAll('.e-input-group .e-input,.e-float-input.e-input-group input');

        // Add 'e-input-focus' class to the input for achive ripple effect when focus on the input field.

        for (let i = 0; i < inputElement.length; i++) {
            inputElement[i].addEventListener("focus", function () {
                let parentElement = this.parentNode;
                if (parentElement.classList.contains('e-input-in-wrap')) {
                    parentElement.parentNode.classList.add('e-input-focus');
                } else {
                    this.parentNode.classList.add('e-input-focus');
                }
            });
            inputElement[i].addEventListener("blur", function () {
                let parentElement = this.parentNode;
                if (parentElement.classList.contains('e-input-in-wrap')) {
                    parentElement.parentNode.classList.remove('e-input-focus');
                } else {
                    this.parentNode.classList.remove('e-input-focus');
                }
            });
        }
    });
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";

  .wrap {
    box-sizing: border-box;
    margin: 0 auto;
    padding: 20px 10px;
    width: 340px;
  }

  #input-container .e-input-group { /* csslint allow: adjoining-classes */
    margin: 30px 0;
  }
  #input-container .e-float-input { /* csslint allow: adjoining-classes */
    margin: 30px 0;
  }
  .e-input-group.e-error .e-input { /* csslint allow: adjoining-classes */
    color: #f44336;
  }

  .e-float-input.e-error input { /* csslint allow: adjoining-classes */
    color: #f44336;
  }

  .wrap label { /* csslint allow: adjoining-classes */
    font-weight:bold;
  }

</style>

```

{% endtab %}
