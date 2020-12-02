# Create mnemonic UI in menu item

A particular character in a text can be underlined in the [`beforeItemRender`](../../api/menu#beforeitemrender) event by
adding `<u>` tag in between the text and assign the innerHTML to the `li` element.

In the following example, the first character in `File`, `Open`, and `Save` menu items are underlined.

{% tab template="menu/getting-started" %}

```html
<template>
    <div>
        <ejs-menu ref="menu" id="menu" :items='menuItems' :beforeItemRender='beforeItemRender'></ejs-menu>
    </div>
</template>

<script>
import Vue from 'vue';
import { MenuPlugin } from "@syncfusion/ej2-vue-navigations";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(MenuPlugin);


export default {
   data: function() {
        return {
           menuItems:   [
        {
            text: 'File',
            iconCss: 'em-icons e-file',
            items: [
                { text: 'Open', iconCss: 'em-icons e-open' },
                { text: 'Save', iconCss: 'e-icons e-save' },
                { separator: true },
                { text: 'Exit' }
            ]
        },
        {
            text: 'Edit',
            iconCss: 'em-icons e-edit',
            items: [
                { text: 'Cut', iconCss: 'em-icons e-cut' },
                { text: 'Copy', iconCss: 'em-icons e-copy' },
                { text: 'Paste', iconCss: 'em-icons e-paste' }
            ]
        },
        { text: 'Format' },
        { text: 'View' },
        { text: 'Bookmarks' },
        { text: 'Tools' },
        { separator: true },
        { text: 'Help' }
    ]
     };
   },
   methods: {
       beforeItemRender: function(args) {
         if (['File', 'Open', 'Save'].indexOf(args.item.text) > -1) {
            // To underline a First character.
            var underlinedText = '<u>' + args.item.text.slice(0, 1) + '</u>' + args.item.text.slice(1);
            args.element.innerHTML = args.element.innerHTML.replace(args.item.text, underlinedText);
          }
       }
   }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";

body {
    margin-top: 100px;
    text-align: center;
}

/**
* ej2 Menu styles
*/
@font-face {
    font-family: 'e-menu';
    src:
    url(data:application/x-font-ttf;charset=utf-8;base64,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) format('truetype');
    font-weight: normal;
    font-style: normal;
}

.em-icons {
    font-family: 'e-menu';
    font-style: normal;
    font-variant: normal;
    font-weight: normal;
    line-height: 1;
    text-transform: none;
}

.e-file::before {
    content: '\e886';
}

.e-edit::before {
    content: '\e822';
}

.e-cut::before {
    content: '\e5a9';
}

.e-copy::before {
    content: '\e5b3';
}

.e-paste::before {
    content: '\e5b2';
}

.e-open::before {
    content: '\e885';
}

.e-save::before {
    content: '\e98e';
}
</style>
```

{% endtab %}
