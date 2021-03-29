---
title: "Infinite Scrolling"
component: "TreeGrid"
description: "Learn how to improve performance in the Essential JS 2 TreeGrid control by using this infinite scroll feature. Also learn about the limitations of this feature."
---

# Infinite scrolling

Infinite scrolling is used to load a huge amount of data without degrading the TreeGrid performance. This feature works like the lazy loading concept, which means the buffer data is loaded only when the scrollbar reaches the end of the scroller.

To enable Infinite scrolling, set `enableInfiniteScrolling` property as true.

> * In this feature, TreeGrid will not make a new data request when you visit the same page again.

{% tab template="treegrid/scroll/virtualscroll" %}

```html
<template>
    <div id="app">
        <ejs-treegrid ref='treegrid' :dataSource="virtualData" :enableInfiniteScrolling='true' :treeColumnIndex='1' childMapping='Crew' :height=317 :pageSettings='pageSettings'>
            <e-columns>
                <e-column field='TaskID' headerText='Player Jersey' width='140' textAlign='Right'></e-column>
                <e-column field='FIELD1' headerText='Player Name' width='140'></e-column>
                <e-column field='FIELD2' headerText='Year' width='105' textAlign='Right'></e-column>
                <e-column field='FIELD3' headerText='Stint' width='90' textAlign='Right'></e-column>
                <e-column field='FIELD4' headerText='TMID' width='90' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
    </div>
</template>
<script>

import Vue from "vue";
import { TreeGridPlugin, InfiniteScroll, TreeGridComponent, Page } from "@syncfusion/ej2-vue-treegrid";
import { DataManager, JsonAdaptor } from '@syncfusion/ej2-data';
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { dataSource, virtualData } from './datasource.js';

Vue.use(TreeGridPlugin);

export default {
  data: function() {
    return {
        virtualData: dataSource(),
        pageSettings: { pageSize: 50 }
    };
  },
  provide: {
      treegrid: [InfiniteScroll, Page]
  }
}
</script>

```

{% endtab %}

## InitialBlocks

You can define the initial loading pages count by using `infiniteScrollSettings.initialBlocks` property. By default, this feature loads three pages in initial rendering.

In the below demo, we have changed this property value to load five page records instead of three.

{% tab template="treegrid/scroll/virtualscroll" %}

```html
<template>
    <div id="app">
        <ejs-treegrid ref='treegrid' :dataSource="virtualData" :enableInfiniteScrolling='true' :treeColumnIndex='1' childMapping='Crew' :height=317 :pageSettings='pageSettings' :infiniteScrollSettings='infiniteScrollSettings'>
            <e-columns>
                <e-column field='TaskID' headerText='Player Jersey' width='140' textAlign='Right'></e-column>
                <e-column field='FIELD1' headerText='Player Name' width='140'></e-column>
                <e-column field='FIELD2' headerText='Year' width='105' textAlign='Right'></e-column>
                <e-column field='FIELD3' headerText='Stint' width='90' textAlign='Right'></e-column>
                <e-column field='FIELD4' headerText='TMID' width='90' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
    </div>
</template>
<script>

import Vue from "vue";
import { TreeGridPlugin, InfiniteScroll, TreeGridComponent, Page } from "@syncfusion/ej2-vue-treegrid";
import { DataManager, JsonAdaptor } from '@syncfusion/ej2-data';
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { dataSource, virtualData } from './datasource.js';

Vue.use(TreeGridPlugin);

export default {
  data: function() {
    return {
        virtualData: dataSource(),
        pageSettings: { pageSize: 50 },
        infiniteScrollSettings : { initialBlocks: 5 }
    };
  },
  provide: {
      treegrid: [InfiniteScroll, Page]
  }
}
</script>

```

{% endtab %}

## Cache Mode

Cache is used to store the loaded rows object in the TreeGrid instance which can be reused for creating the row elements whenever you scroll to already visited page. Also, this mode maintains row elements based on the `infiniteScrollSettings.maxBlocks` count value, once this limit exceeds then it will remove row elements from DOM for new rows.

To enable the cache mode in Infinite scrolling, set `infiniteScrollSettings.enableCache` property as true.

{% tab template="treegrid/scroll/virtualscroll" %}

```html
<template>
    <div id="app">
        <ejs-treegrid ref='treegrid' :dataSource="virtualData" :enableInfiniteScrolling='true' :treeColumnIndex='1' childMapping='Crew' :height=317 :pageSettings='pageSettings' :infiniteScrollSettings='infiniteScrollSettings'>
            <e-columns>
                <e-column field='TaskID' headerText='Player Jersey' width='140' textAlign='Right'></e-column>
                <e-column field='FIELD1' headerText='Player Name' width='140'></e-column>
                <e-column field='FIELD2' headerText='Year' width='105' textAlign='Right'></e-column>
                <e-column field='FIELD3' headerText='Stint' width='90' textAlign='Right'></e-column>
                <e-column field='FIELD4' headerText='TMID' width='90' textAlign='Right'></e-column>
            </e-columns>
        </ejs-treegrid>
    </div>
</template>
<script>

import Vue from "vue";
import { TreeGridPlugin, InfiniteScroll, TreeGridComponent, Page } from "@syncfusion/ej2-vue-treegrid";
import { DataManager, JsonAdaptor } from '@syncfusion/ej2-data';
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { dataSource, virtualData } from './datasource.js';

Vue.use(TreeGridPlugin);

export default {
  data: function() {
    return {
        virtualData: dataSource(),
        pageSettings: { pageSize: 50 },
        infiniteScrollSettings: { enableCache: true}
    };
  },
  provide: {
      treegrid: [InfiniteScroll, Page]
  }
}
</script>

```

{% endtab %}

## Limitations for Infinite Scrolling

* Due to the element height limitation in browsers, the maximum number of records loaded by the treegrid is limited due to the browser capability.
* Initial loading rows total height must be greater than the viewport height.
* Cell selection will not be persisted in cache mode.
* Infinite scrolling is not compatible with batch editing, detail template and hierarchy features.
* The aggregated information and total group items are displayed based on the current view items. To get these information regardless of the view items, refer to the
* Programmatic selection using the [`selectRows`](../api/treegrid/#selectrows) and [`selectRow`](../api/treegrid/#selectrow) method is not supported in infinite scrolling.