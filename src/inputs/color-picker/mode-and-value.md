---
title: "ColorPicker Mode and Value"
component: "ColorPicker"
description: "Vue ColorPicker component has two different modes and allows the user to specify color value to the ColorPicker."
---

# Mode and Value

## Rendering palette at initial load

By default, the `Picker` area will be rendered at initial load. To render the Palette area while opening the ColorPicker pop-up, and specify the [`mode`](.../api/color-picker#mode) property as `Palette`.

In the following sample, it will render the `Palette` at initial load.

{% tab template="color-picker/default", isDefaultActive=true, iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <h4>Choose Color</h4>
    <ejs-colorpicker mode="Palette"></ejs-colorpicker>
</div>
</template>

<script>
import Vue from 'vue';
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
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

## Color value

The [`value`](.../api/color-picker#value) property can be used to specify the color value to the
ColorPicker. It supports either `three` or `six` digit hex codes. To include `opacity`, set the color value as `four` or `eight` digit hex code.

In the following sample, the color value sets as `four` digit hex code, the last digit represents the `opacity` value.

{% tab template="color-picker/default", iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <h4>Choose Color</h4>
    <ejs-colorpicker value="035a" :modeSwitcher="false"></ejs-colorpicker>
</div>
</template>

<script>
import Vue from 'vue';
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
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

>> The [`value`](.../api/color-picker#value) property supports hex code with or without `#` prefix.

## See Also

* [How to render palette alone](./how-to/render-palette-alone)
* [Custom palette](./how-to/customize-colorpicker#custom-palette)
* [No color support in palette](./how-to/handle-no-color-support)