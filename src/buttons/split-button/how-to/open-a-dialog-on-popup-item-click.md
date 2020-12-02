---
title: "Open a dialog on popup item click"
component: "SplitButton"
description: "Vue SplitButton how to section, group popup items using list view component, dialog open on popup item click."
---

# Open a dialog on popup item click

This section explains about how to open a dialog on SplitButton popup item click. This can be achieved by
handling dialog open in [`select`](../../api/split-button#select) event of the SplitButton.

Install Syncfusion `Popup` packages using below command.

```bash
npm install @syncfusion/ej2-vue-popups --save
```

In the following example, Dialog will open while selecting `Update...` item:

{% tab template="split-button/default" %}

```html
<template>
<div>
    <ejs-splitbutton :items='items' :select='onSelect'>Help</ejs-splitbutton>
    <ejs-dialog id="dialog" content="Are you sure want to update?" header='Software Update' :buttons='buttons' width='250px' :visible='false' ></ejs-dialog>
</div>
</template>

<script>
import Vue from 'vue';
import { SplitButtonPlugin } from "@syncfusion/ej2-vue-splitbuttons";
import { DialogPlugin } from "@syncfusion/ej2-vue-popups";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(SplitButtonPlugin);
Vue.use(DialogPlugin);

export default {
    data () {
        return {
            items:[
            {
                text: 'Help'
            },
            {
                text: 'About'
            },
            {
                text: 'Update...'
            }],
            buttons: [{
                buttonModel: {
                    isPrimary: true,
                    content: 'Ok',
                },
                click: function () {
                    this.hide();
                }
            },
            {
                buttonModel: {
                    isPrimary: true,
                    content: 'Cancel',
                },
                click: function () {
                    this.hide();
                }
            }]
        };
    },
    methods: {
        onSelect: function(args) {
            if (args.item.text === 'Update...') {
                document.getElementById("dialog").ej2_instances[0].show();
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
  .e-split-btn-wrapper{
   margin: 20px 20px 5px 5px;
  }
</style>
```

{% endtab %}