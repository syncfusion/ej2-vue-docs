---
title: "Drag and Drop"
component: "TreeView"
description: "This section explains how to drag a single or multiple tree nodes and drop it to the all levels of the same tree view"
---

# Drag and Drop

The TreeView component allows you to drag and drop any node by setting [allowDragAndDrop](../api/treeview#allowdraganddrop)
&nbsp;to **true**. Nodes can be dragged and dropped at all levels of the same TreeView.

The dragged nodes can be dropped at any level by indicator lines with **plus**, **minus/restrict**, and **in between** icons.
It represents the exact position where the node is to be dropped as sibling or child.

If you need to prevent dragging action for a particular node, the [`nodeDragStart`](../api/treeview#nodedragstart) event can be used which is triggered when the node drag is started. If you need to prevent dropping action for a particular node, the [`nodeDragStop`](../api/treeview#nodedragstop) event can be used which is triggered when the drag is stopped.

The [`nodeDragging`](../api/treeview#nodedragging) event is triggered when the TreeView node is being dragged. You can customize the cloned element in this event.

The [`nodeDropped`](../api/treeview#nodedropped) event is triggered when the TreeView node is dropped on the target element successfully.

The following table explains the usage of indicator icons.

| Icons | Description |
|------|-------------|
| Plus icon | Indicates that the dragged node is to be added as child of target node. |
| Minus or restrict icon |Indicates that the dragged node is not to be dropped at the hovered region. |
| In between icon | Indicates that the dragged node is to be added as siblings of hovered region. |

In the following sample, the [allowDragAndDrop](../api/treeview#allowdraganddrop) property is enabled.

{% tab template="treeview/drag-and-drop/single", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div class="control_wrapper">
        <ejs-treeview id='treeview' :fields="fields" :allowDragAndDrop='true'></ejs-treeview>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { TreeViewPlugin } from "@syncfusion/ej2-vue-navigations";

Vue.use(TreeViewPlugin);
export default {
  data () {
    var dataSource =  [
        {
        id: 1, name: 'ASP.NET MVC Team', expanded: true,
        child: [
            { id: 2, pid: 1, name: 'Smith' },
            { id: 3, pid: 1, name: 'Johnson', isSelected: true },
            { id: 4, pid: 1, name: 'Anderson' },
        ]
    },
    {
        id: 5, name: 'Windows Team',
        child: [
            { id: 6, pid: 5, name: 'Clark' },
            { id: 7, pid: 5, name: 'Wright' },
            { id: 8, pid: 5, name: 'Lopez' },
        ]
    },
    {
        id: 9, name: 'Web Team',
        child: [
            { id: 11, pid: 9, name: 'Joshua' },
            { id: 12, pid: 9, name: 'Matthew' },
            { id: 13, pid: 9, name: 'David' },
        ]
    },
    {
        id: 14, name: 'Build Team',
        child: [
            { id: 15, pid: 14, name: 'Ryan' },
            { id: 16, pid: 14, name: 'Justin' },
            { id: 17, pid: 14, name: 'Robert' },
        ]
    },
    {
        id: 18, name: 'WPF Team',
        child: [
            { id: 19, pid: 18, name: 'Brown' },
            { id: 20, pid: 18, name: 'Johnson' },
            { id: 21, pid: 18, name: 'Miller' },
        ]
    }
    ];
    return {
        fields: { dataSource: dataSource, id: 'id', text: 'name', child: 'child', selected: 'isSelected' },
    }
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
 .control_wrapper {
        display: block;
        max-width: 350px;
        max-height: 350px;
        margin: auto;
        overflow: auto;
        border: 1px solid #dddddd;
        border-radius: 3px;
    }
</style>
```

{% endtab %}

## Multiple-node drag and drop

To drag and drop more than one node, you should enable the [allowMultiSelection](../api/treeview#allowmultiselection)
property along with the `allowDragAndDrop` property.

To perform multi-selection, press and hold **CTRL** key and click the desired nodes. To select range of nodes, press and hold
the **SHIFT** key and click the nodes.

In the following sample,  the `allowMultiSelection` property is  enabled along with the `allowDragAndDrop` property.

{% tab template="treeview/drag-and-drop/multiple", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div class="control_wrapper">
        <ejs-treeview id='treeview' :fields="fields" :allowDragAndDrop='true' :allowMultiSelection='true'></ejs-treeview>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { TreeViewPlugin } from "@syncfusion/ej2-vue-navigations";

Vue.use(TreeViewPlugin);
export default {
  data () {
    var dataSource =  [
        {
        id: 1, name: 'ASP.NET MVC Team', expanded: true,
        child: [
            { id: 2, pid: 1, name: 'Smith' },
            { id: 3, pid: 1, name: 'Johnson', isSelected: true },
            { id: 4, pid: 1, name: 'Anderson', isSelected: true },
        ]
    },
    {
        id: 5, name: 'Windows Team',
        child: [
            { id: 6, pid: 5, name: 'Clark' },
            { id: 7, pid: 5, name: 'Wright' },
            { id: 8, pid: 5, name: 'Lopez' },
        ]
    },
    {
        id: 9, name: 'Web Team',
        child: [
            { id: 11, pid: 9, name: 'Joshua' },
            { id: 12, pid: 9, name: 'Matthew' },
            { id: 13, pid: 9, name: 'David' },
        ]
    },
    {
        id: 14, name: 'Build Team',
        child: [
            { id: 15, pid: 14, name: 'Ryan' },
            { id: 16, pid: 14, name: 'Justin' },
            { id: 17, pid: 14, name: 'Robert' },
        ]
    },
    {
        id: 18, name: 'WPF Team',
        child: [
            { id: 19, pid: 18, name: 'Brown' },
            { id: 20, pid: 18, name: 'Johnson' },
            { id: 21, pid: 18, name: 'Miller' },
        ]
    }
    ];
    return {
        fields: { dataSource: dataSource, id: 'id', text: 'name', child: 'child', selected: 'isSelected' },
    }
  }
}
</script>
<style>
   @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
   @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
 .control_wrapper {
        display: block;
        max-width: 350px;
        max-height: 350px;
        margin: auto;
        overflow: auto;
        border: 1px solid #dddddd;
        border-radius: 3px;
    }
</style>
```

{% endtab %}

## See Also

* [How to restrict the drag-and-drop for particular tree nodes](./how-to/restrict-the-drag-and-drop-for-particular-tree-nodes)
