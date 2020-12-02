---
title: "Toggle between the states"
component: "Switch"
description: "Vue Switch how to section, customization of Switch bar and handle, change size, name and value in form submit, toggle between the states."
---

# Change switch state using toggle method

This section explains about how to toggle between the switch states using [`toggle`](../../api/switch/#toggle) method.

{% tab template="switch/getting-started", isDefaultActive=true %}

```html
<template>
  <ejs-switch ref="toggleSwitch" checked=true :created="created"></ejs-switch>
</template>

<script>
import Vue from 'vue';
import { SwitchPlugin } from "@syncfusion/ej2-vue-buttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(SwitchPlugin);

export default {
  methods: {
    created: function(args) {
      this.$refs.toggleSwitch.toggle();
    }
  }
};
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

> Switch triggers [`change`](../../api/switch/#change) event on every state stage to perform custom operations.