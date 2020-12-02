---
title: "Pane Content"
component: "Splitter"
description: "This section explains about user can feed content to pane as plain text content or HTML markup or integrate other JavaScript UI controls."
---

# Pane Content

This section explains how to provide plain text content or HTML markup or integrate other JavaScript UI components as content of splitter.

## HTML Markup

Splitter is a layout based container component. You can render the pane contents from existing HTML markups. Converting HTML markup as splitter pane is easy way to add the panes content dynamically.

{% tab template="splitter/resize-min-max" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='splitter' ref='splitterObj'  width='600px' height='200px'>
        <e-panes>
            <e-pane :content='content1' size = '200px'></e-pane>
            <e-pane :content='content2' size = '200px'></e-pane>
            <e-pane :content='content3' size = '200px'></e-pane>
        </e-panes>
    </ejs-splitter>
</div>
</template>
<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';

Vue.use(SplitterPlugin);
var contentVue1 = Vue.component("contentTemp1", {
    template: `<div class="content"><h3 class="h3">PARIS </h3>Paris, the city of lights and love - this short guide is full of ideas for how to make the most of the romanticism...</div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue2 = Vue.component("contentTemp2", {
    template: `<div class="content"><h3 class="h3">CAMEMBERT </h3>The village in the Orne département of Normandy where the famous French cheese is originated from.</div>`,
    data() {
        return {
            data: {}
        };
    }
});

var contentVue3 = Vue.component("contentTemp3", {
    template: `<div class="content"><h3 class="h3">GRENOBLE </h3>The capital city of the French Alps and a major scientific center surrounded by many ski resorts, host of the Winter Olympics in 1968.</div>`,
    data() {
        return {
            data: {}
        };
    }
});
export default {
    name: 'app',
    data () {
        return {
        content1: function (){
            return { template: contentVue1 }
        },
        content2: function (){
            return { template: contentVue2 }
        },
        content3: function (){
            return { template: contentVue3 }
        }
        }
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

#app {
    margin: 65px auto;
}
.content {
    padding: 10px;
}

.e-splitter {
    margin: 0 auto;
}
</style>

```

{% endtab %}

## JavaScript UI components

You can render any JavaScript UI components along with their native and control events within splitter as pane content.

You can refer [Accordion within splitter](https://ej2.syncfusion.com/vue/demos/#/material/splitter/accordion-navigation-menu.html) and [Listview within splitter](https://ej2.syncfusion.com/vue/demos/#/material/splitter/details-view.html) examples.

## Plain content

You can add the plain text as a pane contents using either inner HTML or [content](../api/splitter/panePropertiesModel/#content) API

{% tab template="splitter/resize-min-max" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='splitter' ref='splitterObj'  width='600px' height='200px'>
        <e-panes>
            <e-pane content='Left Pane' size ='200px'></e-pane>
            <e-pane content='Middle Pane' size ='200px'></e-pane>
            <e-pane content='Right Pane' size ='200px'></e-pane>
        </e-panes>
    </ejs-splitter>
</div>
</template>
<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';

Vue.use(SplitterPlugin);
export default {
    name: 'app',
    data () {
        return { }
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

#app {
    text-align: center;
    margin: 65px auto;
}
.content {
  justify-content: center;
  text-align: center;
  align-items: center;
  padding: 9px;
}

.e-splitter {
    margin: 0 auto;
}

.e-pane {
  text-align: center;
  align-items: center;
  display: grid;
}
</style>

```

{% endtab %}

## Pane content using selector

You can set HTML element as pane [content](../api/splitter/panePropertiesModel/#content) using the query selectors such as ID or CSS class selectors.

The following code demonstrates how to fetch an element from the document and load it to pane using its ID.

{% tab template="splitter/resize-min-max" %}

```html

<template>
<div id="app" class="col-lg-12 control-section default-splitter">
    <ejs-splitter id='splitter' ref='splitterObj' width='600px' height='200px'>
        <e-panes>
            <e-pane content='#left-pane-content' min='60px' size ='200px'></e-pane>
            <e-pane content='#middle-pane-content'  min='60px' size ='200px'></e-pane>
            <e-pane content='#last-pane-content'  min='60px' size ='200px'></e-pane>
        </e-panes>
    </ejs-splitter>

    <!-- pane contents -->
    <div id="left-pane-content" style="display: none;">
        <div>Left pane<div id='panetext'>size: 25%</div>
            <div id='panetext'>min: 60px</div>
        </div>
    </div>

    <div id="middle-pane-content" style="display: none;">
        <span>Middle pane<div id="panetext">size: 50%</div>
            <div id="panetext">min: 60px</div>
        </span>
    </div>

    <div id="last-pane-content" style="display: none;">
        <span>Right pane<div id="panetext">size: 25%</div>
            <div id="panetext">min: 60px</div>
        </span>
    </div>
</div>
</template>
<script>
import Vue from "vue";
import { SplitterPlugin } from '@syncfusion/ej2-vue-layouts';

Vue.use(SplitterPlugin);
export default {
    name: 'app',
    data () {
        return { }
    }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";

#app {
    text-align: center;
    margin: 65px auto;
}
.content {
  justify-content: center;
  text-align: center;
  align-items: center;
  padding: 9px;
}

.e-splitter {
    margin: 0 auto;
}

.e-pane {
  text-align: center;
  align-items: center;
  display: grid;
}
</style>

```

{% endtab %}