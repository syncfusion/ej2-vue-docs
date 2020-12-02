---
title: "DropDownButton Popup Items"
component: "DropDownButton"
description: "Vue DropDownButton allows the end user to customize the whole popup or action items in popup using templates, navigate to other pages on action item click."
---

# Popup items

## Icons

The popup action item have an icon or image to provide visual representation of the action. To place the icon on a popup item,
set the [`iconCss`](../api/drop-down-button#iconcss) property to `e-icons` with the required icon CSS. By default, the icon is
positioned to the left side of the popup action item.

In the following sample, the icons for edit, delete, mark as read  and like message menu items are
added using the iconCss property.

{% tab template="drop-down-button/default", isDefaultActive=true %}

```html
<template>
<ejs-dropdownbutton :items='items' iconCss= 'ddb-icons e-message'>Message</ejs-dropdownbutton>
</template>

<script>
import Vue from 'vue';
import { DropDownButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(DropDownButtonPlugin);

export default {
    data () {
        return {
            items:[
            {
                text: 'Edit',
                iconCss: 'ddb-icons e-edit'
            },
            {
                text: 'Delete',
                iconCss: 'ddb-icons e-delete'
            },
            {
                text: 'Mark As Read',
                iconCss: 'ddb-icons e-read'
            },
            {
                text: 'Like Message',
                iconCss: 'ddb-icons e-like'
            }]
        };
    }
}
</script>

<style>
    @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
    @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
    @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
    @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';

    @font-face {
        font-family: 'ddb-icons';
        src:
        url(data:application/x-font-ttf;charset=utf-8;base64,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) format('truetype');
        font-weight: normal;
        font-style: normal;
    }
    .ddb-icons {
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

    .e-message::before {
    content: '\e702';
    }

    .e-edit::before {
    content: '\e700';
    }

    .e-delete::before {
    content: '\e701';
    }

    .e-read::before {
    content: '\e703';
    }

    .e-like::before {
    content: '\e704';
    }

</style>
```

{% endtab %}

## Navigations

Actions in DropDownButton can be used to navigate to the other web
page when action item is clicked. This can be achieved by
providing link to the action item using `url` property.

In the following sample, navigation URL for Flipkart, Amazon, and
Snapdeal action items are added using the `url` property:

{% tab template="drop-down-button/default", isDefaultActive=true %}

```html
<template>
<ejs-dropdownbutton :items='items' iconCss= 'e-cart-icon e-shopping' :beforeItemRender='onBeforeItemRender'>Shop By</ejs-dropdownbutton>
</template>

<script>
import Vue from 'vue';
import { DropDownButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(DropDownButtonPlugin);

export default {
    data () {
        return {
            items:[
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
    @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
    @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
    @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
    @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';

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

    .e-shopping::before {
        content: '\e700';
    }

    .e-link::before {
        content: '\e700';
    }
</style>
```

{% endtab %}

## Template

### Item templating

Popup items can be customized using the [`beforeItemRender`](../api/drop-down-button#beforeitemrender) event. The item render event
triggers while rendering each popup action item. The event argument will be used to identify the action item and
customize based on the requirement.

The following popup template is customized using `beforeItemRender` event by appending `span` and `div` element on each `li` rendering:

{% tab template="drop-down-button/default", isDefaultActive=true %}

```html
<template>
<ejs-dropdownbutton :items='items' iconCss= 'e-ddb-icons e-paste' cssClass= 'e-vertical' iconPosition= 'Top' :beforeItemRender='onBeforeItemRender'>Paste</ejs-dropdownbutton>
</template>

<script>
import Vue from 'vue';
import { DropDownButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(DropDownButtonPlugin);

export default {
    data () {
        return {
            items:[
            {
                text: 'Edit'
            },
            {
                text: 'Cut'
            }]
        };
    },
    methods: {
        onBeforeItemRender: function(args) {
            if (args.item.text === 'Edit') {
                args.element.innerHTML = '<span></span><div><b>Paste Text</b><div>Provides option to paste only the<br>selected text.</div></div>';
                args.element.style.height = '80px';
                var span = args.element.children[0];
                span.setAttribute('class','e-cm-icons e-pastetext e-align');
                var div = args.element.children[1];
                div.setAttribute('class', 'e-div-align');
                } else {
                args.element.innerHTML = '<span></span><div><b>Paste Special</b><div>Provides options to paste formulas,<br> values, comments, validations etc...</div></div>';
                args.element.style.height = '80px';
                var span = args.element.children[0];
                span.setAttribute('class','e-cm-icons e-pastespecial e-align');
                var div = args.element.children[1];
                div.setAttribute('class', 'e-div-align');
            }
        }
    }
}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
    /* csslint ignore:start */
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

    @font-face {
        font-family: 'ddb-icons';
        src:
        url(data:application/x-font-ttf;charset=utf-8;base64,AAEAAAAKAIAAAwAgT1MvMj0gSRkAAAEoAAAAVmNtYXDnE+dkAAABlAAAADxnbHlmlh33NQAAAdwAAAJMaGVhZBKOK9sAAADQAAAANmhoZWEHeANwAAAArAAAACRobXR4E6AAAAAAAYAAAAAUbG9jYQGOAegAAAHQAAAADG1heHABEwBlAAABCAAAACBuYW1l1LBM9QAABCgAAAI9cG9zdMJntbUAAAZoAAAAUAABAAADUv9qAFoEAAAAAAADygABAAAAAAAAAAAAAAAAAAAABQABAAAAAQAAojXaQl8PPPUACwPoAAAAANfSc4gAAAAA19JziAAA//oDygPsAAAACAACAAAAAAAAAAEAAAAFAFkABAAAAAAAAgAAAAoACgAAAP8AAAAAAAAAAQPtAZAABQAAAnoCvAAAAIwCegK8AAAB4AAxAQIAAAIABQMAAAAAAAAAAAAAAAAAAAAAAAAAAAAAUGZFZABA5wDnAwNS/2oAWgPsAJYAAAABAAAAAAAABAAAAAPoAAAD6AAAA+gAAAPoAAAAAAACAAAAAwAAABQAAwABAAAAFAAEACgAAAAEAAQAAQAA5wP//wAA5wD//wAAAAEABAAAAAEAAgADAAQAAAAAAI4AwgEAASYAAwAA//oDNQPsAA4AHQBYAAAlHgEOAScmJy4BNz4BMzIFFgYHBgcGLgE2NzYzMhYBHgEXDgEHDgEHDgIWFxYXFjY3NjQ3PgE3HgEXFhQXHgE3PgE3PgEuAScuAScuASc+ATc+AQcLASYWAVEfFxo6IBkNCQIHCy8bCQG9BwIJDRkgOhoXHwoKGi/+TR1RDyEOIxo+ExckFAQMFikwVhcMBwYlFRYkBwcMF1YwFCALDAQUIxcUPhojDiAOUR4cAQvEwwsB6gtDTycJCBsSKxYhJ0gWKxIaCQknUEILAycCf2TPI0w2HBUmDg0sOzsaKQ4ONzcniyYXNBgYNBcmiyc3OA8GHRQaOzssDQ4mFRw2TiLOZGdBA/5vAZEDQQAEAAAAAAOqA+kABQANABcAHwAAARUzFSERAyERIzUjNSEBIREhESMVITUjMyMVITUjNSMC733+iT8B9D4+/oj+igE4AXc//c4++j8BOT+7AbZ8+gF2/ksBdz4//ksB9AF2fHw+Pj8AAAIAAAAAA7cD6QACACQAAAEhEwMOAQcVITUmJyY1ND8BIRcWFxYVFAcGKwEVITUmJyYnASMCKP8AguQrOy0BGkIRHREkASstEgEEDhQxEQGaJxUcLP7PDAFNAVL+PHBHCBsbBgsUKR8wX3owBg4NFgsQGxsDFx1zAyMAAAACAAAAAAPKA+oAAgATAAABFxEBDgEHHgEXETMRMxEzETM1IQL+zP1abpADA5t0f2F+XP41AfbMAZgBJwmYcHSbA/48A2r8lgNqfgAAAAASAN4AAQAAAAAAAAABAAAAAQAAAAAAAQAJAAEAAQAAAAAAAgAHAAoAAQAAAAAAAwAJABEAAQAAAAAABAAJABoAAQAAAAAABQALACMAAQAAAAAABgAJAC4AAQAAAAAACgAsADcAAQAAAAAACwASAGMAAwABBAkAAAACAHUAAwABBAkAAQASAHcAAwABBAkAAgAOAIkAAwABBAkAAwASAJcAAwABBAkABAASAKkAAwABBAkABQAWALsAAwABBAkABgASANEAAwABBAkACgBYAOMAAwABBAkACwAkATsgZGRiLWljb25zUmVndWxhcmRkYi1pY29uc2RkYi1pY29uc1ZlcnNpb24gMS4wZGRiLWljb25zRm9udCBnZW5lcmF0ZWQgdXNpbmcgU3luY2Z1c2lvbiBNZXRybyBTdHVkaW93d3cuc3luY2Z1c2lvbi5jb20AIABkAGQAYgAtAGkAYwBvAG4AcwBSAGUAZwB1AGwAYQByAGQAZABiAC0AaQBjAG8AbgBzAGQAZABiAC0AaQBjAG8AbgBzAFYAZQByAHMAaQBvAG4AIAAxAC4AMABkAGQAYgAtAGkAYwBvAG4AcwBGAG8AbgB0ACAAZwBlAG4AZQByAGEAdABlAGQAIAB1AHMAaQBuAGcAIABTAHkAbgBjAGYAdQBzAGkAbwBuACAATQBlAHQAcgBvACAAUwB0AHUAZABpAG8AdwB3AHcALgBzAHkAbgBjAGYAdQBzAGkAbwBuAC4AYwBvAG0AAAAAAgAAAAAAAAAKAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAFAQIBAwEEAQUBBgADY3V0CHBhc3RlXzAxBGZvbnQOcGFyYS1tYXJrLS0tMDMAAA==) format('truetype');
        font-weight: normal;
        font-style: normal;
    }

    .e-ddb-icons {
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
    .e-pastespecial::before {
    content: '\e260';
    }

    .e-pastetext::before {
    content: '\e261';
    }

    .e-paste::before {
    content: '\e701';
    }

    .e-dropdown-popup ul {
    max-width: 400px;
    white-space: nowrap;
    }

    .e-align {
    float: left;
    width: 15%;
    margin-top: 15px;
    font-size: 45px;
    color: grey;
    }

    .e-div-align {
    float: right;
    width: 75%;
    line-height: 23px;
    margin: 0 15px 0 0;
    }
</style>
```

{% endtab %}

### Popup templating

The whole popup can be customized as per the requirement and it can be customized by handling
it in [`target`](../api/drop-down-button#target) property.

In the following sample, the whole popup item is customized as table template by giving `div` as target and it can be achieved
using `target` property.

{% tab template="drop-down-button/default", isDefaultActive=true %}

```html
<template>
    <div>
        <div id="target" style='border: 1px solid grey;'>
        <table>
        <caption style='height: 18px; background-color: #e0e0e0;'><b>Insert Table</b></caption>
        <tr class='e-row'><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td></tr>
        <tr class='e-row'><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td></tr>
        <tr class='e-row'><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td></tr>
        <tr class='e-row'><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td></tr>
        <tr class='e-row'><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td></tr>
        <tr class='e-row'><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td><td class='e-cell'></td></tr>
        </table>
        </div>
        <ejs-dropdownbutton target= '#target' iconCss= 'e-icons e-table' cssClass= 'e-vertical' iconPosition= 'Top'>Table</ejs-dropdownbutton>
    </div>
</template>

<script>
import Vue from 'vue';
import { DropDownButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(DropDownButtonPlugin);

export default {}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
    .e-cell {
    border: 1px solid grey;
    padding: 8px;
    }

    .e-table::before {
    content: '\e705';
    }

    .e-row {
    padding-left: 3px;
    padding-right: 3px;
    }
</style>
```

{% endtab %}

## Separator

The Separators are the horizontal lines that are used to separate the popup items. You `cannot` select the separators.
You can enable separators to group the popup items using the `separator` property.

In the following sample, cut, copy, and paste popup items are grouped using the separator property:

{% tab template="drop-down-button/default", isDefaultActive=true %}

```html
<template>
<ejs-dropdownbutton :items='items'>Clipboard</ejs-dropdownbutton>
</template>

<script>
import Vue from 'vue';
import { DropDownButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(DropDownButtonPlugin);

export default {
    data () {
        return {
            items:[
            {
                text: 'Cut',
                iconCss: 'e-db-icons e-cut'
            },
            {
                text: 'Copy',
                iconCss: 'e-icons e-copy'
            },
            {
                text: 'Paste',
                iconCss: 'e-db-icons e-paste'
            },
            {
                separator: true
            },
            {
                text: 'Font',
                iconCss: 'e-db-icons e-font'
            },
            {
                text: 'Paragraph',
                iconCss: 'e-db-icons e-paragraph'
            }]
        };
    }
}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
  @font-face {
    font-family: 'ddb-icons';
    src:
    url(data:application/x-font-ttf;charset=utf-8;base64,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) format('truetype');
    font-weight: normal;
    font-style: normal;
    }

    .e-db-icons {
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
    .e-edit::before {
    content: '\ea9a';
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

    .e-font::before {
    content: '\e702';
    }

    .e-paragraph::before {
    content: '\e703';
    }
</style>
```

{% endtab %}

## See Also

* [Integration with ListView component](./how-to/group-popup-items-with-listview-component)