---
title: "Getting Started"
component: "Grid"
description: "Learn how to create an Essential JS 2 DataGrid control and enable features like paging, filtering, sorting, and grouping."
---

# Getting Started

This section explains you the steps required to create a simple Grid and demonstrate the basic usage of the Grid component in a Vue environment.

To get start quickly with Vue Grid, you can check on this video:

`youtube:pU0ERPrY2go`

## Setup Vue Environment

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications.
To install Vue CLI use the following commands.

```bash
npm install -g @vue/cli
npm install -g @vue/cli-init
```

## Create a Vue Application

Start a new Vue application using below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart
npm install
```

## Adding Syncfusion Grid package

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg) registry.

To install Vue Grid component, use the following command

```bash
npm install @syncfusion/ej2-vue-grids --save
```

> The **--save** will instruct NPM to include the grid package inside of the **dependencies** section of the **package.json**.

## Registering Grid Component

You can register the Grid component in your application by using the **Vue.use()**.

Refer to the code example given below.

```typescript
import { GridPlugin } from '@syncfusion/ej2-vue-grids';

Vue.use(GridPlugin);
```

> Registering **GridPlugin** in vue, will register the grid component along with its required child directives globally.

## Adding CSS Reference

The Grid has different themes. They are:
* Material
* Office 365
* Fabric
* Bootstrap
* High Contrast

import components CSS as given below in **style** section of the **App.vue** file. Here Material theme is used for this sample.

```html
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';  
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';  
@import '../node_modules/@syncfusion/ej2-calendars/styles/material.css';  
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';  
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';  
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

## Adding Grid Component

Add the Vue Grid by using **ejs-grid** selector in **template** section of the **App.vue** file.

{% raw %}

```html
<template>
  <div id="app">
      <ejs-grid> </ejs-grid>
  </div>
</template>

<script>
import Vue from 'vue';
import { GridPlugin } from '@syncfusion/ej2-vue-grids';

Vue.use(GridPlugin);
export default {
  data () {
    return {
    }
  }
}
</script>
```

{% endraw %}

## Defining Row Data

Data for the Grid component is bind by using [`dataSource`](../api/grid/#datasource) property and value is defined in the vue component.
It accepts either array of JavaScript object or **DataManager** instance.

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data"> </ejs-grid>
    </div>
</template>

<script>
import Vue from "vue";
import { GridPlugin } from "@syncfusion/ej2-vue-grids";

Vue.use(GridPlugin);

export default {
  data () {
    return {
      data: [
          { OrderID: 10248, CustomerID: 'VINET', Freight: 32.38 },
          { OrderID: 10249, CustomerID: 'TOMSP', Freight: 11.61 },
          { OrderID: 10250, CustomerID: 'HANAR', Freight: 65.83 },
          { OrderID: 10251, CustomerID: 'VICTE', Freight: 41.34 },
          { OrderID: 10252, CustomerID: 'SUPRD', Freight: 51.3 },
          { OrderID: 10253, CustomerID: 'HANAR', Freight: 58.17 },
          { OrderID: 10254, CustomerID: 'CHOPS', Freight: 22.98 },
          { OrderID: 10255, CustomerID: 'RICSU', Freight: 148.33 },
          { OrderID: 10256, CustomerID: 'WELLI', Freight: 13.97 }
      ]
    }
  }
}
</script>

<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

## Defining Columns

The Grid has an option to define columns as directives. In these column directives, we have properties to customize columns.
Let’s check the properties used here:

* We have added [`field`](../api/grid/column/#field) to map with a property name an array of JavaScript objects.
* We have added [headerText](../api/grid/column/#headertext) to change the title of columns.
* We have used `textAlign` to change the alignment of columns.
By default, columns will be left aligned. To change columns to right align, we need to define [`textAlign`](../api/grid/column/#textalign) as **Right**.
* Also, we have used another useful property, [format](../api/grid/column/#format).
Using this, we can format number and date values to standard or custom formats.
Here, we have defined it for the conversion of numeric values to currency.

```html
<ejs-grid :dataSource="data">
    <e-columns>
      <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
      <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
      <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
    </e-columns>
</ejs-grid>
```

## Module injection

To create Vue Grid with additional features, inject the required modules. The following modules are used to extend Grid's basic functionality.

* **Page** - Inject this module to use paging feature.
* **Sort** - Inject this module to use sorting feature.
* **Filter** - Inject this module to use filtering feature.
* **Group** - Inject this module to use grouping feature.
* **Aggregate** - Inject this module to use aggregate feature.

Register the required array of modules under the key **grid** in the **provide** section.

> Additional feature modules are available [here](./module)

## Enable Paging

The paging feature enables users to view the Grid record in a paged view.
It can be enabled by setting [`allowPaging`](../api/grid/#allowpaging) property to true.
Also, need to inject the **Page** module in the **provide** section as follows.

If we didn't inject the **Page** module, then the pager will not be rendered in Grid.
The pager can be customized using [`pageSettings`](../api/grid/#pagesettings) property.

{% tab template="grid/getting-started/default" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :allowPaging="true" :pageSettings='pageSettings'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page } from "@syncfusion/ej2-vue-grids";

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: [
          { OrderID: 10248, CustomerID: 'VINET', Freight: 32.38 },
          { OrderID: 10249, CustomerID: 'TOMSP', Freight: 11.61 },
          { OrderID: 10250, CustomerID: 'HANAR', Freight: 65.83 },
          { OrderID: 10251, CustomerID: 'VICTE', Freight: 41.34 },
          { OrderID: 10252, CustomerID: 'SUPRD', Freight: 51.3 },
          { OrderID: 10253, CustomerID: 'HANAR', Freight: 58.17 },
          { OrderID: 10254, CustomerID: 'CHOPS', Freight: 22.98 },
          { OrderID: 10255, CustomerID: 'RICSU', Freight: 148.33 },
          { OrderID: 10256, CustomerID: 'WELLI', Freight: 13.97 }
      ],
      pageSettings: { pageSize: 5 }
    };
  },
  provide: {
    grid: [Page]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

## Enable Sorting

The sorting feature enables the user to order the records.
It can be enabled by setting [`allowSorting`](../api/grid/#allowsorting) property as true.
Also, need to inject the **Sort** module in the **provide** section as follow.
If we didn't inject the **Sort** module, then user not able to sort when click on headers.
Sorting feature can be customized using [`sortSettings`](../api/grid/#sortsettings) property.

{% tab template="grid/getting-started/default" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :allowPaging="true" :allowSorting='true' :pageSettings='pageSettings'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Sort } from "@syncfusion/ej2-vue-grids";

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: [
          { OrderID: 10248, CustomerID: 'VINET', Freight: 32.38 },
          { OrderID: 10249, CustomerID: 'TOMSP', Freight: 11.61 },
          { OrderID: 10250, CustomerID: 'HANAR', Freight: 65.83 },
          { OrderID: 10251, CustomerID: 'VICTE', Freight: 41.34 },
          { OrderID: 10252, CustomerID: 'SUPRD', Freight: 51.3 },
          { OrderID: 10253, CustomerID: 'HANAR', Freight: 58.17 },
          { OrderID: 10254, CustomerID: 'CHOPS', Freight: 22.98 },
          { OrderID: 10255, CustomerID: 'RICSU', Freight: 148.33 },
          { OrderID: 10256, CustomerID: 'WELLI', Freight: 13.97 }
      ],
      pageSettings: { pageSize: 5 }
    };
  },
  provide: {
    grid: [Page, Sort]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

## Enable Filtering

The filtering feature enables the user to view the reduced amount of records based on filter criteria.
It can be enabled by setting [`allowFiltering`](../api/grid/#allowfiltering) property as true.
Also, need to inject the **Filter** module in the **provide** section as follow.
If we didn't inject the **Filter** module, then filter bar will not be rendered in Grid.
Filtering feature can be customized using [`filterSettings`](../api/grid/#filtersettings) property.

{% tab template="grid/getting-started/default" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :allowPaging="true" :allowSorting='true' :allowFiltering='true'  :pageSettings='pageSettings'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Sort, Filter } from "@syncfusion/ej2-vue-grids";

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: [
          { OrderID: 10248, CustomerID: 'VINET', Freight: 32.38 },
          { OrderID: 10249, CustomerID: 'TOMSP', Freight: 11.61 },
          { OrderID: 10250, CustomerID: 'HANAR', Freight: 65.83 },
          { OrderID: 10251, CustomerID: 'VICTE', Freight: 41.34 },
          { OrderID: 10252, CustomerID: 'SUPRD', Freight: 51.3 },
          { OrderID: 10253, CustomerID: 'HANAR', Freight: 58.17 },
          { OrderID: 10254, CustomerID: 'CHOPS', Freight: 22.98 },
          { OrderID: 10255, CustomerID: 'RICSU', Freight: 148.33 },
          { OrderID: 10256, CustomerID: 'WELLI', Freight: 13.97 }
      ],
      pageSettings: { pageSize: 5 }
    };
  },
  provide: {
    grid: [Page, Sort, Filter]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

## Enable Grouping

The grouping feature enables users to view the Grid record in a grouped view.
It can be enabled by setting [`allowGrouping`](../api/grid/#allowgrouping) property to true.
Also, need to inject the **Group** module in the **provide** section as follow.
If we didn't inject the **Group** module, then the group drop area will not be rendered in Grid.
Grouping feature can be customized using [`groupSettings`](../api/grid/#groupsettings) property.

{% tab template="grid/getting-started/default" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :allowPaging="true" :allowSorting='true' :allowFiltering='true' :allowGrouping='true' :pageSettings='pageSettings'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Sort, Filter, Group } from "@syncfusion/ej2-vue-grids";

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: [
          { OrderID: 10248, CustomerID: 'VINET', Freight: 32.38 },
          { OrderID: 10249, CustomerID: 'TOMSP', Freight: 11.61 },
          { OrderID: 10250, CustomerID: 'HANAR', Freight: 65.83 },
          { OrderID: 10251, CustomerID: 'VICTE', Freight: 41.34 },
          { OrderID: 10252, CustomerID: 'SUPRD', Freight: 51.3 },
          { OrderID: 10253, CustomerID: 'HANAR', Freight: 58.17 },
          { OrderID: 10254, CustomerID: 'CHOPS', Freight: 22.98 },
          { OrderID: 10255, CustomerID: 'RICSU', Freight: 148.33 },
          { OrderID: 10256, CustomerID: 'WELLI', Freight: 13.97 }
      ],
      pageSettings: { pageSize: 5 }
    };
  },
  provide: {
    grid: [Page, Sort, Filter, Group]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

## Enable Aggregate

The Aggregate feature enables users to view the aggregates of Grid records.
It can be enabled by configured through **e-aggregates** directive.
The **field** and **type** are the minimum properties required to represent an aggregate column.
Also, need to inject the **Aggregate** module in the **provide** section as follow.
If we didn't inject the **Aggregate** module, then the footer table will not be rendered in Grid.
Check [`aggregate`](./aggregates) to know more about its configuration.

{% tab template="grid/getting-started/default" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :allowPaging="true" :allowSorting='true' :allowFiltering='true' :allowGrouping='true' :pageSettings='pageSettings' >
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
          </e-columns>
          <e-aggregates>
            <e-aggregate>
                <e-columns>
                    <e-column type="Sum" field="Freight" format="C2" :footerTemplate='footerSum'></e-column>
                </e-columns>
            </e-aggregate>
          </e-aggregates>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Sort, Filter, Group, Aggregate } from "@syncfusion/ej2-vue-grids";

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: [
          { OrderID: 10248, CustomerID: 'VINET', Freight: 32.38 },
          { OrderID: 10249, CustomerID: 'TOMSP', Freight: 11.61 },
          { OrderID: 10250, CustomerID: 'HANAR', Freight: 65.83 },
          { OrderID: 10251, CustomerID: 'VICTE', Freight: 41.34 },
          { OrderID: 10252, CustomerID: 'SUPRD', Freight: 51.3 },
          { OrderID: 10253, CustomerID: 'HANAR', Freight: 58.17 },
          { OrderID: 10254, CustomerID: 'CHOPS', Freight: 22.98 },
          { OrderID: 10255, CustomerID: 'RICSU', Freight: 148.33 },
          { OrderID: 10256, CustomerID: 'WELLI', Freight: 13.97 }
      ],
      pageSettings: { pageSize: 5 },
      footerSum: function () {
        return  { template : Vue.component('sumTemplate', {
            template: `<span>Sum: {{data.Sum}}</span>`,
            data () {return { data: {data: {}}};}
            })
          }
      }
    };
  },
  provide: {
    grid: [Page, Sort, Filter, Group, Aggregate]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

## Run the application

The Vue Grid application is configured to compile and run the application in a browser. Use the following command to run the application.

```bash
npm run dev
```

{% tab template="grid/getting-started/default", isDefaultActive=true %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :allowPaging="true" :allowSorting='true' :allowFiltering='true' :allowGrouping='true' :pageSettings='pageSettings'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
          </e-columns>
          <e-aggregates>
            <e-aggregate>
                <e-columns>
                    <e-column type="Sum" field="Freight" format="C2" :footerTemplate='footerSum'></e-column>
                </e-columns>
            </e-aggregate>
          </e-aggregates>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Sort, Filter, Group, Aggregate } from "@syncfusion/ej2-vue-grids";

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: [
          { OrderID: 10248, CustomerID: 'VINET', Freight: 32.38 },
          { OrderID: 10249, CustomerID: 'TOMSP', Freight: 11.61 },
          { OrderID: 10250, CustomerID: 'HANAR', Freight: 65.83 },
          { OrderID: 10251, CustomerID: 'VICTE', Freight: 41.34 },
          { OrderID: 10252, CustomerID: 'SUPRD', Freight: 51.3 },
          { OrderID: 10253, CustomerID: 'HANAR', Freight: 58.17 },
          { OrderID: 10254, CustomerID: 'CHOPS', Freight: 22.98 },
          { OrderID: 10255, CustomerID: 'RICSU', Freight: 148.33 },
          { OrderID: 10256, CustomerID: 'WELLI', Freight: 13.97 }
      ],
      pageSettings: { pageSize: 5 },
      footerSum: function () {
        return  { template : Vue.component('sumTemplate', {
            template: `<span>Sum: {{data.Sum}}</span>`,
            data () {return { data: {}};}
            })
          }
      }
    };
  },
  provide: {
    grid: [Page, Sort, Filter, Group, Aggregate]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

> You can refer to our [Vue Grid]( https://www.syncfusion.com/vue-ui-components/vue-grid) feature tour page for its groundbreaking feature representations. You can also explore our [Vue Grid example]( https://ej2.syncfusion.com/vue/demos/#/material/grid/grid-overview.html) that shows how to render the Grid in Vue.

## See Also

* [Testing the Vue Grid](https://www.syncfusion.com/forums/140772/testing-the-vue-grid)
* [Switching themes programmatically in Vue Grid](https://www.syncfusion.com/forums/145386/switching-themes-programmatically-in-vue-grid)