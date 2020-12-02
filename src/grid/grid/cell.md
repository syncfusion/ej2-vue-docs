---
title: "Cell"
component: "Grid"
description: "Learn how to customize the Essential JS 2 DataGrid cells with styling, text wrapping, adding custom attributes and tooltips."
---

# Cell

## Displaying HTML Content

The HTML tags can be displayed in the Grid header and content by enabling the
[`disableHtmlEncode`](../api/grid/column/#disablehtmlencode) property.

{% tab template="grid/cell/encode" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" height='315'>
          <e-columns>
            <e-column field='OrderID' headerText='<span> Order ID </span>' :disableHtmlEncode='true' textAlign='Right' width=140></e-column>
            <e-column field='CustomerID' headerText='<span> Customer ID </span>' :disableHtmlEncode='false' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=80></e-column>
            <e-column field='OrderDate' headerText='Order Date' textAlign='Right' format='yMd' type='date' width=120> </e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Customize Cell Styles

The appearance of cells can be customized by using the
[`queryCellInfo`](../api/grid/#querycellinfo) event.
The [`queryCellInfo`](../api/grid/#querycellinfo) event
triggers for every cell. In that event handler, you can get
[`QueryCellInfoEventArgs`](../api/grid/queryCellInfoEventArgs/) that contains the details of the cell.

{% tab template="grid/cell/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :enableHover='false' :allowSelection='false' height='315' :queryCellInfo='customiseCell'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
            <e-column field='OrderDate' headerText='Order Date' textAlign='Right' format='yMd' type='date' width=120 > </e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  methods: {
    customiseCell: function(args) {
        if (args.column.field === 'Freight') {
            if (args.data['Freight'] < 30) {
                args.cell.classList.add('below-30');
            } else if (args.data['Freight'] < 80) {
                args.cell.classList.add('below-80');
            } else {
                args.cell.classList.add('above-80');
            }
        }
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
  .below-30 {
  background-color: orangered;
  }
  .below-80 {
  background-color: yellow;
  }
  .above-80 {
  background-color: greenyellow
  }
</style>
```

{% endtab %}

## Auto Wrap

The auto wrap allows the cell content of the grid to wrap to the next line when it exceeds the boundary of the cell width. The Cell Content wrapping works based on the position of white space between words.
To enable auto wrap, set the [`allowTextWrap`](../api/grid/#allowtextwrap) property to **true**.
You can configure the auto wrap mode by setting the [`textWrapSettings.wrapMode`](../api/grid/textWrapSettings/#wrapmode) property.

There are three types of [`wrapMode`](../api/grid/textWrapSettings/#wrapmode). They are

* **Both** - The **Both** value is set by default. The auto wrap will be enabled for both content and Header.
* **Header** - Auto wrap will be enabled only for the header.
* **Content** - Auto wrap will be enabled only for the content.

Note: When a column width is not specified, then auto wrap of columns will be adjusted with respect to the grid's width.

In the below example, the [`textWrapSettings.wrapMode`](../api/grid/textWrapSettings/#wrapmode) is set as **Content**.

{% tab template="grid/cell/autowrap" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :allowPaging='true' :allowTextWrap='true' :textWrapSettings='wrapSettings' height='310'>
            <e-columns>
                <e-column field='Inventor' headerText='Inventor Name' width='180' textAlign="Right"></e-column>
                <e-column field='NumberofPatentFamilies' headerText="Number of Patent Families" width='180' textAlign="Right"></e-column>
                <e-column field='Country' headerText='Country' width='140'></e-column>
                <e-column field='Active' width='120'></e-column>
                <e-column field='Mainfieldsofinvention' headerText='Main fields of invention' width='200'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      wrapSettings: { wrapMode: 'Content' }
    };
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Custom Attributes

You can customize the grid cells by adding a CSS class to the [`customAttribute`](../api/grid/column#customattributes) property of the column.

```CSS
.e-attr {
    background: #d7f0f4;
}
```

```typescript
<e-column
    field='ShipCity' headerText='Ship City' :customAttributes= "{class: 'e-attr'}" width=90 >
</e-column>
```

In the below example, we have customized the cells of `OrderID` and `ShipCity` columns.

{% tab template="grid/cell/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" height='315'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' :customAttributes= "{class: 'e-attr'}" textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='ShipCity' headerText='Ship City' :customAttributes= "{class: 'e-attr'}" textAlign='Right' width=90></e-column>
            <e-column field='OrderDate' headerText='Order Date' textAlign='Right' format='yMd' type='date' width=120 > </e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
  .e-attr {
  background: #d7f0f4;
  }
</style>
```

{% endtab %}

## Grid Lines

The [`gridLines`](../api/grid/#gridlines) have the option to display cell border and it can be defined by the
[`gridLines`](../api/grid/#gridlines) property.

The available modes of grid lines are:

| Modes | Actions |
|-------|---------|
| Both | Displays both the horizontal and vertical grid lines.|
| None | No grid lines are displayed.|
| Horizontal | Displays the horizontal grid lines only.|
| Vertical | Displays the vertical grid lines only.|
| Default | Displays grid lines based on the theme.|

{% tab template="grid/cell/autowrap" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' height='315' gridLines='Both'>
            <e-columns>
                <e-column field='Inventor' headerText='Inventor Name' width='180' textAlign="Right"></e-column>
                <e-column field='NumberofPatentFamilies' headerText="Number of Patent Families" width='180' textAlign="Right"></e-column>
                <e-column field='Country' headerText='Country' width='140'></e-column>
                <e-column field='Active' width='120'></e-column>
                <e-column field='Mainfieldsofinvention' headerText='Main fields of invention' width='200'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

>By default, the grid renders with **Default** mode.

## Clip Mode

The clip mode provides options to display its overflow cell content and it can be defined
by the [`columns.clipMode`](../api/grid/column/#clipmode) property.

There are three types of [`clipMode`](../api/grid/column/#clipmode). They are:

* **Clip**: Truncates the cell content when it overflows its area.
* **Ellipsis**: Displays ellipsis when the cell content overflows its area.
* **EllipsisWithTooltip**: Displays ellipsis when the cell content overflows its area,
also it will display the tooltip while hover on ellipsis is applied.

{% tab template="grid/cell/autowrap" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' height='315' >
            <e-columns>
                <e-column field='Inventor' headerText='Name of the Inventor' clipMode='Clip' width='80'></e-column>
                <e-column field='NumberofPatentFamilies' headerText='Number of Patent Families' clipMode='Ellipsis' width='100'></e-column>
                <e-column field='Country' headerText='Country' width='80'></e-column>
                <e-column field='Number of INPADOC patents' headerText='Number of INPADOC patents' width='100'></e-column>
                <e-column field='Mainfieldsofinvention' headerText='Main fields of invention' clipMode='EllipsisWithTooltip' width='100'></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

>By default, [`columns.clipMode`](../api/grid/column/#clipmode) value is **Ellipsis**.