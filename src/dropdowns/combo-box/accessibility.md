---
title: "Combo box Accessibility"
component: "ComboBox"
description: "This section for Syncfusion vue combo box component explains the WAI-ARIA accessibility support."
---

# Accessibility

The ComboBox component has been designed, keeping in mind the `WAI-ARIA` specifications, and applies
the WAI-ARIA roles, states, and properties along with `keyboard support`. This component is characterized
by complete keyboard interaction support and ARIA accessibility support that makes it easy for people who
use assistive technologies (AT) or those who completely rely on keyboard navigation.

## ARIA attributes

The ComboBox component uses the `combobox` role, and each list item has an `option` role. The following
`ARIA attributes` denote the ComboBox state.

| **Properties** | **Functionalities** |
| --- | --- |
| aria-haspopup | Indicates whether the ComboBox input element has a popup list or not. |
| aria-expanded | Indicates whether the popup list has expanded or not. |
| aria-selected | Indicates the selected option. |
| aria-readonly | Indicates the readonly state of the ComboBox element. |
| aria-disabled | Indicates whether the ComboBox component is in a disabled state or not. |
| aria-activedescendent | This attribute holds the ID of the active list item  to focus its descendant child element. |
| aria-owns | This attribute contains the ID of the popup list to indicate popup as a child element. |
| aria-autocomplete | This attribute contains the ‘both’ to a list of options shows and the currently selected suggestion also shows inline. |

## Keyboard interaction

You can use the following key shortcuts to access the ComboBox without interruptions.

| **Keyboard shortcuts** | **Actions** |
| --- | --- |
| <kbd>Arrow Down</kbd> | Selects the first item in the ComboBox when no item selected. Otherwise, selects the item next to the currently selected item. |
| <kbd>Arrow Up</kbd> | Selects the item previous to the currently selected one. |
| <kbd>Page Down</kbd> | Scrolls down to the next page and selects the first item when popup list opens. |
| <kbd>Page Up</kbd> | Scrolls up to the previous page and selects the first item when popup list opens. |
| <kbd>Enter</kbd> | Selects the focused item and popup list closes when it is in open state. |
| <kbd>Tab</kbd> | Focuses on the next TabIndex element on the page when the popup is closed. Otherwise, closes the popup list and remains the focus of the component. |
| <kbd>Shift + tab </kbd> | Focuses on the previous TabIndex element on the page when the popup is closed. Otherwise, closes the popup list and remains the focus of the component. |
| <kbd>Alt + Down</kbd> | Open the popup list |
| <kbd>Alt + Up</kbd> | Close the popup list|
| <kbd>Esc(Escape)</kbd> | Closes the popup list when it is in an open state and the currently selected item remains the same. |
| <kbd>Home</kbd> | Cursor moves to before of first character in input |
| <kbd>End</kbd> | Cursor moves to next of last character in input  |

> In the below sample, <kbd>alt+t</kbd> keys are used to focus the ComboBox component.

{% tab template="combobox/accessibility", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div id='container' style="margin:50px auto 0; width:250px;">
        <br>
        <ejs-combobox id='combobox' ref='comboboxInstance' :dataSource='gameList' :fields='fields' popupHeight='200px' placeholder='Select a game'></ejs-combobox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(ComboBoxPlugin);

export default {
  mounted () {
    let comboboxObj = this.$refs.comboboxInstance;
      document.onkeyup = function (e) {
          if (e.altKey && e.keyCode === 84) {
          // press alt+t to focus the control.
          comboboxObj.$el.focus();
          }
      }
  },
  data () {
    return {
        gameList: [
            { Id: 'Game2', Game: 'Badminton' },
            { Id: 'Game3', Game: 'Basketball' },
            { Id: 'Game4', Game: 'Cricket' },
            { Id: 'Game5', Game: 'Football' },
            { Id: 'Game6', Game: 'Golf' },
            { Id: 'Game7', Game: 'Hockey' },
            { Id: 'Game8', Game: 'Rugby' },
            { Id: 'Game9', Game: 'Snooker' },
            { Id: 'Game10', Game: 'Tennis' }
        ],
        fields : { text: 'Game', value: 'Id' }
    }
  }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>
```

{% endtab %}
