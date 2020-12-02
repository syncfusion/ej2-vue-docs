---
title: "Sizing"
component: "TextBox"
description: "Explains how to render text box with different sizes such as small and normal, which is applicable for both touch and mouse mode."
---

# Sizing

You can render the TextBox in two different sizes.

Property   | Description
------------ | -------------
  Normal     | By default, the TextBox is rendered with normal size.
  Small      | You need to add `e-small` class to the input element, or else add to the input container.

{% tab template="textbox/icon-samples", isDefaultActive=true %}

```html
<template>
    <div class ='wrap'>
        <div id ='input-container'>
            <h4> Normal Size </h4>
            <div class="e-input-group">
                <input class="e-input" type="text" placeholder="Enter Name" />
            </div>

            <div class="e-float-input">
                <input type='text' required />
                <span class="e-float-line"></span>
                <label class="e-float-text">Enter Name</label>
            </div>

            <div class="e-input-group">
                <input class="e-input" type="text" placeholder="Enter Date" />
                <span class="e-input-group-icon e-input-popup-date"></span>
            </div>

            <h4> Small Size </h4>

            <div class="e-input-group e-small">
                <input class="e-input" type="text" placeholder="Enter Name" />
            </div>

            <div class="e-float-input e-small">
                <input type='text' required />
                <span class="e-float-line"></span>
                <label class="e-float-text">Enter Name</label>
            </div>

            <div class="e-input-group e-small">
                <input class="e-input" type="text" placeholder="Enter Date" />
                <span class="e-input-group-icon e-input-popup-date"></span>
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
  #input-container .e-float-input { /* csslint allow: adjoining-classes */
    margin: 30px 0;
  }
  .e-input-group-icon:before {
    font-family: e-icons;
  }

  .e-input-group .e-input-group-icon.e-input-popup-date { /* csslint allow: adjoining-classes */
    font-size:16px;
  }

  .e-input-group.e-small .e-input-group-icon.e-input-popup-date { /* csslint allow: adjoining-classes */
    font-size:14px;
  }

  .e-input-group-icon.e-input-popup-date:before { /* csslint allow: adjoining-classes */
    content: "";
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
