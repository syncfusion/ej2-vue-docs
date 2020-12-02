---
title: "Show ButtonGroup selected state on initial render"
component: "ButtonGroup"
description: "ButtonGroup how to section, create ButtonGroup using util function, icons, form submit, show selected state on initial render."
---

# Show ButtonGroup selected state on initial render

To show selected state on initial render, `checked` property should to added to the corresponding
input element.

The following example illustrates how to show selected state on initial render.

{% tab template="button-group/getting-started" %}

```html

<template>
  <div id='app'>
    <div class='e-btn-group'>
        <input type="checkbox" id="checkbold" name="font" value="bold" checked/>
        <label class="e-btn" for="checkbold">Bold</label>
        <input type="checkbox" id="checkitalic" name="font" value="italic" />
        <label class="e-btn" for="checkitalic">Italic</label>
        <input type="checkbox" id="checkline" name="font" value="underline"/>
        <label class="e-btn" for="checkline">Underline</label>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';

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

  .e-btn-group {
    margin: 25px 5px 20px 20px;
  }
</style>

```

{% endtab %}