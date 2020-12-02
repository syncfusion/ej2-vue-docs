---
title: "Search"
component: "TreeGrid"
description: "Learn how to search TreeGrid content, change search operators, perform searches using external buttons, and search particular fields."
---

# Search

You can search records in a TreeGrid, by using the [`search`](../api/treegrid/#search) method with search key as a parameter. This also provides an option to integrate search text box in treegrid's toolbar by adding `search` item to the [`toolbar`](../api/treegrid/#toolbar).

To search records, inject the [`Filter`](../api/treegrid/#fitermodule) module in the treegrid.

{% tab template="treegrid/searching/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :toolbar='toolbarOptions' height='270px'>
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
import { TreeGridPlugin, Filter, Toolbar } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbarOptions: ['Search']
    };
  },
  provide: {
      treegrid: [ Filter, Toolbar ]
    }
}
</script>

```

{% endtab %}

## Initial search

To apply search at initial rendering, set the fields, operator, key, and ignoreCase in the [`searchSettings`](../api/treegrid/#searchsettings).

{% tab template="treegrid/searching/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :toolbar='toolbarOptions' height='270px' :searchSettings='searchOptions' >
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
import { TreeGridPlugin, Filter, Toolbar } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
        data: sampleData,
        toolbarOptions: ['Search'],
        searchOptions: { fields: ['taskName'], operator: 'contains', key: 'plan', ignoreCase: true }
    };
  },
  provide: {
      treegrid: [ Filter, Toolbar ]
    }
}
</script>

```

{% endtab %}

> By default, treegrid searches all the bound column values. To customize this behavior define the [`searchSettings.fields`](../api/treegrid/searchSettingsModel/#fields) property.

## Search operators

The search operator can be defined in the [`searchSettings.operator`](../api/treegrid/searchSettingsModel/#operator) property to configure specific searching.

The following operators are supported in searching:

Operator |Description
-----|-----
startsWith |Checks whether a value begins with the specified value.
endsWith |Checks whether a value ends with the specified value.
contains |Checks whether a value contains the specified value.
equal |Checks whether a value is equal to the specified value.
notEqual |Checks for values not equal to the specified value.

> By default, the [`searchSettings.operator`](../api/treegrid/searchSettingsModel/#operator) value is `contains`.

## Search by external button

To search treegrid records from an external button, invoke the [`search`](../api/treegrid/#search) method.

{% tab template="treegrid/searching/default" %}

```html
<template>
<div id="app">
<div class="e-float-input" style="width: 200px; display: inline-block;">
                <input type="text" class="searchtext"/>
                <span class="e-float-line"></span>
                <label class="e-float-text">Search text</label>
            </div>
        <ejs-button id='search' @click.native='search'>Search</ejs-button>
        <ejs-treegrid ref='treegrid' :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' height='220px'>
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
import { ButtonPlugin } from '@syncfusion/ej2-vue-buttons';
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);
Vue.use(ButtonPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
    };
  },
    provide: {
      treegrid: [ Filter ]
    },
    methods:{
        search: function() {
        let searchText = document.getElementsByClassName('searchtext')[0].value;
        this.$refs.treegrid.search(searchText);
    }
}
}
</script>

```

{% endtab %}

## Search specific columns

By default, treegrid searches all visible columns. You can search specific columns by defining the specific column's field names in the [`searchSettings.fields`](../api/treegrid/searchSettingsModel/#fields) property.

{% tab template="treegrid/searching/default" %}

```html
<template>
<div id="app">
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' :toolbar='toolbarOptions' height='270px' :searchSettings='searchOptions'>
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
import { TreeGridPlugin, Filter, Toolbar } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      toolbarOptions: ['Search'],
      searchOptions: {fields: ['taskName', 'duration']}
    };
  },
  provide: {
      treegrid: [ Filter, Toolbar ]
    }
}
</script>

```

{% endtab %}