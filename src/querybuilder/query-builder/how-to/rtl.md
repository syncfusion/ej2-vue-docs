---
title: "Right to left (RTL)"
component: "Query Builder"
description: "Learn how to enable rtl in the Essential JS 2 QueryBuilder control."
---

# Right to left (RTL)

RTL provides an option to switch the text direction and layout of the Query Builder component from right to left. It improves the user experiences and accessibility for users who use right-to-left languages (Arabic, Farsi, Urdu, etc.). To enable RTL, set the [`enableRtl`](https://ej2.syncfusion.com/vue/documentation/right-to-left/) to true.

{% tab template="query-builder/default", isDefaultActive=true %}

```html
<template>
    <div class="control-section">
        <div class="col-lg-12 querybuilder-control">
            <ejs-querybuilder width="70%" :dataSource="dataSource" :rule="importRules" locale="ar-AE" enableRtl="true">
                <e-columns>
                  <e-column field="TaskID" label="Task ID" type="number"></e-column>
                  <e-column field="Name" label="Name" type="string"></e-column>
                  <e-column field="Category" label="Category" type="string"></e-column>
                  <e-column field="SerialNo" label="SerialNo" type="string"></e-column>
                  <e-column field="InvoiceNo" label="InvoiceNo" type="string"></e-column>
                  <e-column field="Status" label="Status" type="string"></e-column>
                </e-columns>
            </ejs-querybuilder>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { QueryBuilderPlugin } from "@syncfusion/ej2-vue-querybuilder";
import { L10n, setCulture } from '@syncfusion/ej2-base';
Vue.use(QueryBuilderPlugin);
setCulture('ar-AE');
L10n.load({
   'ar-AE': {
        'querybuilder': {
            'AddGroup': 'إضافة مجموعة',
            'AddCondition': 'اضافة الشرط',
            'DeleteRule': 'أزل هذا الشرط',
            'DeleteGroup': 'حذف المجموعة',
            'Edit': 'تصحيح',
            'SelectField': 'اختر مجال',
            'DeleteRule': 'أزل هذا الشرط',
            'DeleteGroup': 'حذف المجموعة',
            'SelectOperator': 'حدد المشغل',
            'StartsWith': 'ابدا ب',
            'EndsWith': 'ينتهي مع',
            'Contains': 'يحتوي على',
            'Equal': 'مساو',
            'NotEqual': 'ليس متساوي',
            'LessThan': 'أقل من',
            'LessThanOrEqual': 'اصغر من او يساوي',
            'GreaterThan': 'أكثر من',
            'GreaterThanOrEqual': 'أكبر من أو يساوي',
            'Between': 'ما بين',
            'NotBetween': 'ليس بينهما',
            'In': 'في',
            'NotIn': 'ليس في',
            'Remove': 'إزالة',
            'ValidationMessage': 'هذه الخانة مطلوبه'
        }
    }
});
export default {
    data: function() {
        return {
            dataSource: hardwareData,
            importRules:{
        'condition': 'or',
        'rules': [{
            'label': 'Category',
            'field': 'Category',
            'type': 'string',
            'operator': 'equal',
            'value': 'Laptop'
        }]
    }
        };
    }
}
var hardwareData = [{
      'TaskID': 1,
      'Name': 'Lenovo Yoga',
      'Category': 'Laptop',
      'SerialNo': 'CB27932009',
      'InvoiceNo': 'INV-2878',
      'Status': 'Assigned'
  },
  {
      'TaskID': 2,
      'Name': 'Acer Aspire',
      'Category': 'Others',
      'SerialNo': 'CB35728290',
      'InvoiceNo': 'INV-3456',
      'Status': 'In-repair'
  },
  {
      'TaskID': 3,
      'Name': 'Apple MacBook',
      'Category': 'Laptop',
      'SerialNo': 'CB35628728',
      'InvoiceNo': 'INV-2763',
      'Status': 'In-repair'
  }];
</script>
<style>
    @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-lists/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-vue-querybuilder/styles/material.css";
    .e-query-builder {
        margin: 0 auto;
    }
</style>
```

{% endtab %}