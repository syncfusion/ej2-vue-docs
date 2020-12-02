---
title: "Toolbar Accessibility"
component: "Toolbar"
description: "The Toolbar control has accessibility support to access the features via keyboard, screen readers, or other assistive technology devices."
---

# Accessibility

The Toolbar component has been designed,  keeping in mind the [WAI-ARIA](http://www.w3.org/WAI/PF/aria-practices/) specifications, and
applying the WAI-ARIA roles, states, and properties along with keyboard support for people who use assistive devices. WAI-ARIA accessibility
 support is achieved through attributes like `aria-orientation`, `aria-disabled`, and `aria-haspopup`. It provides
  information about elements in a document for assistive technology.  The component implements keyboard navigation support by following the
  [WAI-ARIA practices](https://www.w3.org/TR/wai-aria-practices/),
   and has been tested in major screen readers.

## ARIA attributes

The Toolbar element is assigned the role of `toolbar`.

| **Property** | **Functionalities** |
| --- | --- |
| role="toolbar" | This attribute added to the ToolBar element describes the actual role of the element. |
| aria-orientation     | Indicates the ToolBar orientation. Default value is `horizontal`. |
| aria-haspopup       | Indicates the popup mode of the Toolbar. Default value is false. When popup mode is enabled,  attribute value has to be changed to `true`. | |
| aria-disabled       | Indicates the disabled state of the ToolBar. |

## Keyboard interaction

Keyboard navigation is enabled, by default. Possible keys are:

| Key           | Description                                                                         |
|---------------|-------------------------------------------------------------------------------------|
| <kbd>Left</kbd>    | Focuses the previous element.                                               |
| <kbd>Right</kbd>   | Focuses the next element.                                                            |
| <kbd>Enter</kbd>         | When focused on a ToolBar command, clicking the key triggers the click of Toolbar element. When popup drop-down icon is focused, the popup opens. |
| <kbd>Esc(Escape)</kbd>           | Closes popup.                                                                     |
| <kbd>Down</kbd>   | Focuses the next popup element.                                                  |
| <kbd>Up</kbd>      | Focuses the previous popup element.                                                |

{% tab template="toolbar/accessibility", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:100%;">
        <br>
         <ejs-toolbar >
    <e-items>
             <e-item text='Cut' prefixIcon = 'e-cut-icon'></e-item>
             <e-item text='Copy' prefixIcon = 'e-copy-icon'></e-item>
             <e-item text='Paste' prefixIcon = 'e-paste-icon'></e-item>
             <e-item type='Separator'></e-item>
             <e-item text='Undo' prefixIcon = 'e-bold-icon'></e-item>
             <e-item text='Redo' prefixIcon = 'e-underline-icon'></e-item>
             <e-item text='Redo' prefixIcon = 'e-italic-icon'></e-item>
             <e-item type='Separator'></e-item>
             <e-item text='A-Z Sort' prefixIcon = 'e-ascending-icon'></e-item>
             <e-item text='Z-A Sort' prefixIcon = 'e-descending-icon'></e-item>
             <e-item text='Clear' prefixIcon = 'e-clear-icon'></e-item>
          </e-items>
    </ejs-toolbar>
    <link href="https://ej2.syncfusion.com/angular/demos/src/toolbar/toolbar.component.css" rel="stylesheet" />
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ToolbarPlugin } from "@syncfusion/ej2-vue-navigations";
Vue.use(ToolbarPlugin);

export default {
  name: 'app',
 data () {
    document.onkeyup = function (e) {
    if (e.altKey && e.keyCode === 84) {
        document.getElementById('Toolbar').focus();
    }
    };
 }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";

.e-tbar-btn .e-icons {
    font-family: 'Material_toolbar';
    font-size: 16px;
    font-style: normal;
    font-weight: normal;
    font-variant: normal;
    text-transform: none;
}

  .custom_bold .e-tbar-btn-text {
    font-weight: 900;
}

.custom_italic .e-tbar-btn-text {
    font-style: italic;
}

.custom_underline .e-tbar-btn-text {
    text-decoration: underline red;
}

.e-txt-casing .e-tbar-btn-text {
    font-variant: small-caps;
}
</style>
```

{% endtab %}
