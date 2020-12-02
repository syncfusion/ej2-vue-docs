# Accessibility

## ARIA attributes

The web accessibility makes web content and web applications more accessible for people with disabilities.
It especially helps in dynamic content change and development of advanced user interface controls with AJAX,
HTML, JavaScript, and related technologies.
SplitButton provides built-in compliance with `WAI-ARIA` specifications. `WAI-ARIA` support is achieved
through the attributes like `aria-expanded`, `aria-owns` and `aria-haspopup` applied for action item in
SplitButton. It helps the people with disabilities by providing information about the widget for assistive
technology in the screen readers. SplitButton component contains the  `menuItem` role.

| Properties | Functionality |
| ------------ | ----------------------- |
| menuItem | This role will be specified for an action items. |
| aria-haspopup | Indicates the availability and type of interactive splitbutton popup element. |
| aria-expanded | Indicates whether the splitbutton popup can be expanded or collapsed, as well as indicates whether its current state is expanded or collapsed. |
| aria-owns | Identifies an elements in order to define a visual, functional, or contextual parent/child relationship between DOM elements where the DOM hierarchy cannot be used to represent the relationship. |

## Keyboard interaction

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Keyboard shortcuts</b></td><td>
<b>Actions</b></td></tr>
<tr>
<td>
<kbd>Esc</kbd></td><td>
Closes the opened popup.</td></tr>
<tr>
<td>
<kbd>Enter</kbd></td><td>
Opens the popup, or activates the highlighted item and closes the popup.</td></tr>
<tr>
<td>
<kbd>Space</kbd></td><td>
Opens the popup.</td></tr>
<tr>
<td>
<kbd>Up</kbd></td><td>
Navigates up or to the previous action item.</td></tr>
<tr>
<td>
<kbd>Down</kbd></td><td>
Navigates down or to the next action item.</td></tr>
<tr>
<td>
<kbd>Alt + Up Arrow</kbd></td><td>
Opens the popup.</td></tr>
<tr>
<td>
<kbd>Alt + Down Arrow</kbd></td><td>
Closes the popup.</td></tr>
</table>

{% tab template="context-menu/default" %}

```html
<template>
<div>
<div id="target">Right click / Touch hold to open the ContextMenu</div>
<ejs-contextmenu id="cmenu" target='#target' :items='menuItems'></ejs-contextmenu>
</div>
</template>

<script>
import Vue from 'vue';
import { ContextMenuPlugin } from "@syncfusion/ej2-vue-navigations";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ContextMenuPlugin);

export default {
    data () {
        return {
            menuItems:[
            {
                text: 'Cut',
                iconCss: 'e-cm-icons e-cut'
            },
            {
                text: 'Copy',
                iconCss: 'e-icons e-copy'
            },
            {
                text: 'Paste',
                iconCss: 'e-cm-icons e-paste'
            }]
        };
    },
    mounted(){
        document.getElementById('cmenu').ej2_instances[0].open(40, 20);
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@font-face {
  font-family: 'e-context-menu';
  src:
  url(data:application/x-font-ttf;charset=utf-8;base64,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) format('truetype');
  font-weight: normal;
  font-style: normal;
}
/* csslint ignore:stop */

.e-cm-icons {
  font-family: 'e-context-menu';
  font-style: normal;
  font-variant: normal;
  font-weight: normal;
  line-height: 1;
  text-transform: none;
}

.e-pastespecial::before {
  content: '\e260';
}

.e-pastetext::before {
  content: '\e261';
}

@font-face {
    font-family: 'ddb-icons';
    src:
    url(data:application/x-font-ttf;charset=utf-8;base64,AAEAAAAKAIAAAwAgT1MvMj0gSRkAAAEoAAAAVmNtYXDnE+dkAAABlAAAADxnbHlmlh33NQAAAdwAAAJMaGVhZBKOK9sAAADQAAAANmhoZWEHeANwAAAArAAAACRobXR4E6AAAAAAAYAAAAAUbG9jYQGOAegAAAHQAAAADG1heHABEwBlAAABCAAAACBuYW1l1LBM9QAABCgAAAI9cG9zdMJntbUAAAZoAAAAUAABAAADUv9qAFoEAAAAAAADygABAAAAAAAAAAAAAAAAAAAABQABAAAAAQAAojXaQl8PPPUACwPoAAAAANfSc4gAAAAA19JziAAA//oDygPsAAAACAACAAAAAAAAAAEAAAAFAFkABAAAAAAAAgAAAAoACgAAAP8AAAAAAAAAAQPtAZAABQAAAnoCvAAAAIwCegK8AAAB4AAxAQIAAAIABQMAAAAAAAAAAAAAAAAAAAAAAAAAAAAAUGZFZABA5wDnAwNS/2oAWgPsAJYAAAABAAAAAAAABAAAAAPoAAAD6AAAA+gAAAPoAAAAAAACAAAAAwAAABQAAwABAAAAFAAEACgAAAAEAAQAAQAA5wP//wAA5wD//wAAAAEABAAAAAEAAgADAAQAAAAAAI4AwgEAASYAAwAA//oDNQPsAA4AHQBYAAAlHgEOAScmJy4BNz4BMzIFFgYHBgcGLgE2NzYzMhYBHgEXDgEHDgEHDgIWFxYXFjY3NjQ3PgE3HgEXFhQXHgE3PgE3PgEuAScuAScuASc+ATc+AQcLASYWAVEfFxo6IBkNCQIHCy8bCQG9BwIJDRkgOhoXHwoKGi/+TR1RDyEOIxo+ExckFAQMFikwVhcMBwYlFRYkBwcMF1YwFCALDAQUIxcUPhojDiAOUR4cAQvEwwsB6gtDTycJCBsSKxYhJ0gWKxIaCQknUEILAycCf2TPI0w2HBUmDg0sOzsaKQ4ONzcniyYXNBgYNBcmiyc3OA8GHRQaOzssDQ4mFRw2TiLOZGdBA/5vAZEDQQAEAAAAAAOqA+kABQANABcAHwAAARUzFSERAyERIzUjNSEBIREhESMVITUjMyMVITUjNSMC733+iT8B9D4+/oj+igE4AXc//c4++j8BOT+7AbZ8+gF2/ksBdz4//ksB9AF2fHw+Pj8AAAIAAAAAA7cD6QACACQAAAEhEwMOAQcVITUmJyY1ND8BIRcWFxYVFAcGKwEVITUmJyYnASMCKP8AguQrOy0BGkIRHREkASstEgEEDhQxEQGaJxUcLP7PDAFNAVL+PHBHCBsbBgsUKR8wX3owBg4NFgsQGxsDFx1zAyMAAAACAAAAAAPKA+oAAgATAAABFxEBDgEHHgEXETMRMxEzETM1IQL+zP1abpADA5t0f2F+XP41AfbMAZgBJwmYcHSbA/48A2r8lgNqfgAAAAASAN4AAQAAAAAAAAABAAAAAQAAAAAAAQAJAAEAAQAAAAAAAgAHAAoAAQAAAAAAAwAJABEAAQAAAAAABAAJABoAAQAAAAAABQALACMAAQAAAAAABgAJAC4AAQAAAAAACgAsADcAAQAAAAAACwASAGMAAwABBAkAAAACAHUAAwABBAkAAQASAHcAAwABBAkAAgAOAIkAAwABBAkAAwASAJcAAwABBAkABAASAKkAAwABBAkABQAWALsAAwABBAkABgASANEAAwABBAkACgBYAOMAAwABBAkACwAkATsgZGRiLWljb25zUmVndWxhcmRkYi1pY29uc2RkYi1pY29uc1ZlcnNpb24gMS4wZGRiLWljb25zRm9udCBnZW5lcmF0ZWQgdXNpbmcgU3luY2Z1c2lvbiBNZXRybyBTdHVkaW93d3cuc3luY2Z1c2lvbi5jb20AIABkAGQAYgAtAGkAYwBvAG4AcwBSAGUAZwB1AGwAYQByAGQAZABiAC0AaQBjAG8AbgBzAGQAZABiAC0AaQBjAG8AbgBzAFYAZQByAHMAaQBvAG4AIAAxAC4AMABkAGQAYgAtAGkAYwBvAG4AcwBGAG8AbgB0ACAAZwBlAG4AZQByAGEAdABlAGQAIAB1AHMAaQBuAGcAIABTAHkAbgBjAGYAdQBzAGkAbwBuACAATQBlAHQAcgBvACAAUwB0AHUAZABpAG8AdwB3AHcALgBzAHkAbgBjAGYAdQBzAGkAbwBuAC4AYwBvAG0AAAAAAgAAAAAAAAAKAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAFAQIBAwEEAQUBBgADY3V0CHBhc3RlXzAxBGZvbnQOcGFyYS1tYXJrLS0tMDMAAA==) format('truetype');
    font-weight: normal;
    font-style: normal;
}

.e-cm-icons {
    font-family: 'ddb-icons' !important;
    speak: none;
    font-size: 55px;
    font-style: normal;
    font-weight: normal;
    font-variant: normal;
    text-transform: none;
    line-height: 1;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

.e-cut::before {
  content: '\e700';
}

.e-copy::before {
  content: '\e70a';
}

.e-paste::before {
  content: '\e701';
}

#target {
  border: 1px dashed;
  height: 150px;
  padding: 10px;
  position: relative;
  text-align: justify;
  color: gray;
  user-select: none;
}
</style>
```

{% endtab %}
