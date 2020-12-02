---
title: "Render a dialog without header"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Render a dialog without header

The dialog can be rendered without header by setting the [header](../../api/dialog/#header) property value as empty string or null. By default, dialog is rendered without header.

{% tab template="dialog/dlg-header" %}

```html
<template>
  <div>
    <div id="target" class="control-section; position:relative" style="height:350px;">
        <!-- Render Button to open the Dialog -->
        <ejs-button id='dlgbtn' v-on:click.native="btnClick">Open Dialog</ejs-button>
        <!-- Render Dialog -->
        <ejs-dialog ref="footerDialog" :target='target' :width='width' :buttons='buttons' :content='content' :close="dlgClose">
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
            target: "#target",
            width: '250px',
            content: 'This is a dialog without header.',
            buttons: [{ click: this.dlgButtonClick, buttonModel: { content: 'OK', isPrimary: true } },
            { click: this.dlgButtonClick, buttonModel: { content: 'Cancel' }}],
            animationSettings: { effect: 'None' }
        }
    },
    mounted: function(){
        document.getElementById('dlgbtn').focus();
    },
    methods: {
        btnClick: function() {
            this.$refs.footerDialog.show();
        },
        dlgClose: function() {
            document.getElementById('dlgbtn').style.display = '';
        },
        dlgButtonClick: function() {
            this.$refs.footerDialog.hide();
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
