---
title: "Globalization"
component: "DateTimePicker"
description: "Learn about how to globalize the date time picker component and how to localize the culture related content."
---

# Globalization

Globalization is the combination of internalization and localization. You can adapt the component to
various languages by parsing and formatting the date or
number [`Internationalization`](../common/internationalization/), and also add culture specific customization and translation to the text [`localization`](../common/localization/).

By default, the date format, week, month, time format and meridian names are specific to the `American English` culture. It utilizes the
[`Essential JavaScript 2 Internationalization`](../common/internationalization/)
package to parse and format the date object based on the culture by using the official [`UNICODE CLDR`](http://cldr.unicode.org/)
JSON data.  It provides the `loadCldr` method to load culture specific CLDR JSON data. To use a different culture other
than `English`, follow the steps below:

* Install the `CLDR-Data` package by using the following command (installs all the CLDR JSON data). To
know more about CLDR-Data refer to the [`CLDR-Data`](http://cldr.unicode.org/index/cldr-spec/json) link.

```cmd
npm install cldr-data --save
```

Once the package is installed, you can find the culture
specific JSON data under the location `\node_modules\cldr-data`.

* Import the installed CLDR JSON data into the `app.vue` file.

* Use the [`loadCldr`](https://ej2.syncfusion.com/vue/documentation/common/internationalization/#cldr-data-dependencies)
method
to load the culture specific CLDR JSON data
from the installed location to `app.vue` file.

* DateTimePicker displayed `Sunday` as the first day of week based on default culture ("en-US"). If you want to display the DateTimePicker with loaded culture’s first day of week, you need to import `weekdata.json` file from the `cldr-data/suppemental` as given in the code example.

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

> The `Localization` library allows you to localize default text content of the DateTimePicker. The DateTimePicker component has static text for  **today** feature that can be changed to other cultures (Arabic, Deutsch, French, etc.) by defining the
[`locale`](../api/datetimepicker#locale) value and translation object.

Locale keywords |Text
-----|-----
today | Name of the button to choose Today date.
placeholder | Hint to describe expected value in input element.

* Before changing to a culture other than `English`, ensure that locale text for the concerned culture is loaded through `load` method of
[L10n](https://ej2.syncfusion.com/documentation/api/base/l10n#load) class.

```typescript

//Load the L10n, loadCldr from ej2-base
import { loadCldr, L10n } from '@syncfusion/ej2-base';

//load the locale object to set the localized placeholder value
L10n.load({
    'de': {
        'datetimepicker': { placeholder: 'Wählen Sie ein Datum und eine Uhrzeit aus', today: 'heute' }
    }
});
```

* Set the culture by using the
[`locale`](../api/datetimepicker#locale)
property.

The following example demonstrates the DateTimePicker in `German` culture.

{% tab template="datetimepicker/locale", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-datetimepicker id="datetime"  locale="de" ></ejs-datetimepicker>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { loadCldr,L10n} from '@syncfusion/ej2-base';
import { DateTimePickerPlugin } from '@syncfusion/ej2-vue-calendars';
// Here we have referred local json files for preview purpose
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as timeZoneNames from './timeZoneNames.json';

Vue.use(DateTimePickerPlugin);
loadCldr(numberingSystems, gregorian, numbers, timeZoneNames);
L10n.load({
    'de': {
      'datetimepicker': { placeholder: "Wählen Sie Datum und Uhrzeit",
             today: "heute"}
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

The DateTimePicker supports RTL (right-to-left) functionality for languages like Arabic and Hebrew to displays
the text in the right-to-left direction. Use
[`enableRtl`](../api/datetimepicker#enablertl)
property to set the RTL direction.
The following code example initialize the DateTimePicker component in `Arabic` culture and
also explains how to set the localized text to
the placeholder using
`load` method of
[L10n](https://ej2.syncfusion.com/documentation/api/base/l10n#load) class.

{% tab template="datetimepicker/locale-rtl", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-datetimepicker id="datetime" :locale="locale" :enableRtl="rtl"  ></ejs-datetimepicker>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { loadCldr,L10n} from '@syncfusion/ej2-base';
import { DateTimePickerPlugin } from '@syncfusion/ej2-vue-calendars';
// Here we have referred local json files for preview purpose
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as timeZoneNames from './timeZoneNames.json';

Vue.use(DateTimePickerPlugin);
loadCldr(numberingSystems, gregorian, numbers, timeZoneNames);
L10n.load({
    'ar': {
      'datetimepicker': { placeholder: 'حدد التاريخ والوقت',
            today: 'اليوم'}
    }
});
export default {
    data () {
       return {
           locale: "ar",
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