---
title: "Submit name and value in form"
component: "Switch"
description: "Vue Switch how to section, customization of Switch bar and handle, change size, name and value in form submit."
---

# Submit name and value in form

The [`name`](../../api/switch#name) attribute of the Switch is used to group Switches. When the Switches are grouped in form, the checked items
[`value`](../../api/switch#value) attribute will post to the server on form submit. The disabled and unchecked Switch values will not be sent to
the server on form submit.

In the following code snippet, USB and Wi-Fi in the checked state, and Bluetooth is in disabled state.
Values that are in checked state only be sent on form submit.

{% tab template="switch/getting-started", isDefaultActive=true %}

```html
<template>
    <form>
        <table class='size'>
            <tr>
                <td class='lSize'><label>USB</label></td>
                <td>
                    <ejs-switch id="switch1" name="tethering" value="USB" checked=true></ejs-switch>
                </td>
            </tr>
            <tr>
                <td class='lSize'><label>Wi-Fi</label></td>
                <td>
                    <ejs-switch id="switch2" name="hotspot" value="wifi" checked=true></ejs-switch>
                </td>
            </tr>
            <tr>
                <td class='lSize'><label class="e-disabled">Bluetooth</label></td>
                <td>
                    <ejs-switch id="switch3" name="tethering" value="bluetooth" disabled=true></ejs-switch>
                </td>
            </tr>
            <tr>
                <td>
                    <ejs-button id="btn" isPrimary=true>Submit</ejs-button>
                </td>
            </tr>
        </table>
    </form>
</template>

<script>
import Vue from 'vue';
import { SwitchPlugin, ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(SwitchPlugin);
Vue.use(ButtonPlugin);

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