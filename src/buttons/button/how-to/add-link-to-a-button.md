---
title: "Add link to a Button"
component: "Button"
description: "Angular Button how to section, block button, repeat button, tooltip for Button, customization of button appearance, input and anchor elements."
---

# Add link to a Button

The appearance of the Button can be changed like a link by `e-link` class using [`cssClass`](../../api/button#cssclass)
property and link navigation can be handled in Button click.

In the following example, link is added in Button click by using `window.open()` method.

{% tab template="button/default" %}

```html
<template>
<ejs-button cssClass='e-link' v-on:click.native='btnClick'>Button</ejs-button>
</template>

<script>
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ButtonPlugin);

export default {
    methods : {
        btnClick: function(event) {
            window.open("https://www.google.com");
        }
    }
}
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