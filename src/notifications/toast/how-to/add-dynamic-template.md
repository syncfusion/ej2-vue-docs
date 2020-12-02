---
title: "Add dynamic template for Vue Toast"
component: "Toast"
description: "This example demonstrates how to dynamically change a template for display in multiple Essential JS 2 Toaster components."
---

# Add dynamic template

Toast supports to change templates dynamically with displaying in multiple toasts. You can change the toast properties while calling in the [`show`](../../api/toast/#show) method.

{% tab template="toast/how_to/template", isDefaultActive=true %}

```html
<template>
   <div id='app'>
       <ejs-button ref='showButtonRef' class="e-btn" id="show_toast" v-on:click.native="showBtnClick">Show Toast</ejs-button>
       <ejs-toast ref='elementRef' id='element' :position='position' :click='onClick'></ejs-toast>
        <div id='templateToast' style="display: none;color:red"> System affected by virus !!! </div>
    </div>
</template>

<script>
import Vue from "vue";
import { ToastPlugin, Toast, ToastClickEventArgs  } from "@syncfusion/ej2-vue-notifications";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
Vue.use(ToastPlugin);
Vue.use(ButtonPlugin);
export default {
  name: 'app',
  data: function(){
        return {
            position:  { X: 'Right', Y: 'Bottom' }
        }
   },
    mounted: function() {
       this.toastFlag = 0;
       this.toasts = [
           { template: '2 Mail has received'},
           { template: 'User Guest Logged in'},
           { template: 'Logging in as Guest'},
           { template: 'Ticket has reserved '},
           { template: '#templateToast' }];
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
       onClick: function(e){
            e.clickToClose = true;
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

<style lang="scss">
#loader {
  color: #008cff;
  height: 40px;
  left: 45%;
  position: absolute;
  top: 45%;
  width: 30%;
}
</style>
```

{% endtab %}