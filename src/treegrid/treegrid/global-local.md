---
title: "Globalization"
component: "TreeGrid"
description: "Learn how to apply localization (l10n), internationalization (i18n), and right-to-left (RTL) in Essential JS 2 TreeGrid control."
---

# Globalization

## Localization

The [`Localization`](../common/localization) library allows you to localize default text content of the TreeGrid. The treegrid component has static text on some features (like toolbar area text, filter menu text, pager information text, etc.) that can be changed to other cultures (Arabic, Deutsch, French, etc.) by defining the
[`locale`](../api/treegrid/#locale) value and translation object.

The following list of properties and its values are used in the treegrid.

Locale keywords |Text
-----|-----
EmptyRecord | No records to display
True | true
False | false
ExpandAll | Expand All
CollapseAll | Collapse All
InvalidFilterMessage | Invalid Filter Data
FilterbarTitle | \s filter bar cell
Add | Add
Edit| Edit
Cancel| Cancel
Update| Update
Delete | Delete
Print | Print
Pdfexport | PDF Export
Excelexport | Excel Export
Wordexport | Word Export
Csvexport | CSV Export
Search | Search
Save | Save
EditOperationAlert | No records selected for edit operation
DeleteOperationAlert | No records selected for delete operation
SaveButton | Save
OKButton | OK
CancelButton | Cancel
EditFormTitle | Details of
AddFormTitle | Add New Record
ConfirmDelete | Are you sure you want to Delete Record?
SearchColumns | search columns
Matchs | No Matches Found
FilterButton | Filter
ClearButton | Clear
StartsWith | Starts With
EndsWith | Ends With
Contains | Contains
Equal | Equal
NotEqual | Not Equal
LessThan | Less Than
LessThanOrEqual | Less Than Or Equal
GreaterThan | Greater Than
GreaterThanOrEqual | Greater Than Or Equal
ChooseDate | Choose a Date
EnterValue | Enter the value
autoFitAll | Auto Fit all columns
autoFit | Auto Fit this column
Export | Export
FirstPage | First Page
LastPage | Last Page
PreviousPage | Previous Page
NextPage | Next Page
SortAscending | Sort Ascending
SortDescending | Sort Descending
EditRecord | Edit Record
DeleteRecord | Delete Record
Above | Above
Below | Below
AddRow | Add Row
FilterMenu | Filter
SelectAll | Select All
Blanks | Blanks
FilterTrue | True
FilterFalse | False
NoResult | No Matches Found
ClearFilter | Clear Filter
NumberFilter | Number Filters
TextFilter | Text Filters
DateFilter | Date Filters
MatchCase | Match Case
Between | Between
CustomFilter | Custom Filter
CustomFilterPlaceHolder | Enter the value
CustomFilterDatePlaceHolder | Choose a date
AND | AND
OR | OR
ShowRowsWhere | Show rows where:
currentPageInfo | {0} of {1} pages
totalItemsInfo | ({0} items)
firstPageTooltip | Go to first page
lastPageTooltip | Go to last page
nextPageTooltip | Go to next page
previousPageTooltip | Go to previous page
nextPagerTooltip | Go to next pager
previousPagerTooltip | Go to previous pager
pagerDropDown | Items per page
pagerAllDropDown | Items
All | All

### Loading translations

To load translation object in an application, use `load` function of the `L10n` class.

The following example demonstrates the TreeGrid in `Deutsch` culture.

{% tab template="treegrid/local/default" %}

```html
<template>
<div id="app">
      <ejs-treegrid :dataSource='data' locale='de-DE' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' :allowFiltering='true' :filterSettings='filterSettings' :toolbar='toolbar'>
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
import { L10n, setCulture } from '@syncfusion/ej2-base';
import { TreeGridPlugin, Page, Toolbar, Filter } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

setCulture('de-DE');

L10n.load({
    'de-DE': {
        'treegrid': {
            'EmptyRecord': 'Keine Aufzeichnungen angezeigt',
            'Expand All': 'Alle erweitern',
            'Collapse All': 'Alles einklappen',
            "Print": "Drucken",
            "Pdfexport": "PDF-Export",
            "Excelexport": "Excel-Export",
            "Wordexport": "Word-Export",
            "FilterButton": "Filter",
            "ClearButton": "klar",
            "StartsWith": "Beginnt mit",
            "EndsWith": "Endet mit",
            "Contains": "Enthält",
            "Equal": "Gleich",
            "NotEqual": "Nicht gleich",
            "LessThan": "Weniger als",
            "LessThanOrEqual": "Weniger als oder gleich",
            "GreaterThan": "Größer als",
            "GreaterThanOrEqual": "Größer als oder gleich",
            "EnterValue": "Geben Sie den Wert ein",
            "FilterMenu": "Filter"
        },
        'pager': {
            'currentPageInfo': '{0} von {1} Seiten',
            'totalItemsInfo': '({0} Beiträge)',
            'firstPageTooltip': 'Zur ersten Seite',
            'lastPageTooltip': 'Zur letzten Seite',
            'nextPageTooltip': 'Zur nächsten Seite',
            'previousPageTooltip': 'Zurück zur letzten Seit',
            'nextPagerTooltip': 'Zum nächsten Pager',
            'previousPagerTooltip': 'Zum vorherigen Pager'
        },
        "dropdowns": {
            "noRecordsTemplate": "Keine Aufzeichnungen gefunden"
        },
        "datepicker": {
            "placeholder": "Wählen Sie ein Datum",
            "today": "heute"
        }
    }
});

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      pageSettings: { pageSize: 7 },
      filterSettings: { type: 'Menu' },
      toolbar: ['Print']
    };
  },
  provide: {
      treegrid: [ Page, Toolbar, Filter ]
    }
}
</script>

```

{% endtab %}

## Internationalization

The [`Internationalization`](../common/internationalization/) library is used to globalize number, date, and time values in treegrid component using format strings in the [`columns.format`](../api/treegrid/column/#format).

{% tab template="treegrid/local/default" %}

```html
<template>
<div id="app">
      <ejs-treegrid :dataSource='data' locale='de-DE' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' :allowFiltering='true' :filterSettings='filterSettings' :toolbar='toolbar'>
        <e-columns>
          <e-column field='orderID' headerText='Order ID' width='90' textAlign='Right'></e-column>
          <e-column field='orderName' headerText='Order Name' width='160'></e-column>
          <e-column field='price' headerText='Price' width='90' :format='formatOptions' textAlign='Right'></e-column>
      </ejs-treegrid>
</div>
</template>
<script>
import Vue from "vue";
import { L10n, loadCldr, setCulture, setCurrencyCode } from '@syncfusion/ej2-base';
import * as currencies from './currencies.json';
import * as cagregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as timeZoneNames from './timeZoneNames.json';
import * as numberingSystems from './numberingSystems.json';
import { TreeGridPlugin, Page, Toolbar, Filter } from "@syncfusion/ej2-vue-treegrid";
import { formatData } from "./datasource.js";

setCulture('de-DE');
setCurrencyCode('EUR');

L10n.load({
    'de-DE': {
        'treegrid': {
            'EmptyRecord': 'Keine Aufzeichnungen angezeigt',
            'Expand All': 'Alle erweitern',
            'Collapse All': 'Alles einklappen',
            "Print": "Drucken",
            "Pdfexport": "PDF-Export",
            "Excelexport": "Excel-Export",
            "Wordexport": "Word-Export",
            "FilterButton": "Filter",
            "ClearButton": "klar",
            "StartsWith": "Beginnt mit",
            "EndsWith": "Endet mit",
            "Contains": "Enthält",
            "Equal": "Gleich",
            "NotEqual": "Nicht gleich",
            "LessThan": "Weniger als",
            "LessThanOrEqual": "Weniger als oder gleich",
            "GreaterThan": "Größer als",
            "GreaterThanOrEqual": "Größer als oder gleich",
            "EnterValue": "Geben Sie den Wert ein",
            "FilterMenu": "Filter"
        },
        'pager': {
            'currentPageInfo': '{0} von {1} Seiten',
            'totalItemsInfo': '({0} Beiträge)',
            'firstPageTooltip': 'Zur ersten Seite',
            'lastPageTooltip': 'Zur letzten Seite',
            'nextPageTooltip': 'Zur nächsten Seite',
            'previousPageTooltip': 'Zurück zur letzten Seit',
            'nextPagerTooltip': 'Zum nächsten Pager',
            'previousPagerTooltip': 'Zum vorherigen Pager'
        },
        "dropdowns": {
            "noRecordsTemplate": "Keine Aufzeichnungen gefunden"
        },
        "datepicker": {
            "placeholder": "Wählen Sie ein Datum",
            "today": "heute"
        }
    }
});

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: formatData,
      pageSettings: { pageSize: 7 },
      filterSettings: { type: 'Menu' },
      formatOptions: { format:'C2' , useGrouping: false, minimumSignificantDigits:1, maximumSignificantDigits:3, currency:'EUR' },
      toolbar: ['Print']
    };
  },
  provide: {
      treegrid: [ Page, Toolbar, Filter ]
    }
}
</script>

```

{% endtab %}

> * In the above sample, `Price` column is formatted by `NumberFormatOptions`.
> * By default, [`locale`](../api/treegrid/#locale) value is `en-US`. If you want to change the `en-US` culture to a different culture, you have to change  the [`locale`](../api/treegrid/#locale) accordingly.

## Right to left (RTL)

RTL provides an option to switch the text direction and layout of the TreeGrid component from right to left. It improves the user experiences and accessibility for users who use right-to-left languages (Arabic, Farsi, Urdu, etc.). To enable RTL Grid, set the [`enableRtl`](../api/treegrid/#enablertl) to true.

{% tab template="treegrid/local/default" %}

```html
<template>
<div id="app">
      <ejs-treegrid :dataSource='data' locale='ar-AE' childMapping='subtasks' :treeColumnIndex='1' :allowPaging='true' :pageSettings='pageSettings' :allowFiltering='true' :filterSettings='filterSettings' :toolbar='toolbar' :enableRtl='true'>
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
import { L10n, setCulture } from '@syncfusion/ej2-base';
import { TreeGridPlugin, Page, Toolbar, Filter } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./datasource.js";

setCulture('ar-AE');

L10n.load({
    'ar-AE': {
        'treegrid': {
            "EmptyRecord": "لا سجلات لعرضها",
            "Print": "طباعة",
            "FilterButton": "منقي",
            "ClearButton": "واضح",
            "StartsWith": "ابدا ب",
            "EndsWith": "ينتهي مع",
            "Contains": "يحتوي على",
            "Equal": "مساو",
            "NotEqual": "غير متساوي",
            "LessThan": "أقل من",
            "LessThanOrEqual": "اصغر من او يساوي",
            "GreaterThan": "أكثر من",
            "GreaterThanOrEqual": "أكبر من أو يساوي",
            "ChooseDate": "اختر تاريخا",
            "EnterValue": "أدخل القيمة",
            "FilterMenu": "منقي"
        },
        'pager': {
            'currentPageInfo': '{0} من {1} صفحة',
            'totalItemsInfo': '({0} العناصر)',
            'firstPageTooltip': 'انتقل إلى الصفحة الأولى',
            'lastPageTooltip': 'انتقل إلى الصفحة الأخيرة',
            'nextPageTooltip': 'انتقل إلى الصفحة التالية',
            'previousPageTooltip': 'انتقل إلى الصفحة السابقة',
            'nextPagerTooltip': 'الذهاب إلى بيجر المقبل',
            'previousPagerTooltip': 'الذهاب إلى بيجر السابقة'
        },
        "dropdowns": {
            "noRecordsTemplate": "لا توجد سجلات"
        },
        "datepicker": {
            "placeholder": "اختر تاريخا",
            "today": "اليوم"
        }
    }
});

Vue.use(TreeGridPlugin);

export default {
  data ()  {
    return {
      data: sampleData,
      pageSettings: { pageSize: 7 },
      filterSettings: { type: 'Menu' },
      toolbar: ['Print']
    };
  },
  provide: {
      treegrid: [ Page, Toolbar, Filter ]
    }
}
</script>

```

{% endtab %}
