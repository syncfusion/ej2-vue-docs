---
title: "Restrict the maximum Vue Toast to show"
component: "Toast"
description: "This example demonstrates how to restrict the maximum Essential JS 2 Toast count is displayed on a screen."
---

# Restrict the maximum toast to show

You can restrict the maximum toast count by using the event callback function and terminate the toast displaying process by setting the cancel event property in the [`beforeOpen`](../../api/toast/#beforeopen) event.

The following sample demonstrates restricting toast displaying up to 3. You can restrict by your own count with custom code blocks.

{% tab template="toast/how_to/maximum", isDefaultActive=true %}

```html
<template>
   <div id='app'>
        <ejs-button ref='showButtonRef' class="e-btn" id="show_toast" v-on:click.native="showBtnClick">Show Toast</ejs-button>
        <ejs-toast ref='elementRef' id='element' title='Sample Toast Title' content='Sample Toast content' :position='position' :beforeOpen='beforeOpen'></ejs-toast>
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
            position: { X: 'Right', Y: 'Bottom' }
        }
   },
  mounted: function() {
      this.toastFlag = 0;
      this.maxCount = 3;
      this.toasts = [
               { title: 'Warning !', content: 'There was a problem with your network connection.' },
               { title: 'Success !', content: 'Your message has been sent successfully.' },
               { title: 'Error !', content: 'A problem has been occurred while submitting your data.' },
               { title: 'Information !', content: 'Please read the comments carefully.' }];
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
          if (this.maxCount === this.$refs.elementRef.ej2Instances.element.childElementCount) {
               e.cancel =true;
          } else {
               e.cancel = false;
          }
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