---
title: "Template"
component: "TreeView"
description: "This section explains how to customize the tree view nodes using node templates"
---

# Template

The TreeView component allows you to customize the look of TreeView nodes by using the [nodeTemplate](../api/treeview#nodetemplate)
property. This property accepts either `template string` or HTML element ID.

In the following sample, employee information such as employee photo, name, and designation have been included using the `nodeTemplate` property.

{% tab template="treeview/template", isDefaultActive=true %}

```html
<template>
  <div id="app">
    <div class="control_wrapper">
        <ejs-treeview id='treeview' :fields="fields" cssClass='custom' :nodeTemplate='Template'></ejs-treeview>
    </div>
  </div>
</template>
<script>
import Vue from 'vue';
import { TreeViewPlugin } from "@syncfusion/ej2-vue-navigations";

Vue.use(TreeViewPlugin);
export default {
  data () {
    var demoVue = Vue.component("demo", {
    template: "<div><img class='eimage' :src='data.eimg' alt='employee'/><div class='ename'>{{data.name}}</div><div class='ejob'>{{data.job}}</div></div>"
    data() {
        return {
        data: {}
        };
    }
    });
    var dataSource =  [
        { id: 1, name: 'Steven Buchanan', eimg: 'https://ej2.syncfusion.com/demos/src/treeview/images/employees/10.png', job: 'CEO', hasChild: true, expanded: true },
        { id: 2, pid: 1, name: 'Laura Callahan', eimg: 'https://ej2.syncfusion.com/demos/src/treeview/images/employees/2.png', job: 'Product Manager', hasChild: true },
        { id: 3, pid: 2, name: 'Andrew Fuller', eimg: 'https://ej2.syncfusion.com/demos/src/treeview/images/employees/7.png', job: 'Team Lead', hasChild: true },
        { id: 4, pid: 3, name: 'Anne Dodsworth', eimg: 'https://ej2.syncfusion.com/demos/src/treeview/images/employees/1.png', job: 'Developer' },
        { id: 5, pid: 1, name: 'Nancy Davolio', eimg: 'https://ej2.syncfusion.com/demos/src/treeview/images/employees/4.png', job: 'Product Manager', hasChild: true },
        { id: 6, pid: 5, name: 'Michael Suyama', eimg: 'https://ej2.syncfusion.com/demos/src/treeview/images/employees/9.png', job: 'Team Lead', hasChild: true },
        { id: 7, pid: 6, name: 'Robert King', eimg: 'https://ej2.syncfusion.com/demos/src/treeview/images/employees/8.png', job: 'Developer ' },
        { id: 8, pid: 7, name: 'Margaret Peacock', eimg: 'https://ej2.syncfusion.com/demos/src/treeview/images/employees/6.png', job: 'Developer' },
        { id: 9, pid: 1, name: 'Janet Leverling', eimg: 'https://ej2.syncfusion.com/demos/src/treeview/images/employees/3.png', job: 'HR' },
    ];
    return {
        fields: { dataSource: dataSource, id: 'id', parentID: 'pid', text: 'name', hasChildren: 'hasChild' },
        Template: function(e) {
            return {
                template: demoVue
            };
        }
    }
  }}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";
 .control_wrapper {
        display: block;
        max-width: 450px;
        max-height: 350px;
        margin: auto;
        overflow: auto;
        border: 1px solid #dddddd;
        border-radius: 3px;
    }
    .custom .e-list-item .e-fullrow {
        height: 72px;
    }

    .custom .e-list-item .e-list-text {
        line-height: normal;
    }

    .eimage {
        float: left;
        padding: 11px 16px 11px 0;
    }

    .ename {
        font-size: 16px;
        padding: 14px 0 0;
    }

    .ejob {
        font-size: 14px;
        opacity: .87;
    }
</style>
```

{% endtab %}

## See Also

* [How to customize the expand and collapse icons](./how-to/customize-the-expand-and-collapse-icons)
* [How to customize the tree nodes based on levels](./how-to/customize-the-tree-nodes-based-on-levels)