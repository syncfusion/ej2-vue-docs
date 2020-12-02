---
title: "Show Vue Dialog with full screen"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Show dialog with full screen

You can show the dialog in fullscreen by passing `true` as argument to the dialog [show](../../api/dialog/#show) method.

{% tab template="dialog/dlg-fullscreen" %}

```html
<template>
  <div>
    <div id="target" class="control-section; position:relative" style="height:360px;">
        <!-- Render Button to open the Dialog -->
        <ejs-button id='dlgbtn' v-on:click.native="btnClick">Open Dialog</ejs-button>
        <!-- Render Dialog -->
        <ejs-dialog ref="footerDialog" :header='header' :target='target' :width='width' :buttons='buttons' :visible='visible' :showCloseIcon='showCloseIcon' :content='content' :close="dlgClose">
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
            header: 'Dialog',
            visible: false,
            showCloseIcon: true,
            content: 'This is a Dialog with fullscreen display.',
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
            this.$refs.footerDialog.show(true);
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
        max-height: 380px;
        overflow: hidden;
    }

</style>

```

{% endtab %}