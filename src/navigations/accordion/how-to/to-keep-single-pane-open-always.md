---
title: "To keep single pane open always"
component: "Accordion"
description: "This example demonstrates how to keep a single pane in an expanded state in the Essential JS 2 Accordion control."
---

# To keep single pane open always

By default, all Accordion panels are collapsible. You can customize the Accordion to keep one panel as expanded state always. This is
applicable for `Single` expand mode.

{% tab template="accordion/how-to/open-always", isDefaultActive=true %}

```html
<template>
    <div id="app">
  <ejs-accordion ref="element" expandMode='Single' :expanding="beforeExpand" :clicked="clicked">
      <e-accordionitems>
        <e-accordionitem expanded='true' header='ASP.NET' content='Microsoft ASP.NET is a set of technologies in the Microsoft .NET Framework for building Web applications and XML Web services'></e-accordionitem>
        <e-accordionitem header='ASP.NET MVC' content='The Model-View-Controller (MVC) architectural pattern separates an application into three main components: the model, the view, and the controller.'></e-accordionitem>
        <e-accordionitem header='JavaScript' content='JavaScript (JS) is an interpreted computer programming language.It was originally implemented as part of web browsers so that client-side scripts could interact with the user, control the browser, communicate asynchronously, and alter the document content that was displayed.'></e-accordionitem>
      </e-accordionitems>
    </ejs-accordion>
  </div>
</template>
<script>
import Vue from 'vue';
import { AccordionPlugin } from '@syncfusion/ej2-vue-navigations';
import {Accordion, ExpandEventArgs, AccordionClickArgs} from '@syncfusion/ej2-navigations';

Vue.use(AccordionPlugin);
export default {
  name: 'app',
  data(){

  },
  methods:{

 clicked: function(e) {
  var clickEle = e.originalEvent.target;
}
 beforeExpand: function(ExpandEventArgs) {
   var obj = this.$refs.element.ej2Instances;
  var expandCount = obj.element.querySelectorAll('.e-selected').length;
  var ele = obj.element.querySelectorAll('.e-selected')[0];
  if (ele) {
    ele = ele.firstChild
  }
  if (expandCount === 1 && ele === this.clickEle) {
    e.cancel = true;
  }
}
  }
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
</style>
```

{% endtab %}
