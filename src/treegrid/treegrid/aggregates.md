---
title: "Aggregates"
component: "TreeGrid"
description: "Learn how to aggregate rows, apply custom aggregates, and format the aggregate values in the Essential JS 2 TreeGrid control."
---

# Aggregates

Aggregate values are displayed in the TreeGrid footer and in parent row footer for child row aggregate values. It can be configured through `aggregates` property.
 [`field`](../api/treegrid/aggregateColumnModel/#field) and [`type`](../api/treegrid/aggregateColumnModel/#type)
 are the minimum properties required to represent an aggregate column.

To use the aggregate feature, you have to inject the `Aggregate` module.

By default, the aggregate value can be displayed in the treegrid footer, and footer of child rows. To show the aggregate value in one of the cells, use the [`footerTemplate`](../api/treegrid/aggregateColumnModel/#footertemplate).

## Built-in aggregate types

The aggregate type should be specified in the [`type`](../api/treegrid/aggregateColumnModel/#type) property to configure an aggregate column.

The built-in aggregates are,
* Sum
* Average
* Min
* Max
* Count
* Truecount
* Falsecount

> * Multiple aggregates can be used for an aggregate column by setting the [`type`](../api/treegrid/aggregateColumnModel/#type) property
with an array of aggregate types.
> * Multiple types for a column is supported only when one of the aggregate templates is used.

## Footer aggregate

Footer aggregate value is calculated for all the rows, and it is displayed in the footer cells. Use the [`footerTemplate`](../api/treegrid/aggregateColumnModel/#footertemplate) property to render the aggregate value in footer cells.

{% tab template="treegrid/aggregates/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='children' :treeColumnIndex='1' height='260px'>
            <e-columns>
                <e-column field='FreightID' headerText='Freight ID' width=90 textAlign='Right'></e-column>
                <e-column field='FreightName' headerText='Freight Name' width=180></e-column>
                <e-column field='UnitWeight' headerText='Unit Per Weight' width=90 type='number' textAlign='Right'></e-column>
                <e-column field='TotalUnits' headerText='Total Units' type='number' width=80 textAlign='Right'></e-column>
            </e-columns>
              <e-aggregates>
                <e-aggregate :showChildSummary='false'>
                    <e-columns>
                        <e-column type="Max" field="UnitWeight" :footerTemplate='footerMax'></e-column>
                        <e-column type="Min" field="TotalUnits" :footerTemplate='footerMin'></e-column>
                    </e-columns>
                </e-aggregate>
          </e-aggregates>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Aggregate } from "@syncfusion/ej2-vue-treegrid";
import { summaryRowData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: summaryRowData,
            footerMin: function () {
        return  { template : Vue.component('minTemplate', {
            template: `<span>Min: {{data.Min}}</span>`,
            data () {return { data: {}};}
            })
          }
      },
      footerMax: function () {
        return  { template : Vue.component('maxTemplate', {
            template: `<span>Max: {{data.Max}}</span>`,
            data () {return { data: {}};}
            })
          }
      }
    };
  },
    provide: {
      treegrid: [Aggregate]
  }
}
</script>

```

{% endtab %}

> The aggregate values must be accessed inside the template using their corresponding [`type`](../api/treegrid/aggregateColumnModel/#type) name.

## Child aggregate

Aggregate value is calculated for child rows, and it is displayed in the parent row footer. Use the [`childSummary`](../api/treegrid/aggregateRowModel/#showchildsummary) property to render the child rows aggregate value.

{% tab template="treegrid/aggregates/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='children' :treeColumnIndex='1' height='260px'>
            <e-columns>
                <e-column field='FreightID' headerText='Freight ID' width=90 textAlign='Right'></e-column>
                <e-column field='FreightName' headerText='Freight Name' width=180></e-column>
                <e-column field='UnitWeight' headerText='Unit Per Weight' width=90 type='number'textAlign='Right'></e-column>
                <e-column field='TotalUnits' headerText='Total Units' type='number' width=80 textAlign='Right'></e-column>
            </e-columns>
              <e-aggregates>
                <e-aggregate :showChildSummary='true'>
                    <e-columns>
                        <e-column type="Max" field="UnitWeight" :footerTemplate='footerMax'></e-column>
                        <e-column type="Min" field="TotalUnits" :footerTemplate='footerMin'></e-column>
                    </e-columns>
                </e-aggregate>
          </e-aggregates>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Aggregate } from "@syncfusion/ej2-vue-treegrid";
import { summaryRowData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: summaryRowData,
            footerMin: function () {
        return  { template : Vue.component('minTemplate', {
            template: `<span>Min: {{data.Min}}</span>`,
            data () {return { data: {}};}
            })
          }
      },
      footerMax: function () {
        return  { template : Vue.component('maxTemplate', {
            template: `<span>Max: {{data.Max}}</span>`,
            data () {return { data: {}};}
            })
          }
      }
    };
  },
    provide: {
      treegrid: [Aggregate]
  }
}
</script>

```

{% endtab %}

## How to format aggregate value

You can format the aggregate value result by using the [`format`](../api/treegrid/aggregateColumnModel/#type) property.

{% tab template="treegrid/aggregates/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource="data" childMapping='subtasks' :treeColumnIndex='1' height='260px'>
            <e-columns>
                <e-column field='category' headerText='Category' width=160 textAlign='Right'></e-column>
                <e-column field='units' headerText='Total Units' width=130  type='number'></e-column>
                <e-column field='unitPrice' headerText='Unit Price($)' width=110 type='number' format= 'C2' textAlign='Right'></e-column>
                <e-column field='price' headerText='Price($)' type='number' width=160 format= 'C2' textAlign='Right'></e-column>
            </e-columns>
              <e-aggregates>
                <e-aggregate>
                    <e-columns>
                        <e-column type="Sum" field="price"  format="C2" :footerTemplate='footerSum'></e-column>
                    </e-columns>
                </e-aggregate>
          </e-aggregates>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Aggregate } from "@syncfusion/ej2-vue-treegrid";
import { summaryData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data() {
    return {
      data: summaryData,
            footerSum: function () {
        return  { template : Vue.component('minTemplate', {
            template: `<span>Sum: {{data.Sum}}</span>`,
            data () {return { data: {}};}
            })
          }
      }
    };
  },
    provide: {
      treegrid: [Aggregate]
  }
}
</script>

```

{% endtab %}