---
title: "Initialize ButtonGroup using util function"
component: "ButtonGroup"
description: "ButtonGroup how to section, create ButtonGroup using util function, icons, form submit, show selected state on initial render."
---

# Initialize ButtonGroup using util function

Though it is a CSS component, for easy initialization of ButtonGroup `createButtonGroup` util function can be used.

To use `createButtonGroup` util function, [`SplitButton dependencies`](./../../split-button/getting-started#dependencies) should be configured and it should be added in
`system.config.js`.

Using `createButtonGroup` method, the Button options, selector, and cssClass is passed and the corresponding classes is added to the
elements.

## For basic ButtonGroup

To create basic ButtonGroup, the target element along with the button elements needs to be created and
`createButtonGroup` is to be imported from `ej2-splitbuttons` package.

## For radio type ButtonGroup

To create a radio type ButtonGroup, the target element along with the input elements should be created with type `radio`.

## For checkbox type ButtonGroup

Checkbox type ButtonGroup creation is similar to radio type ButtonGroup, instead the type of the input elements should be `checkbox`.

The following example illustrates how to create ButtonGroup using `createButtonGroup` function for basic, checkbox and radio
type behavior.

{% tab template="button-group/getting-started", isDefaultActive=true %}

```html
<template>
  <div id='app'>
      <h5>Normal behavior</h5>
      <div id='basic'>
        <button></button>
        <button></button>
        <button></button>
      </div>
      <h5>Checkbox type behavior</h5>
      <div id='checkbox'>
        <input type="checkbox" id="checkbold" name="font" value='bold' />
        <input type="checkbox" id="checkitalic" name="font" value='italic' />
        <input type="checkbox" id="checkunderline" name="font" value='underline' />
      </div>
      <h5>Radiobutton type behavior</h5>
      <div id='radio'>
        <input type="radio" id="radioleft" name="align" value='left'/>
        <input type="radio" id="radiomiddle" name="align" value='middle'/>
        <input type="radio" id="radioright" name="align" value='right'/>
      </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { createButtonGroup } from '@syncfusion/ej2-splitbuttons';
import { ButtonPlugin  } from '@syncfusion/ej2-vue-buttons';

Vue.use(ButtonPlugin);

export default {
  name: 'app',
  mounted() {
    createButtonGroup('#basic', {
      buttons: [
          { content: 'HTML' },
          { content: 'CSS' },
          { content: 'Javascript'}
      ]
  });

  createButtonGroup('#checkbox', {
      buttons: [
          { content: 'Bold' },
          { content: 'Italic' },
          { content: 'Undeline'}
      ]
  });

  createButtonGroup('#radio', {
      buttons: [
          { content: 'Left' },
          { content: 'Center' },
          { content: 'Right'}
      ]
  });
  }
}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
.e-btn-group {
  margin: 0 5px 5px 5px;
}
</style>
```

{% endtab %}