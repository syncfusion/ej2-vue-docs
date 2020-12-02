---
title: "Tools"
component: "Diagram"
description: "Drawing tool allows you to draw any kind of node/connector during runtime by clicking the desired shapes/connector and drawing it on a page. "
---

# Tools

## Drawing tools

Drawing tool allows you to draw any kind of node/connector during runtime by clicking and dragging on the diagram page.

## Shapes

To draw a shape, set the JSON of that shape to the drawType property of the diagram and activate the drawing tool by using the [`tool`](../api/diagram/diagram) property. The following code example illustrates how to draw a rectangle at runtime.

{% tab template="diagram/Tools/shape", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :getNodeDefaults='getNodeDefaults'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,DiagramTools,BasicShapeModel,NodeModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            getNodeDefaults: (obj) => {
        obj.height = 15;
        obj.width = 15;
        obj.borderWidth = 1;
        obj.style = {
            fill: '#6BA5D7',
            strokeWidth: 2,
            strokeColor: '#6BA5D7'
        };
        return obj;
    },
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let drawingshape: BasicShapeModel = { type: 'Basic', shape: 'Rectangle' };
        let node: NodeModel = {
            shape: drawingshape
        };
        diagramInstance.drawingObject = node;
        //To draw an object once, activate draw once
        diagramInstance.tool = DiagramTools.DrawOnce;
        diagramInstance.dataBind();
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Path

The following code example illustrates how to draw a path.

{% tab template="diagram/Tools/path", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :getNodeDefaults='getNodeDefaults'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,DiagramTools,BasicShapeModel,NodeModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            getNodeDefaults: (obj) => {
        obj.height = 15;
        obj.width = 15;
        obj.borderWidth = 1;
        obj.style = {
            fill: '#6BA5D7',
            strokeWidth: 2,
            strokeColor: '#6BA5D7'
        };
        return obj;
    },
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let node: NodeModel = {
            id: "Path",
            style: { fill: "#fbe172" },
            annotations: [{
                content: "Path"
            }],
            shape: {
                type:'Path',
                data: 'M13.560 67.524 L 21.941 41.731 L 0.000 25.790 L 27.120 25.790 L 35.501 0.000 L 43.882 25.790 L 71.000 25.790 L 49.061 41.731 L 57.441 67.524 L 35.501 51.583 z'
            } as PathModel
        };
        diagramInstance.drawingObject = node;
        //To draw an object once, activate draw once
        diagramInstance.tool = DiagramTools.DrawOnce;
        diagramInstance.dataBind();
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Connectors

To draw connectors, set the JSON of the connector to the drawType property. The drawing [`tool`](../api/diagram/diagram) can be activated by using the tool property. The following code example illustrates how to draw a straight line connector.

{% tab template="diagram/Tools/connector", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :getNodeDefaults='getNodeDefaults'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,DiagramTools,BasicShapeModel,ConnectorModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            getNodeDefaults: (obj) => {
        obj.height = 15;
        obj.width = 15;
        obj.borderWidth = 1;
        obj.style = {
            fill: '#6BA5D7',
            strokeWidth: 2,
            strokeColor: '#6BA5D7'
        };
        return obj;
    },
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let connectors: ConnectorModel = {
            id: 'connector1',
            type: 'Straight',
           segments: [{ type: "polyline" }]
        }
        diagramInstance.drawingObject = connectors;
        //To draw an object once, activate draw once
        diagramInstance.tool = DiagramTools.DrawOnce;
        diagramInstance.dataBind();
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Text

Diagram allows you to create a textNode, when you click on the diagram page. The following code illustrates how to draw a text.

{% tab template="diagram/Tools/text", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :getNodeDefaults='getNodeDefaults'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,DiagramTools,BasicShapeModel,TextModel,NodeModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            getNodeDefaults: (obj) => {
        obj.height = 15;
        obj.width = 15;
        obj.borderWidth = 1;
        obj.style = {
            fill: '#6BA5D7',
            strokeWidth: 2,
            strokeColor: '#6BA5D7'
        };
        return obj;
    },
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let node: NodeModel = {
                   shape: {
                type:'Text',
            } as TextModel
        };
        diagramInstance.drawingObject = node;
        //To draw an object once, activate draw once
        diagramInstance.tool = DiagramTools.DrawOnce;
        diagramInstance.dataBind();
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

Once you activate the TextTool, perform label editing of a node/connector.

## Polygon shape

Diagram allows to create the polygon shape by clicking and moving the mouse at runtime on the diagram page.

The following code illustrates how to draw a polygon shape.

{% tab template="diagram/Tools/polygon", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :getNodeDefaults='getNodeDefaults'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,DiagramTools,BasicShapeModel,BasicShapeModel,NodeModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            getNodeDefaults: (obj) => {
        obj.height = 15;
        obj.width = 15;
        obj.borderWidth = 1;
        obj.style = {
            fill: '#6BA5D7',
            strokeWidth: 2,
            strokeColor: '#6BA5D7'
        };
        return obj;
    },
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        let drawingshape: BasicShapeModel = { type: 'Basic', shape: 'Polygon' };
        //JSON to create a polygon
        let node: NodeModel = {
            shape: drawingshape
        };
        diagramInstance.drawingObject = node;
        //To draw an object once, activate draw once
        diagramInstance.tool = DiagramTools.DrawOnce;
        diagramInstance.dataBind();
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Polyline Connector

Diagram allows to create the polyline segments with straight lines and angled vertices at the control points by clicking and moving the mouse at runtime on the diagram page.

The following code illustrates how to draw a polyline connector.

{% tab template="diagram/Tools/polyline", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :getNodeDefaults='getNodeDefaults'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,DiagramTools,ConnectorModel} from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            getNodeDefaults: (obj) => {
        obj.height = 15;
        obj.width = 15;
        obj.borderWidth = 1;
        obj.style = {
            fill: '#6BA5D7',
            strokeWidth: 2,
            strokeColor: '#6BA5D7'
        };
        return obj;
    },
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        //JSON to create a polyline
        let connector: ConnectorModel = { id: 'connector1', type: 'Polyline'};
        diagramInstance.drawingObject = connector;
        //To draw an object once, activate draw once
        diagramInstance.tool = DiagramTools.DrawOnce;
        diagramInstance.dataBind();
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Tool selection

There are some functionalities that can be achieved by clicking and dragging on the diagram surface. They are as follows.

* Draw selection rectangle: MultipleSelect tool
* Pan the diagram: Zoom pan
* Draw nodes/connectors: DrawOnce/DrawOnce

As all the three behaviors are completely different, you can achieve only one behavior at a time based on the tool that you choose.
When more than one of those tools are applied, a tool is activated based on the precedence given in the following table.

|Precedence|Tools|Description|
|----------|-----|-----------|
|1st|ContinuesDraw|Allows you to draw the nodes or connectors continuously. Once it is activated, you cannot perform any other interaction in the diagram.|
|2nd|DrawOnce|Allows you to draw a single node or connector. Once you complete the DrawOnce action, SingleSelect, and MultipleSelect tools are automatically enabled.|
|3rd|ZoomPan|Allows you to pan the diagram. When you enable both the SingleSelect and ZoomPan tools, you can perform the basic interaction as the cursor hovers node/connector. Panning is enabled when cursor hovers the diagram.|
|4th|MultipleSelect|Allows you to select multiple nodes and connectors. When you enable both the MultipleSelect and ZoomPan tools, cursor hovers the diagram. When panning is enabled, you cannot select multiple nodes.|
|5th|SingleSelect|Allows you to select individual nodes or connectors.|
|6th|None|Disables all tools.|

Set the desired [`tool`](../api/diagram/diagram) to the tool property of the diagram model. The following code illustrates how to enable single/multiple tools.

```javascript
export default {
    name: 'app'
        data () {
            return {
                width: "100%",
                height: "350px",
                tool:DiagramTools.DrawOnce || DiagramTools.ZoomPan,
            }
        }
    }

```