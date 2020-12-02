---
title: "Customize selected tab styles"
component: "Tab"
description: "This example demonstrates how to customize selected tab header styles in the Essential JS 2 Tab control."
---

# Customize selected tab styles

You can customize the Tab style by overriding its header and active tab CSS classes. Define HTML string for adding animation and customizing
the Tab header and pass it to [`text`](../../api/tab/header#text) property. Now you can override the style using custom CSS classes added to
the Tab elements.

{% tab template="tab/how-to/customize-tab", isDefaultActive=true %}

```html
<template>
   <div id="wrapper" style='margin-top: 20px'>
     <div>
            <ejs-tab id="element" :items='items'></ejs-tab>
      </div>
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
          items : [
        {
            header: { 'text': '<div><div class="e-image e-andrew"></div><div class="e-title fade-in">Andrew</div></div>' },
            content: 'Andrew received his BTS commercial in 1974 and a Ph.D. in international marketing from the University of Dallas in 1981.He is fluent in French and Italian and reads German.He joined the company as a sales representative, was promoted to sales manager in January 1992 and to vice president of sales in March 1993.Andrew is a member of the Sales Management Roundtable, the Seattle Chamber of Commerce, and the Pacific Rim Importers Association.'
        },
        {
            header: { 'text': '<div><div class="e-image e-margaret"></div><div class="e-title fade-in">Margaret</div></div>' },
            content: 'Margaret holds a BA in English literature from Concordia College (1958) and an MA from the American Institute of Culinary Arts (1966).She was assigned to the London office temporarily from July through November 1992.'
        },
        {
            header: { 'text': '<div><div class="e-image e-janet"></div><div class="e-title fade-in">Janet</div></div>' },
            content: 'Janet has a BS degree in chemistry from Boston College (1984).She has also completed a certificate program in food retailing management.Janet was hired as a sales associate in 1991 and promoted to sales representative in February 1992.'
        }
    ]

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
.container {
    min-width: 350px;
    max-width: 500px;
    margin: 0 auto;
}

.e-image {
background-size: 33px;
width: 33px;
height: 30px;
margin: 0 auto;
}

.e-image.e-andrew {
background-image: url(./1.png);
}

.e-image.e-margaret {
background-image: url(./2.png);
}

.e-image.e-janet {
background-image: url(./3.png);
}

.e-tab .e-toolbar-item .e-title {
    display: none;
}

.e-toolbar .e-toolbar-items .e-toolbar-item:not(.e-separator),
.e-toolbar .e-toolbar-items .e-toolbar-item .e-tab-wrap {
    width: 105px;
    height: 50px;
}

.e-tab .e-tab-header .e-toolbar-item.e-active .e-tab-wrap {
    background-color: #08c;
}
.e-tab .e-tab-header {
    background-color: #e6e6e6;
}
.e-tab .e-tab-header .e-toolbar-item:not(.e-active) .e-tab-wrap:hover {
   background-color: #f2f2f2;
   color:#000;
}
.e-tab .e-toolbar .e-toolbar-items .e-toolbar-item .e-text-wrap {
    height: 50px;
}

.e-tab .e-toolbar-item.e-active .e-image {
    display: none;
}

.e-tab .e-toolbar-item.e-active .e-title {
    display: block;
    color: white;
}

.e-tab .e-toolbar-item .e-text-wrap,
.e-tab .e-toolbar-item .e-tab-text {
    width:  inherit;
    text-align: center;
}

.fade-in {
    opacity: 1;
    animation-name: fadeInOpacity;
    animation-iteration-count: 1;
    animation-timing-function: ease-in;
    animation-duration: 0.5s;
}

@keyframes fadeInOpacity {
    0% {
        opacity: 0;
    }
    100% {
        opacity: 1;
    }
}
</style>
```

{% endtab %}
