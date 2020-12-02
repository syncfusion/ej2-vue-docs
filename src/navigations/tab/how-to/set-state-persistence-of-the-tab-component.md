---
title: "Set state persistence of the Tab component"
component: "Tab"
description: "This example demonstrates how to retain the current model value in the browser cookies for state maintenance of the Essential JS 2 Tab component."
---

# Set state persistence of the Tab component

State persistence allows the Tab to retain the current modal value in the browser cookies for state maintenance. This action is handled through the [`enablePersistence`](../../api/tab#enablepersistence) property which is set to false by default.

When it is set to true, some of the Tab component model values will be retained even after refreshing the page.

The following sample demonstrates how to set state persistence of the Tab component.

{% tab template="tab/how-to/persistence" %}

```html
<template>
    <div id="app">
    <ejs-tab id='element' enablePersistence='true'>
        <e-tabitems>
                   <e-tabitem :header='headerText0' :content="content0"></e-tabitem>
                    <e-tabitem :header='headerText1' :content="content1"></e-tabitem>
                    <e-tabitem :header='headerText2' :content="content2"></e-tabitem>
      </e-tabitems>
    </ejs-tab>
  </div>
</template>
<script>
import Vue from 'vue';
import { TabPlugin } from '@syncfusion/ej2-vue-navigations';

Vue.use(TabPlugin);
export default {
  name: 'app',
   data: function(){
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

        }
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
