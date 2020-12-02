# Dynamic Tooltip content with HTML elements

The Tooltip component loads HTML tags using the [content](https://ej2.syncfusion.com/vue/documentation/api/tooltip/#content) template.

The HTML tags such as `<div>`, `<span>`, `bold`, `italic`, `underline`, etc., can be used. Style attributes can also be applied with HTML tags.

Here, Bold, Italic, Underline, and Anchor tags are used.

{% tab template="tooltip/tags", isDefaultActive=true %}

```html
<template>
   <div id='app'>
        <ejs-tooltip target='#title' cssClass='e-tooltip-css' ref="tooltipTitle" position='BottomCenter' opensOn='Click' ref="tooltip" :content="content">
            <div id="container">
                <div id="tooltipContent">
                    <div class="content">
                        <ejs-button class="text" id="title">HTML(With Title)</ejs-button>
                    </div>
                </div>
            </div>
        </ejs-tooltip>
    </div>
</template>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
#tooltipContent table {
    margin: 0 auto;
}

#tooltipContent {
    display: inline-block;
    position: relative;
    left: 50%;
    transform: translateX(-50%);
    margin-top: 50px;
    height: 200px;
}

.text {
    text-transform: capitalize;
    width: 155px;
}

.header {
    font-family: "Arial Black", Gadget, sans-serif;
    font-size: 12px;
    padding-bottom: 2px;
    margin: 4px -7px 7px -7px;
    padding-right: 5px;
    padding-left: 6px;
    font-weight: bold;
    height: 18px;
    border-bottom: 1px solid white;
}

.e-tooltip-css.e-tooltip-wrap .e-tip-content {
    padding: 0 10px 10px 10px;
}
</style>
<script>
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { TooltipPlugin } from '@syncfusion/ej2-vue-popups';
Vue.use(ButtonPlugin);
Vue.use(TooltipPlugin);

var demoVue = Vue.component("demo", {
  template: `
    <div id="tooltip" ref="content">
        <h2>HTML Tags</h2>
            Through templates, <b><span style="color:#e3165b">tooltip content</span></b> can be loaded with <u><i> inline HTML, images, iframe, videos, maps </i></u>. A title can be added to the content
    </div>`,
  data() {
    return {
      data: {}
    };
  }
});

export default {
  data: function() {
    return {
        content: function () {
            return { template : demoVue}
        }
    };
  }
}
</script>

```

{% endtab %}