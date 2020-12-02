---
title: "Underline a character in the item text"
component: "DropDownButton"
description: "Vue DropDownButton how to section, hide drop down arrow, group popup items using list view component, dialog open on popup item click."
---

# Underline a character in the item text

Underline a particular character in a text can be handled in
[`beforeItemRender`](../../api/drop-down-button#beforeitemrender)event by adding `<u>` tag in between the text and given
as innerHTML in `li` rendering.

In the following example, `C` is underlined in the text `Copy`.

{% tab template="drop-down-button/default", isDefaultActive=true %}

```html
<template>
<ejs-dropdownbutton :items='items' :beforeItemRender='onBeforeItemRender'>Clipboard</ejs-dropdownbutton>
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
                text: 'Cut'
            },
            {
                text: 'Copy'
            },
            {
                text: 'Paste'
            }],
        };
    },
    methods: {
        onBeforeItemRender: function(args) {
            if (args.item.text === 'Copy') {
                //To underline a particular text.
                args.element.innerHTML = '<u>C</u>opy';
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
</style>
```

{% endtab %}