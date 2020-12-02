---
title: "Customize input and anchor elements"
component: "Button"
description: "Vue Button how to section, block button, repeat button, tooltip for Button, customization of button appearance, input and anchor elements."
---

# Customize input and anchor elements

You can customize the appearance of the input and anchor elements using predefined styles through the class property. In the following code
snippet, the input element is customized as a link Button by setting the `e-btn e-link` class, and the anchor element is customized as a
primary Button by setting the `e-btn e-primary` class.

{% tab template= "button/default" %}

```html
<template>
<div>
    <div>
        <input type='button' value='Input Button' class='e-btn e-link' />
    </div>
    <br>
    <div>
        <a id='anchorbtn' class='e-btn e-primary' href='#'>Google</a>
    </div>
</div>
</template>

<script>
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ButtonPlugin);

export default {}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
</style>
```

{% endtab %}