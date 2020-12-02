---
title: "Globalization"
component: "Calendar"
description: "Learn about how to globalize the calendar component and how to localize the culture related content."
---

# Globalization

Globalization is the combination of internationalization and localization. You can adapt the component to
various languages by parsing and formatting the date or
number ([Internationalization](../common/internationalization/), and also add culture specific customization and translation to the
text ([localization](../common/localization/)).

By default, the Calendar date format, week, and month names are specific to American English culture.
It uses the [Essential JavaScript 2 Internationalization](../common/internationalization/) package
to parse and format date object based on the culture using the official [UNICODE CLDR](http://cldr.unicode.org/)  JSON data.
It provides the [loadCldr](../common/internationalization/#loading-culture-data)
method to load the culture-specific CLDR JSON data.

The Calendar component supports only the Gregorian type of calendar.
All the Essential JS 2 component are specific to English culture ('en-US').
If you want to go with the different culture other than `English`, follow the below steps.

* Install the CLDR-Data package by using the below command (installs the CLDR JSON data).
To know more about CLDR data, refer to the [CLDR-Data](http://cldr.unicode.org/index/cldr-spec/json) link.

```cmd
npm install cldr-data --save
```

Once the package installed, you can find the culture
specific JSON data under the location `\node_modules\cldr-data`.

* Now use the `loadCldr`
method
to load the culture specific CLDR JSON data
from the installed location to `app.vue` file.

* Calendar displayed `Sunday` as the first day of week based on default culture ("en-US"). If you want to display the Calendar with loaded culture’s first day of week, you need to import `weekdata.json` file from the `cldr-data/suppemental` as given in the code example.

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

> The `Localization` library allows you to localize default text content of the Calendar. The Calendar component has static text for  **today** feature that can be changed to other cultures (Arabic, Deutsch, French, etc.) by defining the
[`locale`](../api/calendar#locale) value and translation object.

Locale keywords |Text
-----|-----
today | Name of the button to choose Today date.

* Before changing the culture other than `English`, ensure that locale text for the concerned culture is loaded through `load` method of
[L10n](https://ej2.syncfusion.com/documentation/api/base/l10n#load) class.

```typescript

//Load the L10n from ej2-base
import { L10n } from '@syncfusion/ej2-base';

//load the locale object to set the localized today value
L10n.load({
    'de': {
        'calendar': { today: 'heute' }
    }
});
```

* Set the culture by using the [`locale`](../api/calendar#locale)
property.

The following example demonstrates the Calendar in `German` culture

{% tab template="calendar/internationalization", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-calendar id='calendar' locale='de'></ejs-calendar>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { loadCldr, L10n } from '@syncfusion/ej2-base';
import { CalendarPlugin } from "@syncfusion/ej2-vue-calendars";
// Here we have referred local json files for preview purpose
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as timeZoneNames from './timeZoneNames.json';

Vue.use(CalendarPlugin);
loadCldr(numberingSystems, gregorian, numbers, timeZoneNames);

L10n.load({
    'de': {
      'calendar': { today: 'heute'}
    }
});
export default {}
</script>

<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrap {
    margin: 0px auto;
    width: 240px;
}
</style>

```

{% endtab %}

## Right-to-Left

The Calendar supports right-to-left functionality for languages like Arabic,  Hebrew, etc. To display text in the
 right-to-left direction, use
 [`enableRtl`](../api/calendar#enablertl) property.

The following code example initializes the Calendar component in `Arabic` culture.

{% tab template="calendar/rtl", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-calendar id='calendar' locale='ar' enableRtl='true'></ejs-calendar>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { loadCldr, L10n } from '@syncfusion/ej2-base';
import { CalendarPlugin } from "@syncfusion/ej2-vue-calendars";
// Here we have referred local json files for preview purpose
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as timeZoneNames from './timeZoneNames.json';

Vue.use(CalendarPlugin);
loadCldr(numberingSystems, gregorian, numbers, timeZoneNames);

L10n.load({
    'ar': {
      'calendar': {  today: "اليوم"}
    }
});
export default {}
</script>

<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrap {
    margin: 0px auto;
    width: 240px;
}
</style>

```

{% endtab %}
