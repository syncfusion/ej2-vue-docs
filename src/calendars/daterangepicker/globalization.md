---
title: "Globalization"
component: "DateRangePicker"
description: "Learn about how to globalize the date range picker component and how to localize the culture related content."
---

# Globalization

Globalization is the combination of internationalization and localization. You can adapt the component to
various languages by parsing and formatting the date or
number (Internationalization), and also add culture specific customization and translation to the text
(Localization).

By default, DateRangePicker date format, week, and month names are specific to the English culture. It utilizes the
[`Essential JavaScript 2 Internationalization`](../common/internationalization)
package to parse and format the date object based on the culture by using the official [`UNICODE CLDR`](http://cldr.unicode.org/)
JSON data. It allows to load culture specific CLDR JSON data by using
`loadCldr`
method.

To use a different culture other than `English`, follow the below steps:

* Install the `CLDR-Data` package by using the below command (Installs the CLDR JSON data). To
know more about CLDR-Data refer to the
[`CLDR-Data`](http://cldr.unicode.org/index/cldr-spec/json) link.

```cmd
npm install cldr-data --save
```

 Once the package is installed, you can find the culture
specific JSON data under the location `\node_modules\cldr-data`.

* Import the installed CLDR JSON data into the `app.vue` file.

* Use the `loadCldr`
method
to load the culture specific CLDR JSON data
from the installed location to `app.vue` file.

* DateRangePicker displayed `Sunday` as the first day of week based on default culture ("en-US"). If you want to display the DateRangePicker with loaded culture’s first day of week, you need to import `weekdata.json` file from the `cldr-data/suppemental` as given in the code example.

```typescript
//Load the loadCldr from ej2-base
import { loadCldr } from '@syncfusion/ej2-base';

import * as numberingSystems from 'cldr-data/supplemental/numberingSystems.json';
import * as gregorian from 'cldr-data/main/de/ca-gregorian.json';
import * as numbers from 'cldr-data/main/de/numbers.json';
import * as timeZoneNames from 'cldr-data/main/de/timeZoneNames.json';
import * as weekData from 'cldr-data/supplemental/weekdata.json';// To load the culture based first day of week

loadCldr(numberingSystems, gregorian, numbers, timeZoneNames, weekData);
```

> The `Localization` library allows you to localize default text content of the DateRangePicker. The DateRangePicker component has static text for  **today** feature that can be changed to other cultures (Arabic, Deutsch, French, etc.) by defining the
[`locale`](../api/daterangepicker#locale) value and translation object.

Locale keywords |Text
-----|-----
placeholder | Hint to describe expected value in input element.
startLabel | Label to represent the start date.
endLabel | Label to represent the end date.
applyText | Text present in the apply button.
cancelText | Text present in the cancel button.
selectedDays | Text to represent selected days.
days | Text represents days.
customRange | Text present in the custom range button in presets container.

* Before changing to a culture other than `English`, ensure that locale text for the concerned culture is loaded through `load` method of
[L10n](https://ej2.syncfusion.com/documentation/api/base/l10n#load) class.

```typescript

//Load the L10n, loadCldr from ej2-base
import { loadCldr, L10n } from '@syncfusion/ej2-base';

//load the locale object to set the localized placeholder value
L10n.load({
    'de': {
        'daterangepicker': { placeholder: 'Wählen Sie ein Datum aus' }
    }
});
```

* Set the culture by using the
[`locale`](../api/daterangepicker#locale)
property.

The following example demonstrates the DateRangePicker in `German` culture.

{% tab template="daterangepicker/locale", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-daterangepicker id="daterange" locale="de" ></ejs-daterangepicker>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { loadCldr,L10n } from '@syncfusion/ej2-base';
import { DateRangePickerPlugin } from '@syncfusion/ej2-vue-calendars';
// Here we have referred local json files for preview purpose
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as timeZoneNames from './timeZoneNames.json';

Vue.use(DateRangePickerPlugin);
loadCldr(numberingSystems, gregorian, numbers, timeZoneNames);

L10n.load({
'de': {
        'daterangepicker': {
           placeholder: 'Wählen Sie einen Bereich aus',
           startLabel: 'Wählen Sie Startdatum',
           endLabel: 'Wählen Sie Enddatum',
           applyText: 'Sich bewerben',
           cancelText: 'Stornieren',
           selectedDays: 'Ausgewählte Tage',
           days: 'Tage',
           customRange: 'benutzerdefinierten Bereich'
        }
    }
});
export default {}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrapper {
    max-width: 250px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Right-To-Left

The DateRangePicker supports RTL (right-to-left) functionality for languages like Arabic and Hebrew to displays
the text in the right-to-left direction. Use
[`enableRtl`](../api/daterangepicker#enablertl)
property to set the RTL direction.
The following code example initialize the DateRangePicker component in `Hebrew` culture and
also explains how to set the localized text to
the placeholder using
`load` method of
[L10n](https://ej2.syncfusion.com/documentation/api/base/l10n#load) class.

{% tab template="daterangepicker/locale-rtl", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-daterangepicker id="daterange" :locale="locale" :enableRtl="rtl" ></ejs-daterangepicker>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { loadCldr,L10n } from '@syncfusion/ej2-base';
import { DateRangePickerPlugin } from '@syncfusion/ej2-vue-calendars';
// Here we have referred local json files for preview purpose
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as timeZoneNames from './timeZoneNames.json';

Vue.use(DateRangePickerPlugin);
loadCldr(numberingSystems, gregorian, numbers, timeZoneNames);

L10n.load({
    'he': {
        'daterangepicker': {
            placeholder: 'בחר טווח',
            startLabel: 'תווית התחלה',
            endLabel: 'ח',
            applyText: 'להחיל טקסט',
            cancelText: 'בטל טקסט',
            selectedDays: 'ימים נבחרים',
            days: 'أימים',
            customRange: 'טווח מותאם אישית'
        }
    }
});
export default {
   data () {
       return {
           locale: "he",
           rtl: true
        }
    }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrapper {
    max-width: 250px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}

## Customize the date format

Representation of start and end date strings can be customized to required format
by using [`format`](../api/daterangepicker#format) property.
By default, the format is based on the culture.
To know more about the date format standards, refer to the Internationalization Date Format section.
In the following sample, the date strings are formatted to `yyyy-MM-dd` and in between the string "to" is set as a [`separator`](../api/daterangepicker#separator).

{% tab template="daterangepicker/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-daterangepicker :format="dateFormat" :separator="seperate" :placeholder="waterMark"></ejs-daterangepicker>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { DateRangePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(DateRangePickerPlugin);
export default {
   data () {
     return {
           waterMark : 'Select a Range',
           dateFormat : "yyyy-MM-dd",
           seperate : "to"
        }
    }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrapper {
    max-width: 250px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}
