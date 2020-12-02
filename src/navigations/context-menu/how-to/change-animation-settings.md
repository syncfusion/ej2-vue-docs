# Change animation settings

To change the animation of the ContextMenu, [`animationSettings`](https://ej2.syncfusion.com/vue/documentation/api/context-menu/menuAnimationSettingsModel/) property
is used. The supported effects for ContextMenu are,

| Effect | Functionality |
| ------------ | ---------------------- |
| None | Specifies the sub menu transform with no animation effect. |
| SlideDown | Specifies the sub menu transform with slide down effect. |
| ZoomIn | Specifies the sub menu transform with zoom in effect. |
| FadeIn | Specifies the sub menu transform with fade in effect. |

The following sample illustrates how to open ContextMenu with `FadeIn` effect with the `duration` of `800ms`.

{% tab template="context-menu/default" %}

```html
<template>
<div>
<div id="target">Right click / Touch hold to open the ContextMenu</div>
<ejs-contextmenu target='#target' :items='menuItems' :animationSettings='animationSettings'></ejs-contextmenu>
</div>
</template>

<script>
import Vue from 'vue';
import { ContextMenuPlugin } from "@syncfusion/ej2-vue-navigations";
import { MenuEventArgs } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ContextMenuPlugin);

export default {
    data () {
        return {
            menuItems:[
                {
                    text: 'Show All Bookmarks'
                },
                {
                    text: 'Bookmarks Toolbar',
                    items: [
                        {
                            text: 'Most Visited',
                            items:[
                                {
                                    text: 'Gmail'
                                },
                                {
                                    text: 'Google'
                                }
                            ]
                        },
                        {
                            text: 'Recently Added'
                        }
                    ]
                }],
                 animationSettings: { effect: 'FadeIn', duration: 800 }
                }
        }
    };
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";

#target {
  border: 1px dashed;
  height: 150px;
  padding: 10px;
  position: relative;
  text-align: justify;
  color: gray;
  user-select: none;
}
</style>
```

{% endtab %}
