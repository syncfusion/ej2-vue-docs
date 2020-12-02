---
title: "Print"
component: "TreeGrid"
description: "Learn how to print TreeGrid content, set up pages for printing, perform external print, and print visible pages in the Essential JS 2 TreeGrid control."
---

# Print

To print the TreeGrid, use the [`print`](../api/treegrid/#print) method from treegrid instance. The print option can be displayed on the [`toolbar`](../api/treegrid/#toolbar) by adding the `print` toolbar item.

{% tab template="treegrid/print/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' height='265' childMapping='subtasks' :treeColumnIndex='1' :toolbar='toolbarOptions'>
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
import { TreeGridPlugin, Toolbar } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbarOptions: ['Print']
    };
  },
  provide: {
    treegrid: [ Toolbar ]
  }
}
</script>

```

{% endtab %}

## Page setup

Some of the print options cannot be configured through JavaScript code. So, you have to customize the layout, paper size, and margin options using the browser page setup dialog. Please refer to the following links to know more about the browser page setup:

* [`Chrome`](https://support.google.com/chrome/answer/1069693?hl=en&visit_id=1-636335333734668335-3165046395&rd=1)
* [`Firefox`](https://support.mozilla.org/en-US/kb/how-print-web-pages-firefox)
* [`Safari`](http://www.mintprintables.com/print-tips/adjust-margins-osx/)
* [`IE`](http://www.helpteaching.com/help/print/index.htm)

## Print using an external button

To print the treegrid from an external button, invoke the [`print`](../api/treegrid/#print) method.

{% tab template="treegrid/print/default" %}

```html
<template>
<div id="app">
        <ejs-button id='print' @click.native='print'>Print</ejs-button>
        <ejs-treegrid ref='treegrid' :dataSource='data' height='265' childMapping='subtasks' :treeColumnIndex='1'>
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
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);
Vue.use(ButtonPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
    };
  },
  methods: {
    print: function() {
        this.$refs.treegrid.print();
    }
  },
}
</script>

```

{% endtab %}

## Print visible Page

By default, the grid prints all the pages. To print the current page alone, set the [`printMode`](../api/grid/#printmode) to `CurrentPage`.

{% tab template="treegrid/print/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' printMode='CurrentPage' childMapping='subtasks' :treeColumnIndex='1' :toolbar='toolbarOptions' :allowPaging='true' :pageSettings='pageSettings'>
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
import { TreeGridPlugin, Page, Toolbar } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbarOptions: ['Print'],
      pageSettings: { pageSize: 8 },
    };
  },
  provide: {
    treegrid: [ Page, Toolbar ]
  }
}
</script>

```

{% endtab %}

## Print large number of columns

By default, the browser uses A4 as page size option to print pages and to adapt the size of the page the browser print preview will auto-hide the overflowed contents. Hence treegrid with large number of columns will cut off to adapt the print page.

To show large number of columns when printing, adjust the scale option from print option panel based on your content size.

![Scale Option Setting](./images/print-preview.png)

## Show or Hide columns while Printing

You can show a hidden column or hide a visible column while printing the treegrid using [`toolbarClick`](../api/treegrid/#toolbarclick) and [`printComplete`](../api/treegrid/#printcomplete) events.

In the `toolbarClick` event, based on `args.item.text` as `Print`. We can show or hide columns by setting `column.visible` property to `true` or `false` respectively.

In the printComplete event, We have reversed the state back to the previous state.

In the below example, we have `Duration` as a hidden column in the treegrid. While printing, we have changed `Duration` to visible column and `StartDate` as hidden column.

{% tab template="treegrid/print/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid' :dataSource='data' printMode='CurrentPage' childMapping='subtasks' :treeColumnIndex='1' :toolbar='toolbarOptions' :toolbarClick='toolbarClick' :printComplete='printComplete'>
            <e-columns>
              <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
              <e-column field='taskName' headerText='Task Name' width='160'></e-column>
              <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
              <e-column field='duration' headerText='Duration' width='80' :visible='false' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Page, Toolbar } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbarOptions: ['Print'],
    };
  },
  methods: {
      toolbarClick: function() {
          for (var i = 0; i < this.$refs.treegrid.ej2Instances.grid.getColumns().length; i++) {
            if (this.$refs.treegrid.ej2Instances.grid.getColumns()[i].field == "duration") {
              this.$refs.treegrid.ej2Instances.grid.getColumns()[i].visible = true;
            }
            else if (this.$refs.treegrid.ej2Instances.grid.getColumns()[i].field == "startDate") {
              this.$refs.treegrid.ej2Instances.grid.getColumns()[i].visible = false;
            }
        }
      },
      printComplete: function() {
          for (var i = 0; i < this.$refs.grid.getColumns().length; i++) {
            if (this.$refs.treegrid.grid.getColumns()[i].field == "duration") {
              this.$refs.treegrid.grid.getColumns()[i].visible = false;
            }
            else if (this.$refs.treegrid.grid.getColumns()[i].field == "startDate") {
              this.$refs.treegrid.grid.getColumns()[i].visible = true;
            }
        }
      }
  },
  provide: {
    treegrid: [ Page, Toolbar ]
  }
}
</script>

```

{% endtab %}

## Limitations of Printing Large Data

When treegrid contains large number of data, printing all the data at once is not a best option for the browser performance. Because to render all the DOM elements in one page will produce performance issues in the browser. It leads to browser slow down or browser hang.

If printing of all the data is still needed, we suggest to Export the treegrid to `Excel` or `CSV` or `Pdf` and then print it from another non-web based application.