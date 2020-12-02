---
title: "Enable ripple for Switch label"
component: "Switch"
description: "Vue Switch how to section, customization of Switch bar and handle, change size, name and value in form submit."
---

# Enable ripple for Switch label

By default, label with ripple effect is not available in Switch. You can achieve this using `rippleMouseHandler`
method.

The following example illustrates how to enable ripple effect for labels in Switch component.

{% tab template="switch/getting-started", isDefaultActive=true %}

```html
<template>
    <table class='switch-control'>
        <tr>
            <td class='lSize'><label for='switch1'>USB Tethering</label></td>
            <td>
                <ejs-switch id="switch1"></ejs-switch>
            </td>
        </tr>
    </table>
</template>

<script>
import Vue from 'vue';
import { SwitchPlugin } from "@syncfusion/ej2-vue-buttons";
import { enableRipple } from '@syncfusion/ej2-base';
import { rippleMouseHandler } from '@syncfusion/ej2-buttons';

enableRipple(true);
Vue.use(SwitchPlugin);

export default {
    mounted: function(){
        var elemArray = document.querySelectorAll('.switch-control label');
        for (var i = 0, len = elemArray.length; i < len; i++) {
            elemArray[i].addEventListener('mouseup', rippleHandler);
            elemArray[i].addEventListener('mousedown', rippleHandler);
        }
        function rippleHandler(e) {
            var rippleSpan = this.parentElement.nextElementSibling.querySelector('.e-ripple-container');
            rippleSpan && rippleMouseHandler(e, rippleSpan);
        }
    }
};

</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/fabric.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/fabric.css";

.switch-control tr td {
  padding: 10px;
}

.switch-control .lSize {
  font-family: "Roboto", "Segoe UI", "GeezaPro", "DejaVu Serif", "sans-serif";
  font-size: 13px;
  cursor: pointer;
  user-select: none;
}
</style>
```

{% endtab %}