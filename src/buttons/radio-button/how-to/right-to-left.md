---
title: "Right-To-Left"
component: "RadioButton"
description: "Vue RadioButton how to section, name and value in form submit, customize RadioButton appearance."
---

# Right-To-Left

RadioButton component has RTL support. This can be achieved by setting [`enableRtl`](../../api/radio-button#enablertl) as `true`.

The following example illustrates how to enable right-to-left support in RadioButton component.

{% tab template="radio-button/default" %}

```html
<template>
<ul>
<li><ejs-radiobutton label='Option 1' name='default' enableRtl="true"></ejs-radiobutton></li>
<li><ejs-radiobutton label='Option 2' name='default' enableRtl="true" checked=true></ejs-radiobutton></li>
</ul>
</template>

<script>
import Vue from 'vue';
import { RadioButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(RadioButtonPlugin);

export default {}
</script>

<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";

.e-radio-wrapper {
  margin-top: 18px;
}

li {
  list-style: none;
}
</style>
```

{% endtab %}