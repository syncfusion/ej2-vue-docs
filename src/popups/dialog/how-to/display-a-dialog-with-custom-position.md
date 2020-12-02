---
title: "Display a dialog with custom position"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Display a dialog with custom position

By default, the dialog is displayed in the center of the target container. The dialog position can be set using the [position](../../api/dialog/#position) property by providing custom X and Y coordinates.
The dialog can be positioned inside the target based on the given X and Y values.

{% tab template="dialog/dlg-position" %}

```html
<template>
  <div>
     <div id="target" class="control-section">
        <ejs-dialog id='firstDialog' header='Position-01' :position='position' width='360px' ref='dialogObj'
            target='#target' :content='content' :closeOnEscape='false'>
        </ejs-dialog>
        <ejs-dialog ref="secondDialog" header='Position-02' :height='height1' :target='target' width='360px'  :position='position1' :content='content1'>
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
            height: '120px',
            content: 'The dialog is positioned at {X: 160, Y: 14} coordinates.',
            position: { X: 420, Y: 14 },
            height1: '120px',
            content1: 'The dialog is positioned at {X: 160, Y: 240} coordinates',
            position1: { X: 420, Y: 240 }
        }
    },
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
    #defaultDialog table,
    #defaultDialog th,
    #defaultDialog td {
        border: 1px solid #D8D8D8;
        border-collapse: collapse;
    }

    #container {
        height: 365px;
    }

    #defaultDialog.e-dialog .e-footer-content {
        padding: 0px 1px 4px ! important;
    }

    .tableStyle {
        margin: 17px;
        width: 304px;
    }

    .e-dialog .e-dlgcontent{
        padding: 10px 16px 10px;
    }

    .e-radio +label .e-label {
        line-height:18px;
    }

    td {
        padding: 6px;
    }
</style>

```

{% endtab %}