---
title: "Change caret icon"
component: "DropDownButton"
description: "Vue DropDownButton how to section, hide drop down arrow, group popup items using list view component, dialog open on popup item click."
---

# Change caret icon

Dropdown arrow can be customized on popup open and close. It can be handled in [`beforeOpen`](../../api/drop-down-button#beforeopen)
and [`beforeClose`](../../api/drop-down-button#beforeclose) event.

In the following example, the up arrow is updated on popup close and down arrow is updated on popup open using `beforeOpen`
and `beforeClose` event by adding and removing `e-caret-up` class.

{% tab template="drop-down-button/default", isDefaultActive=true %}

```html
<template>
<ejs-dropdownbutton id="ddBtn" :items='items' :beforeOpen='onBeforeOpen' :beforeClose='onBeforeClose'>Clipboard</ejs-dropdownbutton>
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
    },
    methods: {
        // Removing 'e-caret-up' class.
        onBeforeClose: (args) => {
           document.getElementById('ddBtn').ej2_instances[0].cssClass = '';
        },
        // Adding 'e-caret-up' class.
        onBeforeOpen: (args) => {
            document.getElementById('ddBtn').ej2_instances[0].cssClass = 'e-caret-up';
        }
    }
}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
    .e-caret {
        transform: rotate(0deg);
        transition: transform 200ms ease-in-out;
    }

    .e-caret-up .e-caret {
        transform: rotate(180deg);
    }
</style>
```

{% endtab %}