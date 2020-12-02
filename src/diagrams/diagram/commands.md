---
title: "Commands"
component: "Diagram"
description: "Diagram commands allow you to arrange or resize the selected objects or defined objects in the diagram area."
---

# Commands

<!-- markdownlint-disable MD010 -->

There are several commands available in the diagram as follows.

* Alignment commands
* Spacing commands
* Sizing commands
* Clipboard commands
* Grouping commands
* Z-order commands
* Zoom commands
* Nudge commands
* FitToPage commands
* Undo/Redo commands

## Align

Alignment commands enable you to align the selected or defined objects such as nodes and connectors with respect to the selection boundary. Refer to [`align`](../api/diagram#align) commands which shows how to use align methods in the diagram.

<!-- markdownlint-disable MD033 -->

| Parameters | Description |
|:------------| :------: |
|[`Alignment Options`](../api/diagram/alignmentOptions#AlignmentOptions) | <p align="left">Defines the specific direction, with respect to which the objects to be aligned. <br> The accepted values of the argument "alignment options" are as follows.</p> <table><tr><td> Left </td><td align="left"> Aligns all the selected objects at the left of the selection boundary. </td></tr><tr><td> Right </td><td align="left"> Aligns all the selected objects at the right of the selection boundary. </td></tr><tr><td> Center </td><td align="left"> Aligns all the selected objects at the center of the selection boundary. </td></tr><tr><td>Top </td><td align="left"> Aligns all the selected objects at the top of the selection boundary. </td></tr><tr><td> Bottom </td><td align="left"> Aligns all the selected objects at the bottom of the selection boundary. </td></tr><tr><td> Middle </td><td align="left"> Aligns all the selected objects at the middle of the selection boundary. </td></tr></table>|
| Objects | <p align="left">Defines the objects to be aligned. This is an optional parameter. By default, all the nodes and connectors in the selected region of the diagram gets aligned.</p> |
[`Alignment Mode`](../api/diagram/alignmentMode#AlignmentMode)  | <p align="left">Defines the specific mode, with respect to which the objects to be aligned. This is an optional parameter. The default alignment mode is `Object`.<br> The accepted values of the argument "alignment mode" are as follows.</p> <table><tr><td> Object </td><td align="left"> Aligns the objects based on the first object in the selected list. </td></tr><tr><td> Selector </td><td align="left"> Aligns the objects based on the selection boundary. </td></tr></table>|

{% tab template="diagram/commands/align", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,NodeModel,ConnectorModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [
        {
            id: 'node1',
            width: 90,
            height: 60,
            offsetX: 100,
            offsetY: 100,
            style: {
                fill:   '#6BA5D7',
                strokeColor: 'white',
                strokeWidth: 1
            },
        },
        {
            id: 'node2',
            width: 100,
            height: 60,
            offsetX: 100,
            offsetY: 170,
            style: {
                fill:   '#6BA5D7',
                strokeColor: 'white',
                strokeWidth: 1
            },
        },
        {
            id: 'node3',
            width: 140,
            height: 60,
            offsetX: 100,
            offsetY: 240,
            style: {
                fill:   '#6BA5D7',
                strokeColor: 'white',
                strokeWidth: 1
            },
        }
    ];
    export default {
        name: 'app'
        data() {
            return {
                width: "100%",
                height: "350px",
                nodes: nodes
            }
        }
        mounted: function() {
            let diagramInstance: Diagram;
            let diagramObj: any = document.getElementById("diagram");
            diagramInstance = diagramObj.ej2_instances[0];
            let selArray: (NodeModel | ConnectorModel)[] = [];
            selArray.push(diagramInstance.nodes[0], diagramInstance.nodes[1], diagramInstance.nodes[2]);
            //Selects the nodes
            diagramInstance.select(selArray);
            //Sets direction as left
            diagramInstance.align('Left', diagramInstance.selectedItems.nodes, 'Selector');
            diagramInstance.dataBind();
        }
    }
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

![Align Sample](images/Commands_img1.png)

## Distribute

The [`Distribute`](../api/diagram#distribute) commands enable to place the selected objects on the page at equal intervals from each other. The selected objects are equally spaced within the selection boundary.

The factor to distribute the shapes [`DistributeOptions`](../api/diagram/distributeOptions#DistributeOptions) are listed as follows:

* RightToLeft: Distributes the objects based on the distance between the right and left sides of the adjacent objects.
* Left: Distributes the objects based on the distance between the left sides of the adjacent objects.
* Right: Distributes the objects based on the distance between the right sides of the adjacent objects.
* Center: Distributes the objects based on the distance between the center of the adjacent objects.
* BottomToTop: Distributes the objects based on the distance between the bottom and top sides of the adjacent objects.
* Top: Distributes the objects based on the distance between the top sides of the adjacent objects.
* Bottom: Distributes the objects based on the distance between the bottom sides of the adjacent objects.
* Middle: Distributes the objects based on the distance between the vertical center of the adjacent objects.

The following code example illustrates how to execute the space commands.

{% tab template="diagram/commands/distribute", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,NodeModel,ConnectorModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [
        {
            id: 'node1',
            width: 90,
            height: 60,
            offsetX: 100,
            offsetY: 100,
            style: {
                fill:   '#6BA5D7',
                strokeColor: 'white',
                strokeWidth: 1
            },
        },
        {
            id: 'node2',
            width: 90,
            height: 60,
            offsetX: 240,
            offsetY: 100,
            style: {
                fill:   '#6BA5D7',
                strokeColor: 'white',
                strokeWidth: 1
            },
        },
        {
            id: 'node3',
            width: 90,
            height: 60,
            offsetX: 170,
            offsetY: 150,
            style: {
                fill:   '#6BA5D7',
                strokeColor: 'white',
                strokeWidth: 1
            },
        }
    ];
    export default {
        name: 'app'
        data() {
            return {
                width: "100%",
                height: "350px",
                nodes: nodes
            }
        }
        mounted: function() {
            let diagramInstance: Diagram;
            let diagramObj: any = document.getElementById("diagram");
            diagramInstance = diagramObj.ej2_instances[0];
            let selArray: (NodeModel | ConnectorModel)[] = [];
            selArray.push(diagramInstance.nodes[0], diagramInstance.nodes[1], diagramInstance.nodes[2]);
            //Selects the nodes
            diagramInstance.select(selArray);
            //Distributes space between the nodes
            diagramInstance.distribute('RightToLeft', diagramInstance.selectedItems.nodes);
        }
    }
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

![DistributeImage](images/Commands_img2.png)

## Sizing

Sizing [`sameSize`](../api/diagram#sameSize) commands enable to equally size the selected nodes with respect to the first selected object.

[`SizingOptions`](../api/diagram/sizingOptions) are as follows:

* Width: Scales the width of the selected objects.
* Height: Scales the height of the selected objects.
* Size: Scales the selected objects both vertically and horizontally.

The following code example illustrates how to execute the size commands.

{% tab template="diagram/commands/sizing", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,NodeModel,ConnectorModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [
        {
            id: 'node1',
            width: 90,
            height: 60,
            offsetX: 100,
            offsetY: 100,
            style: {
                fill:   '#6BA5D7',
                strokeColor: 'white',
                strokeWidth: 1
            },
        {
            id: 'node2',
            width: 100,
            height: 60,
            offsetX: 100,
            offsetY: 170,
            style: {
                fill:   '#6BA5D7',
                strokeColor: 'white',
                strokeWidth: 1
            },
        },
        {
            id: 'node3',
            width: 130,
            height: 60,
            offsetX: 100,
            offsetY: 230,
            style: {
                fill:   '#6BA5D7',
                strokeColor: 'white',
                strokeWidth: 1
            },
        }
    ];
    export default {
        name: 'app'
        data() {
            return {
                width: "100%",
                height: "350px",
                nodes: nodes
            }
        }
        mounted: function() {
            let diagramInstance: Diagram;
            let diagramObj: any = document.getElementById("diagram");
            diagramInstance = diagramObj.ej2_instances[0];
            let selArray: (NodeModel | ConnectorModel)[] = [];
            selArray.push(diagramInstance.nodes[0], diagramInstance.nodes[1], diagramInstance.nodes[2]);
            //Selects the nodes
            diagramInstance.select(selArray);
            //Resizes the selected nodes with the same width
            diagramInstance.sameSize('Width', diagramInstance.selectedItems.nodes);
        }
    }
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

![Sizing Sample](images/Commands_img3.png)

## Clipboard

Clipboard commands are used to cut, copy, or paste the selected elements. Refer to the following link which shows how to use clipboard methods in the diagram.

* Cuts the selected elements from the diagram to the diagram’s clipboard, [`cut`](../api/diagram#cut).

* Copies the selected elements from the diagram to the diagram’s clipboard, [`copy`](../api/diagram#copy).

* Pastes the diagram’s clipboard data (nodes/connectors) into the diagram, [`paste`](../api/diagram#paste).

{% tab template="diagram/commands/clipboard", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,NodeModel,ConnectorModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [{
        id: 'node1',
        width: 90,
        height: 60,
        offsetX: 100,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    },
    {
        id: 'node2',
        width: 90,
        height: 60,
        offsetX: 240,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    }
];
let connectors = [{
    id: 'connector1',
    sourceID: 'node1',
    targetID: 'node2',
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
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            connectors: connectors
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        diagramInstance.select([diagramInstance.nodes[0], diagramInstance.nodes[1], diagramInstance.connectors[0]]);
        //copies the selected nodes
        diagramInstance.copy();
        //pastes the copied objects
        diagramInstance.paste(diagramInstance.copy() as(NodeModel | ConnectorModel)[]);
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Grouping

**Grouping commands** are used to group/ungroup the selected elements on the diagram. Refer to the following link which shows how to use grouping commands in the diagram.

[`Group`](../api/diagram#group) the selected nodes and connectors in the diagram.

[`Ungroup`](../api/diagram#ungroup) the selected nodes and connectors in the diagram.

The following code illustrates how to execute the grouping commands.

{% tab template="diagram/commands/grouping", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,NodeModel,ConnectorModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [{
        id: 'node1',
        width: 100,
        height: 70,
        offsetX: 100,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    },
    {
        id: 'node2',
        width: 100,
        height: 70,
        offsetX: 300,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    },
    {
        id: 'node3',
        width: 100,
        height: 70,
        offsetX: 200,
        offsetY: 200,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    },
    {
        id: 'group',
        children: ['node1', 'node2', 'connector1']
    },
    {
        id: 'group2',
        children: ['node3', 'group']
    }
];
let connectors = [{
    id: 'connector1',
    sourceID: 'node1',
    targetID: 'node2',
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
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            connectors: connectors
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        diagramInstance.select([diagramInstance.nodes[0], diagramInstance.nodes[1], diagramInstance.connectors[0]]);
        //Selects the diagram
        diagramInstance.selectAll();
        //Groups the selected elements.
        diagramInstance.group();
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Z-Order command

**Z-Order commands** enable you to visually arrange the selected objects such as nodes and connectors on the page.

### bringToFront command

The [`bringToFront`](../api/diagram#bringToFront) command visually brings the selected element to front over all the other overlapped elements. The following code illustrates how to execute the `bringToFront` command.

{% tab template="diagram/commands/bringfront", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,NodeModel,ConnectorModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [{
        id: 'node1',
        width: 90,
        height: 60,
        offsetX: 100,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    },
    {
        id: 'node2',
        width: 90,
        height: 60,
        offsetX: 240,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    },
    {
        id: 'node3',
        width: 90,
        height: 60,
        offsetX: 160,
        offsetY: 90,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    }
];

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let selArray: (NodeModel)[] = [];
        selArray.push(diagramInstance.nodes[2]);
        //Selects the nodes
        diagramInstance.select(selArray);
        //Brings to front
        diagramInstance.bringToFront();
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

### sendToBack command

The [`sendToBack`](../api/diagram#sendToBack) command visually moves the selected element behind all the other overlapped elements. The following code illustrates how to execute the `sendToBack` command.

{% tab template="diagram/commands/sendback", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,NodeModel,ConnectorModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [{
        id: 'node1',
        width: 90,
        height: 60,
        offsetX: 100,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    },
    {
        id: 'node2',
        width: 90,
        height: 60,
        offsetX: 240,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    },
    {
        id: 'node3',
        width: 90,
        height: 60,
        offsetX: 160,
        offsetY: 90,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    }
];

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let selArray: (NodeModel)[] = [];
        selArray.push(diagramInstance.nodes[2]);
        //Selects the nodes
        diagramInstance.select(selArray);
        //Sends to back
        diagramInstance.sendToBack();
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

### moveForward command

The [`moveForward`](../api/diagram#moveForward) command visually moves the selected element over the nearest overlapping element. The following code illustrates how to execute the `moveForward` command.

{% tab template="diagram/commands/moveforward", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,NodeModel,ConnectorModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [{
        id: 'node1',
        width: 90,
        height: 60,
        offsetX: 100,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    },
    {
        id: 'node2',
        width: 90,
        height: 60,
        offsetX: 180,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    }
];

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let selArray: (NodeModel)[] = [];
        selArray.push(diagramInstance.nodes[1]);
        //Selects the nodes
        diagramInstance.select(selArray);
        //Moves forward
        diagramInstance.moveForward();
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

### sendBackward command

The [`sendBackward`](../api/diagram#sendBackward) command visually moves the selected element behind the underlying element. The following code illustrates how to execute the `sendBackward` command.

{% tab template="diagram/commands/sendbackward", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,NodeModel,ConnectorModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [{
        id: 'node1',
        width: 90,
        height: 60,
        offsetX: 100,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    },
    {
        id: 'node2',
        width: 90,
        height: 60,
        offsetX: 180,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    }
];

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let selArray: (NodeModel)[] = [];
        selArray.push(diagramInstance.nodes[1]);
        diagramInstance.select(selArray);
        //Sends backward
        diagramInstance.sendBackward();
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Zoom

The [`zoom`](../api/diagram#zoom) command is used to zoom-in and zoom-out the diagram view.

The following code illustrates how to zoom-in/zoom out the diagram.

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height'  ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,NodeModel,ConnectorModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

  ]

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        diagramInstance.zoom(1.2, {
            x: 100,
            y: 100
        });
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

## Nudge command

The [`nudge`](../api/diagram#nudge) commands move the selected elements towards up, down, left, or right by 1 pixel.

[`NudgeDirection`](../api/diagram/nudgeDirection) nudge command moves the selected elements towards the specified direction by 1 pixel, by default.

The accepted values of the argument "direction" are as follows:

* Up: Moves the selected elements towards up by the specified delta value.
* Down: Moves the selected elements towards down by the specified delta value.
* Left: Moves the selected elements towards left by the specified delta value.
* Right: Moves the selected elements towards right by the specified delta value.

The following code illustrates how to execute nudge command.

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height'  ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,NodeModel,ConnectorModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

  ]

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        diagramInstance.nudge('Right');
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

## Nudge by using arrow keys

The corresponding arrow keys are used to move the selected elements towards up, down, left, or right direction by 1 pixel.

![Nudge Command](images/Commands_img4.png)

Nudge commands are particularly useful for accurate placement of elements.

## BringIntoView

The [`bringIntoView`](../api/diagram#bringIntoView) command brings the specified rectangular region into the viewport of the diagram.

The following code illustrates how to execute the `bringIntoView` command.

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height'  ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,NodeModel,ConnectorModel,Rect} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

  ]

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        //Brings the specified rectangular region of the Diagram content to the viewport of the page.
        let bound: Rect = new Rect(200, 400, 500, 400);
        diagramInstance.bringIntoView(bound);
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

## BringToCenter

The [`bringToCenter`](../api/diagram#bringToCenter) command brings the specified rectangular region of the diagram content to the center of the viewport.

The following code illustrates how to execute the `bringToCenter` command.

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height'  ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,NodeModel,ConnectorModel,Rect} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

  ]

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        //Brings the specified rectangular region of the Diagram content to the center of the viewport.
        let bound: Rect = new Rect(200, 400, 500, 400);
        diagramInstance.bringToCenter(bound);
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

## FitToPage command

The [`fitToPage`](../api/diagram#fitToPage) command helps to fit the diagram content into the view with respect to either width, height, or at the whole.

The [`mode`](../api/diagram/fitModes#modes) parameter defines whether the diagram has to be horizontally/vertically fit into the viewport with respect to width, height, or entire bounds of the diagram.

The [`region`](../api/diagram/diagramRegions#region) parameter defines the region that has to be drawn as an image.

The [`margin`](../api/diagram/iFitOptions#margin) parameter defines the region/bounds of the diagram content that is to be fit into the view.

The [`canZoomIn`](../api/diagram/iFitOptions#canZoomIn) parameter enables/disables zooming to fit the smaller content into a larger viewport.

The [`customBounds`](../api/diagram/iFitOptions#customBounds) parameter the custom region that has to be fit into the viewport.

The following code illustrates how to execute `FitToPage` command.

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height'  ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,NodeModel,ConnectorModel,Rect} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

  ]

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        //fit the diagram to the page with respect to mode and region
        diagramInstance.fitToPage({
            mode: 'Page',
            region: 'Content',
            margin: {
                bottom: 50
            },
            canZoomIn: false
        });
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

## Command manager

Diagram provides support to map/bind command execution with desired combination of key gestures. Diagram provides some built-in commands.
[`CommandManager`](../api/diagram/commandManager#commandManager) provides support to define custom commands. The custom commands are executed, when the specified key gesture is recognized.

## Custom command

To define a custom command, specify the following properties:
* [`execute`](../api/diagram/command#execute): A method to be executed.
* [`canExecute`](../api/diagram/command#canexecute): A method to define whether the command can be executed at the moment.
* [`gesture`](../api/diagram/keyGestureModel#gesture): A combination of [`keys`](../api/diagram/keys#key) and [`KeyModifiers`](../api/diagram/keyModifiers#keymodifiers).
* [`parameter`](../api/diagram/command#parameter): Defines any additional parameters that are required at runtime.
* [`name`](../api/diagram/command#name): Defines the name of the command.

To explore the properties of custom commands, refer to [`Commands`](../api/diagram/command#commands).

The following code example illustrates how to define a custom command.

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :commandManager='commandManager' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,Keys,KeyModifiers} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

  ]

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            commandManager: {
                commands: [{
                    name: 'customCopy',
                    parameter: 'node',
                    //Method to define whether the command can be executed at the current moment
                    canExecute: function() {
                        //Defines that the clone command can be executed, if and only if the selection list is not empty.
                        if (diagramInstance.selectedItems.nodes.length > 0 || diagramInstance.selectedItems.connectors.length > 0) {
                            return true;
                        }
                        return false;
                    },
                    //Command handler
                    execute: function() {
                        //Logic to clone the selected element
                        diagramInstance.copy();
                        diagramInstance.paste();
                        diagramInstance.dataBind();
                    },
                    //Defines that the clone command has to be executed on the recognition of key press.
                    gesture: {
                        key: Keys.G,
                        keyModifiers: KeyModifiers.Shift | KeyModifiers.Alt
                    }
                }]
            },
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let obj: any = document.getElementById("diagram");
        diagramInstance = obj.ej2_instances[0];
    }

}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

## Modify the existing command

When any one of the default commands is not desired, they can be disabled. To change the functionality of a specific command, the command can be completely modified.

The following code example illustrates how to disable a command and how to modify the built-in commands.

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :commandManager='commandManager' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
import {
    DiagramPlugin,
    Keys,
    KeyModifiers
} from '@syncfusion/ej2-vue-diagrams';

Vue.use(DiagramPlugin);

]

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            commandManager: {
            commands: [
                {
                    name: 'nudgeUp',
                    canExecute: function () {
                        return false;
                    },
                    gesture: {
                        key:Keys.Up,  
                    }
                },
                {
                    name: 'nudgeDown',
                    canExecute: function () {
                        return false;
                    },
                    gesture: {
                        key: Keys.Down,
                    }
                },
                {
                  name: 'nudgeRight',
                    canExecute: function () {
                        return false;
                    },
                    gesture: {
                        key: Keys.Right,
                    }
                }
            ]
            },
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let obj: any = document.getElementById("diagram");
        diagramInstance = obj.ej2_instances[0];
    }

}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

## See Also

* [How to create the custom context menu items](./context-menu)