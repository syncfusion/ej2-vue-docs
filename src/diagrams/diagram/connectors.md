---
title: "Connector"
component: "Diagram"
description: "Diagram connector allows you to draw a line to connect two points, nodes or ports."
---

# Connector

Connectors are objects used to create link between two points, nodes or ports to represent the relationships between them.

## Create Connector

Connector can be created by defining the source and target point of the connector. The path to be drawn can be defined with a collection of segments. To explore the properties of a [`connector`](../api/diagram/connector), refer to [`Connector Properties`](../api/diagram/connector).

## Add connectors through connectors collection

* The [`sourcePoint`](../api/diagram/connector#sourcepoint-PointModel) and [`targetPoint`](../api/diagram/connector#targetpoint-PointModel) properties of connector allow you to define the end points of a connector.

The following code example illustrates how to add a connector through connector collection.

{% tab template="diagram/connectors/Connectors", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
     // Name of the connector
     id: "connector1",
     style: {
         strokeColor: '#6BA5D7',
         fill: '#6BA5D7',
         strokeWidth: 2
     },
     targetDecorator: {
         style: {
             fill: '#6BA5D7',
             strokeColor: '#6BA5D7'
         }
     },
     // Sets source and target points
     sourcePoint: {
         x: 100,
         y: 100
     },
     targetPoint: {
         x: 200,
         y: 200
     }
 }]
 export default {
     name: 'app'
     data() {
         return {
             width: "100%",
             height: "350px",
             connectors: connectors
         }
     }
 }
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Add connector at run time**

* Connectors can be added at runtime by using public method, `diagram.add` and can be removed at runtime by using public method, `diagram.remove`.

The following code example illustrates how to add connector at runtime.

{% tab template="diagram/connectors/Connectorsatruntime", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,Diagram,ConnectorModel } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

     let connector: ConnectorModel = {
    // Name of the connector
    id: "connector1",
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    // Sets source and target points
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
}



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
        // Adds to the diagram
        diagramInstance.add(connector)
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Connectors from palette

* Connectors can be predefined and added to the symbol palette. You can drop those connectors into the Diagram, when required.

For more information about adding connectors from symbol palette, refer to [`Symbol Palette`].

## Draw connectors

Connectors can be interactively drawn by clicking and dragging on the Diagram surface by using [`drawingObject`]. For more information about drawing connectors, refer to [`Draw Connectors`](../api/diagram#drawingObject-ConnectorModel).

## Update Connector at runtime

Various Connector properties such as `sourcePoint`, `targetPoint`,`style`,`sourcePortID`,`targetPortID` etc can be update at the run time .

* The following code example illustrates how to update a connector's source point,target point,styles properties  at runtime.

{% tab template="diagram/connectors/Connectorsupdate", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
    // Name of the connector
    id: "connector1",
    // Sets source and target points
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        diagramInstance.connectors[0].style.strokeColor = '#6BA5D7';
        diagramInstance.connectors[0].style.fill = '#6BA5D7';
        diagramInstance.connectors[0].style.strokeWidth = 2;
        diagramInstance.connectors[0].targetDecorator.style.fill = '#6BA5D7';
        diagramInstance.connectors[0].targetDecorator.style.strokeColor = '#6BA5D7';
        diagramInstance.connectors[0].sourcePoint.x = 150;
        diagramInstance.connectors[0].targetPoint.x = 150;
        diagramInstance.dataBind();
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Connect nodes

* The [`sourceID`](../api/diagram/connector#sourceid-string) and [`targetID`](../api/diagram/connector#targetid-string) properties allow to define the nodes to be connected.

* The following code example illustrates how to connect two nodes.

{% tab template="diagram/connectors/ConnectNode", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :connectors='connectors' :getNodeDefaults='getNodeDefaults' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [{
        id: 'Start',
        width: 140,
        height: 50,
        offsetX: 300,
        offsetY: 100,
        annotations: [{
            id: 'label1',
            content: 'Start'
        }],
        shape: {
            type: 'Flow',
            shape: 'Terminator'
        }
    },
    {
        id: 'Init',
        width: 140,
        height: 50,
        offsetX: 300,
        offsetY: 300,
        shape: {
            type: 'Flow',
            shape: 'Process'
        },
        annotations: [{
            content: 'var i = 0;'
        }]
    }
];

let connectors = [{
    id: "connector1",
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    sourceID: "Start",
    targetID: "Init",
    type: 'Orthogonal'
}, ]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            connectors: connectors,
            getNodeDefaults: (node) => {
                node.height = 100;
                node.width = 100;
                node.style.fill = '#6BA5D7';
                node.style.strokeColor = 'white';
                return node;
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

* When you remove NodeConstraints InConnect from Default, the node accepts only an outgoing connection to dock in it. Similarly, when you remove NodeConstraints OutConnect from Default, the node accepts only an incoming connection to dock in it.

* When you remove both InConnect and OutConnect NodeConstraints from Default, the node restricts connector to establish connection in it.

* The following code illustrates how to disable InConnect constraints.

```typescript

//Initialize diagram
let diagram: Diagram = new Diagram({
     nodes:[
         {
            id: 'node', width: 100, height: 100, offsetX: 100, offsetY: 150,
            shape: { type: 'Basic', shape: 'Rectangle' },
            //Disable InConnect constraints
            constraints: NodeConstraints.Default & ~NodeConstraints.InConnect,
         }
     ]
});
diagram.appendTo('#diagram');

```

## Connections with ports

The [`sourcePortID`](../api/diagram/connector#sourceportid-string) and [`targetPortID`](../api/diagram/connector#targetportid-string) properties allow to create connections between some specific points of source/target nodes.

The following code example illustrates how to create port to port connections.

{% tab template="diagram/connectors/Connectorsportupdate", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :connectors='connectors' :getNodeDefaults='getNodeDefaults' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,PointPortModel,PortVisibility } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let port1: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
}
port1.shape = 'Circle';
port1.id = 'nodeportnew'
port1.visibility = PortVisibility.Visible
port1.id = 'port';
port1.offset = {
    x: 1,
    y: 1
};
let port2: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
};
port2.offset = {
    x: 1,
    y: 0.5
};
port2.id = 'port1';
port2.visibility = PortVisibility.Visible
port2.shape = 'Circle';
let port3: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
};
port3.offset = {
    x: 0,
    y: 1
};
port3.id = 'newnodeport1';
port3.visibility = PortVisibility.Visible
port3.shape = 'Circle';

    let nodes = [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        ports: [port1]
    },
    {
        id: 'node1',
        width: 100,
        height: 100,
        offsetX: 300,
        offsetY: 100,
        ports: [port2, port3]
    },
];

let connectors = {
    id: "connector1",
    sourcePoint: {
        x: 100,
        y: 100
    },
    type: 'Orthogonal',
    targetPoint: {
        x: 200,
        y: 200
    },
    sourceID: 'node',
    targetID: 'node1',
    sourcePortID: 'port',
    targetPortID: 'port1'
}
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            connectors: [connectors],
            getNodeDefaults: (node) => {
                node.height = 100;
                node.width = 100;
                node.style.fill = '#6BA5D7';
                node.style.strokeColor = 'white';
                return node;
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

similarly we can change the [`sourcePortID`] or [`targetPortID`]  at the run time by the changing the port [`sourcePortID`](../api/diagram/connector#sourceportid-string) or [`targetPortID`](../api/diagram/connector#targetportid-string)

The following code example illustrates how to create port to port connections.

{% tab template="diagram/connectors/ConnectorsSegments", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :connectors='connectors' :getNodeDefaults='getNodeDefaults' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,PointPortModel,PortVisibility } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let port1: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
}
port1.shape = 'Circle';
port1.id = 'nodeportnew'
port1.visibility = PortVisibility.Visible
port1.id = 'port';
port1.offset = {
    x: 1,
    y: 1
};
let port2: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
};
port2.offset = {
    x: 1,
    y: 0.5
};
port2.id = 'port1';
port2.visibility = PortVisibility.Visible
port2.shape = 'Circle';
let port3: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
};
port3.offset = {
    x: 0,
    y: 1
};
port3.id = 'newnodeport1';
port3.visibility = PortVisibility.Visible
port3.shape = 'Circle';

    let nodes = [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        ports: [port1]
    },
    {
        id: 'node1',
        width: 100,
        height: 100,
        offsetX: 300,
        offsetY: 100,
        ports: [port2, port3]
    },
];

let connectors = {
    id: "connector1",
    sourcePoint: {
        x: 100,
        y: 100
    },
    type: 'Orthogonal',
    targetPoint: {
        x: 200,
        y: 200
    },
    sourceID: 'node',
    targetID: 'node1',
    sourcePortID: 'port',
    targetPortID: 'port1'
}
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            connectors: [connectors],
            getNodeDefaults: (node) => {
                node.height = 100;
                node.width = 100;
                node.style.fill = '#6BA5D7';
                node.style.strokeColor = 'white';
                return node;
            },
        }
    }
     mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        diagramInstance.connectors[0].targetPortID = 'newnodeport1'
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

* When you set PortConstraints to InConnect, the port accepts only an incoming connection to dock in it. Similarly, when you set PortConstraints to OutConnect, the port accepts only an outgoing connection to dock in it.

* When you set PortConstraints to None, the port restricts connector to establish connection in it.

```typescript

//Initialize diagram
let diagram: Diagram = new Diagram({
     nodes:[
         {
            id: 'node', width: 100, height: 100, offsetX: 100, offsetY: 150,
            shape: { type: 'Basic', shape: 'Rectangle' },
            ports: [
             //Enable portConstraints Inconnect
             { id: 'port', height: 10, width: 10, offset: { x: 1, y: 0.5 }, constraints: PortConstraints.InConnect },
           ]
         }
     ]
});
diagram.appendTo('#diagram');

```

## Segments

The path of the connector is defined with a collection of segments. There are three types of segments.

## Straight

To create a straight line, you should specify the [`type`](../api/diagram/segments) of the segment as “straight” and add a straight segment to [`segments`](../api/diagram/connector#segments) collection and need to specify [`type`](../api/diagram/connector#type-Segments) for the connector. The following code example illustrates how to create a default straight segment.

{% tab template="diagram/connectors/ConnectorsSegmentsPoints", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
    id: "connector1",
    type: 'Straight',
    segments: [{
        // Defines the segment type of the connector
        type: 'Straight'
    }],
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

The [`point`](../api/diagram/straightSegment#point-PointModel) property of straight segment allows you to define the end point of it. The following code example illustrates how to define the end point of a straight segment.

{% tab template="diagram/connectors/ConnectorsOrthoSegments", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
    id: "connector1",
    // Defines the segment type of the connector
    segments: [{
        type: 'Straight',
        // Defines the point of the segment
        point: {
            x: 100,
            y: 150
        }
    }],
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Orthogonal

Orthogonal segments are used to create segments that are perpendicular to each other.

Set the segment [`type`](../api/diagram/segments) as “orthogonal” to create a default orthogonal segment and need to specify [`type`](../api/diagram/connector#type-Segments). The following code example illustrates how to create a default orthogonal segment.
* Multiple segments can be defined one after another. To create a connector with multiple segments, define and add the segments to [`connector.segments`](../api/diagram/connector#segments) collection. The Following code example illustrates how to create a connector with multiple segments.

{% tab template="diagram/connectors/ConnectorsOverlapping", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
    id: "connector1",
    // Define the type of the segment
    type: 'Orthogonal',
    segments: [{
        type: 'Orthogonal'
    }],
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

The [`length`](../api/diagram/orthogonalSegment) and [`direction`](../api/diagram/orthogonalSegment) properties allow to define the flow and length of segment. The following code example illustrates how to create customized orthogonal segments.

{% tab template="diagram/connectors/ConnectorsBezier", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
        id: "connector1",
        type: 'Orthogonal',
        segments: [{
            type: 'Orthogonal',
            // Defines the direction for the segment lines
            direction: 'Right',
            // Defines the length for the segment lines
            length: 50
        }],
        style: {
            strokeColor: '#6BA5D7',
            fill: '#6BA5D7',
            strokeWidth: 2
        },
        targetDecorator: {
            style: {
                fill: '#6BA5D7',
                strokeColor: '#6BA5D7'
            }
        },
        sourcePoint: {
            x: 100,
            y: 100
        },
        targetPoint: {
            x: 200,
            y: 200
        }
    },
    {
        id: "connector2",
        type: 'Orthogonal',
        // Defines multile segemnts for the connectors
        segments: [{
                type: 'Orthogonal',
                direction: 'Bottom',
                length: 150
            },
            {
                type: 'Orthogonal',
                direction: 'Right',
                length: 150
            }
        ],
        style: {
            strokeColor: '#6BA5D7',
            fill: '#6BA5D7',
            strokeWidth: 2
        },
        targetDecorator: {
            style: {
                fill: '#6BA5D7',
                strokeColor: '#6BA5D7'
            }
        },
        sourcePoint: {
            x: 300,
            y: 100
        },
        targetPoint: {
            x: 400,
            y: 200
        }
    }
]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

>Note: We need mention the segment type as same as what we mentioned in connector type. There should be no contradiction between connector type and segment type.

## Avoid overlapping

Orthogonal segments are automatically re-routed, in order to avoid overlapping with the source and target nodes. The following preview illustrate how orthogonal segments are re-routed.

{% tab template="diagram/connectors/ConnectorsBezierPoints", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :connectors='connectors' :getNodeDefaults='getNodeDefaults' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,PointPortModel,PortVisibility } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodeport: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
};
nodeport.shape = 'Circle';
nodeport.visibility = PortVisibility.Visible
nodeport.id = 'port';
nodeport.offset = {
    x: 0,
    y: 0.5
};
let port2: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
}
port2.offset = {
    x: 0,
    y: 0.5
};
port2.id = 'port1';
port2.visibility = PortVisibility.Visible
port2.shape = 'Circle';

let nodes = [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        ports: [nodeport]
    },
    {
        id: 'node1',
        width: 100,
        height: 100,
        offsetX: 300,
        offsetY: 100,
        ports: [port2]
    },
];

let connectors = {
    id: "connector1",
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    type: 'Orthogonal',
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    sourceID: 'node',
    targetID: 'node1',
    sourcePortID: 'port',
    targetPortID: 'port1'
}
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            connectors: [connectors],
            getNodeDefaults: (node) => {
                node.height = 100;
                node.width = 100;
                node.style.fill = '#6BA5D7';
                node.style.strokeColor = 'white';
                return node;
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

## Bezier

Bezier segments are used to create curve segments and the curves are configurable either with the control points or with vectors.

To create a bezier segment, the [`segment.type`](../api/diagram/segments) is set as `bezier` and need to specify [`type`](../api/diagram/connector#type-Segments) for the connector. The following code example illustrates how to create a default Bezier segment.

{% tab template="diagram/connectors/ConnectorsBezier", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
    id: 'connector1',
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    type: 'Bezier',
    segments: [{
        // Defines the type of the segment
        type: 'Bezier',
    }],
    sourcePoint: {
        x: 50,
        y: 100
    },
    targetPoint: {
        x: 150,
        y: 200
    },
}, ]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

The [`point1`](../api/diagram/bezierSegment#point1-PointModel) and [`point2`](../api/diagram/bezierSegment#point2-PointModel) properties of bezier segment enable you to set the control points. The following code example illustrates how to configure the Bezier segments with control points.

{% tab template="diagram/connectors/ConnectorsBezierPoints", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
    id: 'connector3',
    type: 'Bezier',
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    segments: [{
        type: 'Bezier',
        // First control point: an absolute position from the page origin
        point1: {
            x: 100,
            y: 100
        },
        // Second control point: an absolute position from the page origin
        point2: {
            x: 200,
            y: 200
        }
    }],
    sourcePoint: {
        x: 100,
        y: 200
    },
    targetPoint: {
        x: 200,
        y: 100
    },
}, ]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

The [`vector1`](../api/diagram/bezierSegment#vector1-VectorModel) and [`vector2`](../api/diagram/bezierSegment#vector2-VectorModel) properties of bezier segment enable you to define the vectors. The following code illustrates how to configure a bezier curve with vectors.

{% tab template="diagram/connectors/ConnectorsBezierVector", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
    id: 'connector2',
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    // Defines the type of the segment
    type: 'Bezier',
    segments: [{
        type: 'Bezier',
        // Length and angle between the source point and the first control point
        vector1: {
            distance: 100,
            angle: 90
        },
        // Length and angle between the target point and the second control point
        vector2: {
            distance: 45,
            angle: 270
        }
    }],
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
}, ]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Decorator

* Start and end points of a connector can be decorated with some customizable shapes like arrows, circles, diamond or path. You can decorate the connection end points with the [`sourceDecorator`](../api/diagram/connector#sourcedecorator-DecoratorModel) and [`targetDecorator`](../api/diagram/connector#targetdecorator-DecoratorModel)properties of connector.

* The [`shape`](../api/diagram/decoratorShapes) property of `sourceDecorator` allows to define the shape of the decorators. Similarly, the [shape](../api/diagram/decoratorShapes) property of `targetDecorator` allows to define the shape of the decorators.

* To create custom shape for source decorator, use [`pathData`](../api/diagram/decorator#pathdata-string) property. similarly, to create custom shape for target decorator, use [`pathData`](../api/diagram/decorator#pathData-string) property.

* The following code example illustrates how to create decorators of various shapes.

{% tab template="diagram/connectors/ConnectorsDecorator", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
        id: "connector1",
        type: 'Straight',
        // Decorator shape- circle
        sourceDecorator: {
            shape: 'Circle',
            // Defines the style for the sourceDecorator
            style: {
                // Defines the strokeWidth for the sourceDecorator
                strokeWidth: 3,
                // Defines the strokeColor for the sourceDecorator
                strokeColor: 'red'
            },

        },
        // Decorator shape - Diamond
        targetDecorator: {
            // Defines the custom shape for the connector's target decorator
            shape: 'Custom',
            //Defines the  path for the connector's target decorator
            pathData: 'M80.5,12.5 C80.5,19.127417 62.59139,24.5 40.5,24.5 C18.40861,24.5 0.5,19.127417 0.5,12.5' +
                'C0.5,5.872583 18.40861,0.5 40.5,0.5 C62.59139,0.5 80.5,5.872583 80.5,12.5 z'
            //defines the style for the target decorator
            style: {
                // Defines the strokeWidth for the targetDecorator
                strokeWidth: 3,
                // Defines the strokeColor for the sourceDecorator
                strokeColor: 'green',
                // Defines the opacity for the sourceDecorator
                opacity: .8
            },
        },
        sourcePoint: {
            x: 100,
            y: 100
        },
        targetPoint: {
            x: 200,
            y: 200
        }
    },
    {
        id: "connectors2",
        type: 'Straight',
        // Decorator shape - IndentedArrow
        sourceDecorator: {
            shape: 'IndentedArrow',
            style: {
                strokeWidth: 3,
                strokeColor: 'blue'
            },

        },
        // Decorator shape - OutdentedArrow
        targetDecorator: {
            shape: 'OutdentedArrow',
            style: {
                strokeWidth: 3,
                strokeColor: 'yellow'
            },
        },
        sourcePoint: {
            x: 400,
            y: 100
        },
        targetPoint: {
            x: 300,
            y: 200
        }
    }
]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Padding

Padding is used to leave the space between the Connector's end point and the object to where it is connected.

* The [`sourcePadding`](../api/diagram/connector#sourcepadding) property of connector defines space between the source point and the source node of the connector.

* The [`targetPadding`](../api/diagram/connector#targetpadding) property of connector defines space between the end point and the target node of the connector.

* The following code example illustrates how to leave space between the connection end points and source and target nodes.

{% tab template="diagram/connectors/ConnectNode", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :connectors='connectors' :getNodeDefaults='getNodeDefaults' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
    },
    {
        id: 'node1',
        width: 100,
        height: 100,
        offsetX: 300,
        offsetY: 100,
    }
];

let connectors = [{
    id: "connector1",
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    sourceID: "node",
    targetID: "node1",
    // Set Source Padding value
    sourcePadding:20,
    // Set Target Padding value
    targetPadding:20
}, ]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            connectors: connectors,
            getNodeDefaults: (node) => {
                node.height = 100;
                node.width = 100;
                node.style.fill = '#6BA5D7';
                node.style.strokeColor = 'white';
                return node;
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

## Flip

The diagram Provides support to flip the connector. The [`flip`](../api/diagram/connector#flip) is performed to give the mirrored image of the original element.

The flip types are as follows:

* HorizontalFlip
 [`Horizontal`](../api/diagram/flipDirection) is used to interchange the connector source and target x points.

* VerticalFlip
[`Vertical`](../api/diagram/flipDirection) is used to interchange the connector source and target y points.

* Both
[`Both`](../api/diagram/flipDirection) is used to interchange the source point as target point and target point as source point

{% tab template="diagram/connectors/ConnectorsDecorator", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
        // Name of the connector
    id: "connector1",
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    // Flip the connector in horizontal direction
      flip:"Horizontal"
    }
]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

>Note: The flip is not applicable when the connectors connect in nodes

## Bridging

Line Bridging creates a bridge for lines to smartly cross over other lines, at points of intersection. By default [`bridgeDirection`](../api/diagram#bridgeDirection-BridgeDirection) is set to top. Depending upon the direction given bridging direction appears.
Bridging can be enabled/disabled either with the [`connector.constraints`] or [`diagram.constraints`]. The following code example illustrates how to enable line bridging.

{% tab template="diagram/connectors/ConnectorsBridging", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :connectors='connectors' :constraints='constraints' :getNodeDefaults='getNodeDefaults' :getConnectorDefaults='getConnectorDefaults'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { Diagram,DiagramPlugin,DiagramConstraints,ConnectorBridging } from '@syncfusion/ej2-vue-diagrams';
    Diagram.Inject(ConnectorBridging);

    Vue.use(DiagramPlugin);

    let nodes = [{
        id: 'Transaction',
        width: 150,
        height: 60,
        offsetX: 300,
        offsetY: 60,
        shape: {
            type: 'Flow',
            shape: 'Terminator'
        },
        annotations: [{
            id: 'label1',
            content: 'Start Transaction',
            offset: {
                x: 0.5,
                y: 0.5
            }
        }],
    },
    {
        id: 'Verification',
        width: 150,
        height: 60,
        offsetX: 300,
        offsetY: 250,
        shape: {
            type: 'Flow',
            shape: 'Process'
        },
        annotations: [{
            id: 'label2',
            content: 'Verification',
            offset: {
                x: 0.5,
                y: 0.5
            }
        }]
    }
];

let connectors = [{
        id: 'connector1',
        type: 'Straight',
        sourceID: 'Transaction',
        targetID: 'Verification'
    }, {
        id: 'connector2',
        type: 'Straight',
        sourcePoint: {
            x: 200,
            y: 130
        },
        targetPoint: {
            x: 400,
            y: 130
        }
    },
    {
        id: 'connector3',
        type: 'Straight',
        sourcePoint: {
            x: 200,
            y: 170
        },
        targetPoint: {
            x: 400,
            y: 170
        }
    }
]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            constraints: DiagramConstraints.Default | DiagramConstraints.Bridging,
            nodes: nodes,
            connectors: connectors,
            getNodeDefaults: (node) => {
                node.height = 100;
                node.width = 100;
                node.style.fill = '#6BA5D7';
                node.style.strokeColor = 'white';
                return node;
            },
            getConnectorDefaults: (obj) => {
                obj.style.strokeColor = '#6BA5D7';
                obj.style.fill = '#6BA5D7';
                obj.style.strokeWidth = 2;
                obj.targetDecorator.style.fill = '#6BA5D7';
                obj.targetDecorator.style.strokeColor = '#6BA5D7';
                return obj;
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

>Note: We Need to inject Connector bridging module into the diagram.

You can use [`bridgeSpace`](../api/diagram/connector#bridgespace-number) property of connectors to define the width for line bridging.

Limitation: Bezier segments do not support bridging.

## Corner radius

Corner radius allows to create connectors with rounded corners. The radius of the rounded corner is set with [`cornerRadius`](../api/diagram/connector#cornerradius-number) property.

{% tab template="diagram/connectors/ConnectorsCornerRadius", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :connectors='connectors' :getNodeDefaults='getNodeDefaults'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [{
        id: 'node1',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
    },
    {
        id: 'node2',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 350,
    },
];

let connectors = [{
    id: "connector1",
    type: 'Orthogonal',
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    // Sets the radius for the rounded corner
    cornerRadius: 10,
    sourceID: 'node1',
    targetID: 'node2',
    segments: [{
        type: 'Orthogonal',
        direction: 'Right',
        length: 50
    }],
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            connectors: connectors,
            getNodeDefaults: (node) => {
                node.height = 100;
                node.width = 100;
                node.style.fill = '#6BA5D7';
                node.style.strokeColor = 'white';
                return node;
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

## Appearance

* The Connector’s [`strokeWidth`](../api/diagram/strokeStyle#strokewidth-number), [`strokeColor`](../api/diagram/strokeStyle#strokecolor-string), [`strokeDashArray`](../api/diagram/strokeStyle#strokedasharray-string) and [`opacity`](../api/diagram/strokeStyle#opacity-number) properties are used to customize the appearance of the connector segments.

* The [`visible`](../api/diagram/connector#visible-boolean) property of the connector enables or disables the visibility of connector.

* Default values for all the  `connectors` can be set using the `getConnectorDefaults` properties. For example, if all connectors have the same type or having the same property then such properties can be moved into `getConnectorDefaults`.

## Segment Appearance

* The following code example illustrates how to customize the segment appearance.

{% tab template="diagram/connectors/ConnectorsAppearance", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :connectors='connectors' :getConnectorDefaults='getConnectorDefaults' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
        id: "connector1",
        targetDecorator: {
            style: {
                strokeColor: '#6BA5D7',
                fill: '#6BA5D7',
                strokeWidth: 2
            }
        },
        style: {
            // Stroke color
            strokeColor: '#6BA5D7',
            fill: '#6BA5D7',
            // Stroke width of the line
            strokeWidth: 2,
            // Line style
            strokeDashArray: '2,2'
        },
        sourcePoint: {
            x: 100,
            y: 100
        },
        targetPoint: {
            x: 200,
            y: 200
        },
        segments: [{
            type: 'Orthogonal',
            direction: 'Right',
            length: 50
        }],
    },
    {
        id: "connector2",
        // Set the visibility of the connector to false
        visible: false,
        targetDecorator: {
            style: {
                strokeColor: '#6BA5D7',
                fill: '#6BA5D7',
                strokeWidth: 2
            }
        },
        style: {
            // Stroke color
            strokeColor: '#6BA5D7',
            fill: '#6BA5D7',
            // Stroke width of the line
            strokeWidth: 2,
            // Line style
            strokeDashArray: '2,2'
        },
        sourcePoint: {
            x: 300,
            y: 300
        },
        targetPoint: {
            x: 400,
            y: 400
        },
        segments: [{
            type: 'Orthogonal',
            direction: 'Right',
            length: 50
        }],
    }
]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors,
            getConnectorDefaults: (obj) => {
                obj.type = 'Orthogonal'
                return obj;
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

## Decorator Appearance

* The source decorator’s [`strokeColor`](../api/diagram/strokeStyle#strokecolor-string), [`strokeWidth`](../api/diagram/strokeStyle#strokewidth-number) and [`strokeDashArray`](../api/diagram/strokeStyle#strokedasharray-string) properties are used to customize the color and width and appearance of the decorator.

* To set the border stroke color, stroke width and stroke dash array for the target decorator, use [`strokeColor`](../api/diagram/strokeStyle#strokecolor-string), [`strokeWidth`](../api/diagram/strokeStyle#strokewidth-number) and [`strokeDashArray`](../api/diagram/strokeStyle#strokedasharray-string).

* To set the size for source decorator, use width and height property. Similarly, to set the size for target decorator, use width and height.

The following code example illustrates how to customize the appearance of the decorator.

{% tab template="diagram/connectors/ConnectorsDecAppearance", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
    id: "connector1",
    type: 'Straight',
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    bridgeSpace: 20,
    // Cutomize the target decorator
    targetDecorator: {
        style: {
            // Fill color of the decorator
            fill: '#6BA5D7',
            // Stroke color of the decorator
            strokeColor: '#6BA5D7'
        }
    },
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Interaction

* Diagram allows to edit the connectors at runtime. To edit the connector segments at runtime, refer to [`Connection Editing`](../api/diagram/connectorEditing).

## Automatic line routing

Diagram provides additional flexibility to re-route the diagram connectors. A connector will frequently re-route itself when a shape moves next to it. The following screenshot illustrates how the connector automatically re-routes the segments.  

* Dependency LineRouting module should be injected to the application as the following code snippet.

```html

<script>
import {DiagramPlugin,LineRouting,Diagram,DiagramConstraints } from '@syncfusion/ej2-vue-diagrams';
Diagram.Inject(LineRouting);
Vue.use(DiagramPlugin);
</script>

```

* Now, the line routing constraints must be included to the default diagram constraints to enable automatic line routing support like below.

```html

/**
 *  Initialize the Diagram
 */
  <ejs-diagram #diagram [constraints]='constraints'>

  <template>
  <div id="app">
        <ejs-diagram   :constraints='constraints' ></ejs-diagram>
    </div>
</template>

<script>
  // Enable line routing constraints.
let  constraints = DiagramConstraints.Default | DiagramConstraints.LineRouting;

</script>

```

* The following code block shows how to create the diagram with specifying nodes, connectors, constraints, and necessary modules for line routing.

{% tab template="diagram/connectors/ConnectorsLineRouting", isDefaultActive=true %}

```html

<template>
  <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :constraints='constraints' :nodes='nodes' :connectors='connectors' :getNodeDefaults='getNodeDefaults'></ejs-diagram>
    </div>
</template>

<script>

  import Vue from 'vue';
  import { DiagramPlugin,LineRouting,Diagram,DiagramConstraints } from '@syncfusion/ej2-vue-diagrams';
  Diagram.Inject(LineRouting);
  Vue.use(DiagramPlugin);

  let nodes = [
    { id: 'shape1', offsetX: 100, offsetY: 100, width: 120, height: 50 },
    { id: 'shape2', offsetX: 300, offsetY: 300, width: 120, height: 50 },
    { id: 'shape3', offsetX: 150, offsetY: 200, width: 120, height: 50 }
  ];

 let connectors  = [
   { id: 'connector', sourceID: 'shape1', targetID: 'shape2', type: 'Orthogonal' }
 ];

 function getNodeDefaults(obj) {
    obj = { style: { strokeColor: '#6BA5D7', fill: '#6BA5D7' } };
    return obj;
  }
let  constraints = DiagramConstraints.Default | DiagramConstraints.LineRouting;
export default {
   name: 'app',
        data () {
            return {
                width: "100%",
                height: "350px",
                connectors:connectors,
                nodes:nodes,
                constraints:constraints,
                getNodeDefaults: (obj) => {
                  obj = { style: { strokeColor: '#6BA5D7', fill: '#6BA5D7' } };
                  return obj;
               },
            }
        }
}
</script>

 <style>
    @import "../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
     @import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
</style>

```

{% endtab %}

* In some situations, automatic line routing enabled diagram needs to ignore a specific connector from automatic line routing. So, in this case, auto routing feature can be disabled to the specific connector using the [`constraints`](../api/diagram/connector#constraints-ConnectorConstraints) property of the connector like the following code snippet.

{% tab template="diagram/connectors/ConnectorsLineRoutingDisabled", isDefaultActive=true %}

```html

<template>
  <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :constraints='constraints' :nodes='nodes' :connectors='connectors' :getNodeDefaults='getNodeDefaults'></ejs-diagram>
    </div>
</template>
<script>

  import Vue from 'vue';
  import { DiagramPlugin,LineRouting,Diagram,DiagramConstraints,ConnectorConstraints } from '@syncfusion/ej2-vue-diagrams';
  Diagram.Inject(LineRouting);
  Vue.use(DiagramPlugin);

  let nodes = [
    { id: 'shape1', offsetX: 100, offsetY: 100, width: 120, height: 50 },
    { id: 'shape2', offsetX: 350, offsetY: 300, width: 120, height: 50 },
    { id: 'shape3', offsetX: 150, offsetY: 200, width: 120, height: 50 },
    { id: 'shape4', offsetX: 300, offsetY: 200, width: 120, height: 50 }
  ];

 let connectors  = [
    { id: 'connector', sourceID: 'shape1', targetID: 'shape2', type: 'Orthogonal', annotations: [{ offset: .7, content: ' Routing \n enabled', style: { fill: "white" } }] },
    { id: 'connector2', sourceID: 'shape1', targetID: 'shape2', annotations: [{ offset: .6, content: ' Routing \n disabled', style: { fill: "white" } }], type: 'Orthogonal', constraints: ConnectorConstraints.Default & ~ConnectorConstraints.InheritLineRouting }
 ];

 function getNodeDefaults(obj) {
    obj = { style: { strokeColor: '#6BA5D7', fill: '#6BA5D7' } };
    return obj;
  }
let  constraints = DiagramConstraints.Default | DiagramConstraints.LineRouting;
export default {
   name: 'app',
        data () {
            return {
                width: "100%",
                height: "350px",
                connectors:connectors,
                nodes:nodes,
                constraints:constraints,
                getNodeDefaults: (obj) => {
                  obj = { style: { strokeColor: '#6BA5D7', fill: '#6BA5D7' } };
                  return obj;
               },
            }
        }
}
</script>

<style>
    @import "../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
     @import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
</style>

```

{% endtab %}

## Constraints

* The [`constraints`](../api/diagram/connector#constraints-ConnectorConstraints) property of connector allows to enable/disable certain features of connectors.

* To enable or disable the constraints refer  [`constraints`](../api/diagram/connectorConstraints)

The following code illustrates how to disable selection.

{% tab template="diagram/connectors/ConnectorsConstraints", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,ConnectorConstraints } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
    id: "connector1",
    // Disables selection constraints
    constraints: ConnectorConstraints.Default & ~ConnectorConstraints.Select,
    type: 'Straight',
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Custom Properties

* The [`addInfo`](../api/diagram/connector#addinfo-Object) property of connectors allows to maintain additional information to connectors.

```javascript

let connectors: ConnectorModel = {
    id: 'connector1',
    // Defines the information about the connector
    addInfo:'centralconnector',
    type: 'Straight',
    sourceID: 'Transaction',
    targetID: 'Verification'
};

```

## Stack Order

* The connectors [`zIndex`](../api/diagram/connector#zindex-number) property specifies the stack order of an connector. A connector with greater stack order is always in front of an connector with a lower stack order.

The following code illustrates how to render connector based on the stack order.

{% tab template="diagram/connectors/zindex", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :connectors='connectors' :getConnectorDefaults='getConnectorDefaults'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,ConnectorConstraints } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let connectors = [{
        id: 'connector1',
        // Defines the z-index value for the connector
        zIndex: 2,
        type: 'Straight',
        sourcePoint: {
            x: 300,
            y: 100
        },
        targetPoint: {
            x: 300,
            y: 200
        }
    },
    {
        id: 'connector2',
        type: 'Straight',
        // Defines the z-index value for the connector
        zIndex: 1,
        sourcePoint: {
            x: 100,
            y: 100
        },
        targetPoint: {
            x: 200,
            y: 200
        }
    }
]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors,
            getConnectorDefaults: (obj) => {
                obj.style.strokeColor = '#6BA5D7';
                obj.style.fill = '#6BA5D7';
                obj.style.strokeWidth = 2;
                obj.targetDecorator.style.fill = '#6BA5D7';
                obj.targetDecorator.style.strokeColor = '#6BA5D7';
                return obj;
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

## See Also

* [How to add annotations to the connector](./labels)
* [How to enable/disable the behavior of the node](./constraints)
* [How to add connectors to the symbol palette](./symbol-palette)
* [How to perform the interaction on the connector](./interaction#connection-editing)
* [How to create diagram connectors using drawing tools](./tools)