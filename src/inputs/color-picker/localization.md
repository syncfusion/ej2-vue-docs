---
title: "ColorPicker Localization"
component: "ColorPicker"
description: "Vue ColorPicker supports localization which allows the end user to localize default text content of the colorpicker in various cultures."
---

# Localization and RTL

## Localization

The `Localization` library allows you to localize default text content of the
ColorPicker. The ColorPicker component has static text for `control buttons (apply / cancel)` and `mode switcher` that can be changed to other cultures (Arabic, Deutsch, French, etc.) by defining the
[`locale`](.../api/color-picker#locale) value and translation object.

The following list of properties and its values are used in the ColorPicker.

Locale key words |Text
-----|-----
Apply |Apply
Cancel |Cancel
ModeSwitcher |Switch Mode

### Loading translations

To load translation object in an application use `load` function of `L10n` class.

The below example demonstrates the ColorPicker in `Deutsch` culture.

{% tab template="color-picker/default", isDefaultActive=true, iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <h4>Choose Color</h4>
    <ejs-colorpicker locale='de-DE'></ejs-colorpicker>
</div>
</template>

<script>
import Vue from 'vue';
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';
import { enableRipple, L10n } from '@syncfusion/ej2-base';

enableRipple(true);

L10n.load({
    'de-DE': {
        'colorpicker': {
            'Apply': 'Anwenden',
            'Cancel': 'Abbrechen',
            'ModeSwitcher': 'Modus wechseln'
        }
    }
});

Vue.use(ColorPickerPlugin);

export default {}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';

.wrap {
  margin: 0 auto;
  width: 300px;
  text-align: center;
}
</style>
```

{% endtab %}

## Right to Left - RTL

ColorPicker component has `RTL` support. It helps to render the ColorPicker from right-to-left direction.
It improves the user experiences and accessibility for users who use right-to-left languages(Arabic, Farsi, Urdu, etc). This can be achieved by setting the [`enableRtl`](.../api/color-picker#enablertl) property to `true`.

The following example illustrates how to enable right-to-left support in ColorPicker component.

{% tab template="color-picker/default", iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <h4>Choose Color</h4>
    <ejs-colorpicker :enableRtl="true" locale='ar-AE'></ejs-colorpicker>
</div>
</template>

<script>
import Vue from 'vue';
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';
import { enableRipple, L10n } from '@syncfusion/ej2-base';

enableRipple(true);

L10n.load({
    'ar-AE': {
        'colorpicker': {
            'Apply': 'تطبيق',
            'Cancel': 'إلغاء',
            'ModeSwitcher': 'مفتاح كهربائي الوضع'
        }
    }
});

Vue.use(ColorPickerPlugin);

export default {}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';

.wrap {
  margin: 0 auto;
  width: 300px;
  text-align: center;
}
</style>
```

{% endtab %}

## See Also

* [More information about localization](./../common/localization)
