---
title: "Set item-wise custom template"
component: "Toolbar"
description: "This example demonstrates how to create custom template into the Essential JS 2 Toolbar component items."
---

# Set item-wise custom template

The Toolbar supports adding template commands using the  `template` property. Template property can be given as the `HTML element` that is
either a `string`  or a `query selector`.

## As a string

The HTML element tag can be given as a string for the template property. Here, the checkbox is rendered as a HTML template.

```hmtl
template: "<div><input type='checkbox' id='check1' checked=''>Accept</input></div>"

```

## As a selector

The template property also allows getting template content through query `selector`. Here, checkbox 'ID' attribute is specified in the template.

```typescript
template: "#Template"

```

{% tab template="toolbar/how-to/toolbar-items-templateID", isDefaultActive=true %}

```html

<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:100%;">
        <br>
         <ejs-toolbar >
    <e-items>
             <e-item text='Cut'></e-item>
             <e-item type='Separator'></e-item>
             <e-item text='Paste'></e-item>
             <e-item type='Separator'></e-item>
             <e-item :template='templateEle'></e-item>
             <e-item text='Undo'></e-item>
             <e-item text='Redo'></e-item>
             <e-item :template='templateEleId'></e-item>
          </e-items>
    </ejs-toolbar>
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
  return {
    templateEle: '<input placeholder="Search" style="height:27px;"/>';
    templateEleId: '#Template';
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