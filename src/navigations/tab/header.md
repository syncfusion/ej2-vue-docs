---
title: "Tab Header"
component: "Tab"
description: "This section explains how to create a Essential JS 2 Tab control header with different styles in an Vue application."
---

# Header

This section explains about modifying the style of Tab header, and configuring its icons and positions.

## Styles

You can customize header styles by adding predefined classes in the Tab root element. The pre-defined CSS class names are as follows:

* **e-fill**: The Selected Tab header background is set as solid fill.
* **e-background**: Tab header has a solid fill background, and the selected header has a highlighted border.
* **e-background e-accent**: Tab header has a solid fill background, and the selected header has a highlighted border with accent color.

> If the above custom style classes are not included in the root element, the default style is applied to the Tab items.

{% tab template="tab/header", isDefaultActive=true %}

```html
<template>
   <div id="wrapper" style='margin-top: 20px'>
   <div id='content' style="margin: 0px auto">
          <div id="default" style="padding-top:20px;width:250px">
            <div class='row'>
                <div>
                    <label> Header Style </label>
                </div><br/>
                <div>
                    <ejs-dropdownlist ref='headerStyles' :dataSource='headerData' :change='onChange' :value='value' :fields='fields' :popupHeight='height'></ejs-dropdownlist>
                </div>
            </div>
        </div>
        <br/>
     <div>
             <ejs-tab id='element' ref="element">
          <e-tabitems>
                    <e-tabitem :header='headerText0' :content="content0"></e-tabitem>
                    <e-tabitem :header='headerText1' :content="content1"></e-tabitem>
                    <e-tabitem :header='headerText2' :content="content2"></e-tabitem>
       </e-tabitems>
    </ejs-tab>
        </div>
      </div>
 </div>
</template>
<script>
import Vue from 'vue';
import { TabPlugin } from '@syncfusion/ej2-vue-navigations';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
Vue.use(TabPlugin);
export default {
  name: 'app',
     data: function(){
        return {
         headerData : [
        { Id: 'header1', headerStyle: 'default', text: 'Default' },
        { Id: 'header2', headerStyle: 'fill', text: 'Fill'},
        { Id: 'header3', headerStyle: 'background',text: 'Background' },
        { Id: 'header4', headerStyle: 'accent', text: 'Accent' }
        ],
      fields: { text: 'text', value: 'headerStyle' },
      height :'220px',
      value : 'default',

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
        },
        methods:{

      onChange: function(e){
       var tabObj =  this.$refs.element.ej2Instances;
        var listObj =  this.$refs.headerStyles.ej2Instances;
        this.removeStyleClass();
        if (listObj.value === 'fill') {
            tabObj.element.classList.add('e-fill');
        } else if (listObj.value === 'background') {
            tabObj.element.classList.add('e-background');
        } else if (listObj.value === 'accent') {
            tabObj.element.classList.add('e-background');
            tabObj.element.classList.add('e-accent');
        }
    }

      removeStyleClass: function(e) {
        var tabObj =  this.$refs.element.ej2Instances;
        tabObj.element.classList.remove('e-fill');
        tabObj.element.classList.remove('e-background');
        tabObj.element.classList.remove('e-accent');
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

## Icon positions

You can customize the position of the Tab header icons using the [`iconPosition`](../api/tab/header#iconposition) property.  This property depends on the header items [`iconCss`](../api/tab/header#iconcss) property.  By default, Tab header icon is placed on left position.  The position values are as follows:

* **Left**: Icon is placed on the left of the Tab header item.
* **Right**: Icon is placed on the right of the Tab header item.
* **Top**: Icon is placed on the top of the Tab header item.
* **Bottom**: Icon is placed on the bottom of the Tab header item.

{% tab template="tab/icon-position" %}

```html
<template>
<div id="wrapper" style='margin-top: 20px'>
   <div id='content' style="margin: 0px auto">
          <div id="default" style="padding-top:20px;width:250px">
            <div class='row'>
                <div>
                    <label> Icon Position </label>
                </div><br/>
                <div>
                    <ejs-dropdownlist ref='iconPosition' :dataSource='iconData' :change='onChange' :value='value' :fields='fields' :popupHeight='height'></ejs-dropdownlist>
                </div>
            </div>
        </div>
        <br/>
     <div>
    <div id="app">
    <ejs-tab id='element' ref="element">
        <e-tabitems>
                   <e-tabitem :header='headerText0' :content="content0"></e-tabitem>
                    <e-tabitem :header='headerText1' :content="content1"></e-tabitem>
                    <e-tabitem :header='headerText2' :content="content2"></e-tabitem>
      </e-tabitems>
    </ejs-tab>
  </div>
</div>
</div>
</div>
</template>
<script>
import Vue from 'vue';
import { TabPlugin } from '@syncfusion/ej2-vue-navigations';
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(DropDownListPlugin);
Vue.use(TabPlugin);
export default {
  name: 'app',
   data: function(){
        return {
          iconData : [
        { Id: '1', position: 'left', text: 'Left' },
        { Id: '2', position: 'right', text: 'Right'},
        { Id: '3', position: 'top',text: 'Top' },
        { Id: '4', position: 'bottom', text: 'Bottom' }
        ],
      fields: { text: 'text', value: 'position' },
      height :'220px',
      value : 'left',

          headerText0: { 'text': 'Twitter', 'iconCss': 'e-twitter' },
          headerText1: { 'text': 'Facebook', 'iconCss': 'e-facebook' },
          headerText2: { 'text': 'WhatsApp', 'iconCss': 'e-whatsapp' },

        content0: 'Twitter is an online social networking service that enables users to send and read short 140-character messages called "tweets".' +
        'Registered users can read and post tweets, but those who are unregistered can only read them. Users access Twitter' +
        'through the website interface, SMS or mobile device app Twitter Inc. is based in San Francisco and has more than 25' +
        'offices around the world. Twitter was created in March 2006 by Jack Dorsey, Evan Williams, Biz Stone, and Noah Glass' +
        'and launched in July 2006. The service rapidly gained worldwide popularity, with more than 100 million users posting' +
        '340 million tweets a day in 2012.The service also handled 1.6 billion search queries per day.',

         content1: 'Facebook is an online social networking service headquartered in Menlo Park, California. Its website was launched on February' +
        '4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo Saverin, Andrew McCollum,' +
        'Dustin Moskovitz and Chris Hughes.The founders had initially limited the website\'\s membership to Harvard students,' +
        'but later expanded it to colleges in the Boston area, the Ivy League, and Stanford University. It gradually added support' +
        'for students at various other universities and later to high-school students.',

         content2: 'WhatsApp Messenger is a proprietary cross-platform instant messaging client for smartphones that operates under a subscription' +
         'business model. It uses the Internet to send text messages, images, video, user location and audio media messages to' +
         'other users using standard cellular mobile numbers. As of February 2016, WhatsApp had a user base of up to one billion,[10]' +
         'making it the most globally popular messaging application. WhatsApp Inc., based in Mountain View, California, was acquired' +
         'by Facebook Inc. on February 19, 2014, for approximately US$19.3 billion.',

        }
   },
   methods:{
      onChange: function(e) {
        var tabObj =  this.$refs.element.ej2Instances;
        var listObj =  this.$refs.iconPosition.ej2Instances;
        console.log(tabObj);
        for(let i: number = 0; i < tabObj.items.length; i++) {
            tabObj.items[i].header.iconPosition = listObj.value;
        }
    }
}
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";

.e-content .e-item {
    font-size: 12px;
    margin: 10px;
    text-align: justify;
}

@font-face {
    font-family: 'Socialicons';
    src: url(data:application/x-font-ttf;charset=utf-8;base64,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) format('truetype');
    font-weight: normal;
    font-style: normal;
}

.e-tab-icon {
    font-family: 'Socialicons' !important;
}

.e-icons.e-tab-icon {
    position: relative;
    top: 1px;
}

.e-twitter:before {
    content: '\a701';
}

.e-facebook:before {
    content: '\a705';
}

.e-whatsapp:before {
    content: '\a700';
}
</style>
```

{% endtab %}

## See Also

* [How to customize selected tab styles](./how-to/customize-selected-tab-styles/)
