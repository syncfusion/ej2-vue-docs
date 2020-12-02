---
title: "Filtering"
component: "TreeGrid"
description: "Learn how to filter rows in the TreeGrid using the filter bar, and menu filtering. Also learn how to use custom filter components in the Essential JS 2 TreeGrid control."
---

# Filtering

Filtering allows you to view specific or related records based on filter criteria. To enable filtering in the TreeGrid, set the [`allowFiltering`](../api/treegrid/#allowfiltering) to true. Filtering options can be configured through [`filterSettings`](../api/treegrid/#filtersettings).

To use filter, inject the `Filter` module in the treegrid.

{% tab template="treegrid/filtering/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :allowFiltering='true' height='275px'>
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
import { TreeGridPlugin, Filter } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
    };
  },
  provide: {
      treegrid: [ Filter ]
    }
}
</script>

```

{% endtab %}

> * You can apply and clear filtering by using [`filterByColumn`](../api/treegrid/#filterbycolumn) and [`clearFiltering`](../api/treegrid/#clearfiltering) methods.
> * To disable filtering for a particular column, set
[`columns.allowFiltering`](../api/treegrid/column/#allowfiltering) to false.

## Filter Hierarchy Modes

TreeGrid provides support for a set of filtering modes with [`filterSettings.filterHierarchyMode`](../api/treegrid/filterSettingsModel/#hierarchymode) property.
The below are the type of filter mode available in TreeGrid.

* **Parent** : This is the default filter hierarchy mode in TreeGrid. The filtered records are displayed with its parent records, if the filtered records not have any parent record then the filtered records only displayed.

* **Child** : The filtered records are displayed with its child record, if the filtered records not have any child record then the filtered records only displayed.

* **Both** : The filtered records are displayed with its both parent and child record, if the filtered records not have any parent and child record then the filtered records only displayed.

* **None** : The filtered records are only displayed.

{% tab template="treegrid/filtering/default" %}

```html
<template>
<div id="app">
 <div style="padding-top: 7px; display: inline-block">Hierarchy Mode</div>
  <div style="display: inline-block; width: 150px">
<ejs-dropdownlist id='mode' :dataSource='ddldata'  :fields='fields' :value='value' :popupHeight='height' :change='change'></ejs-dropdownlist>
</div>
        <ejs-treegrid ref='treegrid' :dataSource='data' childMapping='subtasks' :treeColumnIndex='1'  :allowFiltering='true' height='225px'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='75' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='180'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Filter, TreeGridComponent  } from "@syncfusion/ej2-vue-treegrid";
import { DropDownListPlugin, ChangeEventArgs } from '@syncfusion/ej2-vue-dropdowns';
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);
Vue.use(DropDownListPlugin);

export default {
  data () {
    return {
      data: sampleData,
      height: '220px',
      ddldata : [{ id: 'Parent', mode: 'Parent' },
      { id: 'Child', mode: 'Child' },
      { id: 'Both', mode: 'Both' },
      { id: 'None', mode: 'None' }
    ],
    fields: { text: 'mode', value: 'id' },
    value: 'Parent'
    };
  },
    provide: {
      treegrid: [ Filter ]
    },
    methods: {
        change: function (e: ChangeEventArgs)  {
        let mode: any = e.value;
        this.$refs.treegrid.ej2Instances.filterSettings.hierarchyMode = mode;
        this.$refs.treegrid.clearFiltering();
    }
    }
}
</script>

```

{% endtab %}

## Initial filter

To apply the filter at initial rendering, set the filter `predicate` object in
[`filterSettings.columns`](../api/treegrid/filterSettingsModel/#columns).

{% tab template="treegrid/filtering/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1'  :allowFiltering='true'  :filterSettings='filterOptions' height='275px'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='75' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='180'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Filter } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data () {
    return {
      data: sampleData,
      filterOptions: {
            columns: [{ field: 'taskName', matchCase: false, operator: 'startswith', predicate: 'and', value: 'plan' },
            { field: 'duration', matchCase: false, operator: 'equal', predicate: 'and', value: 5 }]
      }
    };
  },
    provide: {
      treegrid: [ Filter ]
    }
}
</script>

```

{% endtab %}

## Filter operators

The filter operator for a column can be defined in the `filterSettings.columns.operator` property.

The available operators and its supported data types are:

Operator |Description |Supported Types
-----|-----|-----
startswith |Checks whether the value begins with the specified value. |String
endswith |Checks whether the value ends with the specified value. |String
contains |Checks whether the value contains the specified value. |String
equal |Checks whether the value is equal to the specified value. |String &#124; Number &#124; Boolean &#124; Date
notequal |Checks for values not equal to the specified value. |String &#124; Number &#124; Boolean &#124; Date
greaterthan |Checks whether the value is greater than the specified value. |Number &#124; Date
greaterthanorequal|Checks whether a value is greater than or equal to the specified value. |Number &#124; Date
lessthan |Checks whether the value is less than the specified value. |Number &#124; Date
lessthanorequal |Checks whether the value is less than or equal to the specified value. |Number &#124; Date

> By default, the `filterSettings.columns.operator` value is `equal`.

## Filter bar

By setting the [`allowFiltering`](../api/treegrid/#allowfiltering) to true, the filter bar row will render next to the header, which allows you to filter data. You can filter the records with different expressions depending upon the column type.

 **Filter bar expressions:**

 You can enter the following filter expressions (operators) manually in the filter bar.

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
N/A |N/A | `Equal` operator will always be used for date filter. |Date
N/A |N/A |`Equal` operator will always be used for Boolean filter. |Boolean

{% tab template="treegrid/filtering/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1'  :allowFiltering='true' height='275px'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='75' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='180'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Filter } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
    };
  },
   provide: {
    treegrid: [Filter]
  }
}
</script>

```

{% endtab %}

### Change default filter operator

You can change the default filter operator by extending `filterModule.filterOperators`property in [`dataBound`](../api/treegrid#databound) event. In the following sample, we have changed the default operator for string typed columns as `contains` from `startsWith`.

{% tab template="treegrid/filtering/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid ref='treegrid':dataSource='data'  childMapping='subtasks' :treeColumnIndex='1'  :allowFiltering='true' height='275px' :dataBound='dataBound'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='75' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='180'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Filter } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
    };
  },
   provide: {
    treegrid: [Filter]
  },
  methods: {
    dataBound(args){
    this.$refs.treegrid.ej2Instances.grid.filterModule.filterOperators.startsWith="contains"
   }
    }
  }

</script>

```

{% endtab %}

## Filter menu

You can enable filter menu by setting the [`filterSettings.type`](../api/treegrid/filterSettingsModel/#type) as `Menu`. The filter menu UI will be rendered based on its column type, which allows you to filter data.
You can filter the records with different operators.

{% tab template="treegrid/filtering/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1'  :allowFiltering='true' height='275px' :filterSettings='filterSettings'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='75' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='120'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Filter } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data () {
    return {
      data: sampleData,
      filterSettings: {
           type: 'Menu'
      }
    };
  },
  provide: {
      treegrid: [ Filter ]
    }
}
</script>

```

{% endtab %}

> * [`allowFiltering`](../api/treegrid/#allowfiltering) must be set as true to enable filter menu.
> * Setting [`columns.allowFiltering`](../api/treegrid/column/#allowfiltering) as false will prevent filter menu rendering for a particular column.

### Enable different filter for a column

You can use both `Menu` and `Excel` filter in a same TreeGrid. To do so, set the
[`column.filter.type`](../api/treegrid/column/#filter) as `Menu` or `Excel`.

In the following sample menu filter is enabled by default and Excel filter is enabled for the Task Name column using the
[`column.filter.type`](../api/treegrid/column/#filter).

{% tab template="treegrid/filtering/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :allowFiltering='true' height='273px' :filterSettings='filterOptions'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160' :filter='filter'></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='80' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Filter } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      filterOptions: {
        type: 'Menu'
      },
      filter: {
        type : 'Excel';
      }
    };
  },
  provide: {
      treegrid: [ Filter ]
    }
}
</script>

```

{% endtab %}

## Excel like filter

You can enable Excel like filter by defining.
[`filterSettings.type`](../api/treegrid/filterSettingsModel/#type) as `Excel`.The excel menu contains an option such as Sorting, Clear filter, Sub menu for advanced filtering.

{% tab template="treegrid/filtering/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :allowFiltering='true' height='273px' :filterSettings='filterOptions'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160' ></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='90' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Filter } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      filterOptions: {
        type: 'Excel'
      }
    };
  },
  provide: {
      treegrid: [ Filter ]
    }
}
</script>

```

{% endtab %}

### Change default Excel filter operator

You can change the default excel-filter operator by changing the column operator as `contains` from `startsWith` in the [`actionBegin`](../api/treegrid#actionbegin) event.

{% tab template="treegrid/filtering/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :allowFiltering='true' height='273px' :filterSettings='filterOptions' :actionBegin = 'actionBegin'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' width='90' textAlign='Right'></e-column>
                <e-column field='taskName' headerText='Task Name' width='160' ></e-column>
                <e-column field='startDate' headerText='Start Date' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='duration' headerText='Duration' width='90' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Filter } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      filterOptions: {
        type: 'Excel'
      }
    };
  },
  provide: {
      treegrid: [ Filter ]
    },
     methods: {
    actionBegin(args) {
       if(args.requestType === 'filtersearchbegin' && args.column.type === "string")
      {
        args.operator = 'contains';
      }
    }
  }
}
</script>

```

{% endtab %}

## Diacritics

By default, treegrid ignores diacritic characters while filtering. To include diacritic characters, set the
[`filterSettings.ignoreAccent`](../api/treegrid/filterSettingsModel/#ignoreaccent) as `true`.

In the following sample, type **aero** in `Name` column to filter diacritic characters.

{% tab template="treegrid/filtering/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='Children' :treeColumnIndex='0'  :allowFiltering='true' height='275px'  :filterSettings='filterSettings'>
            <e-columns>
                <e-column field='EmpID' headerText='Employee ID' width='90' textAlign='Right'></e-column>
                <e-column field='Name' headerText='Name' width='110'></e-column>
                <e-column field='DOB' headerText='DOB' width='90' format="yMd" textAlign='Right'></e-column>
                <e-column field='Country' width='65'></e-column>
            </e-columns>
        </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { TreeGridPlugin, Filter } from "@syncfusion/ej2-vue-treegrid";
import { diacritics } from "./datasource.js";

Vue.use(TreeGridPlugin),

export default {
  data ()  {
    return {
      data: diacritics,
       filterSettings: {
        ignoreAccent: true
      }
    };
    },
  provide: {
    treegrid: [Filter]
  }
  }
</script>

```

{% endtab %}