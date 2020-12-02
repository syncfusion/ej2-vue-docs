---
title: "Create collapsible Tabs"
component: "Tab"
description: "This example demonstrates how to create tabs in a collapsible state when they are initially rendered in the Essential JS 2 Tab control."
---

# Create collapsible Tabs

You can achieve collapse and expand functionality in Tab by adding/removing a custom CSS class in the click event handler for each tab.
* Define a CSS class to set the style property display as none. Here 'collapse' class is added to the content element for hiding it.
* Bind the `select`  event for Tab to collapse the initially selected Tab item and bind custom click handler for the Tab headers.
* In the event handler, add and remove 'collapse' class to hide and show the corresponding Tab content.

{% tab template="tab/how-to/collapsible-tab", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <div class="info">
        Collapsible Tabs
    </div>
    <span style="margin: 10px;">
        <i>The active tab can be toggled to expand and collapse its content.</i>
    </span>
    <br /><br />
    <ejs-tab id='collapsible_tab' class='e-background' ref='TabInstance' :created="tabCreated" :selected= "tabSelected">
    <e-tabitems>
              <e-tabitem :header='headerText0' :content="content0"></e-tabitem>
              <e-tabitem :header='headerText1' :content="content1"></e-tabitem>
              <e-tabitem :header='headerText2' :content="content2"></e-tabitem>
    <e-tabitems>
    </ejs-tab>
  </div>
</template>
<script>
import Vue from 'vue';
import { TabPlugin } from '@syncfusion/ej2-vue-navigations';
import { Tab, TabComponent, SelectEventArgs } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';
Vue.use(TabPlugin);
export default {
  name: 'app',
   data: function() {
        return {
          headerText0: { 'text': 'Twitter' },
          headerText1: { 'text': 'Facebook' },
          headerText2: { 'text': 'WhatsApp' },

         content0: 'Twitter is an online social networking service that enables users to send and read short'
            + '140-character messages called "tweets". Registered users can read and post tweets, but those'
            + 'who are unregistered can only read them. Users access Twitter through the website interface,'
            + 'SMS or mobile device app Twitter Inc. is based in San Francisco and has more than 25 offices'
            + 'around the world. Twitter was created in March 2006 by Jack Dorsey, Evan Williams, Biz Stone,'
            + 'and Noah Glass and launched in July 2006. The service rapidly gained worldwide popularity,'
            + 'with more than 100 million users posting 340 million tweets a day in 2012.The service also'
            + 'handled 1.6 billion search queries per day.',
         content1: 'Facebook is an online social networking service headquartered in Menlo Park, California.'
            + 'Its website was launched on February 4, 2004, by Mark Zuckerberg with his Harvard College'
            + 'roommates and fellow students Eduardo Saverin, Andrew McCollum, Dustin Moskovitz and Chris'
            + 'Hughes.The founders had initially limited the website\'\s membership to Harvard students, but'
            + 'later expanded it to colleges in the Boston area, the Ivy League, and Stanford University. It'
            + 'gradually added support for students at various other universities and later to high-school'
            + 'students.',
         content2: 'WhatsApp Messenger is a proprietary cross-platform instant messaging client for'
            + 'smartphones that operates under a subscription business model. It uses the Internet to send'
            + 'text messages, images, video, user location and audio media messages to other users using'
            + 'standard cellular mobile numbers. As of February 2016, WhatsApp had a user base of up to one'
            + 'billion,[10] making it the most globally popular messaging application. WhatsApp Inc., based in'
            + 'Mountain View, California, was acquired by Facebook Inc. on February 19, 2014, for '
            + 'approximately US$19.3 billion.',
}

  },

  mounted: function() {
    this.trgIndex;
    this.actLine;
  },

  methods:{
  tabCreated: function() {
    // After tab created first tab content and active line are hidden by adding custom class to make it collapse state
    this.actLine = document.querySelector('.e-indicator');
    document.getElementById("e-content_0").classList.add('collapse');
    this.actLine.classList.add('collapse');
  },
  tabSelected: function(e) {
    // If next tab item selected custom class is removed from content and active line element
    let cnttrgs = document.querySelectorAll('#collapsible_tab.e-tab > .e-content > .e-item');
    for (var i = 0; i < cnttrgs.length; i++) {
        cnttrgs[i].classList.remove('collapse');
    }
    if (this.actLine !== undefined) { this.actLine.classList.remove('collapse'); }
    this.trgIndex = e.selectedIndex;
     // Custom click event binding for each tab item to make collapse/expand
     e.selectedItem.addEventListener('click', function(e) {
        this.updateCollapseClass(this.trgIndex);
    }.bind(this));
  },
  updateCollapseClass: function(index) {
    // Custom classes are added/removed from tab content and active line element, when the same tab item again clicked
    let cntEle = document.getElementById("e-content_" + index);
    if (cntEle.classList.contains('collapse')) {
        cntEle.classList.remove('collapse');
        this.actLine.classList.remove('collapse');
    } else {
        cntEle.classList.add('collapse');
        this.actLine.classList.add('collapse');
    }
  },
 }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";

#container {
    visibility: hidden;
}

#loader {
    color: #008cff;
    height: 40px;
    left: 45%;
    position: absolute;
    top: 45%;
    width: 30%;
}

.e-content .e-item {
    font-size: 12px;
    margin: 10px;
    text-align: justify;
}
.container {
    min-width: 350px;
    margin: 0 10px;
}

.info {
    margin: 10px;
    font-weight: bold;
}

.e-tab .e-content > .e-item.e-active.collapse {
    display: none;
}

.e-tab .e-tab-header .e-indicator.collapse {
    display: none;
}
</style>
```

{% endtab %}
