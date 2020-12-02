---
title: "Switch Accessibility"
component: "Switch"
description: "Vue Switch component has accessibility support to help access the features via keyboard, on-screen readers, or other assistive technology devices."
---

# Accessibility

The web accessibility makes web content and web applications more accessible for people with disabilities. It
especially helps in dynamic content change and development of advanced user interface controls with AJAX, HTML,JavaScript, and related technologies.

Switch provides built-in compliance with `WAI-ARIA` specifications. `WAI-ARIA` support is achieved through the
attributes like `aria-checked` and `aria-disabled`. It helps the people with disabilities by providing information
about the widget for assistive technology in the screen readers, such as screen readers.

| Properties | Functionality |
| ------------ | ----------------------- |
| role | Indicates the switch component. |
| aria-checked | Indicates whether the input is checked, unchecked. |
| aria-disabled | Indicates that the element is perceivable but disabled, so it is not editable or otherwise operable. |

## Keyboard interaction

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Keyboard shortcuts</b></td><td>
<b>Actions</b></td></tr>
<tr>
<td>
<kbd>Space</kbd></td><td>
When the switch has focus, pressing the Space key changes the state of the switch.</td></tr>
</table>

{% tab template="switch/getting-started", isDefaultActive=true %}

```html
<template>
        <table class='size'>
            <tr>
                <td class='lSize'>Checked</td>
                <td>
                    <ejs-switch id="switch1" checked=true></ejs-switch>
                </td>
            </tr>
            <tr>
                <td class='lSize'>Unchecked</td>
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