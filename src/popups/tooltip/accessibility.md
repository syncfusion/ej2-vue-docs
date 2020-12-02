---
title: "Accessibility For Tooltip"
component: "Tooltip"
description: "Vue tooltip component has accessibility support to help access the features via keyboard, on-screen readers, or other assistive technology devices."
---

# Accessibility

The Tooltip component has been designed, keeping in mind the [WAI-ARIA](http://www.w3.org/WAI/PF/aria-practices/) specifications, and
 applies the WAI-ARIA roles, states, and properties along with keyboard support. This makes it easy for people who use assistive
  technologies (AT) or who completely rely on keyboard navigation. As per the accessibility standard, the Tooltip opens on target elements
   to which it is attached as and when those target elements receive either keyboard focus or when the mouse hovers
    over it. When `esc` key is pressed, the Tooltip closes.

The Tooltip is made available to screen readers using the `aria-describedby` property. To be accurate, it must be used with an ARIA compliant
 browser along with the screen reader running from backend.

## ARIA attributes

Tooltip element is assigned with the role of `Tooltip`.

| Attributes | Description |
| --- | --- |
| role="tooltip" | This attribute  added to the Tooltip element describes the actual role of the element. |
| aria-describedby | This attribute is added to the target element on which the Tooltip gets opened, when focusing or hovering over it. It usually holds the randomly generated `Id` value of the Tooltip element. <br /> <br />In case, the target element already holds an `aria-describedby` attribute with `Id` value of some other component, then the Tooltip Id value can be additionally appended to the existing `aria-describedby` attribute separated by a space as shown in the example below.<br /><br /> **For example:** <br /> aria-describedby = "my-text my-tooltip" <br /> **my-text** is the Id of some other component.<br /> **my-tooltip** is the id of Tooltip component. <br /><br/> When the Tooltip is closed, the `aria-describedby` attribute is  removed from the target. |
| aria-hidden | This attribute is assigned to the Tooltip element whose default value is true. <br /><br /> When `true`, it denotes that the Tooltip element is in a hidden or a closed state. When the Tooltip appears on the screen, it’s value changes to `false`.|

## Keyboard interaction

The following are the standard keys that work on Tooltip.

|  Keys | Description |
| --- | --- |
| Tab | A form control receiving focus (say through tab key), opens the Tooltip, and on focus out closes it. |
| Escape | Closes or dismisses the Tooltip. |

> 1. When the Tooltip is being displayed on the target element, focus continues to stay on it.
> 2. If the Tooltip opens on mouse entering into the target element space, then it should be dismissed only when the mouse leaves that target.
> 3. If the Tooltip opens on the target element that receives focus, then it should be closed only when the focus moves out of that target element.
 Likewise, if the Tooltip opens on a click, then it should be closed only on another click action.

In the following preview sample, focusing the input element through `tab` key opens the Tooltip and  pressing the `esc` key closes it.

{% tab template="tooltip/target", isDefaultActive=true %}

```html
<template>
   <div id='app'>
        <ejs-tooltip target='.e-info' position='RightCenter'>
            <div id="container">
                <form id="details" role="form">
                    <div id="user">
                    <div class="info">User Name:</div>
                    <div class="inputs">
                        <input type="text" ref="uname" id="uname" class="e-info e-input" name="firstname" title="Please enter your name">
                    </div>
                    </div>
                    <br/>
                    <div>
                    <div class="info">Email Address:</div>
                    <div class="inputs">
                        <input type="text" id="mail" class="e-info e-input" name="email" title="Enter a valid email address">
                    </div>
                    </div>
                    <br/>
                    <div>
                    <div class="info">Password:</div>
                        <div class="inputs">
                            <input id="pwd" ref="pwd" type="password" class="e-info e-input" name="password" title="Be at least 8 characters length">
                        </div>
                    </div>
                    <br/>
                    <div>
                    <div class="info">Confirm Password:</div>
                    <div class="inputs">
                        <input id="cpwd" ref="cpwd" type="password" class="e-info e-input" name="Cpwd" title="Re-enter your password">
                    </div>
                    </div>
                    <br/>
                    <div class="btn">
                        <ejs-button id="sample" v-on:click.native='onSubmit'>Submit</ejs-button>
                        <ejs-button id='clear' v-on:click.native='onClear'type='reset'>Reset</ejs-button>
                    </div>
                </form>
            </div>
        </ejs-tooltip>
    </div>
</template>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
#container {
    border: 1px solid #ddd;
}

#details .info {
    font-weight: bold;
    width: 165px;
    display: inline-block;
    margin-left: 10px;
}
#details .inputs {
    display: inline-block;
}
#details .btn{
  margin-top: 10px;
  position: relative;
  left: 50%;
  transform: translateX(-50%);
  display: inline-block;
}
#details #sample{
  margin-left:10px;
}
#details #clear{
  margin-left:10px;
}
#details {
  padding-top: 30px;
  padding-bottom: 30px;
  position: relative;
  left: 50%;
  transform: translateX(-50%);
  display: inline-block;
}
</style>
<script>
import Vue from 'vue';
import { TooltipPlugin } from '@syncfusion/ej2-vue-popups';
Vue.use(TooltipPlugin);
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
Vue.use(ButtonPlugin);

export default {
  data: function() {
    return {
    };
  },
  methods: {
    onSubmit:function(args){
    let name = this.$ref.uname.value;
    let pwd = this.$ref.pwd.value;
    let cpwd = this.$ref.cpwd.value;
    if(name.length > 0 & name.length < 4){
        this.$ref.uname.title = 'Required Minimum 4 Characters';
        this.$ref.uname.style.backgroundColor = 'red';
        let target = this.$ref.uname;
        tooltip1.open(target);
    } else {

        this.$ref.uname.style.backgroundColor = 'white';
    }
    if(pwd !== '' && pwd.length < 8){
        this.$ref.pwd.title = 'Required Minimum 8 Characters';
        this.$ref.pwd.style.backgroundColor = 'red';
        let pwdtarget = this.$ref.pwd;
        tooltip3.open(pwdtarget);
    } else {
        this.$ref.pwd.style.backgroundColor = 'white';
    }
    if(name.length >= 4 && pwd !== '' && pwd.length >= 8  &&  pwd == cpwd ){
        alert('Form Submitted');
    } else {
        alert('Details are not Valid');
    }
    },
    onClear:function(args){
        this.$ref.uname.style.backgroundColor = 'white';
        this.$ref.pwd.style.backgroundColor = 'white';
        let target = this.$ref.uname;
        tooltip1.close(target);
        this.$ref.uname.title = 'Please enter your name';
        let pwdtarget = this.$ref.pwd;
        tooltip3.close(pwdtarget);
    }
  }
}
</script>

```

{% endtab %}
