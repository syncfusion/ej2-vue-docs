---
title: "Toolbar Responsive"
component: "Toolbar"
description: "Toolbar has responsive support to adapt toolbar control width based on the devices like mobile and tablet."
---

# Responsive Mode

This section explains the supported display modes of the Toolbar when the content exceeds the viewing area. Possible modes are:

* Scrollable
* Popup

## Scrollable

The default overflow mode of the Toolbar is `Scrollable`. Scrollable display mode supports display of commands in a single line with
horizontal scrolling enabled when commands overflow to available space.

* The right and left navigation arrows are added to the start and end of the Toolbar to navigate to hidden commands.
* You can also see the hidden commands using touch swipe action.
* By default, if navigation icon in the `left` side is disabled, you can see the hidden commands by moving to the `right`.
* By clicking the arrow or by holding the arrow continuously,  hidden commands will become visible.
* If device navigation icons are not available, you can touch swipe to see the hidden commands of the Toolbar.

![Scrollable](images/scrolling.gif)

* Once the Toolbar reaches the last or first command, the  corresponding navigation icon will be disabled and you can move to the opposite direction.

![Touch scroll](images/scrolling_touch.gif)

![Swipe scroll](images/scrolling_swipe.gif)

* You can continuously scroll the Toolbar content by holding the navigation icon.

![Long press scroll](images/scrolling_long_press.gif)

{% tab template="toolbar/responsive-mode/toolbar-scrollable", isDefaultActive=true %}

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
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";

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

.e-tbar-btn .e-icons {
    font-family: 'Material_toolbar';
    font-size: 16px;
    font-style: normal;
    font-weight: normal;
    font-variant: normal;
    text-transform: none;
}
</style>
```

{% endtab %}

## Popup

`Popup` is another type of `overflowMode` in which the Toolbar container holds the commands that can be placed in the available space.
The rest of the overflowing commands that do not fit within
the viewing area moves to the overflow popup container.

The commands placed in the popup can be viewed by opening the popup using the drop down icon given at the end of the Toolbar.

![Toolbar popup](images/popup.gif)

> If the popup content overflows the height of the page, then the rest of the commands will be hidden.

### Priority of commands

Default popup priority is set as `none`, and when the commands of the Toolbar overflow, the ones listed last will be moved to the popup.

You can customize the priority of commands to be displayed on the Toolbar and popup by using the `overflow` property.

Property     | Description
------------ | -------------
  show       | Always shows items on the `Toolbar with primary` priority.
  hide       | Always shows items in the `popup with secondary` priority.
  none       | No priority display, and as per the `normal order` commands are moved to popup when content exceeds viewing area.

If primary priority commands also exceed available space, they are moved to the popup container at top order position and placed before the
secondary priority commands.

> You can maintain toolbar item on popup always by using the [showAlwaysInPopup](../api/toolbar/item/#showalwaysinpopup) property, and this behavior is not applicable for toolbar items with [overflow](../api/toolbar/item/#overflow) property as 'show'.

{% tab template="toolbar/responsive-mode/priority", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:100%;">
        <br>
         <ejs-toolbar >
    <e-items>
             <e-item text='Cut' prefixIcon = 'e-cut-icon' overflow ='Show'></e-item>
             <e-item text='Copy' prefixIcon = 'e-copy-icon' overflow ='Show'></e-item>
             <e-item text='Paste' prefixIcon = 'e-paste-icon' overflow ='Show'></e-item>
             <e-item type='Separator'></e-item>
             <e-item text='Undo' prefixIcon = 'e-bold-icon' ></e-item>
             <e-item text='Redo' prefixIcon = 'e-italic-icon' ></e-item>
             <e-item text='Redo' prefixIcon = 'e-underline-icon' ></e-item>
             <e-item type='Separator'></e-item>
             <e-item text='A-Z Sort' prefixIcon = 'e-ascending-icon' overflow ='Show'></e-item>
             <e-item text='Z-A Sort' prefixIcon = 'e-descending-icon' overflow ='Show'></e-item>
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
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";


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

.e-tbar-btn .e-icons {
    font-family: 'Material_toolbar';
    font-size: 16px;
    font-style: normal;
    font-weight: normal;
    font-variant: normal;
    text-transform: none;
}
</style>

```

{% endtab %}

### Text mode for buttons

The `showTextOn` property is used to decide button text display area on the Toolbar, popup, or both.
This is useful for customization of both text and image representation of commands.

For example, you can show icon only button on the Toolbar, and in the popup container display more information about the commands with icon
and text.

Possible values are,

  Property   | Description
------------ | -------------
  Both     | Button text is visible in both `Toolbar` and `Popup`.
  Overflow | Button text is only visible in `Popup`.
  Toolbar  | Button text is only visible on the `Toolbar`.

In the following code sample, text is only visible in the popup container and not in the Toolbar container.

{% tab template="toolbar/responsive-mode/textmode", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:100%;">
        <br>
         <ejs-toolbar >
    <e-items>
             <e-item text='Cut' prefixIcon = 'e-cut-icon' overflow ='Show' showTextOn = 'overflow'></e-item>
             <e-item text='Copy' prefixIcon = 'e-copy-icon' overflow ='Show' showTextOn = 'overflow'></e-item>
             <e-item text='Paste' prefixIcon = 'e-paste-icon' overflow ='Show' showTextOn = 'overflow'></e-item>
             <e-item type='Separator'></e-item>
             <e-item text='Undo' prefixIcon = 'e-bold-icon' overflow ='Show' showTextOn = 'overflow' ></e-item>
             <e-item text='Redo' prefixIcon = 'e-underline-icon' overflow ='Show' showTextOn = 'overflow' ></e-item>
             <e-item text='Redo' prefixIcon = 'e-italic-icon' overflow ='Show' showTextOn = 'overflow' ></e-item>
             <e-item text='Color-Picker' prefixIcon = 'e-color-icon' overflow ='Hide' showTextOn = 'overflow' ></e-item>
             <e-item type='Separator'></e-item>
             <e-item text='A-Z Sort' prefixIcon = 'e-ascending-icon' overflow ='Show' showTextOn = 'overflow'></e-item>
             <e-item text='Z-A Sort' prefixIcon = 'e-descending-icon' overflow ='Show' showTextOn = 'overflow'></e-item>
             <e-item text='Clear' prefixIcon = 'e-descending-icon' overflow ='Show' showTextOn = 'overflow'></e-item>
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
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";

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

.e-tbar-btn .e-icons {
    font-family: 'Material_toolbar';
    font-size: 16px;
    font-style: normal;
    font-weight: normal;
    font-variant: normal;
    text-transform: none;
}
</style>

```

{% endtab %}