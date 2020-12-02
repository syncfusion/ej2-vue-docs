---
title: "Enable RTL"
component: "Switch"
description: "Vue Switch how to section, customization of Switch bar and handle, change size, name and value in form submit."
---

# Enable RTL

Switch component has RTL support. This can be achieved by setting [`enableRtl`](../../api/switch#enablertl) as `true`.

The following example illustrates how to enable right-to-left support in Switch component.

{% tab template="switch/getting-started", isDefaultActive=true %}

```html
<template>
  <ejs-switch enableRtl=true></ejs-switch>
</template>

<script>
import Vue from 'vue';
import { SwitchPlugin } from "@syncfusion/ej2-vue-buttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(SwitchPlugin);

export default {}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/fabric.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/fabric.css";

.e-switch-wrapper {
  margin: 18px;
}
</style>
```

{% endtab %}