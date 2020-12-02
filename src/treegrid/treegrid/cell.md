---
title: "Cell"
component: "TreeGrid"
description: "Learn how to customize the Essential JS 2 TreeGrid cells with styling, text wrapping, and tooltips."
---

# Cell

## Displaying the HTML content

The HTML tags can be displayed in the TreeGrid header and content by enabling the [`disableHtmlEncode`](../api/treegrid/column/#disablehtmlencode) property.

{% tab template="treegrid/cell/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' height='300px'>
        <e-columns>
        <e-column field='taskID' headerText='<span> Task ID </span>' :disableHtmlEncode='true' width=140 textAlign='Right'></e-column>
        <e-column field='taskName' headerText='<span> Task Name </span>' :disableHtmlEncode='false' width=180 ></e-column>
        <e-column field='startDate' headerText='Start Date' width=80 format="yMd" textAlign='Right'></e-column>
        <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
        </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { htmlData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: htmlData,
    };
  }
}
</script>

```

{% endtab %}

## Customize cell styles

The appearance of cells can be customized by using the [`queryCellInfo`](../api/treegrid/#querycellinfo) event.
The [`queryCellInfo`](../api/treegrid/#querycellinfo) event triggers for every cell. In that event handler, you can get
`QueryCellInfoEventArgs` that contains the details of the cell.

{% tab template="treegrid/cell/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' height='300px' :queryCellInfo='customiseCell'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90 textAlign='Right' ></e-column>
                <e-column field='taskName' headerText='Task Name' width=180></e-column>
                <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
                <e-column field='progress' headerText='Progress' width=80 textAlign='Right'></e-column>
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
  data() {
    return {
      data: sampleData,
    };
  },
    methods: {
    customiseCell: function(args) {
      if (args.column.field === 'progress' && +args.cell.innerHTML > 90 && +args.cell.innerHTML <= 100){
        args.cell.setAttribute('style', 'background-color:#336c12;color:white;');
    } else if (+args.cell.innerHTML > 20 && args.column.field === 'progress') {
        args.cell.setAttribute('style', 'background-color:#7b2b1d;color:white;');
    }
    }
  }
}
</script>

```

{% endtab %}

## Auto wrap

The auto wrap allows the cell content of the treegrid to wrap to the next line when it exceeds the boundary of the cell width. The Cell Content wrapping works based on the position of white space between words.
To enable auto wrap, set the [`allowTextWrap`](../api/treegrid/#allowtextwrap) property to `true`.
You can configure the auto wrap mode by setting the [`textWrapSettings.wrapMode`](../api/treegrid/#textwrapsettings) property.

There are three types of `wrapMode`. They are:

* **`Both`**: `Both` value is set by default. Auto wrap will be enabled for both the content and the header.
* **`Header`**: Auto wrap will be enabled only for the header.
* **`Content`**: Auto wrap will be enabled only for the content.

Note: When a column width is not specified, then auto wrap of columns will be adjusted with respect to the treegrid's width.

In the following example, the `textWrapSettings.wrapMode` is set to `Content`.

{% tab template="treegrid/cell/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' height='300px' :allowTextWrap='true' :textWrapSettings='wrapSettings'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90 textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width=75></e-column>
                <e-column field='startDate' headerText='Start Date' width=90 format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
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
  data() {
    return {
      data: sampleData,
      wrapSettings: { wrapMode: 'Content' }
    };
  },
}
</script>

```

{% endtab %}

## Custom Attributes

You can customize the treegrid cells by adding a CSS class to the [`customAttribute`](../api/treegrid/column/#customattributes) property of the column.

```CSS
.e-attr {
    background: '#d7f0f4';
}
```

```typescript
{
    field: 'taskID', headerText: 'Task ID', width: 90, customAttributes: {class: "e-attr"}, textAlign: 'Right'
}
```

In the below example, we have customized the cells of `TaskID` and `StartDate` columns.

{% tab template="treegrid/cell/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' height='300px'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90 textAlign='Right' :customAttributes= "{class: 'e-attr'}"></e-column>
                <e-column field='taskName' headerText='Task Name' width=160></e-column>
                <e-column field='startDate' headerText='Start Date' width=90 format="yMd" textAlign='Right' :customAttributes= "{class: 'e-attr'}"></e-column>
                <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
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
  data() {
    return {
      data: sampleData,
    };
  },
}
</script>
<style>
.e-attr {
  background: #d7f0f4;
  }
</style>

```

{% endtab %}

## Grid Lines

The [`gridLines`](../api/treegrid/#gridlines) have option to display cell border and it can be defined by the
[`gridLines`](../api/treegrid/#gridlines) property.

The available modes of grid lines are:

| Modes | Actions |
|-------|---------|
| Both | Displays both the horizontal and vertical grid lines.|
| None | No grid lines are displayed.|
| Horizontal | Displays the horizontal grid lines only.|
| Vertical | Displays the vertical grid lines only.|
| Default | Displays grid lines based on the theme.|

{% tab template="treegrid/cell/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' height='300px' gridLines='Both'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90 textAlign='Right' ></e-column>
                <e-column field='taskName' headerText='Task Name' width=180></e-column>
                <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
                <e-column field='progress' headerText='Progress' width=80 textAlign='Right'></e-column>
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
  data() {
    return {
      data: sampleData,
    };
  }
}
</script>

```

{% endtab %}

>By default, the treegrid renders with `Default` mode.

## Clip Mode

The clip mode provides options to display its overflow cell content and it can be defined by the [`columns.clipMode`](../api/treegrid/column/#clipmode) property.

There are three types of [`clipMode`](../api/treegrid/column/#clipmode). They are:

* **`Clip`**: Truncates the cell content when it overflows its area.
* **`Ellipsis`**: Displays ellipsis when the cell content overflows its area.
* **`EllipsisWithTooltip`**: Displays ellipsis when the cell content overflows its area, also it will display the tooltip while hover on ellipsis is applied.

{% tab template="treegrid/cell/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' height='300px' gridLines='Both'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width=90 textAlign='Right' ></e-column>
                <e-column field='taskName' headerText='Task Name' width=90 clipMode='Clip'></e-column>
                <e-column field='assignee.firstName' headerText='Assignee' clipMode='EllipsisWithTooltip' width=40 textAlign='Right'></e-column>
                 <e-column field='priority' headerText='Priority' clipMode='Ellipsis' width=40 textAlign='Right'></e-column>
                 <e-column field='duration' headerText='Duration' width=80 textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
import { complexData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: complexData,
    };
  }
}
</script>

```

{% endtab %}

>By default, [`columns.clipMode`](../api/treegrid/column/#clipmode) value is `Ellipsis`.