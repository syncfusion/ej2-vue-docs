# Right-To-Left

Right To Left (RTL) can be enabled for Syncfusion Vue UI components by calling `enableRtl` with
`true`. This will render all the Syncfusion Vue components in the right to left direction. Find the code snippet
for this below.

{% tab template="common/right-to-left" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data'  locale='ar-AE' :allowPaging='true' :pageSettings='pageOptions'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { L10n, setCulture, enableRtl } from '@syncfusion/ej2-base';
import { GridPlugin, Page } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

setCulture('ar-AE');
// Enables Right to left alignment for all components
enableRtl(true);
L10n.load({
    'ar-AE': {
        'grid': {
            'EmptyRecord': 'لا سجلات لعرضها',
            'EmptyDataSourceError': 'يجب أن يكون مصدر البيانات فارغة في التحميل الأولي منذ يتم إنشاء الأعمدة من مصدر البيانات في أوتوجينيراتد عمود الشبكة'
        },
        'pager':{
            'currentPageInfo': '{0} من {1} صفحة',
            'totalItemsInfo': '({0} العناصر)',
            'firstPageTooltip': 'انتقل إلى الصفحة الأولى',
            'lastPageTooltip': 'انتقل إلى الصفحة الأخيرة',
            'nextPageTooltip': 'انتقل إلى الصفحة التالية',
            'previousPageTooltip': 'انتقل إلى الصفحة السابقة',
            'nextPagerTooltip': 'الذهاب إلى بيجر المقبل',
            'previousPagerTooltip': 'الذهاب إلى بيجر السابقة'
        }
    }
});

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      pageOptions: { pageSize: 7 }
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

## Enable RTL to individual component

To enable the RTL to an individual component, set the `enableRtl` property directly in its model options. For illustration, the `enableRtl` is added to the Grid component in following code snippet.

{% tab template="common/right-to-left" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data'  locale='ar-AE' :enableRtl='true' :allowPaging='true' :pageSettings='pageOptions'>
            <e-columns>
                <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
            </e-columns>
        </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { L10n, setCulture  } from '@syncfusion/ej2-base';
import { GridPlugin, Page } from "@syncfusion/ej2-vue-grids";
import { data } from './datasource.js';

setCulture('ar-AE');
// Enables Right to left alignment for all components
L10n.load({
    'ar-AE': {
        'grid': {
            'EmptyRecord': 'لا سجلات لعرضها',
            'EmptyDataSourceError': 'يجب أن يكون مصدر البيانات فارغة في التحميل الأولي منذ يتم إنشاء الأعمدة من مصدر البيانات في أوتوجينيراتد عمود الشبكة'
        },
        'pager':{
            'currentPageInfo': '{0} من {1} صفحة',
            'totalItemsInfo': '({0} العناصر)',
            'firstPageTooltip': 'انتقل إلى الصفحة الأولى',
            'lastPageTooltip': 'انتقل إلى الصفحة الأخيرة',
            'nextPageTooltip': 'انتقل إلى الصفحة التالية',
            'previousPageTooltip': 'انتقل إلى الصفحة السابقة',
            'nextPagerTooltip': 'الذهاب إلى بيجر المقبل',
            'previousPagerTooltip': 'الذهاب إلى بيجر السابقة'
        }
    }
});

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data,
      pageOptions: { pageSize: 7 }
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
