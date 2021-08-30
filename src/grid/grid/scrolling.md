---
title: "Scrolling"
component: "Grid"
description: "Learn how to set width and height for DataGrid content, display a scrollbar, freeze rows and columns, and make the DataGrid responsive with a parent container."
---

# Scrolling

 The scrollbar will be displayed in the grid when content exceeds the element [`width`](../api/grid/#width) or
 [`height`](../api/grid/#height).
 The vertical and horizontal scrollbars will be displayed based on the following criteria:

* The vertical scrollbar appears when the total height of rows present in the grid exceeds its element height.
* The horizontal scrollbar appears when the sum of columns width exceeds the grid element width.
* The [`height`](../api/grid/#height) and [`width`](../api/grid/#width)
are used to set the grid height and width, respectively.

> The default value for [`height`](../api/grid/#height) and [`width`](../api/grid/#width) is `auto`.

## Set width and height

To specify the [`width`](../api/grid/#width) and [`height`](../api/grid/#height)
of scroller in pixel, set the pixel value as number.

{% tab template="grid/scroll/default" %}

```html
<template>
    <div id="app">
      <ejs-grid :dataSource="data">
          <e-columns>
              <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
              <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
              <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
              <e-column field='ShipCountry' headerText='Ship Country' width=150></e-column>
              <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
          </e-columns>
      </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from "./datasource.js";

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

## Responsive with parent container

Specify the [`width`](../api/grid/#width) and [`height`](../api/grid/#height)
as `100%` to make the grid element fill its parent container.
Setting the [`height`](../api/grid/#height) to `100%` requires the grid parent element to have explicit height.

{% tab template="grid/scroll/default" %}

```html
<template>
    <div id="app">
      <p class="e-text"> The parent container can be resizable by dragging the bottom-right corner.</p>
      <div id='container' class='e-resizable'>
        <ejs-grid :dataSource='data' height='100%' width='100%'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' width=150></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
            </e-columns>
        </ejs-grid>
      </div>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from "./datasource.js";

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

## Scroll To Selected Row

You can scroll the grid content to the selected row position by using the
[`rowSelected`](../api/grid/#rowselected) event.

{% tab template="grid/scroll/selectrow" %}

```html
<template>
    <div id="app">
    <ejs-numerictextbox ref='numeric' format='N' min='0' placeholder='Enter index to select a row' width=200 :showSpinButton='false' :change='onchange'></ejs-numerictextbox>
        <ejs-grid ref='grid' :dataSource='data' height='280' width='100%' :rowSelected='rowSelected'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                <e-column field='ShipCountry' headerText='Ship Country' width=150></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";
import { data } from "./datasource.js";

Vue.use(GridPlugin);
Vue.use(NumericTextBoxPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  methods: {
    onchange: function(){
      this.$refs.grid.selectRow(parseInt(this.$refs.numeric.getText(), 10));
    }
    rowSelected: function (args) {
        let rowHeight = this.$refs.grid.getRows()[this.$refs.grid.getSelectedRowIndexes()[0]].scrollHeight;
        this.$refs.grid.getContent().children[0].scrollTop = rowHeight * this.$refs.grid.getSelectedRowIndexes()[0];
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Hide the scrollbar when the content is not overflown

You can hide the scrollbar of Grid content by using the [`hideScroll`](../api/grid/#hidescroll) method when the content doesn't overflow its parent element.

In the following sample, we have invoked the [`hideScroll`](../api/grid/#hidescroll) method inside the [`dataBound`](../api/grid/#databound) event.

{% tab template="grid/search/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' height='312px' :dataBound='dataBound'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=100></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=100></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js'

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data.slice(0, 2),
    };
  },
  methods: {
    dataBound: function() {
        this.$refs.grid.hideScroll();
    }
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}
