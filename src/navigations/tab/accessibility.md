---
title: "Tab Accessibility"
component: "Tab"
description: "The Tab control has accessibility support to access the features via keyboard, screen readers, or other assistive technology devices."
---

# Accessibility

## ARIA attributes

Tab component is designed by considering [WAI-ARIA](https://www.w3.org/TR/wai-aria-practices/#Tabpanel) standard. Tab is supported with ARIA
Accessibility which is accessible by on-screen readers, and other assistive technology devices.
The following list of attributes are added in the Tab.

| **Roles and Attributes** | **Functionalities** |
| --- | --- |
| `tablist` | This is set to role attribute in the Tab element that describes actual role of the element.|
| `tabpanel` | This is set to role attribute for the Tab content that describes the role for viewing the active content.|
| presentation       | This is set to role attribute for nested elements in the Tab.  |
| aria-orientation    | It indicates the Tab header orientation. Default value of this attribute is `horizontal`. |
| aria-activedescendant    | It indicates the current active child of the Tab component. |
| aria-haspopup       | It indicates the popup mode in the Tab. The default value of this attribute is false. If popup mode is enabled, the attribute value is set to true. |
| aria-disabled       | It indicates the disabled state of the Tab. |
| aria-selected       | It indicates the selection state for Tab items. Active Tab is set to true for this attribute. |
| aria-hidden      | It indicates the hidden element of the Tab. |
| aria-controls       | It indicates the associated `Tabpanel` for the header. |
| aria-labelledby       | It indicates the associated Tab header for the content. |

## Keyboard interaction

By default, keyboard navigation is enabled. This component implements keyboard navigation support by following the WAI-ARIA practices. Once
focused on the active Tab element, you can use the following key combination for interacting with the Tab.

| Key           | Description                                                                         |
|---------------|-------------------------------------------------------------------------------------|
| <kbd>Left</kbd>    | Moves focus to the previous Tab. If focus is on the first Tab, the focus will not move to any Tab. |
| <kbd>Right</kbd>   | Moves focus to the next Tab. If focus is on the last Tab element, the focus will not move to any Tab. |
| <kbd>Enter</kbd> or <kbd> Space</kbd>  | Selects the Tab if it is not selected. Opens the popup dropdown icon if it is focussed. Select the Tab item as active when popup item is focussed. |
| <kbd>Esc(Escape)</kbd>           | Closes the popup if popup is in opened state.       |
| <kbd>Down</kbd> or <kbd>Up</kbd>   | When the popup is open and focused, it will move to previous/next Tab items of the popup in the vertical direction. |
|  <kbd>Home</kbd>    | Moves focus to the first Tab. |
|  <kbd>End </kbd>   | Moves focus to the last Tab. |
|  <kbd>Shift + F10 </kbd>   | If popup mode is enabled, it opens the popup when the Tab is focused. |
|  <kbd>Delete</kbd>    | Deletes the Tab, if close button is enabled in Tab header. |

{% tab template="tab/accessibility", isDefaultActive=true %}

```html
<template>
    <div id="app">
   <ejs-tab id="element" heightAdjustMode='Auto'>
    <e-tabitems>
                    <e-tabitem :header='headerText0' :content="content0"></e-tabitem>
                    <e-tabitem :header='headerText1' :content="content1"></e-tabitem>
                    <e-tabitem :header='headerText2' :content="content2"></e-tabitem>
      </e-tabitems>
        </ejs-tab>
  </div>
</template>
<script>
import Vue from 'vue';
import { TabPlugin } from '@syncfusion/ej2-vue-navigations';

Vue.use(TabPlugin);
export default {
  name: 'app',
     data: function(){
        return {

          headerText0: { text: 'ASP.NET' },
          headerText1: { text: 'ASP.NET MVC' },
          headerText2: { text: 'JavaScript' },

        content0: 'ASP.NET is an open-source server-side web application framework designed for web development to produce ' +
        'dynamic web pages. It was developed by Microsoft to allow programmers to build dynamic web sites, web applications ' +
        'and web services. It was first released in January 2002 with version 1.0 of the .NET Framework, and is the successor ' +
        'to Microsoft\'\s Active Server Pages (ASP) technology. ASP.NET is built on the Common Language Runtime (CLR), allowing ' +
        'programmers to write ASP.NET code using any supported .NET language. The ASP.NET SOAP extension framework allows ' +
        'ASP.NET components to process SOAP messages.',

         content1: 'The ASP.NET MVC is a web application framework developed by Microsoft, which implements the ' +
        'model–view–controller (MVC) pattern. It is open-source software, apart from the ASP.NET Web Forms component which is ' +
        'proprietary. In the later versions of ASP.NET, ASP.NET MVC, ASP.NET Web API, and ASP.NET Web Pages (a platform using ' +
        'only Razor pages) will merge into a unified MVC 6.The project is called ASP.NET vNext.',

         content2: 'JavaScript (JS) is an interpreted computer programming language. It was originally implemented as ' +
        'part of web browsers so that client-side scripts could interact with the user, control the browser, communicate ' +
        'asynchronously, and alter the document content that was displayed.[5] More recently, however, it has become common in ' +
        'both game development and the creation of desktop applications.',

        }
}
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
</style>
```

{% endtab %}