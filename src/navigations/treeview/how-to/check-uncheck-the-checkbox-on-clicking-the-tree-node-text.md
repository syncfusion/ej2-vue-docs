# Check/uncheck the checkbox on clicking the tree node text

You can check and uncheck the checkboxes of tree view by clicking the tree node using the `nodeClicked` event of TreeView.

{% tab template="treeview/how-to/checkbox", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div class="control_wrapper">
        <ejs-treeview id='treeview' :fields="fields" :showCheckBox='true' :nodeClicked='nodeChecked' :keyPress='nodeChecked'></ejs-treeview>
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
        { id: 2, pid: 1, name: 'New South Wales', isChecked: true },
        { id: 3, pid: 1, name: 'Victoria' },
        { id: 4, pid: 1, name: 'South Australia' },
        { id: 6, pid: 1, name: 'Western Australia', isChecked: true },
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
        fields: { dataSource: dataSource, id: 'id', parentID: 'pid', text: 'name', hasChildren: 'hasChild' },
    }
  },
  methods: {
        nodeChecked: function(args) {
           var treeObj = document.getElementById('treeview').ej2_instances[0];
           var checkedNode = [args.node];
            if (args.event.target.classList.contains('e-fullrow') || args.event.key == "Enter") {
                var getNodeDetails = treeObj.getNode(args.node);
                if (getNodeDetails.isChecked == 'true') {
                    treeObj.uncheckAll(checkedNode);
                } else {
                    treeObj.checkAll(checkedNode);
                }
            }
        }
    }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
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