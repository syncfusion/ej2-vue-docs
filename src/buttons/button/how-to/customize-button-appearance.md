---
title: "Customize Button Appearance"
component: "Button"
description: "Vue Button how to section, block button, repeat button, tooltip for Button, customization of button appearance, input and anchor elements."
---

# Customize Button Appearance

You can customize the appearance of the Button by using the Cascading Style Sheets (CSS). Define the CSS according to
your requirement, and assign the class name to the [`cssClass`](../../api/button#cssclass) property. In the following code
snippet the background color, text color, height, width, and sharp corner of the Button can be customized through
the `e-custom` class for all states (hover, focus, and active).

{% tab template= "button/default" %}

```html
<template>
    <ejs-button cssClass='e-custom'>Custom</ejs-button>
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

.e-custom {
  border-radius: 0;
  height: 30px;
  width: 80px;
}

.e-custom, .e-custom:hover, .e-custom:focus, .e-custom:active {
  background-color: #ff6e40;
  color: #fff;
}

button {
  margin: 25px 5px 20px 20px;
}
</style>
```

{% endtab %}