---
title: "Set custom animation"
component: "Accordion"
description: "This example demonstrates how to set custom animation for expand and collapse actions in the Essential JS 2 Accordion control."
---

# Set custom animation

Accordion supports custom animations for both expand and collapse actions from the provided animation option of `Animation` library.

Default animation is given as `SlideDown` for expanding the panel and `SlideUp` for collapsing the panel. You can also disable the animation
by setting animation effect as `none`.

The sample demonstrates some types of animation that suits for Accordion. You can check all the animation effects here.

{% tab template="accordion/how-to/accordion-custom-animation", isDefaultActive=true %}

```html
<template>
    <div id="app">
   <div style='padding-top: 25px'>
    <div class='row'>
    <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
      <label> Expand Animation </label></div>
      <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
      <div class='custom_drop'><ejs-dropdownlist ref="expandInstance" :change= 'expandAnimationChange' index='0' :dataSource='expandAni' placeholder='Expand Animation'></ejs-dropdownlist></div>
    </div></div>
    <div class='row'>
    <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
    <label> Collapse Animation </label></div>
    <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
    <div class='custom_drop'><ejs-dropdownlist ref="expandInstance" :change= 'collapseAnimationChange' index='1' :dataSource='expandAni' placeholder='Collapse Animation'></ejs-dropdownlist></div>
    </div></div>
    <div style='padding-top: 25px'>
    <ejs-accordion ref="acrdnInstance">
      <e-accordionitems>
        <e-accordionitem expanded='true' header='ASP.NET' content='Microsoft ASP.NET is a set of technologies in the Microsoft .NET Framework for building Web applications and XML Web services'></e-accordionitem>
        <e-accordionitem header='ASP.NET MVC' content='The Model-View-Controller (MVC) architectural pattern separates an application into three main components: the model, the view, and the controller.'></e-accordionitem>
        <e-accordionitem header='JavaScript' content='JavaScript (JS) is an interpreted computer programming language.It was originally implemented as part of web browsers so that client-side scripts could interact with the user, control the browser, communicate asynchronously, and alter the document content that was displayed.'></e-accordionitem>
      </e-accordionitems>
    </ejs-accordion>
    </div></div>
  </div>
</template>
<script>
import Vue from 'vue';
import { AccordionPlugin } from '@syncfusion/ej2-vue-navigations';
import {Accordion, AccordionEffect} from '@syncfusion/ej2-navigations';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(AccordionPlugin);
Vue.use(DropDownListPlugin);
export default {
  name: 'app',
 data: function() {
    return {
 expandAni:['SlideDown', 'SlideUp', 'FadeIn', 'FadeOut', 'FadeZoomIn', 'FadeZoomOut', 'ZoomIn', 'ZoomOut', 'None'];
    };
  },
methods: {
 expandAnimationChange: function(e) {
   var obj = this.$refs.acrdnInstance.ej2Instances;
   var ddlobj = this.$refs.expandInstance.ej2Instances;
  obj.animation.expand.effect = ddlobj.value;
  }
 collapseAnimationChange: function(e) {
    var obj = this.$refs.acrdnInstance.ej2Instances;
     var ddlobj = this.$refs.collapseInstance.ej2Instances;
      obj.animation.collapse.effect = ddlobj.value;
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
</style>
```

{% endtab %}