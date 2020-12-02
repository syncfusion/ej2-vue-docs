---
title: "Create a rounded button"
component: "Button"
description: "Vue Button how to section, block button, repeat button, tooltip for Button, customization of button appearance, input and anchor elements."
---

# Create a rounded button

Button with rounded corner can be achieved by adding `border-radius` property.

In the following example, `e-round-corner` class is added with `border-radius` as `5px`.

{% tab template= "button/default" %}

```html
<template>
<ejs-button cssClass='e-round-corner'>Button</ejs-button>
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

.e-round-corner {
  border-radius: 5px;
}

button {
  margin: 25px 5px 20px 20px;
}
</style>
```

{% endtab %}