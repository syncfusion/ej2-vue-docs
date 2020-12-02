---
title: "Close the Vue Toast with click/tap"
component: "Toast"
description: "This example demonstrates how to close the Essential JS 2 Toaster component with a click or tap operation."
---

# Close the toast with click/tap

By default, the toasts are expired based on the timeOut value. You can customize the toast hiding process with click/tap action by setting the event args in the [clicked](../../api/toast/toastClickEventArgs/#clicktoclose) callback function with [static Toast](../timeout/#static-toast).

{% tab template="toast/how_to/close", isDefaultActive=true %}

```html
<template>
   <div id='app'>
       <ejs-button ref='showButtonRef' class="e-btn" id="show_toast" v-on:click.native="showBtnClick">Show Toast</ejs-button>
       <ejs-toast ref='elementRef' id='element' :position='position' title='Matt sent you a friend request' content='You have a new friend request yet to accept' :click='onClick' timeOut=0></ejs-toast>
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
            position:  { X: 'Right', Y: 'Bottom' }
        }
   },
    mounted: function() {
       this.$refs.elementRef.show();
     },
  methods: {
       showBtnClick: function(args){
           this.$refs.elementRef.show();
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