---
title: "Tooltip Content"
component: "Tooltip"
description: "Vue tooltip component's content can be assigned with static text, template, or loaded dynamically via AJAX."
---

# Content

A text or a piece of information assigned to the Tooltip's `content` property will be displayed as the main text stream of the Tooltip.
It can be a string or a template content. If the `content` property is not provided with any specific value, then it takes the value
assigned to the `title` attribute of the target element on which the Tooltip was initialized. The content can also dynamically be
   assigned to the Tooltip via AJAX.

## Template content

Any text or image can be added to the Tooltip, by default. To customize the Tooltip layout or to create your own visualized element on the
 Tooltip, template can be used.

Refer to the following code example to add formatted HTML content to the Tooltip.

{% tab template="tooltip/content", isDefaultActive=true %}

```html
<template>
   <div id='app'>
    <ejs-tooltip id='tooltip' :content='content' target='#target'>
        <p>A green home is a type of house designed to be  <a id="target"><u>environmentally friendly</u></a>
          and sustainable. And also focuses on the efficient use of "energy, water, and building materials." As green homes
          have become more prevalent we have also seen the emergence of green affordable housing.
        </p>
      </ejs-tooltip>
    </div>
</template>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  #tooltipContent {
    padding: 10px;
    font-weight: 400;
    font-size: 14px;
    line-height: 22px;
  }
</style>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
Vue.use(TooltipPlugin);

var demoVue = Vue.component("demo", {
  template: `
    <div id="tooltipContent"><p><strong>Environmentally friendly</strong> or <strong>environment-friendly</strong>, <i>(also referred to as eco-friendly, nature-friendly, and green)</i> are marketing and sustainability terms referring to goods and services, laws, guidelines and policies that inflict reduced, minimal, or no harm upon ecosystems or the environment.</p></div>`,
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

## Dynamic content via AJAX

The Tooltip content can be dynamically loaded  by making use of the AJAX call. The AJAX request is usually made within the `beforeRender`
 event of the Tooltip, and then the Tooltip's `content` is assigned the value retrieved on it's success.

 {% tab template="tooltip/ajax-content", isDefaultActive=true %}

```html
<template>
  <div id='app'>
    <ejs-tooltip style="display:block;" class="e-prevent-select" :content='content' target='.target' position='RightCenter' :beforeRender='onBeforeRender'>
      <div id='container'>
        <h4>National Sports</h4>
        <div id="targetContainer" class="e-prevent-select">
            <div id="countrylist">
                <ul>
                    <li class="target" title="1"><span>Australia</span></li>
                    <li class="target" title="2"><span>Bhutan</span></li>
                    <li class="target" title="3"><span>China</span></li>
                    <li class="target" title="4"><span>Cuba</span></li>
                    <li class="target" title="5"><span>India</span></li>
                    <li class="target" title="6"><span>Switzerland</span></li>
                    <li class="target" title="7"><span>United States</span></li>
                </ul>
            </div>
        </div>
      </div>
    </ejs-tooltip>
  </div>
</template>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
#container {
  width: 350px;
  position: relative;
  left: 50%;
  transform: translateX(-25%);
}

#countrylist {
  padding: 5px;
}

#countrylist ul {
  border: 1px solid #c4c4c4;
  box-sizing: border-box;
  list-style-type: none;
  margin: 0;
  padding: 0;
  width: 100px;
}

#countrylist li {
  padding: 10px;
}

#countrylist li:hover {
  background-color: #ececec;
}

.contentWrap {
  line-height: 16px;
  padding: 3px 0;
}
</style>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
import { Ajax } from '@syncfusion/ej2-base';
Vue.use(TooltipPlugin);
export default {
  data: function() {
    return {
      content : "Loading..",
    };
  },
  methods: {
       onBeforeRender: function(args){
  let ajax: Ajax = new Ajax('./tooltipdata.json', 'GET', true);
    ajax.send().then((result)  =>  {
        result = JSON.parse(result);
            for (var i = 0; i < result.length; i++) {
                 if (result[i].Id === args.target.getAttribute('data-content')) {
                    /* tslint:disable */
                    this.content = "<div class='contentWrap'><div class='def'>" + result[i].Sports + "</div></div>";
                    /* tslint:enable */
                }
                //  this.dataBind();
            }
        }, (reason) => {
            this.content = reason;
            //  this.dataBind();
        });
       }
   }
}
</script>

```

{% endtab %}
