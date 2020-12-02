---
title: "Validation"
component: "TextBox"
description: "Covers how to apply different validation styles to the text box (input) control such as error, warning, and success with a ripple effect."
---

# Validation

The TextBox supports three types of validation styles namely `error`, `warning`, and `success`. These states are
enabled by adding corresponding classes `.e-error`, `.e-warning`, or `.e-success` to the input parent element.

{% tab template="textbox/icon-samples", isDefaultActive=true %}

```html
<template>
    <div class ='wrap'>
        <div id ='input-container'>
            <div class="e-input-group e-warning">
                <input class="e-input" type="text" placeholder="Input with warning" />
            </div>

            <div class="e-input-group e-error">
                <input class="e-input" type="text" placeholder="Input with error" />
            </div>

            <div class="e-input-group e-success">
                <input class="e-input" type="text" placeholder="Input with success" />
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
        let input = document.querySelectorAll('.e-input-group .e-input,.e-float-input.e-input-group input');
        let inputIcon = document.querySelectorAll('.e-input-group-icon');
        let localObj = this;
        for (let i = 0; i < input.length; i++) {
        //Focus Event binding for input component
            input[i].addEventListener('focus', function() {
               localObj.getParentNode(input[i]).classList.add('e-input-focus');
            });
            //Blur Event binding for input component
            input[i].addEventListener('blur', function() {
                localObj.getParentNode(input[i]).classList.remove('e-input-focus');
            });
        }
        for (let i = 0; i < inputIcon.length; i++) {
            inputIcon[i].addEventListener('mousedown',  function() {
                this.classList.add('e-input-btn-ripple');
            });
            inputIcon[i].addEventListener('mouseup',  function() {
                let ele = this;
                setTimeout( function() {
                         ele.classList.remove('e-input-btn-ripple');
                    },
                500);
            });
        }

    },
    methods: {
        getParentNode: function(element) {
            let parentNode = element.parentNode;
            if (parentNode.classList.contains('e-input-in-wrap')) {
                return parentNode.parentNode;
            }
            return parentNode;
        }
    }
});
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