---
title: "Create a Block Button"
component: "Button"
description: "Vue Button how to section, block button, repeat button, tooltip for Button, customization of button appearance, input and anchor elements."
---

# Create a Block Button

You can customize a Button into a Block Button that will span the entire width of its parent element. To create a Block Button,
set the [`cssClass`](../../api/button#cssclass) property to `e-block`.

{% tab template= "button/default", isDefaultActive=true %}

```html
<template>
<div>
    <ejs-button cssClass='e-block'>Block Button</ejs-button>
    <ejs-button cssClass='e-block' isPrimary=true>Block Button</ejs-button>
    <ejs-button cssClass='e-block e-success'>Block Button</ejs-button>
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

button {
  margin: 25px 0;
}
</style>
```

{% endtab %}