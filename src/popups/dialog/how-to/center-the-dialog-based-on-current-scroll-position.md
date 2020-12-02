---
title: "Center the dialog based on current scroll position"
component: "Dialog"
description: "This section explains how to center the dialog based on the current scroll position."
---

# Center the dialog based on the current scroll position

The dialog is always centered based on the target container. If the target is not specified, then the dialog will be rendered based on its body and centered in the position of the current viewpoint.

In the following sample, the model dialog is centered based on its current scroll position of the page.

{% tab template="dialog/center-the-dialog" %}

```html
<template>
  <div>
    <div id="modalTarget" class="control-section; position:relative" style="height:350px;">
        <!-- Render Button to open the modal Dialog -->
        <ejs-button id='modalbtn' v-on:click.native="modalBtnClick">Open</ejs-button>
        <!-- Render modal Dialog -->
        <ejs-dialog ref="modalDialog"  :isModal='isModal' :header='header' :target='target' :width='width' :animationSettings='animationSettings' :content='content' :open="modalDlgOpen" :close="modalDlgClose" :overlayClick="overlayClick">
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
            target: document.body,
            width: '335px',
            header: 'Software Update',
            content: 'Your current software version is up to date.',
            isModal: true,
            animationSettings: { effect: 'None' }
        }
    },
    mounted: function(){
        document.getElementById('modalbtn').focus();
    },
    methods: {
        modalBtnClick: function() {
            this.$refs.modalDialog.show();
        },
        modalDlgClose: function() {
            document.getElementById('modalbtn').style.display = '';
        },
        modalDlgOpen: function() {
            document.getElementById('modalbtn').style.display = 'none';
        },
        overlayClick: function() {
            this.$refs.modalDialog.hide();
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
    body{
      height: 1200px;
    }
</style>

```

{% endtab %}