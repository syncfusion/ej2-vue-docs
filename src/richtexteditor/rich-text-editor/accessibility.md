---
title: "Rich Text Editor Accessibility"
component: "Rich Text Editor"
description: "This section for Syncfusion vue Rich Text Editor component explains the WAI-ARIA accessibility support."
---

# Accessibility

The Rich Text Editor component has been designed, keeping in mind the WAI-ARIA specifications, and applies the WAI-ARIA roles, states, and properties. This component is characterized by complete ARIA accessibility support that makes it easy for people who use assistive technologies (AT) or those who completely rely on keyboard navigation.

## ARIA attributes

The toolbar of Rich Text Editor, assigned the role of Toolbar and has the following list of ARIA attributes.

| **Roles and Attributes** | **Functionalities** |
| --- | --- |
| role="toolbar" | This attribute added to the toolbar element describes the actual role of the element. |
| aria-orientation | Indicates the toolbar orientation. Default value is horizontal. |
| aria-haspopup | Indicates the popup mode of the toolbar. The default value is false. When popup mode is enabled, attribute value has to be changed to true. |
| aria-disabled | Indicates the disabled state of the toolbar. |

For further details of toolbar ARIA attributes, refer the accessibility of [Toolbar](../../toolbar/accessibility) documentation.

The Rich Text Editor element is assigned the role of application.

| **Roles and Attributes** | **Functionalities** |
| --- | --- |
| role="application" | This attribute added to the Rich Text Editor element describes the actual role of the element. |
| aria-disabled | Indicates the disabled state of the Rich Text Editor. |

{% tab template="rich-text-editor/getting-started", isDefaultActive=true %}

```html
<template>
  <ejs-richtexteditor ref="defaultRTE" :height="350" :iframeSettings="iframeData">
    <p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
    <p><b>Key features:</b></p>
    <ul>
      <li>
        <p>Provides IFRAME and DIV modes</p>
      </li>
      <li>
        <p>Capable of handling markdown editing.</p>
      </li>
      <li>
        <p>Contains a modular library to load the necessary functionality on demand.</p>
      </li>
      <li>
        <p>Provides a fully customizable toolbar.</p>
      </li>
      <li>
        <p>Provides HTML view to edit the source directly for developers.</p>
      </li>
      <li>
        <p>Supports third-party library integration.</p>
      </li>
      <li>
        <p>Allows preview of modified content before saving it.</p>
      </li>
      <li>
        <p>Handles images, hyperlinks, video, hyperlinks, uploads, etc.</p>
      </li>
    </ul>
  </ejs-richtexteditor>
</template>

<script>
  import Vue from 'vue';
  import { RichTextEditorPlugin, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-vue-richtexteditor';

  Vue.use(RichTextEditorPlugin);

  export default {
    data() {
      return {
        iframeData: {
          enable: true
        }
      }
    },
    provide: {
      richtexteditor: [Toolbar, Link, Image, HtmlEditor, QuickToolbar]
    }
  }
</script>

<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
</style>
```

{% endtab %}

## See Also

* [Globalization](./globalization/)
* [Keyboard Support](./keyboard-support/#html-formation-key-config-list)