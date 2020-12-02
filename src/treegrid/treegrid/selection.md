---
title: "Selection"
component: "TreeGrid"
description: "Learn how to select rows and cells, use range selection, and use check box selection in the Essential JS 2 TreeGrid control."
---

# Selection

Selection provides an option to highlight a row or cell.
Selection can be done through simple Mouse down or Arrow keys.
To disable selection in the TreeGrid, set the [`allowSelection`](../api/treegrid/#allowselection) to false.

The treegrid supports two types of selection that can be set by using the
[`selectionSettings.type`](../api/treegrid/selectionSettings/#type).They are:

* **`Single`** - The `Single` value is set by default. Allows you to select only a single row or cell.
* **`Multiple`** - Allows you to select multiple rows or cells.
To perform the multi-selection, press and hold CTRL key and click the desired rows or cells.
To select range of rows or cells, press and hold the SHIFT key and click the rows or cells.

{% tab template="treegrid/selection/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :selectionSettings='selectionOptions'>
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
      data: sampleData,
      pageSettings: { pageSize: 7 },
      selectionOptions: { type: 'Multiple' }
    };
  },
  provide: {
      treegrid: [ Page ]
    }
}
</script>

```

{% endtab %}

## Selection Mode

TreeGrid supports three types of selection mode which can be set by using
[`selectionSettings.mode`](../api/treegrid/selectionSettings/#mode). They are:

* **`Row`** - The `row` value is set by default. Allows you to select rows only.
* **`Cell`** - Allows you to select cells only.
* **`Both`** - Allows you to select rows and cells at the same time.

{% tab template="treegrid/selection/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :selectionSettings='selectionOptions' >
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
      data: sampleData,
      selectionOptions: { mode: 'Both' }
    };
  },
  provide: {
      treegrid: [ Page ]
    },
}
</script>

```

{% endtab %}

## Cell Selection

Cell Selection can be done through simple Mouse down or Arrow keys(up, down, left and right).

TreeGrid supports two types of cell selection mode which can be set by using
[`selectionSettings.cellSelectionMode`](../api/treegrid/selectionSettings/#cellselectionmode). They are:

* **`Flow`** - The `Flow` value is set by default.
Select range of cells between the start index and end index which includes in between cells of rows.
* **`Box`** - Select range of cells within the start and end column indexes which includes
in between cells of rows within the range.

{% tab template="treegrid/selection/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :selectionSettings='selectionOptions'>
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
import { TreeGridPlugin, TreeGridComponent,  Page } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

let initialGridLoad = true;

export default {
  data ()  {
    return {
      data: sampleData,
      selectionOptions: { cellSelectionMode: 'Box', type: 'Multiple', mode: 'Cell' }
    };
  },
  provide: {
      treegrid: [ Page ]
  }
}
</script>

```

{% endtab %}

> Cell Selection requires the [`selectionSettings.mode`](../api/grid/selectionSettings/#mode) to be `Cell` or  `Both` and
[`type`](../api/grid/selectionSettings/#type) should be `Multiple`.

## Checkbox Selection

Checkbox Selection provides an option to select multiple TreeGrid records with help of checkbox in each row.

To render checkbox in each treegrid row, you need to use checkbox column with type as `CheckBox` using
column [`type`](../api/treegrid/column/#type) property.

{% tab template="treegrid/selection/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' childMapping='subtasks' :treeColumnIndex='2'>
            <e-columns>
                <e-column type='checkbox' width='50'></e-column>
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
import { TreeGridPlugin, TreeGridComponent,  Page } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
    };
  },
  provide: {
      treegrid: [ Page ]
  }
}
</script>

```

{% endtab %}

> By default selection is allowed by clicking a treegrid row or checkbox in that row. To allow Selection only through checkbox, you can set
[`selectionSettings.checkboxOnly`](../api/treegrid/selectionSettings/#checkboxonly) property to true.
> Selection can be persisted on all the operations
using [`selectionSettings.persistSelection`](../api/treegrid/selectionSettings/#persistselection) property.
For persisting selection on the TreeGrid, any one of the column should be defined as a primary key
using [`columns.isPrimaryKey`](../api/treegrid/column/#isprimarykey) property.

### Checkbox selection Mode

In checkbox selection, selection can also be done by clicking on rows. This selection provides two types of Checkbox Selection mode which can be set by using the following API,
[`selectionSettings.checkboxMode`](../api/treegrid/selectionSettings/#checkboxmode). The modes are;

* **`Default`**: This is the default value of the checkboxMode. In this mode, user can select multiple rows by clicking rows one by one.
* **`ResetOnRowClick`**: In ResetOnRowClick mode, when user clicks on a row it will reset previously selected row. Also you can perform multiple-selection in this mode by press
and hold CTRL key and click the desired rows. To select range of rows, press and hold the SHIFT key and click the rows.

{% tab template="treegrid/selection/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' childMapping='subtasks' :treeColumnIndex='2'
        :selectionSettings='selectionOptions'>
            <e-columns>
                <e-column type='checkbox' width='50'></e-column>
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
import { TreeGridPlugin, TreeGridComponent,  Page } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      selectionOptions: { checkboxMode: 'ResetOnRowClick'}
    };
  },
  provide: {
      treegrid: [ Page ]
  }
}
</script>

```

{% endtab %}

## Toggle selection

The Toggle selection allows to perform selection and unselection of the particular row or cell. To enable toggle selection, set [`enableToggle`](../api/treegrid/selectionSettings/#enableToggle) property of the selectionSettings as true. If you click on the selected row or cell then it will be unselected and vice versa.

{% tab template="treegrid/selection/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' childMapping='subtasks' :treeColumnIndex='1'
        :selectionSettings='selectionOptions'>
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
import { TreeGridPlugin, TreeGridComponent,  Page } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      selectionOptions: { enableToggle: true}
    };
  },
  provide: {
      treegrid: [ Page ]
  }
}
</script>

```

{% endtab %}

>If multi selection is enabled, then first click on any selected row (without pressing Ctrl key), it will clear the multi selection and in second click on the same row, it will be unselected.