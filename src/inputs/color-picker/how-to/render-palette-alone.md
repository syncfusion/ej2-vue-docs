# Render palette alone

To render the `Palette` alone in ColorPicker, specify the [`mode`](./../../api/color-picker#mode) property as `Palette`, and set the [`modeSwitcher`](./../../api/color-picker#modeswitcher) property to `false`.

In the following sample, the [`showButtons`](./../../api/color-picker#showbuttons) property is disabled to hide the control buttons and it renders only the `Palette` area.

{% tab template="color-picker/default", iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <h4>Choose Color</h4>
    <ejs-colorpicker mode="Palette" :showButtons="false" :modeSwitcher="false"></ejs-colorpicker>
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

>> To render `Picker` alone specify the [`mode`](./../../api/color-picker#mode) property as 'Picker'.