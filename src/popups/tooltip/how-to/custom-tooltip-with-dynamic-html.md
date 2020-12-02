# Custom Tooltip with dynamic HTML

Tooltip loads HTML pages via HTML tags such as iframe, video, and map using the [`content`](https://ej2.syncfusion.com/vue/documentation/api/tooltip/#content) property, which supports both string and HTML tags.

To load an `iframe` element in tooltip, set the required iframe in the `content` of tooltip while initializing the tooltip component. Refer to the following code.

```typescript

content= '<iframe src="https://ej2.syncfusion.com/showcase/typescript/expensetracker/#/dashboard"></iframe>

```

{% tab template="tooltip/iframe", isDefaultActive=true %}

```html
<template>
   <div id='app'>
        <ejs-tooltip target='#iframeContent' cssClass='e-tooltip-css' ref="tooltipTitle" :position='position' :opensOn='opensOn' :content='content'>
            <div id='container'>
                <div id="tooltipContent">
                    <div class="content">
                        <ejs-button cssClass="text" id="iframeContent">Embedded Iframe</ejs-button>
                    </div>
                </div>
            </div>
        </ejs-tooltip>
    </div>
</template>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
</style>
<script>
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
Vue.use(ButtonPlugin);
import { TooltipPlugin } from '@syncfusion/ej2-vue-popups';
Vue.use(TooltipPlugin);

export default {
  data: function() {
    return {
      position: 'BottomCenter',
      opensOn: 'Click',
      content: '<iframe src="https://ej2.syncfusion.com/showcase/typescript/expensetracker/#/dashboard"></iframe>'
    };
  },
  methods: {
  }
}
</script>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
#tooltipContent {
    position: relative;
    left: 50%;
    transform: translateX(-50%);
    margin: 65px 10px 0 10px;
}

.content {
    display: inline-block;
    width: 49%;
    height: 250px;
    position: relative;
    left: 50%;
    transform: translateX(-50%);
}

#tooltipFrame {
    width: 332px;
    height: 233px;
}

.content .e-btn {
    position: relative;
    left: 50%;
    transform: translateX(-50%);
}
</style>

```

{% endtab %}