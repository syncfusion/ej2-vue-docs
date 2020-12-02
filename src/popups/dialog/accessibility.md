---
title: "Accessibility"
component: "Dialog"
description: "Describes the accessibility standard of the modal dialog box component such as WAI-ARIA attributes, keyboard interaction, and theming."
---

# Accessibility

The Dialog characterized with complete ARIA Accessibility support which helps to accessible
by on-screen readers and other assistive technology devices. This component designed with the
reference of the guidelines document given in [WAI ARAI Accessibility Practices](https://www.w3.org/TR/wai-aria-practices-1.1/#dialog_modal).

The Dialog component uses the `Dialog` role and following ARIA properties to its element based on its state.

| **Property** | **Functionalities** |
| --- | --- |
| aria-describedby | It indicates the Dialog content description is notified to the user through assistive technologies. |
| aria-labelledby | The Dialog title is notified to the user through assistive technologies. |
| aria-modal | For modal dialog it's value is true and non-modal dialog its value is false |
| aria-grabbed | Enable the draggable Dialog and starts dragging it is value is true and stopping the drag its value is false |

## Keyboard interaction

Keyboard interaction of Dialog component has designed based on
[WAI-ARIA Practices](https://www.w3.org/TR/wai-aria-practices-1.1/#dialog_modal) described for Dialog.
User can use the following shortcut keys to interact with the Dialog.

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Keyboard shortcuts</b></td><td>
<b>Actions</b></td></tr>
<tr>
<td>
<kbd>Esc</kbd></td><td>
Closes the Dialog. This functionality can be controlled by using
<a href="https://ej2.syncfusion.com/vue/documentation/api/dialog/#closeonescape" target="_blank"> `closeOnEscape`</a> </td></tr>
<tr>
<td>
<kbd>Enter</kbd></td><td>
When the Dialog button or any input (except text area) is in focus state, when
pressing the Enter key, the click event associated with the primary button or button will
trigger. Enter key is not working when the Dialog content contains any text area with
initial focus</td></tr>
<tr>
<td>
<kbd>Ctrl + Enter</kbd></td><td>
When the Dialog content contains text area and it is in focus state, and press the Ctrl + Enter
key to call the click event
function associated with primary button</td></tr>
<tr>
<td>
<kbd>Tab</kbd></td><td>
Focus will be changed within the Dialog elements</td></tr>
<tr>
<td>
<kbd>Shift + Tab</kbd></td><td>
The Focus will be changed previous focusable element within the Dialog elements. When focusing a
first focusable element in the Dialog, then press the shift + tab key, it will change the focus
to last focusable element</td></tr>
</table>

{% tab template="dialog/accessibility", isDefaultActive=true %}

```html
<template>
  <div>
    <div id="target" class="control-section; position:relative" style="height:350px;">

        <ejs-button id='modalbtn' v-on:click.native="btnClick">Open</ejs-button>

        <ejs-dialog ref="accessDialog" :header='header' :target='target' :width='width' :height='height' :showCloseIcon='true'  :buttons='buttons' :content='content' :open="dlgOpen" :close="dlgClose">
        </ejs-dialog>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(DialogPlugin);
Vue.use(ButtonPlugin);
export default {
    data: function() {
        return {
            target: '#target',
            width: '335px',
            height: '350px',
            header: 'Feedback',
            content: "<form><div class='form-group'><label for='email'>Email:</label>" +
                "<input type='email' class='form-control' id='email'>" +
                "</div><div class='form-group'>" +
                "</div><div class='form-group'><label for='comment'>Comments:</label>" +
                "<textarea style='resize: none;' class='form-control' rows='4' id='comment'></textarea>" +
                "</div>" +
                "</form>",
            buttons: [{ click: this.dlgButtonClick, buttonModel: { content: 'OK', isPrimary: true } },
            { click: this.dlgButtonClick, buttonModel: { content: 'Cancel' }}]
        }
    },
    mounted: function(){
        document.getElementById('modalbtn').focus();
    },
    methods: {
        btnClick: function() {
            this.$refs.accessDialog.show();
        },
        dlgClose: function() {
            document.getElementById('modalbtn').style.display = '';
        },
        dlgOpen: function() {
            document.getElementById('modalbtn').style.display = 'none';
        },
        dlgButtonClick: function() {
            this.$refs.accessDialog.hide();
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
@import "https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css";
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

## See Also

* [Show dialog with full-screen](./how-to/show-dialog-with-full-screen)
