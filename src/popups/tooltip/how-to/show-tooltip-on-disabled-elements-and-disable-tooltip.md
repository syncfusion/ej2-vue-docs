# Show tooltip on disabled elements and disable tooltip

By default, tooltips will not be displayed on disabled elements. However, you can enable this behavior by using the following steps:
1. Add a disabled element like the `button` element into a div whose display style is set to `inline-block`.
2. Set the pointer event as `none` for the disabled element (button) through CSS.
3. Initialize the tooltip for outer div element that holds the disabled button element.

{% tab template="tooltip/how-to", isDefaultActive=true %}

```html
<template>
   <div id='app'>
    <ejs-tooltip id='tooltip' :content='content' target='#box'>
        <div id='container'>
            <div id="box" style="display: inline-block;">
                <ejs-button id='disabledbutton' disabled=true>Disabled button</ejs-button>
            </div>
        </div>
    </div>
</template>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
#disabledbutton {
    pointer-events: none;
    font-size: 22px;
    padding: 10px;
}
#container {
    display: inline-block;
    position: relative;
    left: 50%;
    transform: translateX(-50%);
    margin-top: 75px;
}
</style>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
Vue.use(TooltipPlugin);
Vue.use(ButtonPlugin);
export default {
  data: function() {
    return {
        content: "Tooltip from disabled element"
    };
  },
}
</script>

```

{% endtab %}
