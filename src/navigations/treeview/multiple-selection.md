---
title: "Multi Selection"
component: "TreeView"
description: "Tree View component allows to select multiple nodes by pressing CTRL key, also can select the range of nodes by pressing SHIFT key."
---

# Multi Selection

Selection provides an interactive support and highlights the node that you select. Selection can be done through simple mouse
down or keyboard interaction.

The TreeView also supports selection of multiple nodes by setting [allowMultiSelection](../api/treeview#allowmultiselection)
to **true**.

To multi-select, press and hold **CTRL** key and click the desired nodes. To select range of nodes, press and hold the
**SHIFT** key and click the nodes.

In the following example, the `allowMultiSelection` property is enabled.

> Multi selection is not applicable through touch interactions.

{% tab template="treeview/multi-selection/selection", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div class="control_wrapper">
        <ejs-treeview id='treeview' :fields="fields" :allowMultiSelection='true'></ejs-treeview>
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
        { id: 1, name: 'Australia', hasChild: true, expanded: true },
        { id: 2, pid: 1, name: 'New South Wales', isSelected: true },
        { id: 3, pid: 1, name: 'Victoria' },
        { id: 4, pid: 1, name: 'South Australia' },
        { id: 6, pid: 1, name: 'Western Australia', isSelected: true },
        { id: 7, name: 'Brazil', hasChild: true },
        { id: 8, pid: 7, name: 'Paraná' },
        { id: 9, pid: 7, name: 'Ceará' },
        { id: 10, pid: 7, name: 'Acre' },
        { id: 11, name: 'China', hasChild: true },
        { id: 12, pid: 11, name: 'Guangzhou' },
        { id: 13, pid: 11, name: 'Shanghai' },
        { id: 14, pid: 11, name: 'Beijing' },
        { id: 15, pid: 11, name: 'Shantou' },
        { id: 16, name: 'France', hasChild: true },
        { id: 17, pid: 16, name: 'Pays de la Loire' },
        { id: 18, pid: 16, name: 'Aquitaine' },
        { id: 19, pid: 16, name: 'Brittany' },
        { id: 20, pid: 16, name: 'Lorraine' },
        { id: 21, name: 'India', hasChild: true },
        { id: 22, pid: 21, name: 'Assam' },
        { id: 23, pid: 21, name: 'Bihar' },
        { id: 24, pid: 21, name: 'Tamil Nadu' },
        { id: 25, pid: 21, name: 'Punjab' }
    ];
    return {
        fields: { dataSource: dataSource, id: 'id', parentID: 'pid', text: 'name', hasChildren: 'hasChild', selected: 'isSelected' },
    }
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
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

## Selected nodes

You can get or set the selected nodes in TreeView at initial rendering and dynamically by using the [selectedNodes](../api/treeview#selectednodes)
property. It will return the selected node’s ID as an array.

The [`nodeselecting`](../api/treeview#nodeselecting) event is triggered before a node is selected/unselected which can be used to prevent the selection.

The [`nodeSelected`](../api/treeview#nodeselected) event is triggered once a node is successfully selected/unselected.

In the following example, **New South Wales** and **Western Australia** nodes are selected at initial rendering. When a node is
selected, the selected node’s ID is displayed in alert.

{% tab template="treeview/multi-selection/selection", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div class="control_wrapper">
        <ejs-treeview id='treeview' :fields="fields" :allowMultiSelection='true' :selectedNodes="selectedNodes" :nodeSelected="nodeSelected"></ejs-treeview>
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
        { id: 1, name: 'Australia', hasChild: true, expanded: true },
        { id: 2, pid: 1, name: 'New South Wales', isSelected: true },
        { id: 3, pid: 1, name: 'Victoria' },
        { id: 4, pid: 1, name: 'South Australia' },
        { id: 6, pid: 1, name: 'Western Australia', isSelected: true },
        { id: 7, name: 'Brazil', hasChild: true },
        { id: 8, pid: 7, name: 'Paraná' },
        { id: 9, pid: 7, name: 'Ceará' },
        { id: 10, pid: 7, name: 'Acre' },
        { id: 11, name: 'China', hasChild: true },
        { id: 12, pid: 11, name: 'Guangzhou' },
        { id: 13, pid: 11, name: 'Shanghai' },
        { id: 14, pid: 11, name: 'Beijing' },
        { id: 15, pid: 11, name: 'Shantou' },
        { id: 16, name: 'France', hasChild: true },
        { id: 17, pid: 16, name: 'Pays de la Loire' },
        { id: 18, pid: 16, name: 'Aquitaine' },
        { id: 19, pid: 16, name: 'Brittany' },
        { id: 20, pid: 16, name: 'Lorraine' },
        { id: 21, name: 'India', hasChild: true },
        { id: 22, pid: 21, name: 'Assam' },
        { id: 23, pid: 21, name: 'Bihar' },
        { id: 24, pid: 21, name: 'Tamil Nadu' },
        { id: 25, pid: 21, name: 'Punjab' }
    ];
    return {
        fields: { dataSource: dataSource, id: 'id', parentID: 'pid', text: 'name', hasChildren: 'hasChild', selected: 'isSelected' },
        selectedNodes: ['2','6'],
    }
  },
  methods: {
        nodeSelected: function(args) {
           var treeObj = document.getElementById('treeview').ej2_instances[0];
            alert("The selected node's id: " + treeObj.selectedNodes); // To alert the selected node's id.
        }
    }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
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