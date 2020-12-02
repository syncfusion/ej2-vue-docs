---
title: "Tooltip Position"
component: "Tooltip"
description: "Vue tooltip can be displayed in 12 (twelve) different positions of target element that automatically collide based on view port."
---

# Tooltip Positioning

Tooltips can be attached to 12 static locations around the target.
On initializing the Tooltip, you can set the position property with any one of the following values:

* `TopLeft`
* `TopCenter`
* `TopRight`
* `BottomLeft`
* `BottomCenter`
* `BottomRight`
* `LeftTop`
* `LeftCenter`
* `LeftBottom`
* `RightTop`
* `RightCenter`
* `RightBottom`

> By default, Tooltip is placed at the `TopCenter` of the target element.

{% tab template="tooltip/position/default", isDefaultActive=true %}

```html
<template>
   <div id='app'>
        <ejs-tooltip ref="tooltip" content="Tooltip content" position='TopCenter' target="#tooltip">
            <div id='container'>
                <ejs-button id="tooltip">Show tooltip</ejs-button>
                <div class="ddl">
                    <select id="positions" ref="positions" class="form-control" style="width:150px" v-on:click='onclick' v-on:change='onchange'>
                        <option value="TopLeft">Top Left</option>
                        <option value="TopCenter" selected>Top Center</option>
                        <option value="TopRight">Top Right</option>
                        <option value="BottomLeft">Bottom Left</option>
                        <option value="BottomCenter">Bottom Center</option>
                        <option value="BottomRight">Bottom Right</option>
                        <option value="LeftTop">Left Top</option>
                        <option value="LeftCenter">Left Center</option>
                        <option value="LeftBottom">Left Bottom</option>
                        <option value="RightTop">Right Top</option>
                        <option value="RightCenter">Right Center</option>
                        <option value="RightBottom">Right Bottom</option>
                    </select>
                </div>
            </div>
        </ejs-tooltip>
    </div>
</template>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
Vue.use(TooltipPlugin);
Vue.use(ButtonPlugin);

export default {
    data() {
    return {
    };
    },
    methods: {
        onclick: function(){
            this.$refs.tooltip.close();
        },
        onchange: function(){
            this.$refs.tooltip.position = this.$refs.positions.value;
            this.$refs.tooltip.dataBind();
        }
    }
}
</script>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
#container {
    display: inline-block;
    position: relative;
    left: 50%;
    margin-top: 100px;
    transform: translateX(-50%);
    height: 200px;
}

#tooltip {
    display: inline-block;
    margin: 30px 130px 30px 50px;
}

.ddl {
    display: inline-block;
    margin: 0 30px;
}

</style>

```

{% endtab %}

## Tip pointer positioning

The Tooltip pointer can be attached or detached from the Tooltip by using the `showTipPointer` property.
Pointer positions can be adjusted using the `tipPointerPosition` property that can be assigned to one of the following values:

* `Auto`
* `Start`
* `Middle`
* `End`

The following code example illustrates how to set the pointer to the start position of the Tooltip.

{% tab template="tooltip/position/tip-position", isDefaultActive=true %}

```html
<template>
   <div id='app'>
        <ejs-tooltip content="Tooltip content" tipPointerPosition="Start" target="#target">
            <ejs-button id="target">Show tooltip</ejs-button>
        </ejs-tooltip>
    </div>
</template>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
Vue.use(TooltipPlugin);
Vue.use(ButtonPlugin);

export default {
    data() {
    return {
    };
    }
}
</script>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
#target {
  position: relative;
  left: 50%;
  margin-top: 100px;
  transform: translateX(-50%)
}
</style>

```

{% endtab %}

By default, tip pointers are auto adjusted so that the arrow does not point outside the target element.

## Dynamic positioning

The Tooltip and its tip pointer can be positioned dynamically based on the target's location. This can be achieved by using the `refresh`
 method, which auto adjusts the Tooltip over the target.

{% tab template="tooltip/position/dynamic-position", isDefaultActive=true %}

```html
<template>
  <div id='app'>
        <ejs-tooltip id="targetContainer" ref="tooltip" content='Drag me !!!' target='#demoSmart' :animation='tooltipAnimation'>
            <div id="demoSmart" ref="demoSmart"></div>
       </ejs-tooltip>
    </div>
</template>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
import { Draggable } from '@syncfusion/ej2-base';
Vue.use(TooltipPlugin);

export default {
    data() {
        return {
            tooltipAnimation: {
                open: { effect: 'None' },
                close: { effect: 'None' }
            }
        };
    },
    mounted: function (args) {
        var ele = this.$refs.demoSmart;
        var drag = new Draggable(ele, {
            clone : false,
            dragArea: '#targetContainer',
            drag: (args) => {
                if (args.element.getAttribute('data-tooltip-id') === null) {
                    this.$refs.tooltip.open(args.element);
                } else {
                    this.$refs.tooltip.refresh(args.element);
                }
            },
            dragStart: (args) => {
                if (args.element.getAttribute('data-tooltip-id') === null) {
                    this.$refs.tooltip.open(args.element);
                }
            },
            dragStop: (args) => {
                this.$refs.tooltip.close();
            }
        });
    }
}
</script>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  #app {
    height: 96%;
    position: absolute;
    width: 98%;
  }
#targetContainer {
    width: 100%;
    height: 100%;
    }

#demoSmart {
    background: rebeccapurple;
    height: 50px;
    left: 35%;
    position: absolute;
    top: 35%;
    width: 50px;
}
</style>

```

{% endtab %}

## Mouse trailing

Tooltips can be positioned relative to the mouse pointer. This behavior can be enabled or disabled by using the `mouseTrail` property.
 By default, it is set to `false`.

{% tab template="tooltip/position/mouse-trail", isDefaultActive=true %}

```html
<template>
  <div id='app'>
        <ejs-tooltip  mouseTrail='true' content='Tooltip content' target="#target" :showTipPointer=false>
          <div id="target">Show tooltip</div>
        </ejs-tooltip>
    </div>
</template>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
Vue.use(TooltipPlugin);

export default {
    data() {
        return {};
    }
}
</script>
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
}
</style>

```

{% endtab %}

> When mouse trailing option is enabled, the tip pointer position gets auto adjusted based on the target, and
> other position values like start, end, and middle are not applied (to prevent the pointer from moving out of target).

## Setting offset values

Offset values are set to specify the distance between the target and tooltip element.
`offsetX` and `offsetY` properties are used to specify the offset left and top values.

* `offsetX` specifies the distance between the target and Tooltip element in X axis.
* `offsetY` specifies the distance between the target and Tooltip element in Y axis.

The following code example illustrates how to set offset values.

{% tab template="tooltip/position/offset-value", isDefaultActive=true %}

```html
<template>
  <div id='app'>
        <ejs-tooltip mouseTrail='true' content='Tooltip content' :offsetX='xvalue' :offsetY='yvalue' :showTipPointer=false target="#target">
          <div id="target">Show tooltip</div>
        </ejs-tooltip>
    </div>
</template>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
Vue.use(TooltipPlugin);

export default {
    data() {
    return {
        xvalue: 30,
        yvalue: 30,
        tip: false
    };
    }
}
</script>
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
}
</style>

```

{% endtab %}

> By default, collision is handled automatically and therefore when collision is detected the Tooltip fits horizontally and flips vertically.
