---
title: "Tooltip"
component: "Diagram"
description: "The tooltip is a message that is displayed when mouse hovers over an element."
---

# Tooltip

<!-- markdownlint-disable MD010 -->

In Graphical User Interface (GUI), the tooltip is a message that is displayed when mouse hovers over an element. The diagram provides tooltip support while dragging, resizing, rotating a node, and when the mouse hovers any diagram element.

## Default tooltip

By default, diagram displays a tooltip to provide the size, position, and angle related information while dragging, resizing, and rotating. The following images illustrate how the diagram displays the node information during an interaction.

| Drag | Resize | Rotate |
|---|---|---|
| ![ToolTip During Drag](images/Tooltip_img1.png) | ![ToolTip During Resize](images/Tooltip_img2.png) | ![ToolTip During Rotate](images/Tooltip_img3.png) |

## Common tooltip for all nodes and connectors

The diagram provides support to show tooltip when the mouse hovers over any node/connector.
To show tooltip on mouse over, the [`tooltip`](../api/diagram#tooltip) property of diagram model needs to be set with the tooltip [`content`](../api/diagram/diagramTooltip/#content) and [`position`](../api/diagram/diagramTooltip/#position) as shown in the following example.

{% tab template="diagram/tooltip/tooltip", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes'
        :tooltip='tooltip'  :constraints='constraints'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,DiagramConstraints } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [{
    id: "node1",
    height: 60,
    offsetX: 300,
    offsetY: 80,
    annotations: [{
        content: "start"
    }]
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            constraints: DiagramConstraints.Default | DiagramConstraints.Tooltip,
            nodes: nodes,
            tooltip: {
                content: 'Nodes',
                position: 'TopLeft'
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

### Disable tooltip at runtime

The tooltip on mouse over can be disabled by assigning the [`tooltip`](../api/diagram#tooltip) property as `null`. The following code example illustrates how to disable the mouse over tooltip at runtime.

```javascript
 export default {
        name: 'app'
        data () {
            return {
                width: "100%",
                height: "350px",
                tooltip: null
            }
        }
    }
```

## Tooltip for a specific node/connector

The tooltip can be customized for each node and connector. Remove the **InheritTooltip** option from the [`constraints`](../api/diagram#constraints) of that node/connector. The following code example illustrates how to customize the tooltip for individual elements.

{% tab template="diagram/tooltip/tooltip", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes'
        :tooltip='tooltip'  :constraints='constraints'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,DiagramConstraints } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

let nodes = [{
    id: "node1",
    height: 60,
    offsetX: 300,
    offsetY: 80,
    annotations: [{
        content: "start"
    }]
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            constraints: DiagramConstraints.Default | DiagramConstraints.Tooltip,
            nodes: nodes,
            //Defines mouse over tooltip for a node
            tooltip: {
                //Sets the content of the Tooltip
                content: 'Node1',
                //Sets the position of the Tooltip
                position: 'BottomRight',
                //Sets the tooltip position relative to the node
                relativeMode: 'Object'
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

## Tooltip template content

Any text or image can be added to the tooltip, by default. To customize the tooltip layout or to create your own visualized element on the tooltip, template can be used.

The following code example illustrates how to add formatted HTML content to the tooltip.

{% tab template="diagram/tooltip/tooltip", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes'
        :tooltip='tooltip'  :constraints='constraints'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,DiagramConstraints } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [{
    id: "node1",
    height: 60,
    offsetX: 300,
    offsetY: 80,
    annotations: [{
        content: "start"
    }]
}]

function getContent(): HTMLElement {
    let tooltipContent: HTMLElement = document.createElement('div');
    tooltipContent.innerHTML = '<div style="background-color: #f4f4f4; color: black; border-width:1px;border-style: solid;border-color: #d3d3d3; border-radius: 8px;white-space: nowrap;"> <span style="margin: 10px;"> Tooltip !!! </span> </div>';
    return tooltipContent;
}
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            constraints: DiagramConstraints.Default | DiagramConstraints.Tooltip,
            nodes: nodes,
            //Defines mouse over tooltip for a node
            tooltip: {
                //Sets the content of the Tooltip
                content: getContent(),
                //Sets the position of the Tooltip
                position: 'TopLeft',
                //Sets the tooltip position relative to the node
                relativeMode: 'Object'
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

## Tooltip alignments

### Tooltip relative to object

The diagram provides support to show tooltip around the node/connector that is hovered by the mouse. The tooltip can be aligned by using the [`position`](../api/diagram/diagramTooltip#position) property of the tooltip.
The [`relativeMode`](../api/diagram/diagramTooltip#relativemode) property of the tooltip defines whether the tooltip has to be displayed around the object or at the mouse position.

The following code example illustrates how to position the tooltip around object.

{% tab template="diagram/tooltip/tooltip", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes'
        :tooltip='tooltip'  :constraints='constraints'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,DiagramConstraints } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

let nodes = [{
    id: "node1",
    height: 60,
    offsetX: 300,
    offsetY: 80,
    annotations: [{
        content: "start"
    }]
}]

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            constraints: DiagramConstraints.Default | DiagramConstraints.Tooltip,
            nodes: nodes,
            //Defines mouse over tooltip for a node
            tooltip: {
                content: 'Node1',
                //Sets the alignment properties
                position: 'BottomRight',
                //Sets to show tooltip around the element
                relativeMode: 'Object',
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

### Tooltip relative to mouse position

To display the tooltip at mouse position, need to set **mouse** option to the [`relativeMode`](../api/diagram/diagramTooltip#relativemode) property of the tooltip.
The following code example illustrates how to show tooltip at mouse position.

{% tab template="diagram/tooltip/tooltip", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes'
        :tooltip='tooltip'  :constraints='constraints'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,DiagramConstraints } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

let nodes = [{
    id: "node1",
    height: 60,
    offsetX: 300,
    offsetY: 80,
    annotations: [{
        content: "start"
    }]
}]

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            constraints: DiagramConstraints.Default | DiagramConstraints.Tooltip,
            nodes: nodes,
            //Defines mouse over tooltip for a node
            tooltip: {
                content: 'Node1',
                //Sets to show tooltip at mouse position
                relativeMode: 'Mouse',
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

## Tooltip animation

To animate the tooltip, a set of specific animation effects are available, and it can be controlled by using the [`animation`](../api/diagram/diagramTooltip#animation) property. The animation property also allows you to set delay, duration, and various other effects of your choice.

{% tab template="diagram/tooltip/tooltip", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes'
        :tooltip='tooltip'  :constraints='constraints'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,DiagramConstraints } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

let nodes = [{
    id: "node1",
    height: 60,
    offsetX: 300,
    offsetY: 80,
    annotations: [{
        content: "start"
    }]
}]

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            constraints: DiagramConstraints.Default | DiagramConstraints.Tooltip,
            nodes: nodes,
            //Defines mouse over tooltip for a node
            tooltip: {
                content: 'Node1',
                position: 'BottomCenter',
                relativeMode: 'Object',
                animation: {
                    //Animation settings to be applied on the Tooltip, while it is being shown over the target.
                    open: {
                        //Animation effect on the Tooltip is applied during open and close actions.
                        effect: 'ZoomIn',
                        //Duration of the animation that is completed per animation cycle.
                        duration: 1000,
                        //Indicating the waiting time before animation begins.
                        delay: 0
                    },
                    //Animation settings to be applied on the Tooltip, when it is closed.
                    close: {
                        effect: 'ZoomOut',
                        duration: 500,
                        delay: 0
                    }
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