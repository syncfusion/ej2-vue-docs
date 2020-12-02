---
title: "Constraints"
component: "Diagram"
description: "Diagram constraints allow you to enable/disable certain behaviors of the diagram, nodes and connectors."
---

# Constraints

Constraints are used to enable/disable certain behaviors of the diagram, nodes and connectors. Constraints are provided as flagged enumerations, so that multiple behaviors can be enabled/disabled using Bitwise operators (&, |, ~, <<, etc.).

To know more about Bitwise operators, refer to [`Bitwise Operations`](#bitwise-operations).

## Diagram constraints

Diagram constraints allow to enable or disable the following behaviors:

* Page editing
* Bridging
* Zoom and pan
* Undo/redo
* Tooltip

The following example illustrates how to disable page editing using the diagram constraints.

```javascript
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            constraints: DiagramConstraints.Default & ~DiagramConstraints.PageEditable
        }
    }
}
```

For more information about diagram constraints, refer to [`DiagramConstraints`](../api/diagram/diagramConstraints).

## Node constraints

Node constraints allows to enable or disable the following behaviors of node. They are as follows:

* Selection
* Deletion
* Drag
* Resize
* Rotate
* Connect
* Shadow
* Tooltip

The following example illustrates how to disable rotation using the node constraints.

```javascript
let nodes = [{
    id: "node1",
    height: 60,
    offsetX: 300,
    offsetY: 80,
    constraints: NodeConstraints.Default & ~NodeConstraints.Rotate,
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
            nodes: nodes,
        }
    }
}
```

For more information about node constraints, refer to [`NodeConstraints`](../api/diagram/nodeConstraints).

## Connector constraints

Connector constraints allow to enable or disable certain behaviors of connectors.

* Selection
* Deletion
* Drag
* Segment editing
* Tooltip
* Bridging

The following code illustrates how to disable selection by using connector constraints.

```javascript
let connectors = [{
    id: 'connector1',
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    constraints: ConnectorConstraints.Default & ~ConnectorConstraints.Select
}]

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors,
        }
    }
}
```

For more information about connector constraints, refer to [`ConnectorConstraints`](../api/diagram/connectorConstraints).

## Port constraints

You can enable or disable certain behaviors of port. They are as follows:

* Connect
* ConnectOnDrag

The following code illustrates how to disable creating connections with a port.

```javascript
let nodes = [{
    id: 'connector1',
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    ports: [{
        constraints: PortConstraints.None
    }]
}]

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
        }
    }
}
```

For more information about port constraints, refer to [`PortConstraints`](../api/diagram/portConstraints).

## Annotation constraints

You can enable or disable read-only mode for the annotations by using the annotation constraints.

The following code illustrates how to enable read-only mode for the annotations.

```javascript
let nodes = [{
    id: 'connector1',
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    annotations: [{
        id: 'anotation_1',
        content: 'annotation',
        constraints: AnnotationConstraints.ReadOnly,
    }]
}]

export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
        }
    }
}
```

For more details about annotation constraints, refer to [`AnnotationConstraints`](../api/diagram/annotationConstraints).

## Selector constraints

Selector visually represents the selected elements with certain editable thumbs. The visibility of the thumbs can be controlled with selector constraints. The part of selector is categorized as follows:

* Resizer
* Rotator
* User handles

The following code illustrates how to hide rotator.

```javascript
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            selectedItems: {
                constraints: SelectorConstraints.All & ~SelectorConstraints.Rotate
            }
        }
    }
}
```

For more information about selector constraints, refer to [`SelectorConstraints`](../api/diagram/selectorConstraints).

## Snap constraints

Snap constraints control the visibility of gridlines and enable/disable snapping. Snap constraints allow to set the following behaviors.

* Show only horizontal or vertical gridlines.
* Show both horizontal and vertical gridlines.
* Snap to either horizontal or vertical gridlines.
* Snap to both horizontal and vertical gridlines.

The following code illustrates how to show only horizontal gridlines.

```javascript
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            snapSettings: {
                constraints: SnapConstraints.ShowHorizontalLines
            }
        }
    }
}
```

For more information about snap constraints, refer to [`SnapConstraints`](../api/diagram/snapConstraints).

## Boundary constraints

Boundary constraints defines a boundary for the diagram inside which the interaction should be done. Boundary constraints allow to set the following behaviors.

* Infinite boundary
* Diagram sized boundary
* Page sized boundary

The following code illustrates how to limit the interaction done inside a diagram within a page.

```javascript
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            pageSettings: {
                boundaryConstraints: 'Page'
            }
        }
    }
}
```

For more information about selector constraints, refer to [`BoundaryConstraints`](../api/diagram/boundaryConstraints).

## Inherit behaviors

Some of the behaviors can be defined through both the specific object (node/connector) and diagram. When the behaviors are contradictorily defined through both, the actual behavior is set through inherit options.

The following code example illustrates how to inherit the line bridging behavior from the diagram model.

```javascript
Diagram.Inject(ConnectorBridging);
let connectors[] = [{
    id: 'connector1',
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    constraints: ConnectorConstraints.Default & ConnectorConstraints.InheritBridging
}];
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            connectors: connectors,
            constraints: DiagramConstraints.Default | DiagramConstraints.Bridging
        }
    }
}
```

## Bitwise operations

Bitwise operations are used to manipulate the flagged enumerations [enum]. In this section, Bitwise operations are illustrated by using node constraints. The same is applicable while working with node constraints, connector constraints, or port constraints.

## Add operation

You can add or enable multiple values at a time by using Bitwise ‘|’ (OR) operator.

```javascript
node.constraints = NodeConstraints.Select | NodeConstraints.Rotate;
```

In the previous example, you can do both the selection and rotation operation.

## Remove Operation

You can remove or disable values by using Bitwise ‘&~’ (XOR) operator.

```javascript
node.constraints = node.constraints & ~(NodeConstraints.Rotate);
```

In the previous example, rotation is disabled but other constraints are enabled.

## Check Operation

You can check any value by using Bitwise ‘&’ (AND) operator.

```javascript
if ((node.constraints & (NodeConstraints.Rotate)) == (NodeConstraints.Rotate));
```

In the previous example, check whether the rotate constraints are enabled in a node. When node constraints have rotate constraints, the expression returns a rotate constraint.