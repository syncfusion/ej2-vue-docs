---
title: "ListBox Accessibility"
component: "ListBox"
description: "Vue ListBox component has accessibility support to help access the features via keyboard, on-screen readers, or other assistive technology devices."
---
# Accessibility

## ARIA Attributes

The web accessibility makes web content and web applications more accessible for people with disabilities. It especially helps in dynamic content change and development of advanced user interface controls with AJAX, HTML, JavaScript, and related technologies. ListBox provides built-in compliance with WAI-ARIA specifications. WAI-ARIA support is achieved through the attributes like `aria-multiselectable` and `aria-selected` applied for ListBox element and selected elements in the ListBox. It helps the people with disabilities by providing information about the widget for assistive technology in the screen readers. ListBox component contains the `listbox` role and `option` role.

| Properties | Functionality |
| ------------ | ----------------------- |
| listbox | This role will be specified for root element. |
| aria-multiselectable | Applied to the element with the ListBox role, tells assistive technologies that the list supports multiple selection. The default value is true. |
| option | Identifies each selectable element containing the name of an option. |
| aria-selected | Applied to elements with role option that are visually styled as selected to inform assistive technologies that the options are selected. |

## Keyboard interaction

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Keyboard shortcuts</b></td><td>
<b>Actions</b></td></tr>
<tr>
<td>
<kbd>Up arrow</kbd></td><td>
Moves focus to the previous option.</td></tr>
<tr>
<td>
<kbd>Down arrow</kbd></td><td>
Moves focus to the next option.</td></tr>
<tr>
<td>
<kbd>Home</kbd></td><td>
Moves focus to first option.</td></tr>
<tr>
<td>
<kbd>End</kbd></td><td>
Moves focus to last option.</td></tr>
<tr>
<td>
<kbd>Space</kbd></td><td>
Changes the selection state of the focused option.</td></tr>
<tr>
<td>
<kbd>Ctrl + A</kbd></td><td>
Selects all options in the list.</td></tr>
<tr>
<td>
<kbd>Ctrl + Shift + Home</kbd></td><td>
Selects the focused option and all options up to the first option.</td></tr>
<tr>
<td>
<kbd>Ctrl + Shift + End</kbd></td><td>
Selects the focused option and all options down to the last option.</td></tr>
<tr>
<td>
<kbd>Ctrl + (Up or Down)</kbd></td><td>
Press Ctrl key with up / down arrow or mouse to select multiple items.</td></tr>
</table>

{% tab template="list-box/getting-started/getting-started", isDefaultActive=true %}

```html

<template>
  <div id="app">
    <div id='container' style="margin:10px auto 0; width:250px;">
        <ejs-listbox :dataSource='data' ></ejs-listbox>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(ListBoxPlugin);
export default {
  data (){
    return {
       data: [
    { text: 'Hennessey Venom', id: 'list-01' },
    { text: 'Bugatti Chiron', id: 'list-02' },
    { text: 'Bugatti Veyron Super Sport', id: 'list-03' },
    { text: 'SSC Ultimate Aero', id: 'list-04' },
    { text: 'Koenigsegg CCR', id: 'list-05' },
    { text: 'McLaren F1', id: 'list-06' },
    { text: 'Aston Martin One- 77', id: 'list-07' },
    { text: 'Jaguar XJ220', id: 'list-08' },
    { text: 'McLaren P1', id: 'list-09' },
    { text: 'Ferrari LaFerrari', id: 'list-10' },
];
    }
  }
}

</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
</style>

```

{% endtab %}