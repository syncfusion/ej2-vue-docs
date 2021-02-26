---
title: "Prevent the focus on the first element"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Prevent the focus on the first element

By default, the dialog focuses on the first elements of the content area which can be active and focusable. You can prevent this default focusing behavior using the [open](../../api/dialog/#open) event and by enabling the `preventFocus` argument.

Bind the open event and enable the preventFocus argument within an event like the below sample.

{% tab template="dialog/dlg-focus" %}

```html

<template>
  <div>
    <div id="dialogTarget" class="control-section; position:relative" style="height:300px;">
        <!-- Render Button to open the Dialog -->
        <ejs-button id='dlgbtn' v-on:click.native="dialogBtnClick">Open Dialog</ejs-button>
        <!-- Render Dialog -->
        <ejs-dialog id="dialog" ref="Dialog" :header='header' :target='target' :width='width' :buttons='buttons' :visible='visible' :open="onOpen">
           <div class='form-group'><label for='email'>Email:</label>
                <input type='email' class='form-control' id='email'>
            </div>
            <div class='form-group'>
                <label for='comment'>Password:</label>
                <input type='password' class='form-control' id='password'>
            </div>
        </ejs-dialog>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
Vue.use(DialogPlugin);
Vue.use(ButtonPlugin);

export default {
    data: function() {
        return {
            target: "#dialogTarget",
            width: '300px',
            header: 'Sign In',
            buttons: [{ click: this.dlgButtonClick, buttonModel: { content: 'Ok', isPrimary: true } }, { click: this.dlgButtonClick, buttonModel: { content: 'Cancel'} }]
        }
    },
    methods: {
        dialogBtnClick: function() {
            this.$refs.Dialog.show();
        },
        dlgButtonClick: function() {
            this.$refs.Dialog.hide();
        },
        onOpen: function(args) {
            args.preventFocus = true;
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";

    #app {
        color: #008cff;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }
    .control-section {
        height: 100%;
        min-height: 200px;
    }
</style>

```

{% endtab %}