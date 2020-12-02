---
title: "Paging"
component: "Grid"
description: "Learn how to add custom elements in Pager using pager template and customize the pager in the Essential JS 2 DataGrid control."
---

# Paging

Paging provides an option to display Grid data in page segments. To enable paging, set the
[`allowPaging`](../api/grid/#allowpaging) to true. When paging is enabled, pager component renders at the bottom of the grid.
Paging options can be configured through the [`pageSettings`](../api/grid/pageSettings/).

In the below sample, [`pageSize`](../api/grid/pageSettings/#pagesize) is calculated based on the grid height by using the [`load`](../api/grid/#load) event.

To use Paging, you need to inject [`Page`](../api/grid/page/) module in the **provide** section.

{% tab template="grid/page/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource="data" :allowPaging="true" :pageSettings='pageSettings' height=323 :load='load'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
            <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page } from "@syncfusion/ej2-vue-grids";
import { data } from "./datasource.js";

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      pageSettings: { pageSize: 5 }
    };
  },
  methods: {
    load: function() {
      let rowHeight = this.$refs.grid.ej2Instances.getRowHeight();  //height of the each row
      let gridHeight = this.$refs.grid.height;  //grid height
      let pageSize = this.$refs.grid.pageSettings.pageSize;   //initial page size
      let pageResize = (gridHeight - (pageSize * rowHeight)) / rowHeight; //new page size is obtained here
      this.$refs.grid.pageSettings = {pageSize: pageSize + Math.round(pageResize)};
    }
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

{% endtab %}

> You can achieve better performance by using grid paging to fetch only a pre-defined number of records from the data source.

## Template

You can use custom elements inside the pager instead of default elements.
The custom elements can be defined by using [`pagerTemplate`](../api/grid/pageSettings/#template).
Inside this template, you can access the [`CurrentPage`](../api/grid/pageSettings/#currentpage),
[`pageSize`](../api/grid/pageSettings/#pagesize),
[`pageCount`](../api/grid/pageSettings/#pagecount),
**totalPage** and **totalRecordCount** values.

{% tab template="grid/page/template" %}

```html
<template>
    <div id="app">
        <ejs-grid ref="grid" :dataSource="data" :allowPaging="true" :pageSettings='pageSettings' :pagerTemplate='pagerTemp'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
            <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page } from "@syncfusion/ej2-vue-grids";
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";
import { data } from "./datasource.js";

Vue.use(GridPlugin);
Vue.use(NumericTextBoxPlugin);

export default {
  data() {
    return {
      data: data,
      pageSettings: { pageSize: 5 },
      pagerTemp: function() {
        return {
          template: Vue.component("pagerTemplate", {
            template: `<div class="e-pagertemplate">
                        <div class="col-lg-12 control-section">
                            <div class="content-wrapper">
                                <ejs-numerictextbox width="100" :value="value" :change='change'></ejs-numerictextbox>
                            </div>
                        </div>
                        <div id="totalPages" class="e-pagertemplatemessage"
                          style="margin-top:5px;margin-left:30px;border: none; display: inline-block ">
                              <span class="e-pagenomsg">{{this.$data.data.currentPage}} of {{this.$data.data.totalPages}} pages
                              ({{this.$data.data.totalRecordsCount}} items)</span>
                        </div>
                      </div>`,
            computed: {
              value: function() {
                return this.$data.data.currentPage;
              }
            },
            methods: {
              change: function(args) {
                let grid: any = this.$el.closest(".e-grid").ej2_instances[0];
                grid.goToPage(args.value);
              }
            }
          })
        };
      }
    };
  },
  provide: {
    grid: [Page]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";

 .e-pagertemplate {
  display: inline-block;
  overflow: hidden;
}

.control-section {
  margin-left: 20px;
  width: 25%
}

.content-wrapper {
  width: 25%;
  margin: 0 auto;
  min-width: 185px;
}

.e-float-input.e-numeric.e-input-group {
  margin-top: 12px;
  display: inline-flex;
  width: 180px;
}

@media (max-width: 1120px) {
  .e-pager .content-wrapper {
      display: inline-block
}
</style>
```

{% endtab %}

## Pager with Page Size Dropdown

The pager Dropdown allows you to change the number of records in the Grid dynamically. It can be enabled by defining the [`pageSettings.pageSizes`](../api/grid/pageSettings/#pagesizes) property as true.

{% tab template="grid/page/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource="data" :allowPaging="true" :pageSettings='pageSettings'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
            <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page } from "@syncfusion/ej2-vue-grids";
import { data } from "./datasource.js";

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      pageSettings: { pageSizes: true, pageSize: 9 }
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

{% endtab %}

## How to render Pager at the Top of the Grid

By default, Pager will be rendered at the bottom of the Grid. You can also render the Pager at the top of the Grid by using the [`dataBound`](../api/grid/#databound) event.

{% tab template="grid/page/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource="data" :allowPaging="true" :pageSettings='pageSettings' :toolbar='toolbar' :dataBound='dataBound'>
          <e-columns>
            <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=90></e-column>
            <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
            <e-column field='Freight' headerText='Freight' textAlign='Right' format='C2' width=90></e-column>
            <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
          </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Page, Toolbar } from "@syncfusion/ej2-vue-grids";
import { data } from "./datasource.js";

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      initialGridLoad: true,
      pageSettings: { pageSizes: true, pageSize: 9 },
      toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel']
    };
  },
  methods: {
    dataBound: function() {
      if (this.initialGridLoad) {
          this.initialGridLoad = false;
          let pager = document.getElementsByClassName('e-gridpager');
          let topElement;
          console.log('allowGroping n toolbar', this.$refs.grid);
        if (this.$refs.grid.allowGrouping || this.$refs.grid.toolbar) {
            topElement = this.$refs.grid.allowGrouping ? document.getElementsByClassName('e-groupdroparea') :
                        document.getElementsByClassName('e-toolbar');
        } else {
            topElement = document.getElementsByClassName('e-gridheader');
        }
        console.log('insetBefore',this.$refs.grid.$el);
        this.$refs.grid.$el.insertBefore(pager[0], topElement[0]);
      }
    }
  },
  provide: {
    grid: [Page, Toolbar]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> During the paging action, the pager component triggers the below three events.
> * The [`created`](../api/pager/pagerModel/#created) event triggers when Pager is created.
> * The [`click`](../api/pager/pagerModel/#click) event triggers when the numeric items in the pager is clicked.
> * The [`dropDownChanged`](../api/pager/pagerModel/#dropdownchanged) event triggers when pageSize DropDownList value is selected.

## See Also

* [Group with Paging](./grouping#group-with-paging)
