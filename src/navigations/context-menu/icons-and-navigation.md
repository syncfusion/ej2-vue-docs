# Icons and Navigation

## Icons

The ContextMenu item have an icon/image in it to provide visual representation of the action.
To place the icon on a menu item, set the [`iconCss`](../api/context-menu/menuItemModel#iconcss)
property to e-icons with the required icon CSS. By default, the icon is positioned to the left
side of the menu item. In the following sample, the icons for Cut, Copy and Paste menu items are
added using the `iconCss` property.

{% tab template="context-menu/default" %}

```html
<template>
<div>
<div id="target">Right click / Touch hold to open the ContextMenu</div>
<ejs-contextmenu target='#target' :items='menuItems'></ejs-contextmenu>
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
                iconCss: 'e-cm-icons e-paste',
            }]
        };
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";

#target {
  border: 1px dashed;
  height: 150px;
  padding: 10px;
  position: relative;
  text-align: justify;
  color: gray;
  user-select: none;
}

@font-face {
    font-family: 'ddb-icons';
    src:
    url(data:application/x-font-ttf;charset=utf-8;base64,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) format('truetype');
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
</style>
```

{% endtab %}

## Navigation

Navigation in ContextMenu is usage to navigate to the other web page when menu item is
clicked. This can be achieved by providing link to the menu item using the
[`url`](../api/context-menu/menuItemModel#url) property.
In the following sample, Navigation URL for Flipkart, Amazon, and Snapdeal menu items
are added using the `url` property.

{% tab template="context-menu/default" %}

```html
<template>
<div>
<div id="target">Right click / Touch hold to open the ContextMenu</div>
<ejs-contextmenu target='#target' :items='menuItems' :beforeItemRender='onBeforeItemRender'></ejs-contextmenu>
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
                text: 'Flipkart',
                iconCss: 'e-cart-icon e-link',
                url: 'https://www.google.co.in/search?q=flipkart'
            },
            {
                text: 'Amazon',
                iconCss: 'e-cart-icon e-link',
                url: 'https://www.google.co.in/search?q=amazon'
            },
            {
                text: 'Snapdeal',
                iconCss: 'e-cart-icon e-link',
                url: 'https://www.google.co.in/search?q=snapdeal'
            }]
        };
    },
    methods: {
        onBeforeItemRender: function(args) {
            args.element.getElementsByTagName('a')[0].setAttribute('target', '_blank');
        }
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";

#target {
  border: 1px dashed;
  height: 150px;
  padding: 10px;
  position: relative;
  text-align: justify;
  color: gray;
  user-select: none;
}

@font-face {
    font-family: 'cart';
    src:
    url(data:application/x-font-ttf;charset=utf-8;base64,AAEAAAAKAIAAAwAgT1MvMj0gSQ4AAAEoAAAAVmNtYXDnEOdVAAABiAAAADZnbHlmGatngwAAAcgAAADYaGVhZBKtP4wAAADQAAAANmhoZWEHmQNpAAAArAAAACRobXR4B+j//gAAAYAAAAAIbG9jYQBsAAAAAAHAAAAABm1heHABDwBQAAABCAAAACBuYW1lfiv21QAAAqAAAAIBcG9zdIZzcJAAAASkAAAAOgABAAADUv9qAFoEAP/+//wD7AABAAAAAAAAAAAAAAAAAAAAAgABAAAAAQAA2UwSaF8PPPUACwPoAAAAANfSfWUAAAAA19J9Zf/+AAAD7APdAAAACAACAAAAAAAAAAEAAAACAEQAAwAAAAAAAgAAAAoACgAAAP8AAAAAAAAAAQP0AZAABQAAAnoCvAAAAIwCegK8AAAB4AAxAQIAAAIABQMAAAAAAAAAAAAAAAAAAAAAAAAAAAAAUGZFZABA5wDnAANS/2oAWgPdAJYAAAABAAAAAAAABAAAAAPo//4AAAACAAAAAwAAABQAAwABAAAAFAAEACIAAAAEAAQAAQAA5wD//wAA5wD//wAAAAEABAAAAAEAAAAAAAAAbAAAAAP//gAAA+wD3QAJABIAQwAAJR4BMjY0JicOAQUeATI2NCYiBgEOAwclIgYXEx4BMwUyFgcOAQclIgYXBhYXBT4BPwE2PwI2NxM+AycmIyIGAeABJzonJx0gJ/6jASc6Jyc6JwMXIDgZPyX9giQkBkIIOyQBaCQgCQo/JP7RIxcBARcjAVgkQg0QDgkICgkNkw4xMBwCBScJE1UdJyc6JwEBJx0dJyc6JycDZQg0PigBAy0k/uAkMAQnHRsmAQMTDA8QAQMBLCIlIhYWFxYhAYciNg4YDBMCAAAAEgDeAAEAAAAAAAAAAQAAAAEAAAAAAAEABAABAAEAAAAAAAIABwAFAAEAAAAAAAMABAAMAAEAAAAAAAQABAAQAAEAAAAAAAUACwAUAAEAAAAAAAYABAAfAAEAAAAAAAoALAAjAAEAAAAAAAsAEgBPAAMAAQQJAAAAAgBhAAMAAQQJAAEACABjAAMAAQQJAAIADgBrAAMAAQQJAAMACAB5AAMAAQQJAAQACACBAAMAAQQJAAUAFgCJAAMAAQQJAAYACACfAAMAAQQJAAoAWACnAAMAAQQJAAsAJAD/IGNhcnRSZWd1bGFyY2FydGNhcnRWZXJzaW9uIDEuMGNhcnRGb250IGdlbmVyYXRlZCB1c2luZyBTeW5jZnVzaW9uIE1ldHJvIFN0dWRpb3d3dy5zeW5jZnVzaW9uLmNvbQAgAGMAYQByAHQAUgBlAGcAdQBsAGEAcgBjAGEAcgB0AGMAYQByAHQAVgBlAHIAcwBpAG8AbgAgADEALgAwAGMAYQByAHQARgBvAG4AdAAgAGcAZQBuAGUAcgBhAHQAZQBkACAAdQBzAGkAbgBnACAAUwB5AG4AYwBmAHUAcwBpAG8AbgAgAE0AZQB0AHIAbwAgAFMAdAB1AGQAaQBvAHcAdwB3AC4AcwB5AG4AYwBmAHUAcwBpAG8AbgAuAGMAbwBtAAAAAAIAAAAAAAAACgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAgECAQMAEHNob3BwaW5nLWNhcnQtMDUAAAAA) format('truetype');
    font-weight: normal;
    font-style: normal;
}

.e-cart-icon {
    font-family: 'cart' !important;
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

.e-link::before {
  content: '\e700';
}
</style>
```

{% endtab %}

> To open the links in new tab, set `target` attribute with the value `_blank` in the
[`beforeItemRender`](../api/context-menu#beforeitemrender) event.

## See Also

* [How to change menu items dynamically](./how-to/change-menu-items-dynamically)