---
title: "Play an audio before open the Vue Toast"
component: "Toast"
description: "This example demonstrates how to play audio in the background while opening the Essential JS 2 Toaster component."
---

# Play an audio before open the toast

The following sample demonstrates how to play an audio in background while opening the toast by including audio play codes into the beforeOpen event function.

> To stop the audio after displaying the toast, use the [`open`](../../api/toast/#open) event in toast. For further customization, check the Toast Events [`APIs`](../../api/toast/#events).

{% tab template="toast/how_to/audio", isDefaultActive=true %}

```html
<template>
   <div id='app'>
       <ejs-button ref='showButtonRef' class="e-btn" id="show_toast" v-on:click.native="showBtnClick">Show Toast</ejs-button>
        <ejs-toast ref='elementRef' id='element' title='Matt sent you a friend request' content='You have a new friend request yet to accept' :position='position' :beforeOpen='beforeOpen'></ejs-toast>
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
  methods: {
       showBtnClick: function(args){
           this.$refs.elementRef.show();
       },
       beforeOpen: function(e){
          var audio = new Audio('https://drive.google.com/uc?export=download&id=1M95VOpto1cQ4FQHzNBaLf0WFQglrtWi7');
          audio.play();
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