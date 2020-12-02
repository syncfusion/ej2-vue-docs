---
title: "Prevent closing of modal dialog"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Prevent closing of modal dialog

You can prevent closing of modal dialog by setting the [beforeClose](../../api/dialog/#beforeclose) event argument cancel value to true.
In the following sample, the dialog is closed when you enter the username value with minimum 4 characters. Otherwise, it will not be closed.

{% tab template="dialog/dlg-validation" %}

```html
<template>
  <div>
    <div id="dialogTarget" class="control-section; position:relative" style="height:350px;">
        <!-- Render Button to open the modal Dialog -->
        <ejs-button id='dlgbtn' v-on:click.native="dlgBtnClick">Open Dialog</ejs-button>
        <!-- Render modal Dialog -->
        <ejs-dialog ref="modalDialog"  :isModal='isModal':beforeClose="validation" :header='header' :target='target' :width='width' :buttons='buttons' :animationSettings='animationSettings' :close="modalDlgClose" >
            <div class='wrap'>
                  <div class="e-float-input">
                      <input id="textvalue" type="text" required/>
                      <span class="e-float-line"></span>
                      <label class="e-float-text">Username</label>
                  </div>
                  <div class="e-float-input">
                      <input id="textvalue2" type="password" required/>
                      <span class="e-float-line"></span>
                      <label class="e-float-text">Password</label>
                  </div>
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
            header: 'Sign in',
            buttons: [{ click: this.dlgButtonClick, buttonModel: { content: 'log in', isPrimary: true } }],
            isModal: true,
            animationSettings: { effect: 'None' }
        }
    },
    mounted: function(){
        document.getElementById('dlgbtn').focus();
    },
    methods: {
        dlgBtnClick: function() {
            this.$refs.modalDialog.show();
        },
        modalDlgClose: function() {
            document.getElementById('dlgbtn').style.display = '';
        },
        dlgButtonClick: function() {
            this.$refs.modalDialog.hide();
        },
        validation: function(args) {
            let text = document.getElementById('textvalue');
            let text1 = document.getElementById('textvalue2');
            if (text.value === "" && text1.value === "") {
                args.cancel= true;
                alert("Enter the username and password")
            } else if (text.value === "") {
                args.cancel= true;
                alert("Enter the username")
            } else if (text1.value === "") {
                args.cancel= true;
                alert("Enter the password")
            } else if (text.value.length < 4) {
                args.cancel= true;
                alert("Username must be minimum 4 characters")
            } else {
                args.cancel= false;
                document.getElementById("textvalue").value = "";
                document.getElementById("textvalue2").value = "";
            }
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
    .wrap {
    box-sizing: border-box;
    margin: 0 auto;
    width: 260px;
    }
    .e-dlg-container .e-float-input {
    margin: 17px 0;
    }
    .e-dlg-container .wrap .e-control .e-btn {
        margin: 3% 26%;
    }

    .text-center {
        text-align: center;
    }

    #content {
        margin-top: 12px;
    }

    .e-dlg-container .e-footer-content {
        padding: 20px 0 0;
        width: 100%;
    }

    .e-dlg-container .e-dialog .e-footer-content .e-btn {
        width: 100%;
        height: 36px;
        margin-left: 0px;
    }

    .e-dlg-container .e-dialog .e-footer-content {
        padding: 0 18px 18px;
    }
    .e-dlg-container .e-dialog .e-dlg-header-content .e-dlg-header {
        color: #333;
        font-weight: bold;
        text-align: center;
        width:  100%;
        font-size: 20px;
    }
</style>

```

{% endtab %}