---
title: "Prevent opening of the dialog"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Prevent opening of the dialog

You can prevent opening of the dialog by setting the [beforeOpen](../../api/dialog/#beforeopen) event argument cancel value to true.
In the following sample, the success dialog is opened when you enter the username value with minimum 4 characters. Otherwise, it will not be opened.

{% tab template="dialog/dlg-check" %}

```html
<template>
  <div>
    <div id="dialogTarget" class="control-section; position:relative" style="height:300px;">
        <div class="login-form">
                <div class='wrap'>
                    <div id="heading">Sign in</div>
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
                    <div class="button-contain">
                        <ejs-button id="dialogbtn" cssClass="e-info" v-on:click.native="dialogBtnClick" >Log in</ejs-button>
                    </div>
                </div>
            </div>
        <ejs-dialog id="dialog" ref="Dialog" :header='header' :isModal='isModal' :target='target' :width='width' :buttons='buttons' :animationSettings='animationSettings' :visible='visible' :content='content' :beforeOpen="validation" :close="modalDlgClose">
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
            width: '250px',
            visible: false,
            header: 'Success',
            isModal: true,
            content: 'Congratulations! Login Success',
            buttons: [{ click: this.dlgButtonClick, buttonModel: { content: 'Dismiss', isPrimary: true } }],
            isModal: true,
            animationSettings: { effect: 'None' }
        }
    },
    mounted: function(){
        document.getElementById('dialogbtn').focus();
    },
    methods: {
        dialogBtnClick: function() {
            this.$refs.Dialog.show();
        },
        modalDlgClose: function() {
            document.getElementById('dialogbtn').style.display = '';
        },
        dlgButtonClick: function() {
            this.$refs.Dialog.hide();
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
        padding: 20px 30px;
        width: 340px;
        background: #f7f7f7;
    }
    .wrap .e-float-input { /* csslint allow: adjoining-classes */
        margin: 17px 0;
    }

    .text-center {
        text-align: center;
    }

    #content {
        margin-top: 12px;
    }

    .button-contain {
        padding: 20px 0 0;
        width: 100%;
    }

    .button-contain .e-btn { /* csslint allow: adjoining-classes */
        width: 100%;
        height: 36px;
    }

    #heading {
        color: #333;
        font-weight: bold;
        margin: 0 0 15px;
        text-align: center;
        font-size: 20px;
    }

    .login-form {
        width: 340px;
        margin: 50px auto;
    }

    #dialog.e-dialog .e-footer-content {
        text-align: center;
    }
</style>

```

{% endtab %}
