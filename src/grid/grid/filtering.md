---
title: "Filtering"
component: "Grid"
description: "Learn how to filter rows in the DataGrid using the filter bar, menu, and Excel-like filtering. Also learn how to use custom filter components in the Essential JS 2 DataGrid control."
---

# Filtering

Filtering allows you to view particular records based on filter criteria. To enable filtering in the Grid,
set the [`allowFiltering`](../api/grid/#allowfiltering) to true.
Filtering options can be configured through [`filterSettings`](../api/grid/filterSettings/).

To use filter, inject `Filter` module in the `provide` section.

To get start quickly with Filtering Options, you can check on this video:

`youtube:-fgRb6tVNaE`

<!-- The Grid supports three types of filter, they are
* Filter bar
* Excel
* Checkbox -->

{% tab template="grid/filter/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :allowFiltering='true' height='273px'>
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
import { GridPlugin, Filter } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js'
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  provide: {
    grid: [Filter]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> * You can apply and clear filtering, by using
[`filterByColumn`](../api/grid/filter/#filterbycolumn) and [`clearFiltering`](../api/grid/filter/#clearfiltering) methods.
> * To disable Filtering for a particular column, by specifying
[`columns.allowFiltering`](../api/grid/column/#allowfiltering) to false.

## Initial filter

To apply the filter at initial rendering, set the filter [`predicate`](../api/grid/predicate/) object in
[`filterSettings.columns`](../api/grid/filterSettingsModel/#columns).

{% tab template="grid/filter/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :allowFiltering='true' :filterSettings='filterOptions' height='273px'>
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
import { GridPlugin, Filter } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js'
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      filterOptions: {
            columns: [{ field: 'ShipCity', matchCase: false, operator: 'startswith', predicate: 'and', value: 'reims' },
            { field: 'ShipName', matchCase: false, operator: 'startswith', predicate: 'and', value: 'Vins et alcools Chevalier' }]
      }
    };
  },
  provide: {
    grid: [Filter]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Filter operators

The filter operator for a column can be defined in [`filterSettings.columns.operator`](../api/grid/predicateModel/#operator) property.

The available operators and its supported data types are,

Operator |Description |Supported Types
-----|-----|-----
startsWith |Checks whether a value begins with the specified value. |String
endsWith |Checks whether a value ends with specified value. |String
contains |Checks whether a value contains with specified value. |String
equal |Checks whether a value equal to specified value. |String &#124; Number &#124; Boolean &#124; Date
notEqual |Checks whether a value not equal to specified value. |String &#124; Number &#124; Boolean &#124; Date
greaterThan |Checks whether a value is greater than with specified value. |Number &#124; Date
greaterThanOrEqual|Checks whether a value is greater than or equal to specified value. |Number &#124; Date
lessThan |Checks whether a value is less than with specified value. |Number &#124; Date
lessThanOrEqual |Checks whether a value is less than or equal to specified value. |Number &#124; Date

> By default, the [`filterSettings.columns.operator`](../api/grid/predicateModel/#operator) value is **equal**.

## Filter bar

By defining the [`allowFiltering`](../api/grid/#allowfiltering) to true,
then filter bar row will be rendered next to header which allows you to filter data.
 You can filter the records with different expressions depending upon the column type.

 **Filter bar Expressions:**

 You can enter the following filter expressions(operators) manually in the filter bar.

Expression |Example |Description |Column Type
-----|-----|-----|-----
= |=value |equal |Number
!= |!=value |notequal |Number
> |>value |greaterthan |Number
< |<value |lessthan |Number
>= |>=value |greaterthanorequal |Number
<=|<=value|lessthanorequal |Number
* |*value |startswith |String
% |%value |endswith |String
N/A |N/A |Always **equal** operator will be used for Date filter |Date
N/A |N/A |Always **equal** operator will be used for Boolean filter |Boolean

{% tab template="grid/filter/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :allowFiltering='true' height='273px'>
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
import { GridPlugin, Filter } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js'
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  provide: {
    grid: [Filter]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Filter bar template with custom component

The [`filterBarTemplate`](../api/grid/column/#filterbartemplate) is used to add a custom component
for a particular column and this contains the following functions.
* **create** – It is used for creating custom components.
* **write** - It is used to wire events for custom components.

In the following sample dropdown is used  as custom component in EmployeeID column.

{% tab template="grid/filter/default" %}

```html
<template>
    <div id="app">
        <ejs-grid ref='grid' :dataSource='data' :allowFiltering='true' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='EmployeeID' headerText='Employee ID' width=120 :filterBarTemplate='templateOptions'></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=100></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=100></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Filter } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js'
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      templateOptions: {
            create: function (args) {
                let dd = document.createElement('select');
                dd.id = 'EmployeeID';
                let dataSource = ['All','1','3','4','5','6','8','9'];
                for(let i =0; i<dataSource.length;i++){
                    let option = document.createElement('option');
                    option.value = dataSource[i];
                    option.innerHTML = dataSource[i];
                    dd.appendChild(option);
                }
                return dd;
            },
            write: function (args) {
                args.element.addEventListener('input', (args) => {
                    if(args.currentTarget.value !== 'All') {
                        let value = +args.currentTarget.value;
                        this.$refs.grid.filterByColumn(args.currentTarget.id, 'equal', value);
                    } else {
                        this.$refs.grid.removeFilteredColsByField(args.currentTarget.id);
                    }
                });
            }
        }
    };
  },
  provide: {
    grid: [Filter]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Filter menu

You can enable filter menu by setting the [`filterSettings.type`](../api/grid/filterSettings/#type) as **Menu**.
The filter menu UI will be rendered based on its column type, which allows you to filter data.
You can filter the records with different operators.

{% tab template="grid/filter/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :allowFiltering='true' :filterSettings='filterOptions' height='273px'>
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
import { GridPlugin, Filter } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js'
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      filterOptions: {
           type: 'Menu'
        }
    };
  },
  provide: {
    grid: [Filter]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> * [`allowFiltering`](../api/grid/#allowfiltering) must be set as true to enable filter menu.
> * Setting [`columns.allowFiltering`](../api/grid/column/#allowfiltering) as false will prevent
 filter menu rendering for a particular column.

### Custom component in filter menu

The [`column.filter.ui`](../api/grid/column/#filter) is used to add custom filter components to a particular column.
To implement custom filter ui, define the following functions:

* **create**:  Creates custom component.
* **write**: Wire events for custom component.
* **read**: Read the filter value from custom component.

In the following sample, dropdown is used  as custom component in the OrderID column.

{% tab template="grid/filter/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :allowFiltering='true' :filterSettings='filterOptions' height='273px'>
            <e-columns>
                <e-column field='OrderID' :filter= 'filter' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=120></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=100></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=100></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Filter } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';
import { DropDownList } from "@syncfusion/ej2-dropdowns";
import { DataManager } from "@syncfusion/ej2-data";
import {createElement} from "@syncfusion/ej2-base";

Vue.use(GridPlugin);

export default {
  data() {
      let dropInstance = null;
    return {
      data: data,
      filterOptions: {
           type: 'Menu'
        },
        filter: {
            ui: {
                create: function (args) {
                    let db = new DataManager(data);
                    let flValInput = createElement('input', { className: 'flm-input' });
                    args.target.appendChild(flValInput);
                    dropInstance = new DropDownList({
                    dataSource: new DataManager(data),
                    fields: { text: 'OrderID', value: 'OrderID' },
                    placeholder: 'Select a value',
                    popupHeight: '200px'
                });
                dropInstance.appendTo(flValInput);
                },
                write: function (args) {
                    dropInstance.value = args.filteredValue;
                },
                read: function (args) {
                    args.fltrObj.filterByColumn(args.column.field, args.operator, dropInstance.value);
                }
            }
        }
    };
  },
  provide: {
    grid: [Filter]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

### Enable different filter for a column

You can use both **Menu** and **Checkbox** filter in a same Grid. To do so, set the
[`column.filter.type`](../api/grid/column/#filter) as **Menu** or **Checkbox**.

In the following sample menu filter is enabled by default and checkbox filter is enabled for the CustomerID column using the
[`column.filter.type`](../api/grid/column/#filter).

{% tab template="grid/filter/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :allowFiltering='true' :filterSettings='filterOptions' height='273px'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=100></e-column>
                <e-column field='CustomerID' :filter='filter' headerText='Customer ID' width=120></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=100></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=100></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Filter } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js'
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      filterOptions: {
        type: 'Menu'
      },
      filter: {
        type : 'CheckBox'
      }
    };
  },
  provide: {
    grid: [Filter]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## Diacritics

By default, grid ignores diacritic characters while filtering. To include diacritic characters, set the
[`filterSettings.ignoreAccent`](../api/grid/filterSettings/#ignoreaccent) as **true**.

In the following sample, type **mun** in **Ship City** column to filter diacritic characters.

{% tab template="grid/filter/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' :allowFiltering='true' :filterSettings='filterOptions' height='273px'>
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
import { GridPlugin, Filter } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js'
Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      filterOptions: {
        ignoreAccent: true
      }
    };
  },
  provide: {
    grid: [Filter]
  }
}
</script>
<style>
 @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

## See also

* [Customizing filter menu operators list](./how-to/customizing-filter-menu-operators-list)
