---
title: "Search"
component: "Grid"
description: "Learn how to search DataGrid content, change search operators, perform searches using external buttons, and search particular fields."
---

# Search

You can search records in a Grid, by using the [`search`](../api/grid/#search) method with search key as a parameter.
This also provides an option to integrate search text box in grid's toolbar by adding **Search** item to the
[`toolbar`](../api/grid/#toolbar).

To use searching, you need to inject [`Search`](../api/grid/search) module in the **provide** section.

{% tab template="grid/search/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :toolbar='toolbarOptions' height='272px'>
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
import { GridPlugin, Toolbar, Search } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js'
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      toolbarOptions: ['Search']
    };
  },
  provide: {
    grid: [Toolbar, Search]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Initial search

To apply search at initial rendering, set the fields, operator, key, and ignoreCase in the [`searchSettings`](../api/grid/#searchsettings).

{% tab template="grid/search/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :searchSettings='searchOptions' :toolbar='toolbarOptions' height='272px'>
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
import { GridPlugin, Toolbar, Search } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js'
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      toolbarOptions: ['Search'],
      searchOptions: { fields: ['CustomerID'], operator: 'contains', key: 'Ha', ignoreCase: true }
    };
  },
  provide: {
    grid: [Toolbar, Search]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> By default, grid searches all the bound column values. To customize this behavior define
the [`searchSettings.fields`](../api/grid/searchSettings/#fields) property.

## Search operators

The search operator can be defined in [`searchSettings.operator`](../api/grid/searchSettings/#operator) property
to configure specified searching.

The following operators are supported in searching:

Operator |Description
-----|-----
startsWith |Checks whether a value begins with the specified value.
endsWith |Checks whether a value ends with specified value.
contains |Checks whether a value contains with specified value.
equal |Checks whether a value equal to specified value.
notEqual |Checks whether a value not equal to specified value.

## Search by external button

To search grid records from an external button, invoke the [`search`](../api/grid/#search) method.

{% tab template="grid/search/default" %}

```html
<template>
    <div id="app">
        <div class="e-float-input" style="width: 200px; display: inline-block;">
                <input type="text" class="searchtext"/>
                <span class="e-float-line"></span>
                <label class="e-float-text">Search text</label>
            </div>
        <ejs-button id='search' @click.native='search'>Search</ejs-button>
        <ejs-grid ref='grid' :dataSource='data' height='262px'>
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
import { GridPlugin, Toolbar, Search } from "@syncfusion/ej2-vue-grids";
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { data } from './datasource.js'

Vue.use(GridPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  methods: {
    search: function() {
        let searchText = document.getElementsByClassName('searchtext')[0].value;
        this.$refs.grid.search(searchText);
    }
  },
  provide: {
    grid: [Search]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Search Specific Columns

By default, grid searches all visible columns. You can search specific columns by defining the specific column's field names in the
[`searchSettings.fields`](../api/grid/searchSettings/#fields) property.

{% tab template="grid/search/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :searchSettings='searchOptions' :toolbar='toolbarOptions' height='272px'>
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
import { GridPlugin, Toolbar, Search } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js'
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      toolbarOptions: ['Search'],
      searchOptions: {fields: ['CustomerID', 'ShipCity']}
    };
  },
  provide: {
    grid: [Toolbar, Search]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Clear search by external button

To clear the searched grid records from the external button, set [`searchSettings.key`](../api/grid/searchSettings/#key) property as **empty** string.

{% tab template="grid/search/default" %}

```html
<template>
    <div id="app">
        <ejs-button id='clear' @click.native='clear'>Clear Search</ejs-button>
        <ejs-grid ref='grid' :dataSource='data' :searchSettings='searchOptions' :toolbar='toolbarOptions' height='262px'>
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
import { GridPlugin, Toolbar, Search } from "@syncfusion/ej2-vue-grids";
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { data } from './datasource.js'

Vue.use(GridPlugin);
Vue.use(ButtonPlugin);

export default {
  data() {
    return {
      data: data,
      toolbarOptions: ['Search'],
      searchOptions: { fields: ['CustomerID'], operator: 'contains', key: 'Ha', ignoreCase: true }
    };
  },
  methods: {
    clear: function() {
        this.$refs.grid.ej2Instances.searchSettings.key = "";
    }
  },
  provide: {
    grid: [Search,Toolbar]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}
