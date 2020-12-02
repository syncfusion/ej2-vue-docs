# Template and Multilevel nesting

## Template

The ContextMenu items can be customized by using the
[`Render`](../api/context-menu#beforeitemrender) event.
The item render event triggers while rendering each menu item. The event argument will be used to identify
the menu item and customize it based on the requirement. In the following sample, the menu item is rendered
with keycode for specified action in ContextMenu using the template. Here, the keycode is specified for Save as,
View page source, and Inspect in the right side corner of the menu items by adding span element
in the [`beforeItemRender`](../api/context-menu#beforeitemrender) event.

{% tab template="context-menu/default" %}

```html
<template>
<div>
<div id="target">Right click / Touch hold to open the ContextMenu</div>
<ejs-contextmenu target='#target' :items='menuItems' :beforeItemRender="onBeforeItemRender"></ejs-contextmenu>
</div>
</template>

<script>
import Vue from 'vue';
import { ContextMenuPlugin } from "@syncfusion/ej2-vue-navigations";
import { enableRipple, createElement } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ContextMenuPlugin);

export default {
    data () {
        return {
            menuItems:[
            {
                text: 'Save as...'
            },
            {
                text: 'View page source'
            },
            {
                text: 'Inspect'
            }]
        };
    },
    methods: {
        onBeforeItemRender: function(args) {
            var shortCutSpan = createElement('span');
            var text = args.item.text;
            var shortCutText = text === 'Save as...' ? 'Ctrl + S' : (text === 'View page source' ?
            'Ctrl + U'      : 'Ctrl + Shift + I');
            shortCutSpan.textContent = shortCutText;
            args.element.appendChild(shortCutSpan);
            shortCutSpan.setAttribute('class','shortcut');
        }
    }
}
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

.shortcut {
  float: right;
  font-size: 10px;
  opacity: 0.5;
  padding-left: 50px;
}

</style>
```

{% endtab %}

> To create span element, `createElement` utility function used from `ej2-base`.

## Multilevel nesting

The Multiple level nesting supports in ContextMenu. It can be achieved by mapping the
[`items`](../api/context-menu/menuItemModel#items) property inside the parent
[`menuItems`](../api/context-menu#items). In the below sample, three level nesting of ContextMenu
is provided.

{% tab template="context-menu/default" %}

```html
<template>
<div>
<div id="target">Right click / Touch hold to open the ContextMenu</div>
<ejs-contextmenu target='#target' :items='menuItems'></ejs-contextmenu>
</div>
</template>

<script>
import Vue from 'vue';
import { ContextMenuPlugin } from "@syncfusion/ej2-vue-navigations";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ContextMenuPlugin);

export default {
    data () {
        return {
            menuItems:[
            {
                text: 'Show All Bookmarks',
            },
            {
                text: 'Bookmarks Toolbar',
                items: [
                    {
                        text: 'Most Visited',
                        items: [
                        {
                            text: 'Google',
                        },
                        {
                            text: 'Gmail'
                        }]
                    },
                    {
                        text: 'Recently Added'
                    }
                ]
            }]
        };
    }
}
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
