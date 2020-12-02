---
title: "Close the Vue Dialog while click on outside of dialog"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Close dialog while click on outside of dialog

By default, dialog can be closed by pressing Esc key and clicking the close icon on the right of dialog header. It can also be closed by clicking outside of the dialog using hide method.
Set the [CloseOnEscape](../../api/dialog/#closeonescape) property value to false to prevent closing of the dialog when pressing Esc key.

In the following sample, dialog is closed when clicking outside the dialog area using [hide](../../api/dialog/#hide) method.

{% tab template="dialog/outside-click" %}

```html
<template>
  <div>
    <div id="dialogTarget" class="control-section; position:relative" v-on:click.self="btnClick" style="height:350px;">
        <center><ejs-button ref='button' id="dialogbtn" cssClass="e-info" v-on:click.native="dialogBtnClick">Open</ejs-button></center>
        <ejs-dialog id="dialog" ref="Dialog" :header='header' :showCloseIcon='showCloseIcon' :target='target' :width='width' :buttons='buttons' :animationSettings='animationSettings' :visible='visible' :content='content' :closeOnEscape='closeOnEscape'>
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
            header: 'Delete Multiple Items',
            content: "Are you sure you want to permanently delete all of these items?",
            showCloseIcon: true,
            visible: false,
            buttons: [{ buttonModel: { isPrimary: true, content: 'Yes' }, click: this.btnClick }, { buttonModel: { content: 'No' }, click: this.btnClick }],
            target: document.body,
            height: 'auto',
            width: '300px',
            animationSettings: { effect: 'Zoom' },
            closeOnEscape: true
        }
    },
    methods: {
        dialogBtnClick: function() {
            this.$refs.Dialog.show();
        },
        btnClick: function() {
            this.$refs.Dialog.hide();
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
</style>

```

{% endtab %}