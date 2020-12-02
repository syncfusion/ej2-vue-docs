---
title: "Undo and redo"
component: "Diagram"
description: "Undo and redo provides support to reverse and restore the performed changes."
---

# History List

Diagram tracks the history of actions that are performed after initializing the diagram and provides support to reverse and restore those changes.

## Undo and redo

Diagram provides built-in support to track the changes that are made through interaction and through public APIs. The changes can be reverted or restored either through shortcut keys or through commands.

>Note: If you want to use Undo-Redo in diagram, you need to inject UndoRedo in the diagram.

## Undo/redo through shortcut keys

Undo/redo commands can be executed through shortcut keys. Shortcut key for undo is Ctrl+z and shortcut key for redo is Ctrl+y.

## Undo/redo through public APIs

The client-side methods [`undo`](../api/diagram/diagram) and [`redo`](../api/diagram/diagram) help you to revert/restore the changes. The following code example illustrates how to undo/redo the changes through script.

```javascript
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
        // Reverts the last action performed
        diagramInstance.undo();

        // Restores the last undone action
        diagramInstance.redo();
    }
}

```

When a change in the diagram is reverted or restored (undo/redo), the historyChange event gets triggered.

### Group multiple changes

History list allows to revert or restore multiple changes through a single undo/redo command. For example, revert/restore the fill color change of multiple elements at a time.

The client-side method [`startGroupAction`](../api/diagram/diagram) is used to notify the diagram to start grouping the changes. The client-side method [`endGroupAction`](../api/diagram/diagram) is used to notify to stop grouping the changes. The following code illustrates how to undo/redo fillColor change of multiple elements at a time.

{% tab template="diagram/undo-redo/undo-redo", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes' :getNodeDefaults='getNodeDefaults' ></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin ,UndoRedo,Diagram} from '@syncfusion/ej2-vue-diagrams';
    Diagram.Inject(UndoRedo);

    Vue.use(DiagramPlugin);

    let nodes = [{
    id: 'Start',
    width: 140,
    height: 50,
    offsetX: 300,
    offsetY: 50,
    annotations: [{
        id: 'label1',
        content: 'Start'
    }],
    shape: {
        type: 'Flow',
        shape: 'Terminator'
    }
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            getNodeDefaults: (node) => {
                node.height =  100;
                node.width =  100;
                node.style.fill =  '#6BA5D7';
                node.style.strokeColor =  'white';
                return  node;
            },
        }
    }
    mounted: function() {
        let diagramInstance: Diagram;
        let diagramObj: any = document.getElementById("diagram");
        diagramInstance = diagramObj.ej2_instances[0];
        //Start to group the changes
        diagramInstance.startGroupAction();
        //Makes the changes
        let color: string[] = ['black', 'red', 'green', 'yellow']
        for (var i = 0; i < color.length; i++) {
            // Updates the fillColor for all the child elements.
            diagramInstance.nodes[0].style.fill = color[i];
            diagramInstance.dataBind();
        }

        //Ends grouping the changes
        diagramInstance.endGroupAction();
    }
}
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

### Track custom changes

Diagram provides options to track the changes that are made to custom properties. For example, in case of an employee relationship diagram, track the changes in the employee information. The historyList of the diagram enables you to track such changes.
The following example illustrates how to track such custom property changes.

Before changing the employee information, save the existing information to historyList by using the client-side method push of historyList.
The historyList canLog method can be used which takes a history entry as argument and returns whether the specific entry can be added or not.

The following code example illustrates how to save the existing property values.

```javascript
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
        //Creates a custom entry
        let entry: HistoryEntry = {
            undoObject: diagramInstance.nodes[0];
        };
        // adds that to history list
        diagramInstance.historyList.push(entry);
        diagramInstance.dataBind();
    }
}

```

## canLog

canLog in the history list, which takes a history entry as argument and returns whether the specific entry can be added or not.

{% tab template="diagram/undo-redo/undo-redo", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes'
        :getNodeDefaults='getNodeDefaults'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,UndoRedo ,Diagram} from '@syncfusion/ej2-vue-diagrams';
    Diagram.Inject(UndoRedo);

    Vue.use(DiagramPlugin);

    let nodes = [{
    id: 'Start',
    width: 140,
    height: 50,
    offsetX: 300,
    offsetY: 50,
    annotations: [{
        id: 'label1',
        content: 'Start'
    }],
    shape: {
        type: 'Flow',
        shape: 'Terminator'
    }
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
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
        // canLog decide whether the entry add or not in history List
        diagramInstance.historyList.canLog = function(entry: HistoryEntry) {
            entry.cancel = true;
            return entry;
        }
    }
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

### Track undo/redo actions

The historyList undoStack property is used to get the collection of undo actions which should be performed in the diagram.
The undoStack/redoStack is the read-only property.

```javascript
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
        //get the collection of undoStack objects
        let undoStack = diagramInstance.historyList.undoStack;
        //get the collection of redoStack objects
        let redoStack = diagramInstance.historyList.redoStack;
    }
}

```

## History change event

The [`historychange`](../api/diagram/diagram) event triggers, whenever the interaction of the node and connector is take place.

```javascript
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
        diagramInstance.historyChange = (arg: IHistoryChangeArgs) => {
            //causes of history change
            let cause: string = arg.cause;
        }
    }
}

```

## Stack limit

The [`stackLimit`](../api/diagram) property of history manager is used to limits the number of actions to be stored on the history manager.

{% tab template="diagram/undo-redo/undo-redo", isDefaultActive=true %}

```html
<template>
    <div id="app">
        <ejs-diagram id="diagram"  :width='width' :height='height' :nodes='nodes'
        :getNodeDefaults='getNodeDefaults'></ejs-diagram>
    </div>
</template>
<script>
    import Vue from 'vue';
    import { DiagramPlugin,UndoRedo ,Diagram} from '@syncfusion/ej2-vue-diagrams';
    Diagram.Inject(UndoRedo);

    Vue.use(DiagramPlugin);

    let nodes = [{
     id: 'Start',
    width: 140,
    height: 50,
    offsetX: 300,
    offsetY: 50,
    annotations: [{
        id: 'label1',
        content: 'Start'
    }],
    shape: {
        type: 'Flow',
        shape: 'Terminator'
    }
}]
export default {
    name: 'app'
    data() {
        return {
            width: "100%",
            height: "350px",
            nodes: nodes,
            getNodeDefaults: (node) => {
                node.height = 100;
                node.width = 100;
                node.style.fill = '#6BA5D7';
                node.style.strokeColor = 'white';
                return node;
            },
            historyManager:{
                stackLimit:2
            }
        }
    }
</script>
<style>
    @import "../../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
```

{% endtab %}

## Retain selection

You can retain a selection at undo/redo operation by using the client-side API Method called `updateSelection`.  Using this method, we can select a diagram objects.

```typescript
let diagramInstance: DiagramComponent;
ReactDOM.render( < DiagramComponent id = "diagram" ref={diagram => diagramInstance = diagram}
        width = {
            '100%'
        }
        height = {
            '600px'
        }
        nodes = {
            nodes
        }
        />,   document.getElementById("diagram") );
        // history change event
        diagramInstance.updateSelection: (object: NodeModel, diagram: Diagram) => {
                    let selArr = [];
                    selArr.push(object)
                    diagram.select(selArr);
                },

```