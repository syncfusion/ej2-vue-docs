---
title: "Set disabled state"
component: "Switch"
description: "Vue Switch how to section, customization of Switch bar and handle, change size, name and value in form submit."
---

# Set disabled state

Switch can be disabled by setting the [`disabled`](../../api/switch#disabled) property to true.

The following example illustrates how to disable support in Switch component.

{% tab template="switch/getting-started", isDefaultActive=true %}

```html
<template>
  <ejs-switch disabled=true ></ejs-switch>
</template>

<script>
import Vue from 'vue';
import { SwitchPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(SwitchPlugin);

export default {}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/fabric.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/fabric.css";

.e-switch-wrapper {
  margin-top: 18px;
}
</style>
```

{% endtab %}