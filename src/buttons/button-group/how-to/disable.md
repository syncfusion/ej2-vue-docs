---
title: "Disable"
component: "ButtonGroup"
description: "ButtonGroup how to section, create ButtonGroup using util function, icons, form submit, show selected state on initial render."
---

# Disable

## Particular button

To disable a particular button in a ButtonGroup, [`disabled`](../../api/button#disabled) attribute needs to be added to corresponding button element.

## Whole ButtonGroup

To disable whole ButtonGroup, [`disabled`](../../api/button#disabled) attribute needs to be added to all the button elements.

The following example illustrates how to disable the particular and the whole ButtonGroup.

{% tab template="button-group/getting-started", isDefaultActive=true %}

```html

<template>
  <div id='app'>
    <div class='e-btn-group'>
        <ejs-button >HTML</ejs-button>
        <ejs-button disabled='true'>CSS</ejs-button>
        <ejs-button >Javascript</ejs-button>
    </div>
    <div class='e-btn-group'>
        <ejs-button disabled='true'>HTML</ejs-button>
        <ejs-button disabled='true'>CSS</ejs-button>
        <ejs-button disabled='true'>Javascript</ejs-button>
    </div>
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
  .e-btn-group {
    margin: 25px 5px 20px 20px;
  }
</style>

```

{% endtab %}

> To disable radio/checkbox type ButtonGroup, the `disabled` attribute should be added to the input element.