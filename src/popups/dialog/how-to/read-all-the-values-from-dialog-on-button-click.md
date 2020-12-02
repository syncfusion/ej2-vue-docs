---
title: "Read all the values from dialog on button click"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Read all the values from dialog on button click

You can read the dialog element values by binding the action handler to the footer buttons. The buttons property provides the options to bind events to the action buttons.
For detailed information about buttons, refer to the [footer](../template/#footer) section.
In the below sample, value of input elements within the dialog has been checked in the footer button click event and send the values as the content of confirmation dialog.

{% tab template="dialog/read-all" %}

```html
<template>
  <div>
    <div id="target">
        <center> <ejs-button id="dialogbtn" v-on:click.native="btnClick">Open</ejs-button></center>
        <ejs-dialog id="dialog" ref="Dialog" :header='header' :target='target' :width='width' :buttons='buttons' :visible='visible' :content='content' :animationSettings='animateSettings'  :showCloseIcon="showCloseIcon">
        </ejs-dialog>

        <ejs-dialog id="modalDialog" ref="ModalDialog" :header='model_header' :isModal='isModal' :target='target' :buttons='mbuttons' :animationSettings='animationSettings' :visible='visible' >
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
            header: 'User details',
            content: "<form><div class='form-group'><label for='name'>Name:</label>" +
            "<input type='name' value='' class='form-control' id='name'>" +
            "</div><div class='form-group'><label for='email'>Email Id:</label>" +
            "<input type='email' value='user@syncfusion.com' class='form-control' id='email'>" +
            "</div><div class='form-group'><label for='contact'>Contact Number:</label>" +
            "<input type='contact' class='form-control' id='contact'>" +
            "</div><div class='form-group'><label for='address'>Address:</label>" +
            "<textarea class='form-control' rows='2' id='address'></textarea>" +
            "</div></form>",
            showCloseIcon: true,
            visible: false,
            buttons: [{
                buttonModel: { isPrimary: true, content: 'Submit' }, click: this.createModalDialog }
            ],
            target: document.querySelector('body'),
            width: '400px',
            animationSettings: { effect: 'Zoom' },
            animateSettings: { effect: 'Zoom' },
            model_header: 'User details',
            showCloseIcon: true,
            isModal: true,
            mbuttons: [{
                buttonModel: {isPrimary: true, content: 'Yes'}, click:  function() {
                    this.hide();
                }}, {
                buttonModel: {isPrimary: false, content: 'No'}, click: this.showDialog
                }
            ],
        }
    },
    methods: {
        btnClick: function () {
            this.$refs.Dialog.show();
        },
        createModalDialog: function() {
            this.$refs.Dialog.hide();
            this.$refs.ModalDialog.content = this.getDynamicContent();
            this.$refs.ModalDialog.show();
        },
        showDialog: function() {
            this.$refs.ModalDialog.hide();
            this.$refs.Dialog.show();
        }

        getDynamicContent: function() {
            if (!document.getElementById('dialog')) {return;}
            let input =  document.getElementById('dialog').querySelector('#name');
            let email =  document.getElementById('dialog').querySelector('#email');
            let contact =  document.getElementById('dialog').querySelector('#contact');
            let address =  document.getElementById('dialog').querySelector('#address');
            let template = "<div class='row'><div class='col-xs-6 col-sm-6 col-lg-6 col-md-6'><b>Confirm your details</b></div>" +
            "</div><div class='row'><div class='col-xs-6 col-sm-6 col-lg-6 col-md-6'><span id='name'> Name: </span>" +
            "</div><div class='col-xs-6 col-sm-6 col-lg-6 col-md-6'><span id='nameValue'>"+ input.value + "</span> </div></div>" +
            "<div class='row'><div class='col-xs-6 col-sm-6 col-lg-6 col-md-6'><span id='email'> Email: </span>" +
            "</div><div class='col-xs-6 col-sm-6 col-lg-6 col-md-6'><span id='emailValue'>" + email.value +
            "</span></div></div><div class='row'><div class='col-xs-6 col-sm-6 col-lg-6 col-md-6'>"+
            "<span id='Contact'> Contact number: </span></div><div class='col-xs-6 col-sm-6 col-lg-6 col-md-6'>"+
            "<span id='contactValue'>"+ contact.value +" </span></div></div><div class='row'><div class='col-xs-6 col-sm-6 col-lg-6 col-md-6'>"+
            "<span id='Address'> Address: </span> </div><div class='col-xs-6 col-sm-6 col-lg-6 col-md-6'><span id='AddressValue'>" + address.value +"</span></div></div>"
            return template;
        },
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
#modalDialog {
    margin: 20px;
}
html,
body {
    height: 100%;
    width: 100%;
    overflow: hidden;
}

.row {
    padding: 10px 3px;
}
</style>

```

{% endtab %}