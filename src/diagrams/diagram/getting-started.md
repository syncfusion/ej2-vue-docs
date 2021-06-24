---
title: "Getting Started"
component: "Diagram"
description: "Diagram getting started creates your first flow diagram and organizational chart diagram."
---

# Getting started

This section explains the steps required to create a simple diagram and demonstrates the basic usage of the diagram control.

## Dependencies

The following list of dependencies are required to use the `Diagram` component in your application.

```javascript
|-- @syncfusion/ej2-vue-diagrams
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-splitbuttons
    |-- @syncfusion/ej2-diagrams
    |-- @syncfusion/ej2-vue-base
```

## Get Started with Vue CLI

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications.
To install Vue CLI use the following command.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

Start a new project using below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install

```

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`Node Package Manager`](https://www.npmjs.com/~syncfusionorg) registry.
You can choose the component that you want to install. For this application, we are going to use Diagram component.

To install Diagram component, use the following command

```bash
npm install @syncfusion/ej2-vue-diagrams –save
```

## Registering Vue Component

For Registering Vue Component two ways are available. They are as follows.
* Vue.use()
* Vue.component()

### Using Vue.use()

Import the Component Plugin from the EJ2 Vue Package and register the same using Vue.use() with Component Plugin as its argument.

Refer the code snippet given below.

```typescript
import { DiagramPlugin } from '@syncfuion/ej2-vue-diagrams';

Vue.use(DiagramPlugin);
```

Note : By Registering Component Plugin in Vue, all child directives are also globally registered.

### Using Vue.component()

Import the Component and Component Plugin from EJ2 Vue Package,
register the same using the Vue.component() with name of Component from ComponentPlugin
and the EJ2 Vue Component as its arguments.

Refer the code snippet given below.

```typescript
import { DiagramComponent, DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

Vue.component(DiagramPlugin.name, DiagramComponent);
```

> By using Vue.component(), only the EJ2 Vue Component is registered. Child directives needs to be registered separately.

## Creating Vue Sample

Add the EJ2 Vue Diagram using `<ejs-diagrams>` to the `<template>` section of the `App.vue` file in src directory,
the content attribute of the Diagram component is provided as name in data option in the `<script>` section.

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);
    export default {
        name: 'app'
        data () {
            return {
                width: "100%",
                height: "350px"
            }
        }
    }
</script>
```

## Adding CSS Reference

Add Diagram component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
    @import "../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

## Running the Application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="diagram/getting-started/initialize", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' ></ejs-diagram>
    </div>
</template>
<script>
import Vue from 'vue';
import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

Vue.use(DiagramPlugin);
export default {
    name: 'app'
    data () {
        return {
            width: "100%",
            height: "350px"
        }
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Module Injection

Diagram component are segregated into individual feature-wise modules. In order to use a particular feature,
you need to inject its feature service in the AppModule. Please find relevant
feature service name and description as follows.

* `BpmnDiagrams` - Inject this provider to add built-in BPMN Shapes to diagrams.
* `ConnectorBridging` - Inject this provider to add bridges to connectors.
* `ConnectorEditing` - Inject this provider to edit the segments for connector.
* `ComplexHierarchicalTree` - Inject this provider to complex hierarchical tree like structure.
* `DataBinding` - Inject this provider to populate nodes from given data source.
* `DiagramContextMenu` - Inject this provider to manipulate context menu.
* `HierarchicalTree` - Inject this provider to use hierarchical tree like structure.
* `LayoutAnimation` - Inject this provider animation to layouts.
* `MindMap` - Inject this provider to use mind map.
* `PrintAndExport` - Inject this provider to print or export the objects.
* `RadialTree` - Inject this provider to use Radial tree like structure.
* `Snapping` - Inject this provider to Snap the objects.
* `SymmetricLayout` - Inject this provider to render layout in symmetrical method.
* `UndoRedo` - Inject this provider to revert and restore the changes.

These modules should be imported and injected into the Diagram component using `Diagram.Inject` method as follows.

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' ></ejs-diagram>
    </div>
</template>
<script>
import Vue from 'vue';
import { DiagramPlugin, HierarchicalTree, MindMap, RadialTree, ComplexHierarchicalTree, DataBinding, Snapping, PrintAndExport, BpmnDiagrams, SymmetricLayout, ConnectorBridging, UndoRedo, LayoutAnimation, DiagramContextMenu, ConnectorEditing } from '@syncfusion/ej2-vue-diagrams';

Vue.use(DiagramPlugin);
export default {
    name: 'app'
    data () {
            return {
                width: "100%",
                height: "350px"
            }
    },
    provide:{
        diagram: [BpmnDiagrams, ConnectorBridging, ConnectorEditing, ComplexHierarchicalTree, DataBinding,DiagramContextMenu, HierarchicalTree, LayoutAnimation, MindMap, PrintAndExport, RadialTree, Snapping, SymmetricLayout, UndoRedo]
    },
}
</script>
```

## Flow Diagram

### Create and Add Node

Create and add a `node` (JSON data) with specific position, size, label, and shape.

{% tab template="diagram/getting-started/addnode", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [
        {
            id: "node1",
            height: 60,
            offsetX: 300,
            offsetY: 80,
            annotations: [
                {
                    content: "start"
                }
            ]
        }
    ]
    export default {
        name: 'app'
        data () {
            return {
                width: "100%",
                height: "350px",
                nodes: nodes,
            }
        }
    }
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

### Connect Nodes

Add two node to the diagram as shown in the previous example. Connect these nodes by adding a connector using the `connector` property and refer the source and target end by using the `sourceNode` and `targetNode` properties.

{% tab template="diagram/getting-started/connectnode", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :connectors='connectors' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [
        {
            id: "node1",
            height: 100,
            width: 100,
            offsetX: 200,
            offsetY: 100,
        },
        {
            id: "node2",
            height: 100,
            width: 100,
            offsetX: 200,
            offsetY: 300,
        }
    ];

    let connectors = [
        {
            id: "connector1",
            sourceID: "node1",
            targetID: "node2"
        },
    ]
    export default {
    name: 'app'
        data () {
            return {
                width: "100%",
                height: "350px",
                nodes: nodes,
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

Default values for all `nodes` and `connectors` can be set using the `getNodeDefaults` and `getConnectorDefaults` properties, respectively. For example, if all nodes have the same width and height, such properties can be moved into `getNodeDefaults`.

### Complete Flow Diagram

Similarly, the required nodes and connectors can be added to form a complete flow diagram.

{% tab template="diagram/getting-started/flowdiagram", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :connectors='connectors' :getNodeDefaults='getNodeDefaults' :getConnectorDefaults='getConnectorDefaults' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin } from '@syncfusion/ej2-vue-diagrams';

    Vue.use(DiagramPlugin);

    let nodes = [
        {
            id: "node1",
            offsetY: 50,
            shape: { type: "Flow", shape: "Terminator" },
            annotations: [
            {
                content: "Start"
            }
            ]
        },
        {
            id: "node2",
            offsetY: 140,
            shape: { type: "Flow", shape: "Process" },
            annotations: [
            {
                content: "var i = 0;"
            }
            ]
        },
        {
            id: "node3",
            offsetY: 230,
            shape: { type: "Flow", shape: "Decision" },
            annotations: [
            {
                content: "i < 10?"
            }
            ]
        },
        {
            id: "node4",
            offsetY: 320,
            shape: { type: "Flow", shape: "PreDefinedProcess" },
            annotations: [
            {
                content: 'print("Hello!!");',
                style: { fill: "white" }
            }
            ]
        },
        {
            id: "node5",
            offsetY: 410,
            shape: { type: "Flow", shape: "Process" },
            annotations: [
            {
                content: "i++;"
            }
            ]
        },
        {
            id: "node6",
            offsetY: 500,
            shape: { type: "Flow", shape: "Terminator" },
            annotations: [
            {
                content: "End"
            }
            ]
        }
    ];

    let connectors = [
        {
            id: "connector1",
            sourceID: "node1",
            targetID: "node2"
        },
        {
            id: "connector2",
            sourceID: "node2",
            targetID: "node3"
        },
        {
            id: "connector3",
            sourceID: "node3",
            targetID: "node4",
            annotations: [{ text: "Yes" }]
        },
        {
            id: "connector4",
            sourceID: "node3",
            targetID: "node6",
            labels: [{ text: "No" }],
            segments: [
            { length: 30, direction: "Right" },
            { length: 300, direction: "Bottom" }
            ]
        },
        {
            id: "connector5",
            sourceID: "node4",
            targetID: "node5"
        },
        {
            id: "connector6",
            sourceID: "node5",
            targetID: "node3",
            segments: [
            { length: 30, direction: "Left" },
            { length: 200, direction: "Top" }
            ]
        }
    ];
    export default {
        name: 'app',
        data () {
            return {
                width: "100%",
                height: "600px",
                nodes: nodes,
                connectors: connectors,
                getNodeDefaults: (node) => {
                    node.height = 60;
                    node.width = 100;
                    node.offsetX = 300;
                    return node;
                },
                getConnectorDefaults: (obj) => {
                    obj.type = 'Orthogonal';
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

## Automatic Organization Chart

In the 'Flow Diagram' section, how to create a diagram manually was discussed. This section explains how to create and position the diagram automatically.

### Business object (Employee information)

Define Employee Information as JSON data. The following code example shows an employee array whose, `Name` is used as an unique identifier and `ReportingPerson` is used to identify the person to whom an employee report to, in the organization.

```typescript

    public data: Object[] = [
        {
            Name: "Elizabeth",
            Role: "Director"
        },
        {
            Name: "Christina",
            ReportingPerson: "Elizabeth",
            Role: "Manager"
        },
        {
            Name: "Yoshi",
            ReportingPerson: "Christina",
            Role: "Lead"
        },
        {
            Name: "Philip",
            ReportingPerson: "Christina",
            Role: "Lead"
        },
        {
            Name: "Yang",
            ReportingPerson: "Elizabeth",
            Role: "Manager"
        },
        {
            Name: "Roland",
            ReportingPerson: "Yang",
            Role: "Lead"
        },
        {
            Name: "Yvonne",
            ReportingPerson: "Yang",
            Role: "Lead"
        }
    ];

```

### Map data source

You can configure the above "Employee Information" with diagram, so that the nodes and connectors are automatically generated using the mapping properties. The following code example show how `dataSourceSettings` is used to map ID and parent with property name identifiers for employee information.

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram" :width='width' :height='height' :dataSourceSettings='dataSourceSettings' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin, HierarchicalTree, DataBinding } from '@syncfusion/ej2-vue-diagrams';
    import { DataManager } from "@syncfusion/ej2-data";
    Vue.use(DiagramPlugin);

    export let localdata = [
        {
            Name: "Elizabeth",
            Role: "Director"
        },
        {
            Name: "Christina",
            ReportingPerson: "Elizabeth",
            Role: "Manager"
        },
        {
            Name: "Yoshi",
            ReportingPerson: "Christina",
            Role: "Lead"
        },
        {
            Name: "Philip",
            ReportingPerson: "Christina",
            Role: "Lead"
        },
        {
            Name: "Yang",
            ReportingPerson: "Elizabeth",
            Role: "Manager"
        },
        {
            Name: "Roland",
            ReportingPerson: "Yang",
            Role: "Lead"
        },
        {
            Name: "Yvonne",
            ReportingPerson: "Yang",
            Role: "Lead"
        }
    ];
    export default {
        name: 'app',
        data () {
            return {
                width: "100%",
                height: "350px",
                dataSourceSettings: {
                    id: 'Name', parentId: 'ReportingPerson',
                    dataManager: new DataManager(localdata),
                    doBinding: (nodeModel, localdata, diagram) => {
                        nodeModel.shape = {
                            type: "Text",
                            content: (localdata).Role,
                        }
                    }
                }
            }
        }
    }
</script>
```

### Visualize employee

The following code examples indicate how to define the default appearance of nodes and connectors. The `setNodeTemplate` is used to update each node based on employee data.

{% tab template="diagram/getting-started/orgchart", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram" :width='width' :height='height'  :getNodeDefaults='getNodeDefaults' :getConnectorDefaults='getConnectorDefaults' :layout='layout' :dataSourceSettings='dataSourceSettings' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin, HierarchicalTree, DataBinding } from '@syncfusion/ej2-vue-diagrams';
    import { DataManager } from "@syncfusion/ej2-data";
    Vue.use(DiagramPlugin);

    export let localdata = [
            {
                Name: "Elizabeth",
                Role: "Director"
            },
            {
                Name: "Christina",
                ReportingPerson: "Elizabeth",
                Role: "Manager"
            },
            {
                Name: "Yoshi",
                ReportingPerson: "Christina",
                Role: "Lead"
            },
            {
                Name: "Philip",
                ReportingPerson: "Christina",
                Role: "Lead"
            },
            {
                Name: "Yang",
                ReportingPerson: "Elizabeth",
                Role: "Manager"
            },
            {
                Name: "Roland",
                ReportingPerson: "Yang",
                Role: "Lead"
            },
            {
                Name: "Yvonne",
                ReportingPerson: "Yang",
                Role: "Lead"
            }
        ];
    export default {
        name: 'app',
        data () {
            return {
                width: "100%",
                height: "350px",
                getNodeDefaults: (node) => {
                    node.height = 60;
                    node.width = 100;
                    return node;
                },
                getConnectorDefaults: (obj) => {
                    obj.type = 'Orthogonal';
                    return obj;
                },
                layout: {
                    type: "OrganizationalChart",
                },
                dataSourceSettings: {
                    id: 'Name', parentId: 'ReportingPerson',
                    dataManager: new DataManager(localdata),
                    doBinding: (nodeModel, localdata, diagram) => {
                        nodeModel.shape = {
                            type: "Text",
                            content: (localdata).Role,
                        }
                    }
                }
            }
        },
        provide: {diagram: [DataBinding, HierarchicalTree]},
    }
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}
