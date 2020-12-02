---
title: "Node Editing"
component: "TreeView"
description: "This section explains about node editing functionality of tree view, you can edit any node text by double click on it or pressing F2."
---

# Node Editing

The TreeView allows you to edit nodes by setting the [allowEditing](../api/treeview#allowediting) property to **true**.
To directly edit the nodes in place, **double click** the TreeView node or **select** the node and press **F2** key.

When editing is completed by focus out or by pressing the **Enter** key, the modified node’s text saves automatically.
If you do not want to save the modified node’s text in TreeView node, press **Escape** key. It does not save the edited text to the
TreeView node.

Node editing can also be performed programmatically by using the [`beginEdit`](../api/treeview#beginedit) method. On passing the node ID or element through this method, the edit textbox will be created for the particular node thus allowing us to edit it.

If you need to validate or prevent editing, the [`nodeEditing`](../api/treeview#nodeediting) event can be used which is triggered before the TreeView node is renamed. On successfully renaming a node the [`nodeEdited`](../api/treeview#nodeedited) event will be triggered.

In the following example, the first level node’s text cannot be changed, but all other level nodes' text can be changed.

{% tab template="treeview/node-editing", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div class="control_wrapper">
        <ejs-treeview id='treeview' :fields="fields" :allowEditing='true' :nodeEditing='editing'></ejs-treeview>
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
        { id: '01', name: 'Local Disk (C:)', expanded: true,
            subChild: [
                {
                    id: '01-01', name: 'Program Files',
                    subChild: [
                        { id: '01-01-01', name: '7-Zip' },
                        { id: '01-01-02', name: 'Git' },
                        { id: '01-01-03', name: 'IIS Express' },
                    ]
                },
                {
                    id: '01-02', name: 'Users', expanded: true,
                    subChild: [
                        { id: '01-02-01', name: 'Smith' },
                        { id: '01-02-02', name: 'Public' },
                        { id: '01-02-03', name: 'Admin' },
                    ]
                },
                {
                    id: '01-03', name: 'Windows',
                    subChild: [
                        { id: '01-03-01', name: 'Boot' },
                        { id: '01-03-02', name: 'FileManager' },
                        { id: '01-03-03', name: 'System32' },
                    ]
                },
            ]
        },
        {
            id: '02', name: 'Local Disk (D:)',
            subChild: [
                {
                    id: '02-01', name: 'Personals',
                    subChild: [
                        { id: '02-01-01', name: 'My photo.png' },
                        { id: '02-01-02', name: 'Rental document.docx' },
                        { id: '02-01-03', name: 'Pay slip.pdf' },
                    ]
                },
                {
                    id: '02-02', name: 'Projects',
                    subChild: [
                        { id: '02-02-01', name: 'ASP Application' },
                        { id: '02-02-02', name: 'TypeScript Application' },
                        { id: '02-02-03', name: 'React Application' },
                    ]
                },
                {
                    id: '02-03', name: 'Office',
                    subChild: [
                        { id: '02-03-01', name: 'Work details.docx' },
                        { id: '02-03-02', name: 'Weekly report.docx' },
                        { id: '02-03-03', name: 'Wish list.csv' },
                    ]
                },
            ]
        },
        {
            id: '03', name: 'Local Disk (E:)', icon: 'folder',
            subChild: [
                {
                    id: '03-01', name: 'Pictures',
                    subChild: [
                        { id: '03-01-01', name: 'Wind.jpg' },
                        { id: '03-01-02', name: 'Stone.jpg' },
                        { id: '03-01-03', name: 'Home.jpg' },
                    ]
                },
                {
                    id: '03-02', name: 'Documents',
                        subChild: [
                        { id: '03-02-01', name: 'Environment Pollution.docx' },
                        { id: '03-02-02', name: 'Global Warming.ppt' },
                        { id: '03-02-03', name: 'Social Network.pdf' },
                    ]
                },
                {
                    id: '03-03', name: 'Study Materials',
                    subChild: [
                        { id: '03-03-01', name: 'UI-Guide.pdf' },
                        { id: '03-03-02', name: 'Tutorials.zip' },
                        { id: '03-03-03', name: 'TypeScript.7z' },
                    ]
                },
            ]
        }
    ];
    return {
        fields: { dataSource: dataSource, id: 'id', text: 'name', child: 'subChild' },
        checkedNodes: ['2','6']
    }
  },
  methods: {
        editing: function(args) {
           //check whether node is root node or not
            if (args.node.parentNode.parentNode.nodeName !== "LI") {
                args.cancel = true;
            }
        }
    }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
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

* [How to validate the text when renaming the tree node](./how-to/validate-the-text-when-renaming-the-tree-node)
* [How to process the tree node operations using context menu](./how-to/process-the-tree-node-operations-using-context-menu)