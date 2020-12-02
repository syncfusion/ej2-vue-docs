---
title: "Checkbox Two-Way Binding"
component: "Checkbox"
description: "Vue Checkbox component supports two-way binding."
---

# Two-Way Binding

It can be achieved by using the `v-model` directive in vue. In the following sample, when you check or uncheck a value in one CheckBox will automatically check or unchecks the value in the other CheckBox. It updates the other CheckBox using `value` property.

{% tab template="radio-button/default", isDefaultActive=true %}

```html
<template>
<div>
<div id="wrapper1">
<ejs-checkbox label='Default' v-model="value" :checked="value"></ejs-checkbox>
</div>
<div id="wrapper2">
<ejs-checkbox label='Default' v-model="value" :checked="value"></ejs-checkbox>
</div>
</div>
</template>

<script>
import Vue from 'vue';
import { CheckBoxPlugin } from "@syncfusion/ej2-vue-buttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(CheckBoxPlugin);

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

.e-checkbox-wrapper {
  margin-top: 18px;
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