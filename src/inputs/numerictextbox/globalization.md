---
title: "Globalization"
component: "NumericTextBox"
description: "Globalization support in numeric textbox"
---

# Globalization

## Localization

[`Localization`](../common/localization/) library allows users to localize the default text contents
of the NumericTextBox to different cultures using the [`locale`](../api/numerictextbox#locale) property.
In NumericTextBox, spin buttons title for the tooltip will be localized based on the culture.

| Locale key | en-US (default)  |
|------|------|
| incrementTitle |  Increment value |
| decrementTitle |  Decrement value |

### Loading translations

To load translation object in your application use `load` function of `L10n` class.

The below example demonstrates the NumericTextBox in `German` culture with the spin buttons tooltip.

{% tab template="numeric-textbox/locale", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-numerictextbox id="numeric" locale='de' :value="value"></ejs-numerictextbox>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { L10n } from '@syncfusion/ej2-base';
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";

Vue.use(NumericTextBoxPlugin);

// Load `German` culture to override spin buttons tooltip text
L10n.load({
    'de': {
        'numerictextbox': {
            incrementTitle: 'Wert erhöhen', decrementTitle: 'Dekrementwert'
        }
    },

});
export default {
  data () {
    return {
        value: 10,
    }
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
 .wrap {
    margin: 0px auto;
    width: 240px;
}
</style>
```

{% endtab %}

## Internationalization

Internationalization library provides support for formatting and parsing the number by using the
official [Unicode CLDR](http://cldr.unicode.org/) JSON data and also provides the
`loadCldr` method to load the culture specific CLDR JSON data. The NumericTextBox comes with built-in
internationalization support to adapt based on culture. For more information about internationalization,
refer to this [link](../common/internationalization/).

By default, all the Essential JS 2  component are specific to English culture ('en-US').
If you want to go with the different culture other than `English`, follow the below steps.

* Install the `CLDR-Data` package by using the below command (it installs the CLDR JSON data). For more information about CLDR-Data,
refer to this [link](http://cldr.unicode.org/index/cldr-spec/json).

```cmd
npm install cldr-data --save
```

Once the package installed, you can find the culture
specific JSON data under the location `\node_modules\cldr-data`.

* Now import the installed CLDR JSON data into the `app.vue` file.
To import JSON data we need to install the JSON plugin loader. Here we have used the SystemJS JSON plugin loader.

```sh
npm install systemjs-plugin-json --save-dev
```

* Once installed, configure the `system.config.js` configuration settings as like below to map the
`systemjs-plugin-json` loader.

* Now import the required culture
from the installed location to `app.vue` file as like the below code snippets.

* Set the culture by using the [`locale`](../api/numerictextbox#locale) property.

The below example demonstrates the NumericTextBox in `German` culture with the `EUR` currency format.

{% tab template="numeric-textbox/internationalization", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-numerictextbox id="numeric" locale='de' currency='EUR' format='c2' :value='value'></ejs-numerictextbox>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { loadCldr,L10n,Ajax } from '@syncfusion/ej2-base';
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";

import * as numberingSystems from './numberingSystems.json';
import * as currencyData from './currencyData.json';
import * as numbers from './numbers.json';
import * as currencies from './currencies.json';

Vue.use(NumericTextBoxPlugin);

loadCldr(numberingSystems, currencyData, numbers, currencies);

L10n.load({
    'de': {
      'numerictextbox': { incrementTitle: 'Wert erhöhen', decrementTitle: 'Dekrementwert'}
    }
});
export default {
  data (){
      return {
        value : 100
      }
    }
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
 .wrap {
    margin: 0px auto;
    width: 240px;
}
</style>
```

{% endtab %}

## Right to Left(RTL)

`Localization` library allows users to localize the default text contents
of the NumericTextBox to different cultures using the [`locale`](../api/numerictextbox#locale) property.
In NumericTextBox, spin buttons title for the tooltip will be localized based on the culture.
RTL provides an option to switch the text direction and layout of the NumericTextBox component from right to left. It improves the user experiences and accessibility for users who use right-to-left languages (Arabic, Farsi, Urdu, etc.). To enable RTL NumericTextBox, set the [`enableRtl`](../api/numerictextbox#enablertl) to true.

{% tab template="numeric-textbox/rtl", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-numerictextbox id="numeric" locale='ar-AE' floatLabelType='Auto' placeholder='أدخل القيمة' :enableRtl='true' :value='value'></ejs-numerictextbox>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { loadCldr,L10n,Ajax } from '@syncfusion/ej2-base';
import { NumericTextBoxPlugin } from "@syncfusion/ej2-vue-inputs";

Vue.use(NumericTextBoxPlugin);

L10n.load({
    'ar-AE': {
      'numerictextbox': { incrementTitle: 'قيمة الزيادة', decrementTitle: 'قيمة تناقص'}
    }
});
export default {
  data (){
      return {
        value : 100
      }
    }
  }
}
</script>
<style>
  @import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
 .wrap {
    margin: 0px auto;
    width: 240px;
}
</style>
```

{% endtab %}
