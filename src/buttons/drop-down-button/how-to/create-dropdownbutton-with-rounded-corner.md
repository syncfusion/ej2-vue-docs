---
title: "Create DropDownButton with rounded corner"
component: "DropDownButton"
description: "Vue DropDownButton how to section, hide drop down arrow, group popup items using list view component, dialog open on popup item click."
---

# Create DropDownButton with rounded corner

DropDownButton with rounded corner can be achieved by adding `border-radius` CSS property to button element.

In the following example, `e-round-corner` class is defined with `5px` `border-radius` property and
added that class to button element using [`cssClass`](../../api/drop-down-button#cssclass) property.

{% tab template="drop-down-button/default", isDefaultActive=true %}

```html
<template>
<ejs-dropdownbutton :items='items' cssClass='e-round-corner'>Clipboard</ejs-dropdownbutton>
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
    .e-round-corner {
        border-radius: 5px;
    }
</style>
```

{% endtab %}