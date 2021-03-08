---
title: "Vue Toast Template"
component: "Toast"
description: "The Essential JS 2 Toast component template section explains how to customize the toast component as needed."
---

# Template

The Template property in toast can be defined as `HTML element`, this can be either a `string` or `selector`.

The HTML element tag can be given as a string for the [Template](../api/toast/#template) property.

```typescript
template: "<div>Toast Content</div>"

```

The Template property allows getting the template content using the query `selector`. Here, the element `ID` attribute is specified in the template.

```typescript
template: "#Template"

```

{% tab template="toast/template", isDefaultActive=true %}

```html
<template>
   <div id='app'>
       <ejs-button ref='showButtonRef' class="e-btn" id="show_toast" v-on:click.native="showBtnClick">Show Toast</ejs-button>
       <div id='element'></div>
       <script id="template_toast_ele" type="text/x-template">
    <div id='template_toast'>
        <div class="horizontal-align">
            <div class='toast-content'>
                <div class='toast-title'>
                    Weekend Alarm
                </div>
                <div class='toast-message'> With traffic, its likely to take 45 minutes to get to jenny's 24th Birthday Bash at Hillside Bar, 454 E.
                    Olive Way by 10:00PM </div>
            </div>
        </div>
        <img src="https://ej2.syncfusion.com/demos/src/toast/resource/map.jpg" width="100%" height="70%">
    </div>
</script>
   </div>
</template>

<script>
import Vue from "vue";
import { ToastPlugin, Toast, ToastOpenArgs, ToastCloseArgs, ToastBeforeOpenArgs } from "@syncfusion/ej2-vue-notifications";
import { DropDownListPlugin, DropDownList, ChangeEventArgs } from '@syncfusion/ej2-vue-dropdowns';
import { compile, Browser, closest } from '@syncfusion/ej2-base';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';

Vue.use(ToastPlugin);
Vue.use(ButtonPlugin);
Vue.use(DropDownListPlugin);
export default {
  name: 'app',
  mounted: function() {
       this.toastObj = new Toast({
           template: document.getElementById('template_toast_ele').innerHTML,
           position:  { X: 'Right', Y: 'Bottom' },
           target: document.body,
           extendedTimeout: 0,
           timeOut: 120000,
       });
      this.toastObj.appendTo('#element');
      this.toastObj.show();
  },
  methods: {
      showBtnClick: function(args){
          this.toastObj.show();
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

#snooze,
#dismiss {
    background-color: #fff;
}

body>#element .e-toast {
    width: 400px !important;
}

.toast-template-section #reminder {
    text-align: center;
    margin: 15px;
}

#toast_custom .e-toast-template {
    display: inline-flex;
}

#template_toast .toast-icons {
    font-size: 35px;
    height: auto;
    margin: auto;
}

#template_toast .toast-icons.e-alarm::before {
    content: "\e702";
}

#template_toast .horizontal-align {
    display: inline-flex;
    flex-direction: row;
    width: 100%;
}

#template_toast .horizontal-align,
#template_toast #snoozedropDown,
#template_toast .snooze,
#template_toast .snoozeBtn {
    margin: 10px 0;
}

#template_toast .horizontal-align .toast-content .toast-title {
    font-weight: 500;
}

#template_toast .horizontal-align .toast-content .toast-message {
    opacity: 0.4;
}

#template_toast .horizontal-align .toast-content {
    display: inline-flex;
    flex: 1;
    flex-direction: column;
    margin-left: 10px;
}
</style>

```

{% endtab %}

## See Also

* [Add template dynamically](./how-to/add-dynamic-template)