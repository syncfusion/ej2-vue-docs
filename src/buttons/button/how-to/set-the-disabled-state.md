---
title: "Set the disabled state"
component: "Button"
description: "Vue Button how to section, block button, repeat button, tooltip for Button, customization of button appearance, input and anchor elements."
---

# Set the disabled state

Button component can be enabled/disabled by giving [`disabled`](../../api/button#disabled) property. To disable Button component,
the `disabled` property can be set as `true`.

The following example demonstrates Button in `disabled` state.

{% tab template= "button/default" %}

```html
<template>
    <ejs-button disabled=true>Disabled</ejs-button>
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

button {
  margin: 25px 5px 20px 20px;
}
</style>
```

{% endtab %}