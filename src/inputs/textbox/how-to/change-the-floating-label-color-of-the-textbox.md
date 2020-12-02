---
title: "Change the floating label color of the TextBox"
component: "Textbox"
description: "Covers customization of the text box component such as a rounded corner, disabled, read-only state, background color, and font color."
---

# Change the floating label color of the TextBox

You can change the floating label color of the TextBox for both `success` and `warning` validation states by applying the following CSS styles.

```CSS

    /* For Success state */
    .e-float-input.e-success label.e-float-text,
    .e-float-input.e-success input:focus ~ label.e-float-text,
    .e-float-input.e-success input:valid ~ label.e-float-text {
      color: #22b24b;
    }

    /* For Warning state */
    .e-float-input.e-warning label.e-float-text,
    .e-float-input.e-warning input:focus ~ label.e-float-text,
   .e-float-input.e-warning input:valid ~ label.e-float-text {
      color: #ffca1c;
    }

```

{% tab template="textbox/validation-state", isDefaultActive=true %}

```html
<template>
    <div class ='wrap'>
        <div id ='input-container'>
            <div class="e-input-group e-float-input e-success">
                <input type="text" required>
                <span class="e-float-line"></span>
                <label class="e-float-text">Success</label>
            </div>
            <div class="e-input-group e-float-input e-warning">
                <input type="text" required>
                <span class="e-float-line"></span>
                <label class="e-float-text">Warning</label>
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

        // Add 'e-input-btn-ripple' class to the icon element for achive ripple effect when click on the icon.

        var inputIcon = document.querySelectorAll('.e-input-group-icon');
        for (let i = 0; i < inputIcon.length; i++) {
            inputIcon[i].addEventListener('mousedown', function () {
                this.classList.add('e-input-btn-ripple');
            });
            inputIcon[i].addEventListener('mouseup', function () {
                let element = this;
                setTimeout(function () {
                    element.classList.remove('e-input-btn-ripple');
                }, 500);
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
  .e-float-input.e-success label.e-float-text{ /* csslint allow: adjoining-classes */
    color: #22b24b;
  }
  .e-float-input.e-success input:focus ~ label.e-float-text{ /* csslint allow: adjoining-classes */
    color: #22b24b;
  }
  .e-float-input.e-success input:valid ~ label.e-float-text { /* csslint allow: adjoining-classes */
    color: #22b24b;
  }

  .e-float-input.e-warning label.e-float-text{ /* csslint allow: adjoining-classes */
    color: #ffca1c;
  }
  .e-float-input.e-warning input:focus ~ label.e-float-text{ /* csslint allow: adjoining-classes */
    color: #ffca1c;
  }
  .e-float-input.e-warning input:valid ~ label.e-float-text { /* csslint allow: adjoining-classes */
    color: #ffca1c;
  }

</style>

```

{% endtab %}