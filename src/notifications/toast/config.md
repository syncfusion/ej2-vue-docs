---
title: "Vue Toast Configuring Options"
component: "Toast"
description: "The Toast component configuration section explains how to customize the appearance of the Toast component using built-in APIs."
---

# Configuring Options

This section explains the steps required to customize the appearance of the toast using built-in APIs.

## Title and content template

Toast can be created with the notification message. The message contains [title](../api/toast/#title) and [content](../api/toast/#content) of the toasts. The title and contents are adaptable in any resolution.

> The Title or Content property can be given as HTML element/element ID to a string that can be displayed as a toast.

{% tab template="toast/config/title_content", isDefaultActive=true %}

```html
<template>
  <div id="app">
       <ejs-button ref='showButtonRef' class="e-btn" id="show_toast" v-on:click.native="showBtnClick">Show Toast</ejs-button>
       <ejs-toast ref='defaultRef' title='Matt sent you a friend request' content='You have a new friend request yet to accept' :position='position'></ejs-toast>
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
      showBtnClick: function(args){
          this.$refs.defaultRef.show();
      }
  }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-vue-notifications/styles/material.css";
</style>
```

{% endtab %}

## Specifying custom target

By default, the toast can be rendered in the document body. You can change the target position for toast rendering using the [target](../api/toast/#target) property. Based on the target, the [position](../api/toast/#position) will be updated.

## Close button

By default, the [showCloseButton](../api/toast/#showclosebutton) is not enabled. You can enable it by setting the true value. Before expiring the toast, you can use this button to close or destroy toasts manually.

## Progress bar

By default, the [showProgressBar](../api/toast/#showprogressbar) is not enabled. If it is enabled, it can visually indicate how long to get toast expires. Based on the [timeOut](../api/toast/#timeout) property, progress bar will appear.

### Progress bar direction

By default, the [progressDirection](../api/toast/#progressDirection) is set to "Rtl" and it will appear from right to left direction. You can change the progressDirection to "Ltr" to make it appear from left to right direction.

## Newest on top

By default, the newly created toasts will append next with existing toasts. You can change the sequence like inserting before the toast by enabling the [newestOnTop](../api/toast/#newestontop).

Here, The following sample demonstrates the combination of the `target`, `showCloseButton`, `showProgressBar`, and `newestOnTop` properties in toast.

{% tab template="toast/config/custom_target", isDefaultActive=true %}

```html
<template>
  <div id="app">
       <ejs-button ref='showButtonRef' class="e-btn" id="show_toast" v-on:click.native="showBtnClick">Show Toast</ejs-button>
       <ejs-toast ref='defaultRef' title='File Downloading' content='<div class="progress"><span style="width: 80%"></span></div>' :position='position' showCloseButton=true target='#toast_target' newestOnTop=true showProgressBar=true progressDirection="Ltr"></ejs-toast>
       <br/><br/>
       <div id='toast_target'></div>
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
      showBtnClick: function(args){
          this.$refs.defaultRef.show();
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

.e-toast-message {
    width: 100%;
}

.progress {
    height: 20px;
    position: relative;
    margin: 20px 0 20px 0;
    background: #555;
    -moz-border-radius: 25px;
    -webkit-border-radius: 25px;
    border-radius: 25px;
    box-shadow: inset 0 -1px 1px rgba(255, 255, 255, 0.3);
}

.progress span {
    background-color: #f0a3a3;
    background-image: -webkit-gradient(linear, left top, left bottom, color-stop(0, #f0a3a3), color-stop(1, #f42323));
    display: block;
    height: 100%;
    border-radius: 10px;
    width: 50%;
    position: relative;
    overflow: hidden;
}

.progress span::after {
  background-image: -webkit-gradient(linear, 0 0, 100% 100%,
    color-stop(.25, rgba(255, 255, 255, .2)),
    color-stop(.25, transparent), color-stop(.5, transparent),
    color-stop(.5, rgba(255, 255, 255, .2)),
    color-stop(.75, rgba(255, 255, 255, .2)),
    color-stop(.75, transparent), to(transparent));
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    background-size: 50px 50px;
    -webkit-animation: moveAnimate 2s linear infinite;
    overflow: hidden;
}

@-webkit-keyframes moveAnimate {
    0% {
       background-position: 0 0;
    }
    100% {
       background-position: 50px 50px;
    }
}
</style>

```

{% endtab %}

## Width and height

The dimensions of the toast can be set using the [width](../api/toast/#width) and [height](../api/toast/#height) properties. This will individually set all toasts. You can create different custom dimension toasts.

By default, the toast can be rendered with `300px` width with `auto` height.

> In mobile devices, the default width of the toast gets '100%' width of the page.
> When you set toast width as '100%', the toast occupies full width and will be displayed at the top or bottom based on the position `Y` property.

Both the width and height properties allow setting pixels/numbers/percentage. The number value is considered as pixels.

{% tab template="toast/config/width_height", isDefaultActive=true %}

```html
<template>
  <div id="app">
       <div id='container'>
        <ejs-button ref='showButtonRef' class="e-btn" id="show_toast" v-on:click.native="showBtnClick">Show Toast</ejs-button>
        <ejs-toast ref='defaultRef' id='element' title='Matt sent you a friend request' content='You have a new friend request yet to accept' :position='position' width=400 height=150></ejs-toast>
            <div class='row' style="padding-top: 20px" id= "toast_pos_target">
              <table>
                <tr>
                  <td>
                      <div style='padding:25px 0 0 0;'>
                          <ejs-radiobutton ref='topAlign' label='Top' name='toast' value='Target' :change='checkboxChange'></ejs-radiobutton>
                      </div>
                  </td>
                  <td>
                      <div style='padding:25px 0 0 0;'>
                          <ejs-radiobutton ref='bottomAlign' label='Bottom' checked=true name='toast' value='Global' :change='checkboxChange1'></ejs-radiobutton>
                      </div>
                  </td>
                </tr>
                <tr>
                   <td>
                     <div style='padding:25px 0 0 0;'>
                          <ejs-checkbox label='100% Width' :change='onChange'></ejs-checkbox>
                      </div>
                   </td>
                </tr>
              </table>
            </div>
        <br/><br/>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { ToastPlugin } from '@syncfusion/ej2-vue-notifications';
import { ButtonPlugin, RadioButtonPlugin, CheckBoxPlugin, ChangeEventArgs as CheckBoxChange, ChangeEventArgs } from '@syncfusion/ej2-vue-buttons';
Vue.use(ToastPlugin);
Vue.use(RadioButtonPlugin);
Vue.use(CheckBoxPlugin);
Vue.use(ButtonPlugin);
export default {
  name: 'app',
  data: function(){
    return {
        position: { X: "Center", Y: "Bottom" },
    }
  },
  mounted: function() {
      this.$refs.defaultRef.show();
      this.timeDelay = 500;
      this.toast = document.getElementById('element').ej2_instances[0];
  },
  methods: {
      showBtnClick: function(args){
          this.$refs.defaultRef.show();
      },
      onChange: function(e) {
          if (e.checked) {
             this.toast.hide();
             this.toast.width = "100%";
             this.toast.title="";
             this.toast.content="<div class='e-custom'>Take a look at our next generation <b>Javascript</b> <a href='https://ej2.syncfusion.com/home/index.html' target='_blank'>LEARN MORE</a></div>";
             this.toastShow(this.timeDelay);
          } else {
             this.toast.hide();
             this.toast.width= 300;
             this.toast.title= 'Matt sent you a friend request',
             this.toast.content='You have a new friend request yet to accept',
             this.toastShow(this.timeDelay);
         }
      },
      checkboxChange: function(e) {
        if (e.event.target.checked) {
            this.toast.position.Y = "Top";
            this.toast.hide();
            this.toastShow(this.timeDelay);
        }
      },

      checkboxChange1: function(e) {
        if (e.event.target.checked) {
            this.toast.position.Y = "Bottom";
            this.toast.hide();
            this.toastShow(this.timeDelay);
        }
      },

      toastShow: function(timeOutDelay) {
         setTimeout(() => {
            this.toast.show();
        }, timeOutDelay);
      }
   }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-vue-notifications/styles/material.css";
</style>

<style lang="scss">
#container {
  margin: 25px;
}

#loader {
  color: #008cff;
  height: 40px;
  left: 45%;
  position: absolute;
  top: 45%;
  width: 30%;
}

table td {
width: 50%;
}
</style>

```

{% endtab %}

## See Also

* [Prevent duplicate toasts](./how-to/prevent-duplicate-toast-display)
* [Customize the progress bar](./how-to/customize-progress-bar-theme-and-sizing)