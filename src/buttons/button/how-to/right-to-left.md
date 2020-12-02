---
title: "Right-To-Left"
component: "Button"
description: "Vue Button how to section, block button, repeat button, tooltip for Button, customization of button appearance, input and anchor elements."
---

# Right-To-Left

Button component has RTL support. This can be achieved by setting [`enableRtl`](../../api/button#enablertl) as
`true`.

The following example illustrates how to enable right-to-left support in Button component.

{% tab template= "button/default" %}

```html
<template>
    <ejs-button iconCss='e-icons e-setting-icon' enableRtl=true>Settings</ejs-button>
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

.e-setting-icon::before {
  content: '\e434';
}

button {
  margin: 25px 5px 20px 20px;
}
</style>
```

{% endtab %}