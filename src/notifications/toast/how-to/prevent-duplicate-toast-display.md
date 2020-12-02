---
title: "Prevent duplicate Vue Toast display"
component: "Toast"
description: "This example demonstrates how to prevent the identical same Essential JS 2 Toast is displayed on a screen."
---

# Prevent duplicate toast display

You can prevent identical same toast displaying in a screen by the event function and terminate the toast displaying process by setting the cancel event property in the [`beforeOpen`](../../api/toast/#beforeopen) event.

The following sample demonstrates preventing duplicate title toast element displaying with custom code blocks.

{% tab template="toast/how_to/duplicate", isDefaultActive=true %}

```html
<template>
   <div id='app'>
        <ejs-button ref='showButtonRef' class="e-btn" id="show_toast" v-on:click.native="showBtnClick">Show Toast</ejs-button>
        <ejs-toast ref='elementRef' id='element' title='Sample Toast Title' content='Sample Toast content' :position='position' :beforeOpen='beforeOpen' :close="onClose" :created="onCreated"></ejs-toast>
   </div>
</template>

<script>
import Vue from "vue";
import { ToastPlugin, Toast } from "@syncfusion/ej2-vue-notifications";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
Vue.use(ToastPlugin);
Vue.use(ButtonPlugin);
export default {
  name: 'app',
  data: function(){
        return {
            position: { X: 'Center' }
        }
   },
  mounted: function() {
      this.toastFlag = 0;
      this.toasts = [
               { title: 'Warning !', content: 'There was a problem with your network connection.', isOpen: false },
               { title: 'Success !', content: 'Your message has been sent successfully.', isOpen: false },
               { title: 'Error !', content: 'A problem has been occurred while submitting your data.', isOpen: false }];
      this.$refs.elementRef.show(this.toasts[this.toastFlag]);
      ++this.toastFlag;
  },
  methods: {
       showBtnClick: function(args){
        this.$refs.elementRef.show(this.toasts[this.toastFlag]);
        ++this.toastFlag;
        if (this.toastFlag === (this.toasts.length)) {
            this.toastFlag = 0;
        }
       },
       beforeOpen: function(e){
        if (this.preventDuplicate(e)) {
            e.cancel = true;
        }
       },
       onCreated: function() {
            this.toastInstance.show(this.toasts[this.toastFlag]);
            ++this.toastFlag;
        },
        onClose: function(e) {
            for (let i: number = 0; i < this.toasts.length; i++) {
                if (this.toasts[i].title === e.options.title) {
                    this.toasts[i].isOpen = false;
                }
            }
        },
        preventDuplicate: function(e){
           for (let i = 0; i < this.toasts.length; i++) {
            if (this.toasts[i].title === e.options.title && !this.toasts[i].isOpen) {
                this.toasts[i].isOpen = true;
                return false;
            }
           }
           return true;
       }
    }
}
</script>
<style>
@import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-popups/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-vue-notifications/styles/material.css';
</style>

```

{% endtab %}