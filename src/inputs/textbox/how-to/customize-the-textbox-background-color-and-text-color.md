---
title: "Customize the textbox background-color and text-color"
component: "Textbox"
description: "Covers customization of the text box component such as a rounded corner, disabled, read-only state, background color, and font color."
---

# Customize the textbox background-color and text-color

You can customize the textbox styles such as background-color, text-color and border-color by overriding its default styles.

> To change the styles of the `floating label`, you must override the style to the input element.

{% tab template="textbox/textbox-customize", isDefaultActive=true %}

```html
<template>
    <div class ='wrap'>
        <div id ='input-container'>
            <label>Normal Input</label>
            <div class="e-input-group">
                <input class="e-input" type="text" placeholder="First Name" />
            </div>
                <label> Floating Input </label>
            <div class="e-float-input">
                <input type="text" required />
                <span class="e-float-line"> </span>
                <label class="e-float-text">Last Name</label>
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
                this.parentNode.classList.add('e-input-focus');
            });
            inputElement[i].addEventListener("blur", function () {
                this.parentNode.classList.remove('e-input-focus');
            });
        }
    });
});
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";

.wrap {
  box-sizing: border-box;
  margin: 0 auto;
  padding: 20px 10px;
  width: 260px;
}

.wrap label { /* csslint allow: adjoining-classes */
 font-weight:bold;
}

.wrap .e-float-input {/* csslint allow: adjoining-classes */
   margin:30px 0;
}

.wrap .e-input-group {/* csslint allow: adjoining-classes */
   margin:25px 0;
}

/* To change the background-color and text-color for textbox */
.e-input-group,
.e-float-input,
.e-float-input.e-input-group { /* csslint allow: adjoining-classes */
  background : yellow;
  color: green;
}

/* To change the border-color of the textbox */
.e-input-group:not(.e-success):not(.e-warning):not(.e-error):not(.e-float-icon-left),
.e-input-group:hover:not(.e-success):not(.e-warning):not(.e-error):not(.e-float-icon-left) { /* csslint allow: adjoining-classes */
  border-color: #0800ff;
}

/* To change the border-color of the floating-label textbox */
.e-float-input input,
.e-float-input:hover:not(.e-input-group):not(.e-success):not(.e-warning):not(.e-error):not(.e-disabled) input:not([disabled]) { /* csslint allow: adjoining-classes */
    border-color: #0800ff;
}
</style>
```

{% endtab %}
