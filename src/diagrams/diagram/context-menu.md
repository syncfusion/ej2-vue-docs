---
title: "Context Menu"
component: "Diagram"
description: "Diagram context menu describes how to execute frequently used commands by using context menu items."
---

# Context Menu

<!-- markdownlint-disable MD010 -->

In graphical user interface (GUI), a context menu is a type of menu that appears when you perform right-click operation. Nested level of context menu items can be created.
Diagram provides some in-built context menu items and allows to define custom menu items through the [`contextMenuSettings`](../api/diagram#contextMenuSettings) property.

## Customize context menu

The [`show`](../api/diagram/contextMenuSettings#show-boolean) property helps you to enable/disable the context menu. Diagram provides some default context menu items to ease the execution of some frequently used commands.
The following code illustrates how to enable the default context menu items.

{% tab template="diagram/contextmenu/events", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :connectors='connectors' :contextMenuSettings='contextMenuSettings'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,DiagramContextMenu,Diagram } from '@syncfusion/ej2-vue-diagrams';
    Diagram.Inject(DiagramContextMenu);
    Vue.use(DiagramPlugin);

    let nodes = [{
        id: 'node1',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
        annotations: [{
            id: 'label1',
            content: 'Rectangle1',
            offset: {
                x: 0.5,
                y: 0.5
            },
            style: {
                color: 'white'
            }
        }]
    },
    {
        id: 'node2',
        width: 100,
        height: 100,
        offsetX: 300,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
        annotations: [{
            id: 'label2',
            content: 'Rectangle2',
            offset: {
                x: 0.5,
                y: 0.5
            },
            style: {
                color: 'white'
            }
        }]
    }
];

let connectors = [{
    id: 'connector1',
    sourceID: 'node1',
    targetID: 'node2',
    type: 'Straight',
    style: {
        strokeColor : '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth :  2,
        targetDecorator: {
            style: {
                fill : '#6BA5D7',
                strokeColor :   '#6BA5D7'
            }
        }
    }
}, ]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            connectors: connectors,
            contextMenuSettings: {
                show: true,
            }
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

Context menu can be defined for individual node with the desired context menu items.

* Apart from the default context menu items, define some additional context menu items. Those additional items have to be defined and added to the [`items`](../api/diagram/contextMenuSettingsModel#items) property of the context menu.

* Set text and ID for context menu item using the context menu [`text`](../api/diagram/contextMenuItemModel#text-string) and [`ID`](../api/diagram/contextMenuItemModel#id-string) properties respectively.

* Set an image for the context menu item using the context menu [url](../api/diagram/contextMenuItemModel#url) property.

* The [`iconCss`](../api/diagram/contextMenuItemModel#iconCss-string) property defines the class/multiple classes separated by a space for the menu item that is used to include an icon. Menu item can include font icon and sprite image.

* The [`target`](../api/diagram/contextMenuItemModel#target-string) property used to set the target to show the menu item.

* The [`separator`](../api/diagram/contextMenuItemModel#separator-boolean) property defines the horizontal lines that are used to separate the menu items. You cannot select the separators. You can enable separators to group the menu items using the separator property.

The following code example illustrates how to add custom context menu items.

{% tab template="diagram/contextmenu/default", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :connectors='connectors' :contextMenuSettings='contextMenuSettings'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,DiagramContextMenu,Diagram,DiagramBeforeMenuOpenEventArgs } from '@syncfusion/ej2-vue-diagrams';
    Diagram.Inject(DiagramContextMenu);
    Vue.use(DiagramPlugin);

    let nodes = [{
    id: 'node1',
    width: 100,
    height: 100,
    offsetX: 100,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
    annotations: [{
        id: 'label1',
        content: 'Rectangle1',
        offset: {
            x: 0.5,
            y: 0.5
        },
        style: {
            color: 'white'
        }
    }]
},
    {
    id: 'node2',
    width: 100,
    height: 100,
    offsetX: 300,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
    annotations: [{
        id: 'label2',
        content: 'Rectangle2',
        offset: {
            x: 0.5,
            y: 0.5
        },
        style: {
            color: 'white'
        }
    }]
}
];

let connectors = [{
    id: 'connector1',
    sourceID: 'node1',
    targetID: 'node2',
    type: 'Straight',
    style: {
        strokeColor : '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth :  2,
        targetDecorator: {
            style: {
                fill : '#6BA5D7',
                strokeColor :   '#6BA5D7'
            }
        }
    }
} ]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            connectors: connectors,
            contextMenuSettings: {
        //Enables the context menu
        show: true,
        // Defines the custom context menu items
        items: [{
                // Text to be displayed
                text: 'Save',
                //Sets the id for the item
                id: 'save',
                //ContextMenu can be visible based on the target in which you open the ContextMenu.
                target: '.e-elementcontent',
                // Sets the css icons for the item
                iconCss: 'e-save'
            },
            {
                text: 'Load',
                id: 'load',
                target: '.e-elementcontent',
                iconCss: 'e-load'
            },
            {
                text: 'Clear',
                id: 'clear',
                target: '.e-elementcontent',
                iconCss: 'e-clear'
            }
        ],
        // Hides the default context menu items
        showCustomMenuOnly: false,
    }
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

To display the custom context menu items alone, set  the [`showCustomMenuOnly`](../api/diagram/contextMenuSettingsModel#showCustomMenuOnly) property to true.

## Template Support for Context menu

* Diagram provides template support for context menu. The context menu items can be customized by using the `contextMenuBeforeItemRender` event. The contextMenuBeforeItemRender event triggers while rendering each menu item.

* In the following sample, the menu item is rendered with key code for specified action in Context Menu using the template. Here, the key code is specified for the cut and copy at right corner of the menu items by adding a span element in the `contextMenuBeforeItemRender` event.

{% tab template= "diagram/contextmenu/menutemplate", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :connectors='connectors' :contextMenuSettings='contextMenuSettings'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,DiagramContextMenu,Diagram ,
    MenuEventArgs,} from '@syncfusion/ej2-vue-diagrams';
    Diagram.Inject(DiagramContextMenu);
    Vue.use(DiagramPlugin);

    let nodes = [{
    id: 'node1',
    width: 100,
    height: 100,
    offsetX: 100,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
    annotations: [{
        id: 'label1',
        content: 'Rectangle1',
        offset: {
            x: 0.5,
            y: 0.5
        },
        style: {
            color: 'white'
        }
    }]
},
    {
    id: 'node2',
    width: 100,
    height: 100,
    offsetX: 300,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
    annotations: [{
        id: 'label2',
        content: 'Rectangle2',
        offset: {
            x: 0.5,
            y: 0.5
        },
        style: {
            color: 'white'
        }
    }]
}
];

let connectors = [{
    id: 'connector1',
    sourceID: 'node1',
    targetID: 'node2',
    type: 'Straight',
    style: {
        strokeColor : '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth :  2,
        targetDecorator: {
            style: {
                fill : '#6BA5D7',
                strokeColor :   '#6BA5D7'
            }
        }
    }
} ]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            connectors: connectors,
            contextMenuSettings: {
              //Enables the context menu
              show: true,
              items: [{
                 text: 'Cut', id: 'Cut', target: '.e-diagramcontent',
                 iconCss: 'e-Cut'
              },
              {
                 text: 'Copy', id: 'Copy', target: '.e-diagramcontent',
                 iconCss: 'e-Copy'
              }],
              // Hides the default context menu items
             showCustomMenuOnly: true,
            contextMenuBeforeItemRender: function (args: MenuEventArgs) {
                // To render template in li.
                let shortCutSpan: HTMLElement = createElement('span');
                let text: string = args.item.text;
                let shortCutText: string = text === 'Cut' ? 'Ctrl + S' : (text === 'Copy' ?
                    'Ctrl + U' : 'Ctrl + Shift + I');
                shortCutSpan.textContent = shortCutText;
                args.element.appendChild(shortCutSpan);
                shortCutSpan.setAttribute('class', 'shortcut');
             }
           },
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Context menu events

You would be notified with events, when you try to open the context menu items [`contextMenuOpen`](../api/diagram/diagramBeforeMenuOpenEventArgs#DiagramBeforeMenuOpenEventArgs) and when you click the menu items `contextMenuClick`
The following code example illustrates how to define those events.

{% tab template="diagram/contextmenu/custom", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram" ref="diagram"  :width='width' :height='height' :nodes='nodes' :connectors='connectors' :contextMenuSettings='contextMenuSettings':contextMenuOpen="contextMenuOpen" :contextMenuClick="contextMenuClick" ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,DiagramContextMenu,Diagram ,DiagramBeforeMenuOpenEventArgs,
    MenuEventArgs,} from '@syncfusion/ej2-vue-diagrams';
    Diagram.Inject(DiagramContextMenu);
    Vue.use(DiagramPlugin);

    let nodes = [{
    id: 'node1',
    width: 100,
    height: 100,
    offsetX: 100,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
    annotations: [{
        id: 'label1',
        content: 'Rectangle1',
        offset: {
            x: 0.5,
            y: 0.5
        },
        style: {
            color: 'white'
        }
    }]
},
    {
    id: 'node2',
    width: 100,
    height: 100,
    offsetX: 300,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
    annotations: [{
        id: 'label2',
        content: 'Rectangle2',
        offset: {
            x: 0.5,
            y: 0.5
        },
        style: {
            color: 'white'
        }
    }]
}
];

let connectors = [{
    id: 'connector1',
    sourceID: 'node1',
    targetID: 'node2',
    type: 'Straight',
    style: {
        strokeColor : '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth :  2,
        targetDecorator: {
            style: {
                fill : '#6BA5D7',
                strokeColor :   '#6BA5D7'
            }
        }
    }
} ]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            connectors: connectors,
            contextMenuSettings: {
        //Enables the context menu
                show: true,
               items: [{
                 text: 'delete',
                 id: 'delete',
               }],
        // Hides the default context menu items
        showCustomMenuOnly: false,
    },
    contextMenuOpen: (args) => {
        var diagram = this.$refs.diagram.ej2Instances;
            //do your custom action here.
            for (let item of args.items) {
                if (item.text === 'delete') {
                    if (!diagram.selectedItems.nodes.length && !diagram.selectedItems.connectors.length) {
                        args.hiddenItems.push(item.text);
                    }
                }
            }
        },
        contextMenuClick: (args) => {
            var diagram = this.$refs.diagram.ej2Instances;
            //do your custom action here.
            if (args.item.id === 'delete') {
                if ((diagram.selectedItems.nodes.length + diagram.selectedItems.connectors.length) > 0) {
                    diagram.cut();
                }
            }
        }
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}