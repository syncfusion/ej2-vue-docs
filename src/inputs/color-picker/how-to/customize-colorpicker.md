# Customize ColorPicker

## Custom palette

By default, the Palette will be rendered with default colors. To load custom colors in the palette, specify the colors in the [`presetColors`](./../../api/color-picker#presetcolors) property. To customize the color palette, add a custom class to palette tiles using [`BeforeTileRender`](./../../api/color-picker#beforetilerender) event.

The following sample demonstrates the above functionalities.

{% tab template="color-picker/default", iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <div id="preview"></div>
    <h4>Choose Color</h4>
    <ejs-colorpicker mode="Palette" value="#ba68c8" :columns="4" :inline="true" :showButtons="false" :modeSwitcher="false" :presetColors="customColors" :beforeTileRender="tileRender" :change="onChange"></ejs-colorpicker>
</div>
</template>

<script>
import Vue from 'vue';
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ColorPickerPlugin);

export default {
data() {
    return {
        customColors: {
            'custom1': ['#ef9a9a', '#e57373', '#ef5350', '#f44336', '#f48fb1', '#f06292',
                    '#ec407a', '#e91e63', '#ce93d8', '#ba68c8', '#ab47bc', '#9c27b0', '#b39ddb',
                    '#9575cd', '#7e57c2', '#673AB7'],
            'custom2': ['#9FA8DA', '#7986CB', '#5C6BC0', '#3F51B5', '#90CAF9', '#64B5F6',
                    '#42A5F5', '#2196F3', '#81D4FA', '#4FC3F7', '#29B6F6', '#03A9F4',
                    '#80DEEA', '#4DD0E1', '#26C6DA', '#00BCD4'],
            'custom3': ['#80CBC4', '#4DB6AC', '#26A69A', '#009688', '#A5D6A7', '#81C784',
                    '#66BB6A', '#4CAF50', '#C5E1A5', '#AED581', '#9CCC65', '#8BC34A', '#E6EE9C',
                    '#DCE775', '#D4E157', '#CDDC39']
        },
    };
  },
  methods: {
        onChange: function(args) {
                document.getElementById("preview").style.backgroundColor = args.currentValue.hex;
        },
        tileRender: function(args) {
                args.element.classList.add("e-icons");
                args.element.classList.add("e-custom-tile");
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

.e-container {
  background-color: transparent;
  border-color: transparent;
  box-shadow: none;
}

/* Tile customization styles */
.e-container .e-palette .e-custom-tile {
  border: 0;
  color: #fff;
  height: 36px;
  font-size: 18px;
  width: 36px;
  line-height: 36px;
  border-radius: 50%;
  margin: 2px 5px;
}

.e-container .e-custom-palette.e-palette-group {
  height: 182px;
}

/* Selected state icon */
.e-container .e-palette .e-custom-tile.e-selected::before {
  content: '\e933';
}

.e-container .e-palette .e-custom-tile.e-selected {
  outline: none;
}

.wrap {
  margin: 0 auto;
  width: 300px;
  text-align: center;
}

#preview {
  background-color: #ba68c8;
  height: 50px;
  width: 100%;
}
</style>
```

{% endtab %}

## Hide input area from picker

By default, the input area will be rendered in ColorPicker. To hide the input area from it, add
`e-hide-value` class to ColorPicker using the [`cssClass`](./../../api/color-picker#cssclass) property.

In the following sample, the ColorPicker is rendered without input area.

{% tab template="color-picker/default", iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <h4>Choose Color</h4>
    <ejs-colorpicker cssClass="e-hide-value" :modeSwitcher="false"></ejs-colorpicker>
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

## Custom handle

Color picker handle shape and UI can be customized. Here, we have customized the handle as `svg icon`. The same way you can customize the handle based on your requirement.

The following sample show the customized color picker handle.

{% tab template="color-picker/default", iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <h4>Choose Color</h4>
    <ejs-colorpicker cssClass="e-custom-picker" value="#344aae" :modeSwitcher="false" :open="onOpen"></ejs-colorpicker>
</div>
</template>

<script>
import Vue from 'vue';
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ColorPickerPlugin);

export default {
  methods: {
        onOpen: function(args) {
          args.element.querySelector('.e-handler').classList.add('e-icons');
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

/* To hide the handle balloon preview */
.e-color-picker-tooltip.e-popup.e-popup-open {
    display: none;
}

/* Handle customization styles */
.e-custom-picker .e-container .e-hsv-container .e-handler {
    background: transparent url('data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4KPCEtLSBHZW5lcmF0b3I6IEFkb2JlIElsbHVzdHJhdG9yIDIyLjEuMCwgU1ZHIEV4cG9ydCBQbHVnLUluIC4gU1ZHIFZlcnNpb246IDYuMDAgQnVpbGQgMCkgIC0tPgo8c3ZnIHZlcnNpb249IjEuMSIgaWQ9IkxheWVyXzEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHg9IjBweCIgeT0iMHB4IgoJIHZpZXdCb3g9IjAgMCAxNiAxNiIgc3R5bGU9ImVuYWJsZS1iYWNrZ3JvdW5kOm5ldyAwIDAgMTYgMTY7IiB4bWw6c3BhY2U9InByZXNlcnZlIj4KPHN0eWxlIHR5cGU9InRleHQvY3NzIj4KCS5zdDB7ZmlsbDojRkZGRkZGO30KPC9zdHlsZT4KPGc+Cgk8cG9seWdvbiBjbGFzcz0ic3QwIiBwb2ludHM9IjE2LDYgMTAsNiAxMCwwIDYsMCA2LDYgMCw2IDAsMTAgNiwxMCA2LDE2IDEwLDE2IDEwLDEwIDE2LDEwIAkiLz4KPC9nPgo8cGF0aCBkPSJNMTAsNlYwSDZ2NkgwdjRoNnY2aDR2LTZoNlY2SDEweiBNMTUsOUg5djZIN1Y5SDFWN2g2VjFoMnY2aDZWOXoiLz4KPC9zdmc+Cg==');
    font-size: 16px;
    height: 16px;
    line-height: 16px;
    margin-left: -8px;
    margin-top: -8px;
    border: none;
    box-shadow: none;
    width: 16px;
}
</style>
```

{% endtab %}

## Custom primary button

By default, the applied color will be updated in primary button of the color picker. You can customize that as `icon`.

In the following sample, the `picker` icon is added to primary button and using [`change`](./../../api/color-picker#change) event the selected color will be updated in bottom portion of the icon.

{% tab template="color-picker/default", iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <h4>Choose Color</h4>
    <ejs-colorpicker id="element" :change="onChange"></ejs-colorpicker>
</div>
</template>

<script>
import Vue from 'vue';
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
Vue.use(ColorPickerPlugin);

export default {
  methods: {
    onChange: function(args) {
      document.querySelector('.e-colorpicker-wrapper .e-selected-color').style.borderBottomColor = args.currentValue.rgba;
    }
  },
  mounted: function() {
      var previewIcon = document.querySelector('.e-colorpicker-wrapper .e-selected-color');
      previewIcon.classList.add("e-icons");
  }
};
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

/* Icon customization  */
.e-colorpicker-wrapper #element+.e-split-btn-wrapper .e-split-btn .e-selected-color {
  background: none;
  border-bottom-style: solid;
  border-bottom-width: 3px;
  width: 14px;
  margin: 0px 2px;
  border-bottom-color: #008000;
}
.e-colorpicker-wrapper #element+.e-split-btn-wrapper .e-split-btn .e-selected-color .e-split-preview {
  display: none;
}

.e-colorpicker-wrapper #element+.e-split-btn-wrapper .e-split-btn .e-selected-color::before {
  content: '\e35c';
}
</style>
```

{% endtab %}

>> The Essential JS 2 provides a set of icons that can be loaded by applying `e-icons` class name to the element. You can also use third party icon to customize the primary button.

## Display hex code in input

The color picker input element can be showcased in the place of primary button. The applied color hex code will be updated in the primary button input.

The following sample shows the color picker with input.

{% tab template="color-picker/default", iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <h4>Choose Color</h4>
    <ejs-colorpicker id="element" type="text" class="e-input"></ejs-colorpicker>
</div>
</template>

<script>
import Vue from 'vue';
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';

Vue.use(ColorPickerPlugin);

export default {
  mounted: function() {
    var target = document.getElementById("element");
    target.nextElementSibling.insertBefore(target, target.nextElementSibling.children[1]);
  }
};
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

/* Input element customization */
.e-colorpicker-wrapper .e-split-btn-wrapper #element.e-input {
  height: 16px;
  margin: 0;
  opacity: 1;
  position: initial;
  width: 75px;
}

/* To hide primary button */
.e-colorpicker-wrapper .e-split-btn-wrapper .e-split-btn {
  display: none;
}

/* Secondary button customization */
.e-colorpicker-wrapper .e-split-btn-wrapper .e-btn.e-dropdown-btn {
  background: transparent;
  border-color: transparent;
  border-bottom-color: rgba(0, 0, 0, 0.42);
}

.e-colorpicker-wrapper .e-split-btn-wrapper .e-input:focus+.e-btn.e-dropdown-btn {
  padding-bottom: 3px;
  border-bottom-width: 2px;
  border-bottom-color: #e3165b;
}

.e-colorpicker-wrapper .e-split-btn-wrapper .e-btn.e-dropdown-btn .e-caret {
  transform: rotate(0deg);
  transition: transform 200ms ease-in-out;
}

.e-colorpicker-wrapper .e-split-btn-wrapper .e-btn.e-dropdown-btn.e-active .e-caret {
  transform: rotate(180deg);
}
</style>
```

{% endtab %}

## Custom UI

The color picker UI can be customized in all possible ways. The following sample shows the excel like UI customization with help of SplitButton and Dialog component. In that by clicking the more colors option from color palette, the dialog contains color picker will open.

{% tab template="color-picker/default", iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <ul id="target" tabindex="0">
      <li class="e-item e-palette-item">
        <ejs-colorpicker ref="palette" id="palette" mode="Palette" :inline="true" :showButtons="false" :modeSwitcher="false" :change="onPaletteChange"></ejs-colorpicker>
      </li>
      <li class="e-item" tabindex="-1">
        <span class="e-menu-icon"></span>
        More colors...
      </li>
    </ul>
    <h4>Select color</h4>
    <ejs-splitbutton id="splitbtn" ref="splitBtn" iconCss="e-icons e-font-icon" target="#target" :open="onDdPopupOpen" :beforeClose="onBeforeDdPopupClose"></ejs-splitbutton>
     <ejs-dialog id="pickerdlg" ref="pickerDlg" cssClass="e-dlg-picker" :isModal="true" :target="target" :width="width" :height="height" :visible="false" :animationSettings="animationSettings" :content="pickerDlgContent" :open="pickerDlgOpen" :overlayClick="closePickerDlg"></ejs-dialog>
</div>
</template>

<script>
import Vue from 'vue';
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';
import { SplitButtonPlugin } from '@syncfusion/ej2-vue-splitbuttons';
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';

Vue.use(ColorPickerPlugin);
Vue.use(SplitButtonPlugin);
Vue.use(DialogPlugin);

var pickerDlgContent = Vue.component("demo", {
    template: '<div class="dialogContent"><ejs-colorpicker id="picker" :inline="true" :modeSwitcher="false" :change="onPickerChange"></ejs-colorpicker></div>',
    data() {
        return {
            data: {}
        };
    },
    methods: {
      onPickerChange: function(args) {
        document.getElementById('splitbtn').children[0].style.borderBottomColor = args.currentValue.rgba;
        document.getElementById('pickerdlg').ej2_instances[0].hide();
      }
    }
});

export default {
  data() {
    return {
      target: ".wrap",
      width: "270px",
      height: "336px",
      animationSettings: { effect: 'Zoom' },
      pickerDlgContent: function () {
        return { template : pickerDlgContent }
      }
    };
  },
  methods: {
        onPaletteChange: function(args) {
          document.getElementById('splitbtn').children[0].style.borderBottomColor = args.currentValue.rgba;
        },
        onDdPopupOpen: function(args) {
          args.element.children[1].addEventListener('click', this.openPickerDlg);
        },
        onBeforeDdPopupClose: function(args) {
          args.element.children[1].removeEventListener('click', this.openPickerDlg);
        },
        pickerDlgOpen: function() {
          var colorPickerInst = document.getElementById('picker').ej2_instances[0];
          colorPickerInst.refresh();
          colorPickerInst.element.nextElementSibling.querySelector('.e-ctrl-btn .e-cancel').addEventListener('click', this.closePickerDlg);
        },
        openPickerDlg: function() {
          this.$refs.pickerDlg.ej2Instances.show();
        },
        closePickerDlg: function() {
          this.$refs.pickerDlg.ej2Instances.hide();
        }
  }
};
</script>

<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';

.wrap {
  margin: 0 auto;
  min-height: 345px;
  text-align: center;
}

/* Primary button icon preview */
.e-btn-icon.e-font-icon {
  border-bottom-style: solid;
  border-bottom-width: 3px;
}

/* Primary button icon */
.e-btn-icon.e-font-icon::before {
  content: '\e34c';
}

.e-colorpicker-wrapper.e-hide-palette {
  display: none;
}

.e-dropdown-popup ul .e-item:first-child.e-palette-item {
  height: auto;
  padding: 0;
}

.e-dlg-picker.e-dialog .e-dlg-content {
  padding: 0;
  background-color: transparent;
}

/* Sets ColorPicker height */
.e-dlg-picker.e-dialog {
  max-height: 336px !important;
  background-color: transparent;
}

/* More colors li icon customization */
.e-dropdown-popup ul .e-item:last-child .e-menu-icon {
  height: 24px;
  margin-top: 6px;
  width: 24px;
  background-image: linear-gradient(to bottom, #fff 0, #000 100%);
  background-color: #0450c2;
  background-blend-mode: hard-light;
}
</style>
```

{% endtab %}