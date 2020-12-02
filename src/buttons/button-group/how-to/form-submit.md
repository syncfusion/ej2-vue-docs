---
title: "Form submit"
component: "ButtonGroup"
description: "ButtonGroup how to section, create ButtonGroup using util function, icons, form submit, show selected state on initial render."
---

# Form submit

The name attribute of the input element  is used to group checkbox/radio type ButtonGroup. When the radio/checkbox type are grouped
in form, the checked items value attribute will be post to server on form submit that can be retrieved through the name. The disabled
radio/checkbox type value will not be sent to the server on form submit.

In the following code snippet, the radio type ButtonGroup is explained with male value as checked.
Now, the value that is in checked state will be sent on form submit.

{% tab template="button-group/getting-started" %}

```html

<template>
  <div id='app'>
    <form>
        <div class='e-btn-group'>
            <input type="radio" id="male" name="gender" value="male" checked/>
            <label class="e-btn" for="male">Male</label>
            <input type="radio" id="female" name="gender" value="female"/>
            <label class="e-btn" for="female">Female</label>
            <input type="radio" id="transgender" name="gender" value="transgender"/>
            <label class="e-btn" for="transgender">Transgender</label>
        </div>
        <ejs-button isPrimary='true'>Submit</ejs-button>
    </form>
  </div>
</template>
<script>
import Vue from 'vue';
import { ButtonPlugin  } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
Vue.use(ButtonPlugin);
export default {
  name: 'app'
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
  #app {
   margin: 20px;
  }

  .e-btn-group, button {
   margin: 20px 5px 20px 20px;
  }
</style>

```

{% endtab %}