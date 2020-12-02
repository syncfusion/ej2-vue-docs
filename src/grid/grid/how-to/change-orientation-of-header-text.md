---
title: "Change the Orientation of Header Text"
component: "Grid"
description: "Learn how to Change the Orientation of Header Text."
---

# Change the Orientation of Header Text

You can change the orientation of the header text by using the [`customAttributes`](../../api/grid/column/#customattributes) property.

To change the Orientation of Header Text, Ensure the following steps:

**Step 1**:

Create a css class with orientation style for grid header cell.

```css
.orientationcss .e-headercelldiv {
    transform: rotate(90deg);
}
```

**Step 2**:

Add the custom css class to particular column by using [`customAttributes`](../../api/grid/column/#customattributes) property.

```html
    <e-column field='Freight' headerText='Freight' textAlign='Center' format='C2' :customAttributes='customAttributes' width=80></e-column>
```

**Step 3**:

Resize the header cell height by using the following code.

```typescript
setHeaderHeight(args) {
    let textWidth = document.querySelector(".orientationcss > div").scrollWidth;//Obtain the width of the headerText content.
    let headerCell = document.querySelectorAll(".e-headercell");
    for(let i = 0; i < headerCell.length; i++) {
       (headerCell.item(i)).style.height = textWidth + 'px'; //Assign the obtained textWidth as the height of the headerCell.
    }
}

```

{% tab template="grid/how-to/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :created='setHeaderHeight' height='240px' >
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='Freight' headerText='Freight' textAlign='Center' format='C2' :customAttributes='customAttributes' width=80></e-column>
               <e-column field='ShipCity' headerText='Ship City' width=100></e-column>
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
  data: () => {
    return {
      data: data,
      customAttributes : {class : 'orientationcss'},
    };
  },
  methods: {
    setHeaderHeight: function(args) {
      let textWidth = document.querySelector(".orientationcss > div").scrollWidth;//Obtain the width of the headerText content.
      let headerCell = document.querySelectorAll(".e-headercell");
      for (let i = 0; i < headerCell.length; i++) {
        (headerCell.item(i)).style.height = textWidth + 'px'; //Assign the obtained textWidth as the height of the headerCell.
      }
    }
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
   .orientationcss .e-headercelldiv {
    transform: rotate(90deg);
    padding-top:5px;
}
</style>
```

{% endtab %}
