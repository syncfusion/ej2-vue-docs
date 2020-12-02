---
title: "Tooltip Open Mode"
component: "Tooltip"
description: "Vue tooltip supports the mode on which the Tooltip is to be opened on a page, i.e., on hovering, focusing, or clicking on the target elements."
---

# Open Mode

You can decide the mode on which the Tooltip is to be opened on a page, i.e., on hovering, focusing, or clicking on the target elements.

> On mobile devices, Tooltips appear when you tap and hold the element, even if the `opensOn` option is assigned with `hover`.
> Tooltips are also displayed as long as you continue to tap and hold the element. On lift, it  disappears in the next 1.5 seconds.
> If there is another action before that time ends, then the Tooltip disappears.

The `opensOn` property can take either a single or a combination of multiple values, separated by space from the following options.
 The table  below explains how the Tooltip opens on both desktop and mobile based on the value(s) assigned to the `opensOn` property.
  By default, it takes `auto` value.

| Values | Desktop | Mobile |
| ------------- | ------------- | ------------- |
| `Auto` | Tooltip appears when you hover over the target or when the target element receives the focus. | Tooltip opens on tap and hold of the target element. |
| `Hover` | Tooltip appears when you hover over the target. | Tooltip opens on tap and hold of the target element. |
| `Click` | Tooltip appears when you click a target element. | Tooltip appears when you single tap the target element. |
| `Focus` | Tooltip appears when you focus (say through tab key) on a target element. | Tooltip appears with a single tap on the target element. |
| `Custom` | Tooltip is not triggered by any default action. So, you have to bind your own events and use either `open` or `close` public methods. | Same as Desktop. |

To open the Tooltip for multiple actions, say while hovering over or clicking on a target element, the `opensOn` property can be assigned
 with multiple values, separated by space as `Hover Click`.

> `Auto` value cannot be used with any combination for multiple values.

The following code example shows how to set the open mode for Tooltips.

{% tab template="tooltip/open-mode", isDefaultActive=true %}

```html
<template>
   <div id='app'>
        <div id='container'>
            <ejs-tooltip id="tooltipHover" opensOn='Hover' content='Tooltip from hover' target="#tooltiphover">
                <ejs-tooltip target="#tooltipclick" id="tooltipClick" opensOn='Click' content='Tooltip from click'>
                    <ejs-tooltip target="#tooltipfocus" id="tooltipFocus" opensOn='Focus' content='Tooltip from focus'>
                        <ejs-tooltip target="#tooltipopen" ref="tooltip" opensOn='Custom' content='Tooltip from custom mode'>
                            <table style="margin-top: 50px;transform: translateX(-50%);position: relative;left: 50%;height: 250px;">
                                <tbody>
                                    <tr>
                                        <td style="padding:25px">
                                            <div id="tooltiphover" class="blocks e-btn">
                                                <span>Hover Me !(Default)</span>
                                            </div>
                                        </td>
                                        <td style="padding:25px">
                                            <div id="tooltipclick" class="blocks e-btn">
                                                <span>Click Me !</span>
                                            </div>
                                        </td>
                                    </tr>
                                    <tr>
                                        <td style="padding:25px">
                                            <div class="">
                                                <span id="textbox" class="e-float-input">
                                                    <input id="tooltipfocus" type="text" placeholder="Focus and blur" />
                                                </span>
                                            </div>
                                        </td>
                                        <td style="padding:25px">
                                            <div id="tooltipcustom">
                                                <div>
                                                    <input id="tooltipopen" type="button" class="e-btn" value="Click to open tooltip manually" v-on:click="onCustomOpen" />
                                                </div>
                                            </div>
                                        </td>
                                    </tr>
                                </tbody>
                            </table>
                        </ejs-tooltip>
                    </ejs-tooltip>
                </ejs-tooltip>
            </ejs-tooltip>
        </div>
    </div>
</template>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
.blocks {
    width: 260px;
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
    };
  },
  methods: {
        onCustomOpen: function(args){
           if (args.target.getAttribute('data-tooltip-id')) {
           this.$refs.tooltip.close();
        } else {
            this.$refs.tooltip.open(args.target);
        }
        }
    }
}
</script>

```

{% endtab %}

## Custom open mode

Other than the above specified options, the `custom` mode makes the Tooltip appear on screen for user-defined custom actions such as
 `right-click`, `double-click`, and so on. Here, the tooltip is not triggered by any default action, and you have to bind your own events
  and use either `open` or `close` public methods to show or hide the Tooltips.

The following code example shows how to define custom open mode for the Tooltip.

{% tab template="tooltip/custom-open", isDefaultActive=true %}

```html
<template>
   <div id='app'>
    <ejs-tooltip ref="tooltip" id="tooltip" content='Tooltip from custom mode' opensOn='Custom' v-on:dblclick.native='customOpen'>
            <div id="box">Double-click to open Tooltip.</div>
    </ejs-tooltip>
    </div>
</template>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
#box {
    background-color: #cfd8dc;
    border: 3px solid #eceff1;
    box-sizing: border-box;
    margin: 80px auto;
    padding: 20px 0;
    width: 300px;
    text-align: center;
    color: #424242;
    font-size: 20px;
    user-select: none;
}
</style>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
Vue.use(TooltipPlugin);
export default {
  data: function() {
    return {
    };
  },
  methods: {
        customOpen: function(args){
           if (args.target.getAttribute('data-tooltip-id')) {
           this.$refs.tooltip.close();
        } else {
            this.$refs.tooltip.open(args.target);
        }
        }
    }
}
</script>

```

{% endtab %}

## Sticky mode

With this mode set to `true`, Tooltips can be made to show up on the screen as long as the close icon is pressed. In this mode, close
 icon is attached to the Tooltip located at the top right corner. This mode can be enabled or disabled using the `isSticky` property.

{% tab template="tooltip/sticky", isDefaultActive=true %}

```html
<template>
   <div id='app'>
        <ejs-tooltip id="tooltip" content='Click close icon to close me' isSticky='true'>
            <div id="target">
                Show tooltip
            </div>
    </ejs-tooltip>
    </div>
</template>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
#target {
    background-color: #cfd8dc;
    border: 3px solid #eceff1;
    box-sizing: border-box;
    margin: 80px auto;
    padding: 20px 0;
    width: 200px;
    text-align: center;
    color: #424242;
    font-size: 20px;
    user-select: none;
}
</style>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
Vue.use(TooltipPlugin);
export default {
  data: function() {
    return {
    };
  }
}
</script>

```

{% endtab %}

## Open/Close Tooltip with delay

The Tooltips can be opened or closed after some delay by using the `openDelay` and `closeDelay` properties.

{% tab template="tooltip/open-close", isDefaultActive=true %}

```html
<template>
   <div id='app'>
        <ejs-tooltip id="tooltip" content='Tooltip with delay' openDelay='1000' closeDelay='1000'>
                <div id="target">
                    Show tooltip
                </div>
        </ejs-tooltip>
    </div>
</template>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
#target {
    background-color: #cfd8dc;
    border: 3px solid #eceff1;
    box-sizing: border-box;
    margin: 80px auto;
    padding: 20px 0;
    width: 200px;
    text-align: center;
    color: #424242;
    font-size: 20px;
    user-select: none;
}
</style>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
Vue.use(TooltipPlugin);
export default {
  data: function() {
    return {
    };
  }
}
</script>

```

{% endtab %}
