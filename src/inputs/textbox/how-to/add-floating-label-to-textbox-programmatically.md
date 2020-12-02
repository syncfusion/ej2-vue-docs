---
title: "Add Floating Label to TextBox Programmatically"
component: "Textbox"
description: "Covers customization of the text box component such as a rounded corner, disabled, read-only state, background color, and font color."
---

# Add Floating Label to TextBox Programmatically

The `Floating Label TextBox` floats label above the TextBox after focusing, or entering a value in the TextBox.

Floating label supports the types of actions as given below.

Type     | Description
------------ | -------------
  Auto       | The floating label will float above the input after focusing, or entering a value in the input.
  Always     | The floating label will always float above the input.
  Never      | By default, never float the label in the input when the placeholder is available.

* Import the `Input` modules from `ej2-inputs` library as shown below.

```html
import {Input} from '@syncfusion/ej2-inputs';
```

* Pass the `HTML Input` element and [floatLabelType](../../api/textbox/#floatlabeltype) property as `Auto` to the `createInput` method.

* Set the `placeholder` value to the input element via `element attribute` or pass the parameter to the `createInput` method.

The `watermark label` will be updated based on the specified `placeholder` value of the `Floating Label TextBox`.

* You can add the `icons` on the input by passing `buttons` property value with the
class name `e-input-group-icon` as parameter to the `createInput` method.

{% tab template="textbox/floating-label", isDefaultActive=true %}

```html
<template>
    <div class ='wrap'>
        <div id="input-container">
            <h4> FloatLabelType as Auto </h4>
        </div>
        <div id="input-container-01">
            <h4> FloatLabelType as Always </h4>
        </div>
        <div id="input-container-02">
            <h4> FloatLabelType as Never </h4>
        </div>
        <div id="input-container-03">
            <h4> Float label input with icons </h4>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { Input, InputObject } from  '@syncfusion/ej2-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

export default {
   data: function() {
        return { }
    },
    mounted: function() {
        let inputObj;

        let element = document.createElement('input');
        document.getElementById('input-container').appendChild(element);
        Input.createInput({
            element: element,
            floatLabelType: "Auto",
            properties:{
                placeholder:'Enter Name'
            }
        });

        let element2 = document.createElement('input');
        document.getElementById('input-container-01').appendChild(element2);
        Input.createInput({
            element: element2,
            floatLabelType: "Always",
            properties:{
                placeholder:'Enter Name'
            }
        });

        let element3 = document.createElement('input');
        document.getElementById('input-container-02').appendChild(element3);
        Input.createInput({
            element: element3,
            floatLabelType: "Never",
            properties:{
                placeholder:'Enter Name'
            }
        });

        // Render float label TextBox with icon

        let element4 = document.createElement('input');
        document.getElementById('input-container-03').appendChild(element4);
        Input.createInput({
            element: element4,
            floatLabelType: "Auto",
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
  #input-container .e-float-input { /* csslint allow: adjoining-classes */
    margin: 30px 0;
  }
  .e-input-group-icon:before {
    font-family: e-icons;
  }

  .e-input-group .e-input-group-icon.e-input-popup-date { /* csslint allow: adjoining-classes */
    font-size:16px;
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
