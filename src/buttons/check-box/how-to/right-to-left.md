---
title: "Right-To-Left"
component: "CheckBox"
description: "Vue CheckBox how to section, name and value in form submit, and customization of CheckBox appearance, frame & check icon."
---

# Right-To-Left

CheckBox component has RTL support. This can be achieved by setting [`enableRtl`](../../api/check-box#enablertl) as `true`.

The following example illustrates how to enable right-to-left support in CheckBox component.

{% tab template= "check-box/default" %}

```html
<template>
<ejs-checkbox label='Default' enableRtl=true></ejs-checkbox>
</template>

<script>
import Vue from 'vue';
import { CheckBoxPlugin } from '@syncfusion/ej2-vue-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(CheckBoxPlugin);

export default {}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';

.e-checkbox-wrapper {
  margin-top: 18px;
}
</style>
```

{% endtab %}