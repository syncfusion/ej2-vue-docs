---
title: "Change Size"
component: "Switch"
description: "Vue Switch how to section, customization of Switch bar and handle, change size, name and value in form submit."
---

# Change Size

The different Switch sizes available are default and small. To reduce the size of default Switch to small,
set the [`cssClass`](../../api/switch#cssclass) property to `e-small`.

{% tab template="switch/getting-started", isDefaultActive=true %}

```html
<template>
        <table class='size'>
            <tr>
                <td class='lSize'>Small</td>
                <td>
                    <ejs-switch id="switch1" checked=true cssClass="e-small"></ejs-switch>
                </td>
            </tr>
            <tr>
                <td class='lSize'>Default</td>
                <td>
                    <ejs-switch id="switch2"></ejs-switch>
                </td>
            </tr>
        </table>
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

.size tr td {
  padding: 10px;
}

.size .lSize {
  font-family: "Roboto", "Segoe UI", "GeezaPro", "DejaVu Serif", "sans-serif";
  font-size: 13px;
  cursor: pointer;
  user-select: none;
}
</style>
```

{% endtab %}