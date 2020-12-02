# ColorPicker in DropDownButton

This section explains about how to render the ColorPicker in DropDownButton. The
[`target`](../../api/drop-down-button#target) property of the DropDownButton helps to achieve this scenario. To know about the usage of `target` property refer to [`Popup templating`](./../../drop-down-button/popup-items#popup-templating) section.

In the below sample, the color picker is rendered as inline type by setting [`inline`](./../../api/color-picker#inline) property as `true` and the rendered color picker wrapper is passed as a `target` to the DropDownButton to achieve the above scenario.

{% tab template="color-picker/default", iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <h4>Choose Color</h4>
    <ejs-colorpicker :inline="true" :modeSwitcher="false" :change="onChange"></ejs-colorpicker>
    <ejs-dropdownbutton id="dropdownbtn" ref="ddb" target=".e-colorpicker-wrapper" iconCss="e-dropdownbtn-preview" :beforeClose="beforeDdbClose" :open="ddbOpen"></ejs-dropdownbutton>
</div>
</template>

<script>
import Vue from 'vue';
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';
import { DropDownButtonPlugin } from '@syncfusion/ej2-vue-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ColorPickerPlugin);
Vue.use(DropDownButtonPlugin);

export default {
  methods: {
        onChange: function(args) {
          this.$refs.ddb.ej2Instances.element.children[0].style.backgroundColor = args.currentValue.rgba;
          this.closePopup();
        },
        ddbOpen: function(args) {
          args.element.querySelector('.e-cancel').addEventListener('click', this.closePopup);
        },
        beforeDdbClose: function(args) {
          args.element.querySelector('.e-cancel').removeEventListener('click', this.closePopup);
        },
        closePopup: function() {
          this.$refs.ddb.ej2Instances.toggle()
        }
  }
}
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

/* DropDownButton preview customization */
#dropdownbtn .e-btn-icon.e-dropdownbtn-preview {
  background-color: #008000;
  height: 18px;
  width: 18px;
  margin-top: 0;
}

#dropdownbtn {
  padding: 4px;
}
</style>
```

{% endtab %}