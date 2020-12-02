---
title: "Clipboard"
component: "TreeGrid"
description: "Learn how to use the copy to clipboard functionality in the Essential JS 2 Tree Grid Control."
---

# Clipboard

The clipboard provides an option to copy selected rows or cells data into the clipboard.

The following list of keyboard shortcuts is supported in the Tree Grid to copy selected rows or cells data into clipboard.

Interaction keys |Description
-----|-----
<kbd>Ctrl + C</kbd> |Copy selected rows or cells data into clipboard.
<kbd>Ctrl + Shift + H</kbd> |Copy selected rows or cells data with header into clipboard.

{% tab template="treegrid/clipboard/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='treeGridData' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' height='260px' :selectionSettings='selectionOptions'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      treeGridData: sampleData,
      pageSettings: { pageSize: 10 },
      selectionOptions: { type: 'Multiple'}
    };
  },
  provide: {
      treegrid: [ Page ]
    }
}
</script>

```

{% endtab %}

## Copy to clipboard by external buttons

To copy selected rows or cells data into clipboard with help of external buttons, you need to invoke the [`copy`](../api/treegrid/#copy)
method.

{% tab template="treegrid/clipboard/default" %}

```html
<template>
<div id="app">
<ejs-button id='copy' @click.native='copy'>Copy</ejs-button>
        <ejs-button id='copyHeader' @click.native='copyHeader'>CopyHeader</ejs-button>
        <ejs-treegrid ref=treegrid :dataSource='treeGridData' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' height='230px' :selectionSettings='selectionOptions'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page } from "@syncfusion/ej2-vue-treegrid";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);
Vue.use(ButtonPlugin);

export default {
  data ()  {
    return {
      treeGridData: sampleData,
      pageSettings: { pageSize: 10 },
      selectionOptions: { type: 'Multiple'}
    };
  },
  provide: {
      treegrid: [ Page ]
    },
    methods: {
    copy: function() {
        this.$refs.treegrid.copy();
    },
    copyHeader: function() {
        this.$refs.treegrid.copy(true);
    }
  }
}
</script>

```

{% endtab %}

## Copy Hierarchy Modes

Tree Grid provides support for a set of copy modes with [`copyHierarchyMode`](../api/treegrid/#copyhierarchymode) property. The below are the type of filter mode available in TreeGrid.

* **Parent** : This is the default copy hierarchy mode in Tree Grid. Clipboard value have the selected records with its parent records. If the selected records not have any parent record then the selected record will be in clipboard.

* **Child** : Clipboard value have the selected records with its child record. If the selected records do not have any child record then the selected records will be in clipboard.

* **Both** : Clipboard value have the selected records with its both parent and child record. If the selected records do not have any parent and child record then the selected records alone in clipboard.

* **None** : Only the Selected records will be in clipboard.

{% tab template="treegrid/clipboard/default" %}

```html
<template>
    <div id="app">
    <div style="padding-top: 7px; float:left">Hierarchy Mode</div><div style="padding-left: 10px; display: inline-block">
            <ejs-dropdownlist id='ddlelement' :dataSource='dropData' value='Parent' :fields='fields' :change="onChange"></ejs-dropdownlist></div>
        <ejs-treegrid ref=treegrid :dataSource='treeGridData' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' copyHierarchyMode='Parent' :pageSettings='pageSettings' height='230px' :selectionSettings='selectionOptions'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, CopyHierarchyType } from "@syncfusion/ej2-vue-treegrid";
import { DropDownListPlugin, ChangeEventArgs} from "@syncfusion/ej2-vue-dropdowns";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);
Vue.use(DropDownListPlugin);

export default {
  data ()  {
    return {
      treeGridData: sampleData,
      pageSettings: { pageSize: 10 },
      selectionOptions: { type: 'Multiple'},
      fields:  { text: 'mode', value: 'id' },
      dropData: [
        { id: 'Parent', mode: 'Parent' },
        { id: 'Child', mode: 'Child' },
        { id: 'Both', mode: 'Both' },
        { id: 'None', mode: 'None' },
    ];
    };
  },
  provide: {
      treegrid: [ Page ]
    },
    methods: {
    onChange: function(e: ChangeEventArgs): void {
      let mode:CopyHierarchyType = e.value.toString();
      this.$refs.treegrid.ej2Instances.copyHierarchyMode = mode;
    }
  }
}
</script>

```

{% endtab %}

### Limitations of Copy Functionality

* Only current view records will be available in copy clipboard.

## AutoFill

AutoFill Feature allows you to copy the data of selected cells and paste it to another cells by just dragging the autofill icon of the selected cells up to required cells. This feature is enabled by defining [`enableAutoFill`](../api/treegrid/#enableautofill) property as true.

{% tab template="treegrid/clipboard/default" %}

```html

<template>
    <div id="app">
        <ejs-treegrid :dataSource='treeGridData' :enableAutoFill='true' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' height='220px' :selectionSettings='selectionOptions' :editSettings='editSettings' :toolbar='toolbar'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' :isPrimaryKey='true' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Edit, Page, Toolbar } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      treeGridData: sampleData,
      pageSettings: { pageSize: 10 },
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Batch' },
      toolbar: ['Add', 'Update', 'Cancel'],
      selectionOptions: { type: 'Multiple', mode: 'Cell', cellSelectionMode: 'Box' }
    };
  },
  provide: {
      treegrid: [ Edit, Page, Toolbar ]
    }
  }

</script>


```

{% endtab %}

> * If [`enableAutoFill`](../api/treegrid/#enableautofill) is set to true, then the autofill icon will be displayed on cell selection to copy cells.
> * It requires the selection [`mode`](../api/treegrid/selectionSettings/#mode) to be **Cell**,  [`cellSelectionMode`](../api/treegrid/selectionSettings/#cellselectionmode) to be **Box** and also Batch Editing should be enabled.

### Limitations of AutoFill

* Since the string values are not parsed to number and date type, so when the selected string type cells are dragged to number type cells then it will display as **NaN**. For date type cells, when the selected string type cells are dragged to date type cells then it will display as an **empty cell**.
* Linear series and the sequential data generations are not supported in this autofill feature.

## Paste

You can able to copy the content of a cell or a group of cells by selecting the cells and pressing <kbd>Ctrl + C</kbd> shortcut key and paste it to another set of cells by selecting the cells and pressing <kbd>Ctrl + V</kbd> shortcut key.

{% tab template="treegrid/clipboard/default" %}

```html

<template>
    <div id="app">
        <ejs-treegrid :dataSource='treeGridData' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' height='220px' :selectionSettings='selectionOptions' :editSettings='editSettings' :toolbar='toolbar'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' :isPrimaryKey='true' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Edit, Page, Toolbar } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      treeGridData: sampleData,
      pageSettings: { pageSize: 10 },
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Batch' },
      toolbar: ['Add', 'Update', 'Cancel'],
      selectionOptions: { type: 'Multiple', mode: 'Cell', cellSelectionMode: 'Box' }
    };
  },
  provide: {
      treegrid: [ Edit, Page, Toolbar ]
    }
  }

</script>

```

{% endtab %}

> To perform paste functionality, it requires the selection [`mode`](../api/treegrid/selectionMode/) to be **Cell**,  [`cellSelectionMode`](../api/treegrid/cellSelectionMode/) to be **Box** and also Batch Editing should be enabled.

### Limitations of Paste Functionality

* Since the string values are not parsed to number and date type, so when the copied string type cells are pasted to number type cells then it will display as **NaN**. For date type cells, when the copied string format cells are pasted to date type cells then it will display as an **empty cell**.