# Open and close ContextMenu

Open and close the ContextMenu manually whenever required by using the open and close methods.

Install Syncfusion `Button` packages using below command.

```bash
npm install @syncfusion/ej2-vue-buttons --save
```

In the following sample, the ContextMenu is opened using the
[`open`](../../api/context-menu#open) method at the specified position with `X` and `Y` coordinates
and to close the ContextMenu, [`close`](../../api/context-menu#close) method is called
internally on ContextMenu item click or document click.

{% tab template="context-menu/default" %}

```html
<template>
<div>
<ejs-contextmenu id='cmenu' :items='menuItems'></ejs-contextmenu>
<ejs-button v-on:click.native='btnClick'>Open ContextMenu</ejs-button>
</div>
</template>

<script>
import Vue from 'vue';
import { ContextMenuPlugin } from "@syncfusion/ej2-vue-navigations";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ContextMenuPlugin);
Vue.use(ButtonPlugin);
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
                }
            ]
        };
    },
    methods: {
        btnClick: function(event) {
            document.getElementById('cmenu').ej2_instances[0].open(40, 20);
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
</style>
```

{% endtab %}
