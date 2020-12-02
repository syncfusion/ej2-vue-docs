# Template

## Show table in sub ContextMenu

Menu items of the ContextMenu can be customized according to the requirement. The section explains about how to customize table template
in sub menu item.

This can be achieved by appending table layout while `li` rendering by using [`beforeItemRender`](../../api/context-menu/#beforeitemrender) event.

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
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ContextMenuPlugin);

export default {
    data () {
        return {
            menuItems:[
                {
                    text: 'Cut',
                    iconCss: 'e-cm-icons e-cut'
                },
                {
                    text: 'Copy',
                    iconCss: 'e-icons e-copy'
                },
                {
                    text: 'Paste',
                    iconCss: 'e-cm-icons e-paste'
                },
                {
                    separator: true
                },
                {
                    text: 'Link',
                    iconCss: 'e-icons e-link'
                },
                {
                    text: 'Table',
                    iconCss: 'e-icons e-table',
                    items: [
                        {
                        id: 'table'
                        }
                    ]
                }]
        };
    },
    methods: {
        onBeforeItemRender: function(args) {
            // To create header element.
            var header = document.createElement('h4');
            header.textContent = 'Insert Table';

            // To create table with five rows and six columns.
            var table = document.createElement('table');
            for (var i = 0; i < 5; i++) {
                var row = document.createElement('tr');
                table.appendChild(row);
                for (var j = 0; j < 6; j++) {
                    var col = document.createElement('td');
                    row.appendChild(col);
                    col.setAttribute('class', 'e-border');
                }
            }
            // To append table on `li` rendering.
            if (args.item.id === 'table') {
                args.element.classList.add('bg-transparent');
                args.element.appendChild(header);
                args.element.appendChild(table);
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

.list {
  display: none;
}

.e-border {
  border: 1px solid rgba(0, 0, 0, 0.87);
  padding: 8px;
}

#target {
  border: 1px dashed;
  height: 150px;
  padding: 10px;
  position: relative;
  text-align: justify;
  color: gray;
  user-select: none;
}

@font-face {
    font-family: 'ddb-icons';
    src:
    url(data:application/x-font-ttf;charset=utf-8;base64,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) format('truetype');
    font-weight: normal;
    font-style: normal;
}

.e-cm-icons {
    font-family: 'ddb-icons' !important;
    speak: none;
    font-size: 55px;
    font-style: normal;
    font-weight: normal;
    font-variant: normal;
    text-transform: none;
    line-height: 1;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

.e-cut::before {
  content: '\e700';
}

.e-copy::before {
  content: '\e70a';
}

.e-paste::before {
  content: '\e701';
}

.e-link::before {
  content: '\e290';
}

.e-table::before {
  content: '\e705';
}

.e-contextmenu-wrapper ul .e-menu-item.bg-transparent {
    background-color: transparent;
    line-height: normal;
    height: auto;
}

h4 {
    text-align: center;
    margin-top: 5px;
    margin-bottom: 5px;
}
</style>
```

{% endtab %}

## Show UI components in ContextMenu

UI components can also be placed inside the each `li` element of ContextMenu.

In the following example, CheckBox component is placed inside each `li` element and this can be achieved by creating
CheckBox component in [`beforeItemRender`](../../api/context-menu/#beforeitemrender) event and appending it into the `li` element.

{% tab template="context-menu/default" %}

```html
<template>
<div>
<div id="target">Right click / Touch hold to open the ContextMenu</div>
<ejs-contextmenu target='#target' :items='menuItems' :beforeItemRender='itemRender' :beforeClose='beforeClose'></ejs-contextmenu>

</div>
</template>

<script>
import Vue from 'vue';
import { ContextMenuPlugin } from "@syncfusion/ej2-vue-navigations";
import { enableRipple, closest, createElement } from '@syncfusion/ej2-base';
import { createCheckBox } from '@syncfusion/ej2-buttons';

enableRipple(true);
Vue.use(ContextMenuPlugin);

export default {
    data () {
        return {
            menuItems:[
                { text: 'Option 1' },
                { text: 'Option 2' },
                { text: 'Option 3' }
            ]
        };
    },
    methods: {
        itemRender: function(args ) {
            var check = createCheckBox(createElement, false, {
                label: args.item.text,
                checked: (args.item.text == 'Option 2') ? true : false
            });
            args.element.innerHTML = '';
            args.element.appendChild(check);
        },
        beforeClose: function(args ) {
            if (args.event.target.closest('.e-menu-item')) {
                args.cancel = true;
                var selectedElem, i, checkbox, ele, frame;
                selectedElem = args.element.querySelectorAll('.e-selected');
                for(i = 0; i < selectedElem.length; i++){
                    ele = selectedElem[i];
                    ele.classList.remove('e-selected');
                }
                checkbox = closest(args.event.target, '.e-checkbox-wrapper');
                frame = checkbox && checkbox.querySelector('.e-frame');
                if (checkbox && frame.classList.contains('e-check')) {
                    frame.classList.remove('e-check');
                } else if (checkbox) {
                    frame.classList.add('e-check');
                }
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

.list {
  display: none;
}

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
