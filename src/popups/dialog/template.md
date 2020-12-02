---
title: "Vue Dialog template"
component: "Dialog"
description: "Explains how to customize the dialog's user interface (UI) elements such as header, footer, and content using a template."
---

# Template

In Dialog the template support is provided to the header, content and footer sections. So any text or HTML content can be appending in these sections.

## Header

The Dialog header content can be provided through the [header](../api/dialog/#header) property, and it will allow both text and any HTML content as a string. Also in header, close button is provided as built-in support, and this can be enabled through the [showCloseIcon](../api/dialog/#showcloseicon) property.

## Footer

The Dialog footer can be enabled by adding built-in [buttons](../api/dialog/#buttons) or providing any HTML string through the [footerTemplate](../api/dialog/#footertemplate).

> The [buttons](../api/dialog/#buttons) and [footerTemplate](../api/dialog/#footertemplate) properties can't be used at the same time.

The below example demonstrates the usage of header and footer template in the Dialog

{% tab template="dialog/template", isDefaultActive=true %}

```html
<template>
  <div>
    <div id="target" class="control-section; position:relative" style="height:350px;">
        <!-- Render Button to open the Dialog -->
        <ejs-button id='modalBtn' v-on:click.native="btnClick">Open Dialog</ejs-button>
        <!-- Render Dialog -->
        <ejs-dialog id='dialog' ref="templateDialog" :header='headerTemplate' :target='target' :height='height' :width='width' :footerTemplate='footerTemplate' :showCloseIcon='true' :animationSettings='animationSettings' :content='contentTemplate' :open="dlgOpen" :close="dlgClose">
        </ejs-dialog>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { isNullOrUndefined } from '@syncfusion/ej2-base';

Vue.use(DialogPlugin);
Vue.use(ButtonPlugin);

var footerTemplateVue = Vue.component("demo", {
    template: '<span> <input id="inVal" class="e-input" type="text" placeholder="Enter your message here!"/><button id="sendButton" class="e-control e-btn e-primary sendButton" data-ripple="true">Send</button> </span>',
    data() {
        return {
            data: {}
        };
    }
});

var headerTemplateVue = Vue.component("demo1", {
    template: '<span><img class="img2" src="https://ej2.syncfusion.com/products/typescript/dialog/template/images/1.png" style="display: inline-block;" alt="header image"> <div title="Nancy" class="e-icon-settings dlg-template"> Nancy </div></span>',
    data() {
        return {
            data: {}
        };
    }
});

var contentTemplateVue = Vue.component("demo2", {
    template: '<div><div class="dialogContent"> <span class="dialogText">Greetings Nancy! When will you share me the source files of the project?</span></div></div>',
    data() {
        return {
            data: {}
        };
    }
});

export default {
    data: function() {
        return {
            target: '#target',
            height: '75%',
            width: '435px',
            footerTemplate: function (){
                return { template: footerTemplateVue }
            },
            headerTemplate: function (){
                return { template: headerTemplateVue }
            },
            contentTemplate: function (){
                return { template: contentTemplateVue }
            },
            animationSettings: { effect: 'None' }
        }
    },
    mounted: function(){
        document.getElementById('modalBtn').focus();
    },
    methods: {
        btnClick: function() {
            this.$refs.templateDialog.show();
        },
        dlgClose: function() {
            document.getElementById('modalBtn').style.display = 'block';
        },
        dlgOpen: function() {
            document.getElementById('sendButton').keypress = (e) => {
                if (e.keyCode === 13) { this.updateTextValue(); }
            };
            document.getElementById('inVal').onkeydown = (e) => {
                if (e.keyCode === 13) { this.updateTextValue(); }
            };
            document.getElementById('sendButton').onclick = () => {
                this.updateTextValue();
            };
            document.getElementById('modalBtn').style.display = 'none';
        },
        updateTextValue: function() {
            var enteredVal = document.getElementById('inVal');
            var dialogTextElement = document.getElementsByClassName('dialogText')[0];
            var dialogTextWrap = document.getElementsByClassName('dialogContent')[0];
            if (!isNullOrUndefined(document.getElementsByClassName('contentText')[0])) {
                detach(document.getElementsByClassName('contentText')[0]);
            }
            if (enteredVal.value !== '') {
                dialogTextElement.innerHTML = enteredVal.value;
            }
            enteredVal.value = '';
        }
        dlgButtonClick: function() {
            this.$refs.templateDialog.hide();
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
    html,
    body,
    #dialog-container {
        display: block;
        height: 100%;
        overflow: hidden;
        width: 100%;
    }

    #container {
        visibility: hidden;
    }
    .e-dialog .e-dlg-header-content {
        background-color: #007DD1;
    }
    #target {
    min-height:350px;
    }

    .e-dialog .e-dlg-header-content .e-btn.e-dlg-closeicon-btn {
        top: 3px;
        left: -11px;
    }

    .e-dialog .e-dlg-header {
        position: relative;
        padding: 0;
    }

    .e-dialog .e-dlg-header-content {
        padding: 6px;
    }
    #dialog.e-dialog .e-dlg-header-content{
        padding: 13px;
    }
    .target-element .e-open-icon::before {
        content: '\e782';
    }
    .e-dialog .e-dlg-header img.img2 {
        height: 36px;
        width: 36px;
        border-radius: 50%;
        vertical-align: middle;
        display: inline-block;
    }
    .e-dialog .e-dlg-header .dlg-template {
        display: inline-block;
        padding: 0px 10px;
        vertical-align: middle;
        height: 30px;
        line-height: 30px;
        color: #fff;
    }
    .e-dialog .e-footer-content input.e-input {
        width: 75%;
        float: left;
    }

    .e-icon-settings.e-icons {
        float: left;
        position: relative;
        left: 14%;
        top: -33px;
    }

    #dialog.e-dialog .e-footer-content {
        padding: 15px;
    }
    .dialogContent .dialogText {
        font-size: 13px;
        padding: 5%;
        word-wrap: break-word;
        border-radius: 6px;
        text-align: justify;
        font-style: initial;
        display: block;
    }
    .e-dialog .e-dlg-header .e-icon-settings, .target-element .e-icon-btn {
        color: #fff;
    }

    .dialogContent .dialogText  {
        background-color: #f5f5f5;
    }

    #dialog.e-dialog .e-footer-content {
        border-top: 0.5px solid rgba(0, 0, 0, 0.42);
        padding-left: 35px;
    }

    .e-dialog .e-dlg-content .dialogContent {
        display: block;
        font-size: 15px;
        word-wrap: break-word;
        text-align: center;
        font-style: italic;
        border-radius: 6px;
        padding: 3%;
        position: relative;
        top: 6px;
    }

    .control-wrapper .e-control.e-dialog {
        width: 30%;
    }
    .e-dialog .e-dlg-header-content .e-icon-dlg-close {
    color: #fff;
    }
    .e-dialog .e-btn.e-dlg-closeicon-btn:hover span{
        color: #8ECBFF;
    }
    .e-dialog .e-dlg-header-content .e-btn.e-dlg-closeicon-btn:hover,
    .e-dialog .e-dlg-header-content .e-btn.e-dlg-closeicon-btn:focus {
        background-color: rgba(255,255,255, 0.10);
    }
    .e-dialog .e-dlg-header-content .e-btn.e-dlg-closeicon-btn:active .e-icon-dlg-close ,
    .e-dialog .e-dlg-header-content .e-btn.e-dlg-closeicon-btn:focus .e-icon-dlg-close,
    .e-dialog .e-dlg-header-content .e-btn.e-dlg-closeicon-btn:hover .e-icon-dlg-close {
        color: #fff;
    }

</style>
```

{% endtab %}

## See Also

* [How to add an icon to dialog buttons](./how-to/add-an-icons-to-dialog-buttons)
* [How to customize the dialog appearance](./how-to/customize-the-dialog-appearance)
