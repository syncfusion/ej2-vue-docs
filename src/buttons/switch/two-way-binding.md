---
title: "Checkbox Two-Way Binding"
component: "Checkbox"
description: "Vue Checkbox component supports two-way binding."
---

# Two-Way Binding

It can be achieved by using the `v-model` directive in vue. In the following sample, when you enable or disable a value in one Switch will automatically enable or disable the value in other Switch. It updates the other Switch using `value` property.

{% tab template="radio-button/default", isDefaultActive=true %}

```html
<template>
<div>
<div id="wrapper1">
<ejs-switch v-model="value" :checked="value"></ejs-switch>
</div>
<div id="wrapper2">
<ejs-switch v-model="value" :checked="value"></ejs-switch>
</div>
</div>
</template>

<script>
import Vue from 'vue';
import { SwitchPlugin } from "@syncfusion/ej2-vue-buttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(SwitchPlugin);

export default {
  data(){
    return{
      value: true
    }
  }
}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

.e-switch-wrapper {
  margin: 18px;
}

#wrapper1 {
  float: left;
  padding: 0 0 0 80px;
}

#wrapper2 {
  float: right;
  padding: 0 460px 0 0;
}
</style>
```

{% endtab %}