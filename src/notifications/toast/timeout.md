---
title: "Vue Toast Time out"
component: "Toast"
description: "This section explains how to set time-out value for the Toast component, which is used to display toast till the time-out reaches without user interaction."
---

# Time out

The toast can be expired based on the [`timeOut`](../api/toast/#timeout) property. The toast can live till the time out reaches without user interaction, a time out value is considered as a millisecond.

* The [timeOut](../api/toast/#timeout) delay can be visually represented using [`Progress Bar`](./config/#progress-bar).

* The [`extendedTimeOut`](../api/toast/#extendedtimeout) property determines how long the toast should be displayed after a user hovers over it.

> You can terminate the process by using the [showCloseButton](../api/toast/#showclosebutton) property for destroying the toast at any time.

{% tab template="toast/time_out/time", isDefaultActive=true %}

```html
<template>
   <div id='app'>
       <div class="e-float-input"><input class="e-input" id="toast_input_index" required="" value="0"><span class="e-float-line"></span><label class="e-float-text">Enter timeOut</label></div>
       <ejs-button ref='showButtonRef' class="e-btn" id="show_toast" v-on:click.native="showBtnClick">Show Toast</ejs-button>
       <ejs-toast ref='elementToastTime' id='elementToastTime' :position='position' title='Anjolie Stokes' content='<p><img src="https://ej2.syncfusion.com/vue/demos/src/toast/resource/laura.png"></p>' width=230 height=250 :buttons='button'></ejs-toast>
   </div>
</template>

<script>
import Vue from "vue";
import { ToastPlugin, Toast } from "@syncfusion/ej2-vue-notifications";
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ToastPlugin);
Vue.use(ButtonPlugin);
export default {
  name: 'app',
  data: function(){
    return {
        position:  { X: 'Right', Y: 'Bottom' },
        button: [{
            model: { content: "Ignore" }
        }, {
            model: { content: "reply" }
        }]
    }
  },
  methods: {
      showBtnClick: function(args){
          let value = parseInt(document.getElementById('toast_input_index').value)
          this.$refs.elementToastTime.show({timeOut: value});
      }
  }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-vue-notifications/styles/material.css";
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
#app {
    max-width: 200px;
}

#elementToastTime {
    text-align: center;
  }

  #elementToastTime img{
    width: 100px;
    height: 100px;
    border-radius: 50%;
  }

  #elementToastTime .e-toast-message {
    width: inherit;
  }

</style>

```

{% endtab %}

## Static toast

You can prevent auto hiding in a toast as visible like static by setting zero (`0`) value in the [timeOut](../api/toast/#timeout) Property.

{% tab template="toast/time_out/static", isDefaultActive=true %}

```html
<template>
   <div id='app'>
       <ejs-button ref='showButtonRef' class="e-btn" id="show_toast" v-on:click.native="showBtnClick">Show Toast</ejs-button>
       <ejs-toast ref='element' id='element' :position='position' title='Matt sent you a friend request' content='Hey, wanna dress up as wizards and ride our hoverboards?' showCloseButton=true timeOut=0></ejs-toast>
   </div>
</template>

<script>
import Vue from "vue";
import { ToastPlugin, Toast } from "@syncfusion/ej2-vue-notifications";
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ToastPlugin);
Vue.use(ButtonPlugin);
export default {
  name: 'app',
  data: function(){
    return {
        position:  { X: "Right" }
    }
  },
  mounted: function() {
      this.$refs.element.show();
  },
  methods: {
      showBtnClick: function(args){
          this.$refs.element.show();
      }
  }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-vue-notifications/styles/material.css";
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

.e-laura {
    border-radius: 50%;
    background-image: url('https://ej2.syncfusion.com/demos/src/toast/resource/laura.png');
    background-repeat: no-repeat;
    background-size: cover;
    height: 50px !important;
    width: 50px !important;
    margin-bottom: 2px;
    margin-top: auto;
    margin-bottom: auto;
}

</style>

```

{% endtab %}

## See Also

* [Hide the toast on click](./how-to/close-the-toast-with-click-tap)