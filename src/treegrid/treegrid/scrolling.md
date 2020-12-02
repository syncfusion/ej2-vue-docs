---
title: "Scrolling"
component: "TreeGrid"
description: "Learn how to set width and height for TreeGrid content, display a scrollbar and make the TreeGrid responsive with a parent container."
---

# Scrolling

The scrollbar will be displayed in the treegrid when content exceeds the element [`width`](../api/treegrid/#width) or [`height`](../api/treegrid/#height). The vertical and horizontal scrollbars will be displayed based on the following criteria:

* The vertical scrollbar appears when the total height of rows present in the treegrid exceeds its element height.
* The horizontal scrollbar appears when the sum of columns width exceeds the treegrid element width.
* The [`height`](../api/treegrid/#height) and [`width`](../api/treegrid/#width) are used to set the treegrid height and width, respectively.

> The default value for [`height`](../api/treegrid/#height) and [`width`](../api/treegrid/#width) is `auto`.

## Set width and height

To specify the [`width`](../api/treegrid/#width) and [`height`](../api/treegrid/#height) of the scroller in the pixel, set the pixel value to a number.

{% tab template="treegrid/scroll/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :height='315' :width='400'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='180'></e-column>
                <e-column field='startDate' headerText='Start Date' width='120' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='110' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData
    };
  }
}
</script>

```

{% endtab %}

## Responsive with parent container

Specify the [`width`](../api/treegrid/#width) and [`height`](../api/treegrid/#height) as `100%` to make the treegrid element fill its parent container.
Setting the [`height`](../api/treegrid/#height) to `100%` requires the treegrid parent element to have explicit height.

{% tab template="treegrid/scroll/default" %}

```html
<template>
<div id="app">
    <p class="e-text"> The parent container can be resizable by dragging the bottom-right corner.</p>
      <div id='container' class='e-resizable'>
        <ejs-treegrid :dataSource='data' childMapping='subtasks' height='100%' width= '100%' :treeColumnIndex='1' >
            <e-columns>
              <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
              <e-column field='taskName' headerText='Task Name' width='180'></e-column>
              <e-column field='startDate' headerText='Start Date' width='120' format="yMd" textAlign='Right'></e-column>
              <e-column field='duration' headerText='Duration' width='110' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
      </div>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData
    };
  }
}
</script>

<style>
  .e-resizable {
      resize: both;
      overflow: auto;
      border: 1px solid red;
      padding: 10px;
      height: 300px;
      min-height: 250px;
      min-width: 250px;
  }
</style>

```

{% endtab %}

## Scroll to selected row

You can scroll the treegrid content to the selected row position by using the [`rowSelected`](../api/treegrid/#rowselected) event.

{% tab template="treegrid/scroll/selectrow" %}

```html
<template>
<div id="app">
    <ejs-numerictextbox ref='numeric' format='N' min='0' placeholder='Enter index to select a row' width=200 :showSpinButton='false' :change='onchange'></ejs-numerictextbox>
        <ejs-treegrid ref='treegrid' :dataSource='data' childMapping='subtasks' height='280' width='100%' :treeColumnIndex='1' :rowSelected='rowSelected'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='180'></e-column>
                <e-column field='startDate' headerText='Start Date' width='120' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='110' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);
Vue.use(NumericTextBoxPlugin);

export default {
  data ()  {
    return {
      data: sampleData
    };
  },
  methods: {
    onchange: function(){
      this.$refs.treegrid.selectRow(parseInt(this.$refs.numeric.getText(), 10));
    }
    rowSelected: function (args) {
        let rowHeight = this.$refs.treegrid.getRows()[this.$refs.treegrid.getSelectedRowIndexes()[0]].scrollHeight;
        this.$refs.treegrid.getContent().children[0].scrollTop = rowHeight * this.$refs.treegrid.getSelectedRowIndexes()[0];
    }
  }
}
</script>

```

{% endtab %}

## Frozen rows and columns

Frozen rows and columns provides an option to make rows and columns always visible in the top and left side of the treegrid while scrolling.

To use frozen rows and columns support, inject the `Freeze` module in the `provide` section.

In this demo, the [`frozenColumns`](../api/treegrid/#frozencolumns) is set as '2' and the [`frozenRows`](../api/treegrid/#frozenrows)
is set as '3'. Hence, the left two columns and top three rows are frozen.

{% tab template="treegrid/scroll/frozencolumn" %}

```html
<template>
    <div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' height=310 :frozenColumns='2' :frozenRows='3' :allowSelection='false'>
            <e-columns>
               <e-column field='taskID' headerText='Task ID' width='110' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='230'></e-column>
                <e-column field='startDate' headerText='Start Date' width='120' format="yMd" textAlign='Right'></e-column>
                <e-column field='endDate' headerText='End Date' width='120' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='110' textAlign='Right'></e-column>
                <e-column field='progress' headerText='Progress' width='120' textAlign='Right'></e-column>
                <e-column field='priority' headerText='Priority' width='120'></e-column>
                <e-column field='approved' headerText='Approved' width='110' textAlign='Left'></e-column>
            </e-columns>
        </ejs-treegrid>
    </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Freeze } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: sampleData
    };
  },
  provide: {
    treegrid: [Freeze]
  }
}
</script>
```

{% endtab %}

### Freeze particular columns

You can use [`isFrozen`](../api/treegrid/column/#isfrozen) property to freeze selected columns in treegrid.

In this demo, the columns with field name `taskName` and `startDate` is frozen using
the `isFrozen` property.

{% tab template="treegrid/scroll/isfrozen" %}

```html
<template>
    <div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' height=310  :allowSelection='false'>
            <e-columns>
               <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='230' isFrozen='true'></e-column>
                <e-column field='startDate' headerText='Start Date' isFrozen='true' width='120' format="yMd" textAlign='Right'></e-column>
                <e-column field='endDate' headerText='End Date' width='120' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='110' textAlign='Right'></e-column>
                <e-column field='progress' headerText='Progress' width='120' textAlign='Right'></e-column>
                <e-column field='priority' headerText='Priority' width='120'></e-column>
                <e-column field='approved' headerText='Approved' width='110' textAlign='Left'></e-column>
            </e-columns>
        </ejs-treegrid>
    </div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Freeze } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: sampleData
    };
  },
  provide: {
    treegrid: [Freeze]
  }
}
</script>
```

{% endtab %}

### Limitations

The following features are not supported in frozen rows and columns:

* Row Template
* Detail Template
* Cell Editing