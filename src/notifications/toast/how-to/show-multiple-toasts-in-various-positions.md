---
title: "Show multiple Vue Toast in various positions"
component: "Toast"
description: "This example demonstrates how to create multiple Essential JS 2 Toast component in various position on the screen."
---

# Show multiple toasts in various positions

By default, the positions of the new toasts are only updated after the visible toasts have been destroyed. If You need to display multiple toasts with different positions, initiate another toasts.

The following sample demonstrates adding multiple toasts in different positions.

{% tab template="toast/how_to/position", isDefaultActive=true %}

```html
<template>
   <div id='app'>
       <ejs-button ref='showButtonRef' class="e-btn" id="show_toast" v-on:click.native="showBtnClick">Show Right Position Toast</ejs-button>
       <ejs-button ref='showButton1Ref' class="e-btn" id="show_toast1" v-on:click.native="showBtn1Click">Show Left Position Toast</ejs-button>
       <ejs-toast ref='elementRef' id='element' :position='position' title='Warning !' content='There was a problem with your network connection.' :click='onClick'></ejs-toast>
       <ejs-toast ref='element1Ref' id='element1' :position='position1' title='Success !' content='Your message has been sent successfully.' :click='onClick'></ejs-toast>
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
            position: { X: 'Right', Y: 'Bottom' },
            position1: { X: 'Left', Y: 'Bottom' },
        }
   },
    mounted: function() {
       this.$refs.elementRef.show();
       this.$refs.element1Ref.show();
     },
  methods: {
       showBtnClick: function(args){
           this.$refs.elementRef.show();
       },
       showBtn1Click: function(args){
           this.$refs.element1Ref.show();
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