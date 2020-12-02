# Change menu items dynamically

The items visible in the ContextMenu can be changed dynamically based on the target in which you open
the ContextMenu. To achieve this behavior, initialize ContextMenu with all items using
[`items`](../../api/context-menu#items) property and then based on the context you open hide/show
required items using [`hideItems`](../../api/context-menu#hideitems)/
[`showItems`](../../api/context-menu#showitems) method in [`beforeOpen`](../../api/context-menu#beforeopen) event.

In the following example, the datasource for Clipboard div is `Cut`, `Copy`, `Paste` and for the Editor div
is `Add`, `Edit`, `Delete` is changed on [`beforeOpen`](../../api/context-menu#beforeopen) event
using [`hideItems`](../../api/context-menu#hideitems) and [`showItems`](../../api/context-menu#showitems) method.

{% tab template="context-menu/default" %}

```html
<template>
<div>
    <div id="target">
        <div id='left' class='e-div'>Clipboard</div>
        <div id='right' class='e-div'>Editor</div>
    </div>
    <ejs-contextmenu id='cmenu' target='#target' :items='menuItems' :beforeOpen="onBeforeOpen"></ejs-contextmenu>
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
                    text: 'Cut'
                },
                {
                    text: 'Copy'
                },
                {
                    text: 'Paste'
                },
                {
                    text: 'Add'
                },
                {
                    text: 'Edit'
                },
                {
                    text: 'Delete'
                }
            ]
        };
    },
    methods: {
        onBeforeOpen: function(args) {
            var menuObj = document.getElementById("cmenu").ej2_instances[0];
            // To hide/show items on right click.
            if ((args.event.target).id === 'right') {
                menuObj.hideItems(['Cut', 'Copy', 'Paste']);
                menuObj.showItems(['Add', 'Edit', 'Delete']);
            } else if (args.event.target.id === 'left') {
                menuObj.showItems(['Cut', 'Copy', 'Paste']);
                menuObj.hideItems(['Add','Edit','Delete']);
            }
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
  user-select: none;
}

.e-div {
  width: 40%;
  border: 1px dashed;
  height: 150px;
  margin: 10px;
  text-align: center;
  line-height: 150px;
  display: inline-block;
}
</style>
```

{% endtab %}
