---
title: "Customize the dialog appearance"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Customize the dialog appearance

You can customize the dialog appearance by providing dialog template as string or HTML element to the [content](../../api/dialog/#content) property. In the following sample, dialog is customized as  error window appearance.

{% tab template="dialog/custom-dialog" %}

```html
<template>
   <div>
    <div id="dialogTarget" class="control-section; position:relative" style="height:300px;">
        <center><ejs-button ref='button' id="dialogbtn" cssClass="e-info" v-on:click.native="dialogBtnClick">Open</ejs-button></center>
        <ejs-dialog id="dialog" ref="Dialog" :header='header' :showCloseIcon='showCloseIcon' :target='target' :width='width' :buttons='buttons' :animationSettings='animationSettings' :visible='visible' :content='content'>
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
            header: 'File and Folder Rename',
            content: "<div class = 'dialog-content'><div class='msg-wrapper  col-lg-12'><span class='e-icons        close-icon col-lg-2'></span>" +
                "<span  class='error-msg col-lg-10'>Can not rename 'pictures' because a file or folder with that name already exists </span>" +
                "</div><div class='error-detail col-lg-8'><span>Specify a different name</span> </div></div>",
            showCloseIcon: true,
            visible: false,
            buttons: [{
                buttonModel: { isPrimary: true, content: 'close' }, click:  function() {
                    this.hide();
                }
            }],
            target: document.querySelector('body'),
            width: '400px',
            animationSettings: { effect: 'Zoom' }
        }
    },
    methods: {
        dialogBtnClick: function() {
            this.$refs.Dialog.show();
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-vue-popups/styles/bootstrap.css";
@import "https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css";
    #app {
        color: #008cff;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }
    .row {
        padding: 10px 3px;
    }

    span.close-icon {
        width: 24px;
        height: 24px;
        position: relative;
        /* background-color: yellow; */
        display: inline-block;
        top: 17px;
    }
    span.error-msg {
        color: #66afe9;
        display: inline-block;
        position: relative;
        top: 18px;
        left: 20px;
        width: 80%;
        padding: 0px 16px 27px;
    }
    .error-detail {
        position: relative;
        left: 45px;
        margin: 20px 0px 21px;
    }
    .close-icon:before {
        content: '\e7e9';
        font-size: 26px;
        color:#d9534f;
        position: relative;
        left: 5px;
    }

    .e-dialog .e-footer-content {
        background-color: #f8f8f8;
    }

    .e-dialog, .e-dialog .e-dlg-header-content {
        background-color: #d9edf7;
    }
    .e-dialog {
        padding:3px;
    }
    .e-dialog .e-dlg-header-content {
        padding: 10px;
    }
    .e-dialog .e-footer-content {
        padding: 8px 12px;
    }

    .e-dialog .e-dlg-content {
        padding: 15px 0px 0px;
    }
</style>

```

{% endtab %}
