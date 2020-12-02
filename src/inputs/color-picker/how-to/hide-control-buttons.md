# Hide control buttons

ColorPicker can be rendered without control buttons (Apply/Cancel). In this case, while selecting a color, the
ColorPicker pop-up is closed and selected colors can be applied directly. To hide control buttons, set the [`showButtons`](./../../api/color-picker#showbuttons) property to `false`.

{% tab template="color-picker/default", isDefaultActive=true, iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <h4>Choose Color</h4>
    <ejs-colorpicker :showButtons="false"></ejs-colorpicker>
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