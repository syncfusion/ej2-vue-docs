---
title: "Set custom animation"
component: "Tab"
description: "This example demonstrates how to set custom animation for both previous and next actions on Essential JS 2 Tab component when the tab select."
---

# Set custom animation

Tab supports custom animations for both previous and next actions from the provided animation option of `Animation` library.

The [`animation`](../../api/tab#animation) property also allows you to set [`easing`](../../api/tab/tabActionSettings#easing), [`duration`](../../api/tab/tabActionSettings#duration), and various other [`effects`](../../api/tab/tabActionSettings#effect).

Default animation is given as `SlideLeftIn` for [`previous`](../../api/tab/tabAnimationSettings#previous) tab animation and `SlideRightIn` for [`next`](../../api/tab/tabAnimationSettings#next) tab animation. You can also disable the animation by setting the animation effect as `None`. Also, please use the following CSS to disable indicator animation for animation effect as `None`.

```CSS

.e-tab .e-tab-header:not(.e-vertical) .e-indicator, .e-tab .e-tab-header.e-vertical .e-indicator {
    transition: none;
}

```

The sample demonstrates some types of animation that suits Tab. You can check all the animation effects here.

{% tab template="tab/how-to/custom-animation" %}

```html
<template>
    <div id="app">
   <div style='padding-top: 25px'>
    <div class='row'>
    <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
      <label> Previous Animation </label></div>
      <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
      <div class='custom_drop'><ejs-dropdownlist ref="previousInstance" :change= 'previousAnimationChange' index='0' :dataSource='animationData' placeholder='Previous Animation'></ejs-dropdownlist></div>
    </div></div>
    <div class='row'>
    <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
    <label> Next Animation </label></div>
    <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
    <div class='custom_drop'><ejs-dropdownlist ref="nextInstance" :change= 'nextAnimationChange' index='1' :dataSource='animationData' placeholder='Next Animation'></ejs-dropdownlist></div>
    </div></div>
    <div style='padding-top: 25px'>
        <ejs-tab id='element' ref="element">
        <e-tabitems>
                   <e-tabitem :header='headerText0' :content="content0"></e-tabitem>
                    <e-tabitem :header='headerText1' :content="content1"></e-tabitem>
                    <e-tabitem :header='headerText2' :content="content2"></e-tabitem>
      </e-tabitems>
    </ejs-tab>
    </div></div>
  </div>
</template>
<script>
import Vue from 'vue';
import { TabPlugin } from '@syncfusion/ej2-vue-navigations';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(TabPlugin);
Vue.use(DropDownListPlugin);
export default {
  name: 'app',
 data: function() {
    return {
        headerText0: { text: 'ASP.NET' },
          headerText1: { text: 'ASP.NET MVC' },
          headerText2: { text: 'JavaScript' },

        content0: 'ASP.NET is an open-source server-side web application framework designed for web development to produce ' +
        'dynamic web pages. It was developed by Microsoft to allow programmers to build dynamic web sites, web applications ' +
        'and web services. It was first released in January 2002 with version 1.0 of the .NET Framework, and is the successor ' +
        'to Microsoft\'\s Active Server Pages (ASP) technology. ASP.NET is built on the Common Language Runtime (CLR), allowing ' +
        'programmers to write ASP.NET code using any supported .NET language. The ASP.NET SOAP extension framework allows ' +
        'ASP.NET components to process SOAP messages.',

         content1: 'The ASP.NET MVC is a web application framework developed by Microsoft, which implements the ' +
        'model–view–controller (MVC) pattern. It is open-source software, apart from the ASP.NET Web Forms component which is ' +
        'proprietary. In the later versions of ASP.NET, ASP.NET MVC, ASP.NET Web API, and ASP.NET Web Pages (a platform using ' +
        'only Razor pages) will merge into a unified MVC 6.The project is called ASP.NET vNext.',

         content2: 'JavaScript (JS) is an interpreted computer programming language. It was originally implemented as ' +
        'part of web browsers so that client-side scripts could interact with the user, control the browser, communicate ' +
        'asynchronously, and alter the document content that was displayed.[5] More recently, however, it has become common in ' +
        'both game development and the creation of desktop applications.',
 animationData:['SlideLeftIn', 'SlideRightIn', 'FadeIn', 'FadeOut', 'FadeZoomIn', 'FadeZoomOut', 'ZoomIn', 'ZoomOut', 'None'];
    };
  },
methods: {
 previousAnimationChange: function(e) {
   var tabObj = this.$refs.element.ej2Instances;
   var ddlobj = this.$refs.previousInstance.ej2Instances;
  tabObj.animation.previous.effect = ddlobj.value;
  }
 nextAnimationChange: function(e) {
      var tabObj = this.$refs.element.ej2Instances;
      var ddlobj = this.$refs.nextInstance.ej2Instances;
      tabObj.animation.next.effect = ddlobj.value;
  }
}
</script>

<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
</style>
```

{% endtab %}
