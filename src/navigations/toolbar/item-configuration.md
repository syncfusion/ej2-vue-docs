---
title: "Toolbar Item configuration"
component: "Toolbar"
description: "Toolbar items are constructed with built-in command types or item templates such as separator, button, and input."
---

# Item Configuration

The Toolbar can be rendered by defining an array of items. Items can be constructed with the following built-in command types or item template.

## Button

`Button` is the default command `type`, and it can be rendered by using the `text` property.
Properties of the button command type:

  Property   | Description
------------ | -------------
  text       | The text to be displayed for button.
 id         | The ID of the button to be rendered. If the ID is not given, auto ID is generated.
  prefixIcon | Defines the class used to specify an icon for the button. The icon is `positioned before` the text if text is available or the icon alone button is rendered.
suffixIcon | Defines the class used to specify an icon for the button. The icon is `positioned after` the text if text is available. If both `prefixIcon` and `suffixIcon` are specified, only `prefixIcon` is considered.
  width      | Used to set the width of the button.

## Separator

The `Separator` type adds a vertical separation between the Toolbar's single/multiple commands.

{% tab template="toolbar/toolbar-items", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:100%;">
        <br>
         <ejs-toolbar >
    <e-items>
             <e-item text='Cut'></e-item>
             <e-item text='Copy'></e-item>
             <e-item text='Paste'></e-item>
             <e-item type='Separator'></e-item>
             <e-item text='Bold'></e-item>
             <e-item text='Italic'></e-item>
             <e-item text='Underline'></e-item>
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

> If `Separator` is added as the first or the last item, it will not be visible.

## See Also

* [How to set item wise custom template](./how-to/set-item-wise-custom-template/)