---
title: "Tab Content Height"
component: "Tab"
description: "This section explains how to customize the Syncfusion Essentail JS 2 Tab content height based on different needs."
---

# Customize Tab content height

You can change the Tab content height by using the [`heightAdjustMode`](../../api/tab#heightadjustmode) property. By default, the Tab content [`heightAdjustMode`](../../api/tab#heightadjustmode) property is set to `Content` value.

* **None**: Each tab content height is set based on the Tab height. This value is used only the tab component having the [`height`](../../api/tab#height) property.
* **Auto**: Each tab content height will take the maximum height of all other tabs content.
* **Content**: Each tab content height is set based on their own content.
* **Fill**: Each tab content height is set based on the full height of Tabs parent element.

{% tab template="tab/how-to/height", isDefaultActive=true %}

```html
<template>
    <div id="app">
   <div style='padding-top: 25px'>
    <div class='row'>
    <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
      <label>Height Adjust Mode</label></div>
      <div class="col-xs-6 col-sm-6 col-lg-6 col-md-6">
      <div class='custom_drop'><ejs-dropdownlist id='contentHeight' ref="contentHeight" :change= 'onChange' index='1' :dataSource='heightData'></ejs-dropdownlist></div>
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
 heightData:['None', 'Content', 'Fill', 'Auto'];
    };
  },
methods: {
 onChange: function(e) {
   var tabObj = this.$refs.element.ej2Instances;
   var ddlobj = this.$refs.contentHeight.ej2Instances;
   tabObj.heightAdjustMode = ddlobj.value;
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