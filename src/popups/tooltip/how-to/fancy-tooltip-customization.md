# Fancy Tooltip customization

The arrow of the tooltip can be customized as needed by customizing CSS in the sample-side.
The EJ2 tooltip component is achieved through CSS3 format and positioned the tip arrow according to the tooltip positions like `TopCenter`, `BottomLeft`, `RightTop`, and more.

Here, the tip arrow is customized as Curved tooltip and Bubble tooltip.

## Curved tip

The content for the tip pointer arrow has been added. To customize the curved tip arrow, override the following CSS class of tip arrow.

```typescript

      .e-arrow-tip-outer.e-tip-bottom,
      .e-arrow-tip-outer.e-tip-top {
           border-left: none !important;
           border-right: none !important;
           border-top: none !important;
      }
      .e-arrow-tip.e-tip-top {
           transform: rotate(170deg);
      }

```

## Bubble tip

The two `divs`(inner div and outer div) have been added to achieve the bubble tip arrow. To customize the bubble tip arrow, override the following CSS class of tip arrow.

```typescript

    .e-arrow-tip-outer.e-tip-bottom, .e-arrow-tip-outer.e-tip-top
      {
         border-radius: 50px;
         height: 10px;
         width: 10px;
      }

      .e-arrow-tip-inner.e-tip-bottom, .e-arrow-tip-inner.e-tip-top
        {
         border-radius: 50px;
         height: 10px;
         width: 10px;
        }
```

These tip arrow customizations have been achieved through CSS changes in the sample level. The tooltip position can be changed by using the radio button click event.

The arrow tip pointer can also be disabled by using the [`showTipPointer`](https://ej2.syncfusion.com/vue/documentation/api/tooltip/#showtippointer) property in a tooltip.

{% tab template="tooltip/customize", isDefaultActive=true %}

```html
<template>
   <div id='app'>
        <ejs-tooltip ref='tooltip_1' cssClass="curvetips e-tooltip-css" content="Tooltip arrow customized" target="#target">
            <ejs-tooltip mouseTrail=true :showTipPointer=false content='Disabled tooltip pointer' target='#tooltip' cssClass='pointertip e-tooltip-css'>
                <ejs-tooltip position="TopRight" content='Tooltip arrow customized as balloon tip' target='#bubbletip' cssClass='bubbletip e-tooltip-css' ref="tooltip_2">
                    <div id='container'>
                        <div id="customization" class="customTipContainer">
                            <ejs-button id="target">
                                Customized Tip Arrow
                            </ejs-button>
                            <div id="positions">
                                <ul>
                                    <li>
                                        <ejs-radiobutton id='element1' label='TopCenter' name='default' value='TopCenter' checked=true  v-on:change='onChange'/>
                                    </li>
                                    <li>
                                        <ejs-radiobutton id='element2' label='BottomLeft' name='default' value='BottomLeft' v-on:change='onChange'/>
                                    </li>
                                </ul>
                            </div>
                        </div>
                        <div id="balloon" class="customTipContainer">
                            <ejs-button id="bubbletip">
                                Bubble Tip Arrow
                            </ejs-button>
                            <div id="btn">
                                <ul>
                                    <li>
                                        <ejs-radiobutton id='radio1' label='BottomLeft' name='position' value='BottomLeft' v-on:change='onChanged'/>
                                    </li>
                                    <li>
                                        <ejs-radiobutton id='radio2' label='TopRight' name='position' value='TopRight'  checked=true v-on:change='onChanged'/>
                                    </li>
                                </ul>
                            </div>
                        </div>
                        <div id="disabledContainer" class="customTipContainer">
                            <ejs-button id="tooltip">
                                Disabled Tip Arrow
                            </ejs-button>
                        </div>
                    </div>
                </ejs-tooltip>
            </ejs-tooltip>
        </ejs-tooltip>
    </div>
</template>
<script>
import Vue from 'vue';
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
Vue.use(ButtonPlugin);
import { TooltipPlugin } from '@syncfusion/ej2-vue-popups';
Vue.use(TooltipPlugin);
import { RadioButtonPlugin } from "@syncfusion/ej2-vue-buttons";
Vue.use(RadioButtonPlugin);

export default {
  data: function() {
    return {
    };
  },
  methods: {
        onChange(args) {
            this.$refs.tooltip_1.position = args.value;
            this.$refs.tooltip_1.dataBind();
        },
        onChanged(args) {
            this.$refs.tooltip_2.position = args.value;
            if(this.$refs.tooltip_2.position == 'BottomLeft'){
             this.$refs.tooltip_2.offsetY = -30;
            } else {
             this.$refs.tooltip_2.offsetY = 0;
            }
             this.$refs.tooltip_2.dataBind();
        }

  }
}
</script>

<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
#bubbletip {
  border-color: #d2a679;
}

#target {
  border-color: #e86238;
}

li {
  list-style: none;
}

.e-radio-wrapper {
  margin-top: 18px;
}

#target,
#bubbletip,
#tooltip {
  box-sizing: border-box;
  padding: 20px;
  width: 200px;
  text-align: center;
  top: -17px;
  margin-bottom: 40px;
}

/* csslint ignore:start */

@font-face {
  font-family: "tip";
  src: url("https://ej2.syncfusion.com/products/typescript/tooltip/customization/Fonts/tip.tff") format("truetype"), url("https://ej2.syncfusion.com/products/typescript/tooltip/customization/Fonts/tip.woff") format("woff"), url("https://ej2.syncfusion.com/products/typescript/tooltip/customization/Fonts/tip.eot") format("eot"), url("https://ej2.syncfusion.com/products/typescript/tooltip/customization/Fonts/tip.svg?#tip") format("svg");
  font-weight: normal;
  font-style: normal;
}

/* csslint ignore:end */

/* csslint ignore:start */

#container {
  width: 100%;
}

.customTipContainer {
  width: 400px;
  position: relative;
  left: 50%;
  transform: translateX(-50%);
  top: 50px;
}

#disabledContainer {
  margin-top: 25px;
}

.pointertip.e-tooltip-wrap .e-tip-content,
.curvetips.e-tooltip-wrap .e-tip-content {
  color: white;
}

.pointertip.e-tooltip-wrap.e-popup {
  background-color: #80180d;
  border: 3px solid #ff9999;
}

.curvetips .e-arrow-tip.e-tip-top {
  margin-left: -20px;
  top: -16px;
  transform: rotate(177deg);
  left: 50px;
}

.curvetips.e-tooltip-wrap {
  padding: 17px;
  border-radius: 5px;
}

.curvetips.e-tooltip-wrap .e-arrow-tip-outer.e-tip-bottom:before,
.curvetips.e-tooltip-wrap .e-arrow-tip-outer.e-tip-top:before {
  font-family: "tip" !important;
  speak-as: none;
  font-size: 21px;
  font-style: normal;
  font-weight: normal;
  font-variant: normal;
  text-transform: none;
  line-height: 1;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\e700";
  color: #e86238;
}

.curvetips.e-tooltip-wrap.e-popup {
  background: #e86238;
  border: none;
}

.curvetips.e-tooltip-wrap .e-arrow-tip-outer.e-tip-bottom,
.curvetips.e-tooltip-wrap .e-arrow-tip-outer.e-tip-top {
  border-left: none;
  border-right: none;
  border-top: none;
}

.curvetips.e-tooltip-wrap .e-arrow-tip-inner.e-tip-bottom:before,
.curvetips.e-tooltip-wrap .e-arrow-tip-inner.e-tip-top:before {
  content: none;
}

.curvetips.e-tooltip-wrap .e-arrow-tip-outer.e-tip-bottom,
.curvetips.e-tooltip-wrap .e-arrow-tip-outer.e-tip-top {
  top: -1px;
}

.curvetips.e-tooltip-wrap .e-arrow-tip.e-tip-bottom,
.curvetips.e-tooltip-wrap .e-arrow-tip.e-tip-top {
  position: absolute;
  height: 18px;
  width: 28px;
}

#positions {
  display: inline-block;
}

#btn {
  display: inline-block;
}

#target .e-tip-content {
  padding: 0px;
}

.bubbletip.e-tooltip-wrap {
  padding: 8px;
}

.bubbletip.e-tooltip-wrap .e-tip-content {
  border-radius: 50%;
  text-align: center;
  color: white;
}

.bubbletip.e-tooltip-wrap .e-arrow-tip.e-tip-bottom {
  height: 40px;
  width: 50px;
}

.bubbletip.e-tooltip-wrap .e-arrow-tip.e-tip-top {
  height: 40px;
  width: 40px;
}

.bubbletip.e-tooltip-wrap .e-arrow-tip.e-tip-left {
  height: 12px;
  width: 20px;
}

.bubbletip.e-tooltip-wrap .e-arrow-tip.e-tip-right {
  height: 12px;
  width: 20px;
}

.bubbletip.e-tooltip-wrap.e-popup {
  border: 5px solid #dfccad;
  background-color: #7b5e32;
}

.bubbletip.e-tooltip-wrap .e-arrow-tip-outer.e-tip-bottom {
  height: 10px;
  width: 10px;
  border: 1px solid #dfccad;
  background-color: #7b5e32;
  border-radius: 50px;
  margin-top: 20px;
  margin-right: 20px;
}

.e-arrow-tip.e-tip-top {
  margin-left: 60px;
}

.bubbletip.e-tooltip-wrap .e-arrow-tip-outer.e-tip-top {
  border: 1px solid #dfccad;
  border-radius: 50px;
  background-color: #7b5e32;
  width: 10px;
  height: 10px;
  margin-left: 20px;
}

.bubbletip.e-tooltip-wrap .e-arrow-tip-outer.e-tip-left {
  border-bottom: 6px solid transparent;
  border-right: 20px solid #dfccad;
  border-top: 6px solid transparent;
}

.bubbletip.e-tooltip-wrap .e-arrow-tip-outer.e-tip-right {
  border-bottom: 6px solid transparent;
  border-left: 20px solid #dfccad;
  border-top: 6px solid transparent;
}

.bubbletip.e-tooltip-wrap .e-arrow-tip-inner.e-tip-bottom {
  margin-top: -2px;
  margin-left: 8px;
  content: none;
  top: 1px !important;
  border: 2px solid #dfccad;
  width: 20px;
  height: 20px;
  border-radius: 50px;
  background-color: #7b5e32;
}

.bubbletip .e-arrow-tip.e-tip-top {
  left: 44px !important;
  top: -19px !important;
}

.bubbletip .e-arrow-tip.e-tip-bottom {
  top: 88.9% !important;
  left: 4px !important;
}

.bubbletip.e-tooltip-wrap .e-arrow-tip-inner.e-tip-top {
  top: 10px !important;
  border: 2px solid #dfccad;
  width: 20px;
  height: 20px;
  border-radius: 50px;
  background-color: #7b5e32;
}

.bubbletip.e-tooltip-wrap .e-arrow-tip-inner.e-tip-top:before {
  content: None;
}

.bubbletip.e-tooltip-wrap .e-tip-content {
  border-radius: inherit;
}

.bubbletip.e-tooltip-wrap.bubbletip {
  width: 150px !important;
  border-radius: 50%;
}

/* csslint ignore:end */
</style>

```

{% endtab %}
