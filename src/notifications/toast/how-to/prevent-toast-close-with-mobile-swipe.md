---
title: "Prevent toast close with mobile swipe"
component: "Toast"
description: "This example demonstrates how to prevent the identical same Essential JS 2 Toast is displayed on a screen."
---

# Prevent toast close with mobile swipe

You can prevent the toast close with mobile swipe action by setting [beforeClose](../../api/toast/#beforeClose) argument cancel value to true while argument type as a swipe. The following code shows how to prevent toast close with mobile swipe.

The following sample demonstrates preventing toast close with mobile swipe element displaying with custom code blocks.

{% tab template="toast/how_to/preventSwipe", isDefaultActive=true %}

```html
<template>
  <div id="app">
       <ejs-button ref='showButtonRef' class="e-btn" id="show_toast" v-on:click.native="showBtnClick">Show Toast</ejs-button>
       <ejs-toast ref='defaultRef' title='Matt sent you a friend request' content='You have a new friend request yet to accept' :beforeClose='onBeforeClose' :position='position'></ejs-toast>
  </div>
</template>

<script>
import Vue from 'vue';
import { ToastPlugin } from '@syncfusion/ej2-vue-notifications';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
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
      this.$refs.defaultRef.show();
  },
  methods: {
      showBtnClick: function(){
          this.$refs.defaultRef.show();
      },
      onBeforeClose: function(e) {
        if (e.event.type === "swipe") {
            this.toast.cancel = true;
        }
    }
  }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-vue-notifications/styles/material.css";
</style>

```

{% endtab %}