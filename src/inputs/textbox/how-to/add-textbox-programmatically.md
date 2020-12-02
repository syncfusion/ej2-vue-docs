---
title: "Add TextBox Programmatically"
component: "Textbox"
description: "Covers customization of the text box component such as a rounded corner, disabled, read-only state, background color, and font color."
---

# Add TextBox Programmatically

* Create a TypeScript file and import the `Input` modules
from `ej2-inputs` library as shown below.

```typescript
import {Input} from '@syncfusion/ej2-inputs';
```

* Pass the `HTML Input` element as parameter to the `createInput` method.

* You can also add the `icons` on the input by passing `buttons` property value with the class
name `e-input-group-icon` as parameter to the `createInput` method.

{% tab template="textbox/utility-rendering", isDefaultActive=true %}

```html
<template>
    <div class ='wrap'>
        <div id ='input-container'>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { Input, InputObject } from  '@syncfusion/ej2-inputs';

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
                this.parentNode.classList.add('e-input-focus')
            });
            inputElement[i].addEventListener("blur", function () {
                this.parentNode.classList.remove('e-input-focus')
            });
        }

        // Add 'e-input-btn-ripple' class to the icon element for achive ripple effect when click on the icon.

        var inputIcon = document.querySelectorAll('.e-input-group-icon');
        for (let i = 0; i < inputIcon.length; i++) {
            inputIcon[i].addEventListener('mousedown', function () {
                this.classList.add('e-input-btn-ripple');
            });
            inputIcon[i].addEventListener('mouseup', function () {
                var element = this;
                setTimeout(function () {
                    element.classList.remove('e-input-btn-ripple');
                }, 500);
            });
        }

        let inputObj;

        let element = document.createElement('input');
        document.getElementById('input-container').appendChild(element);
        Input.createInput({
            element: element,
            properties:{
                placeholder:'Enter Name'
            }
        });

        let element1 = document.createElement('input');
        document.getElementById('input-container').appendChild(element1);
        Input.createInput({
            element: element1,
            buttons: ['e-input-group-icon e-input-down'],
            properties:{
                placeholder:'Enter Value'
            }
        });
    }
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
  .e-input-group .e-input-group-icon.e-input-popup-date { /* csslint allow: adjoining-classes */
    font-size:16px;
  }

  .e-input-group-icon:before {
    font-family: e-icons;
  }

  .e-input-group-icon.e-input-up:before { /* csslint allow: adjoining-classes */
    content: '\e85e';
  }

  .e-input-group-icon.e-input-down:before { /* csslint allow: adjoining-classes */
    content: "";
  }

  .e-input-group-icon.e-input-plus:before { /* csslint allow: adjoining-classes */
    content: '\e7ba';
  }

  .e-input-group-icon.e-input-minus:before { /* csslint allow: adjoining-classes */
    content: '\e814';
  }

  .e-input-group-icon.e-input-popup-date:before { /* csslint allow: adjoining-classes */
    content: "";
  }

  .e-input-group-icon.e-input-date:before { /* csslint allow: adjoining-classes */
    content: "";
  }

  .e-input-group-icon.e-input-left:before { /* csslint allow: adjoining-classes */
    content: '\e904';
  }

  .e-input-group-icon.e-input-right:before { /* csslint allow: adjoining-classes */
    content: '\e913';
  }

  .e-input-group-icon.e-input-reload:before { /* csslint allow: adjoining-classes */
    content: '\e837';
  }

  .e-input-group-icon.e-input-search:before { /* csslint allow: adjoining-classes */
    content: '\e806';
  }

</style>

```

{% endtab %}
