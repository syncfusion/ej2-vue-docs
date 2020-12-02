# Handle no color support

The ColorPicker component supports no color functionality. By clicking the no color tile from palette, the selected color becomes `empty` and considered as no color has been selected from color picker.

## Default no color

To achieve this, set [`noColor`](./../../api/color-picker#nocolor) property as `true`.

In the following sample, the first tile of the color palette represents the no color tile. By clicking the no color tile you can achieve the above functionalities.

{% tab template="color-picker/default", isDefaultActive=true, iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <div id='preview'></div>
    <h4>Select Color</h4>
    <ejs-colorpicker id="element" value="#ba68c8" mode="Palette" :noColor="true" :showButtons="false" :modeSwitcher="false" :change="onChange"></ejs-colorpicker>
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
      var preview = document.getElementById('preview');
      preview.style.backgroundColor = args.currentValue.hex;
      preview.textContent = args.currentValue.hex ? args.currentValue.hex : 'No color';
    }
  },
  mounted: function() {
      var preview = document.getElementById('preview');
      preview.style.backgroundColor = '#ba68c8';
      preview.textContent = '#ba68c8';
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

#preview {
  border: 1px solid;
  height: 40px;
  line-height: 40px;
}

h4, #preview {
    font-family: 'Helvetica Neue', 'Helvetica', 'Arial', 'sans-serif';
    font-size: 14px;
}
</style>
```

{% endtab %}

## Custom no color

The following sample show the color palette with custom no color option.

{% tab template="color-picker/default", iframeHeight="500px" %}

```html
<template>
<div class='wrap'>
    <ul id="target" tabindex="0">
          <li class="e-item e-palette-item">
            <ejs-colorpicker id="element" ref="colorPicker" value="#f44336" mode="Palette" :inline="true" :columns="4" :showButtons="false" :modeSwitcher="false" :presetColors="presets" :beforeTileRender="beforeTileRender" :change="onChange"></ejs-colorpicker>
          </li>
          <li class="e-item" id="no-color" tabindex="-1">
            <span class="e-menu-icon e-nocolor"></span>
            No color
          </li>
      </ul>
    <div>
      <div id='preview'></div>
      <h4>Select Color</h4>
      <ejs-splitbutton id="splitbtn" ref="splitBtn" iconCss="e-cp-icons e-picker-icon" target="#target"></ejs-splitbutton>
    </div>
</div>
</template>

<script>
import Vue from 'vue';
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';
import { SplitButtonPlugin } from '@syncfusion/ej2-vue-splitbuttons';

Vue.use(ColorPickerPlugin);
Vue.use(SplitButtonPlugin);

export default {
  data() {
    return {
      presets: {
        'custom': ['#f44336', '#e91e63', '#9c27b0', '#673ab7', '#2196f3', '#03a9f4', '#00bcd4', '#009688',             '#8bc34a', '#cddc39', '#ffeb3b', '#ffc107']
      }
    };
  },
  methods: {
    onChange: function(args) {
      document.querySelector(".e-split-btn .e-picker-icon").style.borderBottomColor = args.currentValue.hex;
      var preview = document.getElementById('preview');
      var splitBtnObj = this.$refs.splitBtn.ej2Instances;
      preview.style.backgroundColor = args.currentValue.hex;
      preview.textContent = args.currentValue.hex;
      if (splitBtnObj.element.getAttribute("aria-expanded")) {
        splitBtnObj.toggle();
        splitBtnObj.element.focus();
      }
    },
    beforeTileRender: function(args) {
      args.element.classList.add('e-custom-tile');
    }
  },
  mounted: function() {
      var preview = document.getElementById('preview');
      preview.style.backgroundColor = '#ba68c8';
      preview.textContent = '#ba68c8';
      document.getElementById('no-color').onclick = function() {
          //sets color picker value property to null
          this.$refs.colorPicker.ej2Instances.setProperties({ 'value': '' }, true);
          document.querySelector('.e-split-btn .e-picker-icon').style.borderBottomColor = 'transparent';
          preview.textContent = 'No color';
          preview.style.backgroundColor = 'transparent';
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

/* Preview area styles */
#preview {
  border: 1px solid;
  height: 40px;
  line-height: 40px;
  width: 100%;
}

  @font-face {
  font-family: 'paint';
  src:
  url(data:application/x-font-ttf;charset=utf-8;base64,AAEAAAAKAIAAAwAgT1MvMj0gSRIAAAEoAAAAVmNtYXDnEOdVAAABiAAAADZnbHlmIZD+uwAAAcgAAADMaGVhZBKhhHQAAADQAAAANmhoZWEHjANrAAAArAAAACRobXR4B+j/8wAAAYAAAAAIbG9jYQBmAAAAAAHAAAAABm1heHABDgBKAAABCAAAACBuYW1ln6hzswAAApQAAAINcG9zdEkLMmUAAASkAAAANgABAAADUv9qAFoEAP/z//4D6gABAAAAAAAAAAAAAAAAAAAAAgABAAAAAQAAAZfc6F8PPPUACwPoAAAAANfSn9kAAAAA19Kf2f/z//wD6gPhAAAACAACAAAAAAAAAAEAAAACAD4AAgAAAAAAAgAAAAoACgAAAP8AAAAAAAAAAQP0AZAABQAAAnoCvAAAAIwCegK8AAAB4AAxAQIAAAIABQMAAAAAAAAAAAAAAAAAAAAAAAAAAAAAUGZFZABA5wDnAANS/2oAWgPhAJYAAAABAAAAAAAABAAAAAPo//MAAAACAAAAAwAAABQAAwABAAAAFAAEACIAAAAEAAQAAQAA5wD//wAA5wD//wAAAAEABAAAAAEAAAAAAAAAZgAAAAL/8//8A+oD4QAKAD0AAAEWBgceATc1JiQHJTMmNjceARcVJx4BBx4BFQ4BIiYnNDY3PgEvAS4BIw4BBwEGHgI3AT4BLwE1LgEnDgEDeiRlCgulCxP+8RT+GyYDQFxOZQwTBQEDDxEBJzonAREOCQkPJQ4cDBcdAf6oG1a3nx8BWQ4RHKADeG1oWwHTLHVwYVmL6Kx1BHEqfwYFqWUHEx4tDAocEx0nJx0RHgoVUDQpDgsBFAH+px2guFUaAVkNOiCgCXnhCAWOAAAAAAAAEgDeAAEAAAAAAAAAAQAAAAEAAAAAAAEABQABAAEAAAAAAAIABwAGAAEAAAAAAAMABQANAAEAAAAAAAQABQASAAEAAAAAAAUACwAXAAEAAAAAAAYABQAiAAEAAAAAAAoALAAnAAEAAAAAAAsAEgBTAAMAAQQJAAAAAgBlAAMAAQQJAAEACgBnAAMAAQQJAAIADgBxAAMAAQQJAAMACgB/AAMAAQQJAAQACgCJAAMAAQQJAAUAFgCTAAMAAQQJAAYACgCpAAMAAQQJAAoAWACzAAMAAQQJAAsAJAELIHBhaW50UmVndWxhcnBhaW50cGFpbnRWZXJzaW9uIDEuMHBhaW50Rm9udCBnZW5lcmF0ZWQgdXNpbmcgU3luY2Z1c2lvbiBNZXRybyBTdHVkaW93d3cuc3luY2Z1c2lvbi5jb20AIABwAGEAaQBuAHQAUgBlAGcAdQBsAGEAcgBwAGEAaQBuAHQAcABhAGkAbgB0AFYAZQByAHMAaQBvAG4AIAAxAC4AMABwAGEAaQBuAHQARgBvAG4AdAAgAGcAZQBuAGUAcgBhAHQAZQBkACAAdQBzAGkAbgBnACAAUwB5AG4AYwBmAHUAcwBpAG8AbgAgAE0AZQB0AHIAbwAgAFMAdAB1AGQAaQBvAHcAdwB3AC4AcwB5AG4AYwBmAHUAcwBpAG8AbgAuAGMAbwBtAAAAAAIAAAAAAAAACgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAgECAQMADHBhaW50LWJ1Y2tldAAAAAA=) format('truetype');
  font-weight: normal;
  font-style: normal;
  }

  .e-cp-icons {
  font-family: 'paint' !important;
  speak: none;
  font-size: 55px;
  font-style: normal;
  font-weight: normal;
  font-variant: normal;
  text-transform: none;
  line-height: 1;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  }

.wrap {
  margin: 0 auto;
  width: 300px;
  text-align: center;
}

.e-dropdown-popup ul#target {
  padding: 0;
}

.e-dropdown-popup ul .e-item.e-palette-item {
  height: auto;
  padding: 0;
}

.e-btn-icon.e-picker-icon {
  border-bottom-color: #f44336;
  border-bottom-style: solid;
  border-bottom-width: 3px;
}

/* Picker icon */
.e-btn-icon.e-picker-icon::before {
  content: '\e700';
}

/* No color li styles */
.e-dropdown-popup ul .e-item .e-menu-icon.e-nocolor {
  height: 22px;
  margin-top: 8px;
  width: 22px;
  background: transparent url('data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB3aWR0aD0iNnB4IiBoZWlnaHQ9IjZweCIgdmlld0JveD0iMCAwIDYgNiIgdmVyc2lvbj0iMS4xIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIj4KICAgIDwhLS0gR2VuZXJhdG9yOiBTa2V0Y2ggNTAgKDU0OTgzKSAtIGh0dHA6Ly93d3cuYm9oZW1pYW5jb2RpbmcuY29tL3NrZXRjaCAtLT4KICAgIDx0aXRsZT5Hcm91cCA5PC90aXRsZT4KICAgIDxkZXNjPkNyZWF0ZWQgd2l0aCBTa2V0Y2guPC9kZXNjPgogICAgPGRlZnM+PC9kZWZzPgogICAgPGcgaWQ9IlBhZ2UtMSIgc3Ryb2tlPSJub25lIiBzdHJva2Utd2lkdGg9IjEiIGZpbGw9Im5vbmUiIGZpbGwtcnVsZT0iZXZlbm9kZCI+CiAgICAgICAgPGcgaWQ9Ikdyb3VwLTkiPgogICAgICAgICAgICA8cmVjdCBpZD0iUmVjdGFuZ2xlLTExIiBmaWxsPSIjRTBFMEUwIiB4PSIwIiB5PSIwIiB3aWR0aD0iMyIgaGVpZ2h0PSIzIj48L3JlY3Q+CiAgICAgICAgICAgIDxyZWN0IGlkPSJSZWN0YW5nbGUtMTEtQ29weS0yIiBmaWxsPSIjRkZGRkZGIiB4PSIwIiB5PSIzIiB3aWR0aD0iMyIgaGVpZ2h0PSIzIj48L3JlY3Q+CiAgICAgICAgICAgIDxyZWN0IGlkPSJSZWN0YW5nbGUtMTEtQ29weSIgZmlsbD0iI0ZGRkZGRiIgeD0iMyIgeT0iMCIgd2lkdGg9IjMiIGhlaWdodD0iMyI+PC9yZWN0PgogICAgICAgICAgICA8cmVjdCBpZD0iUmVjdGFuZ2xlLTExLUNvcHktMyIgZmlsbD0iI0UwRTBFMCIgeD0iMyIgeT0iMyIgd2lkdGg9IjMiIGhlaWdodD0iMyI+PC9yZWN0PgogICAgICAgIDwvZz4KICAgIDwvZz4KPC9zdmc+');
}

/* Tile customization */
.e-container .e-palette .e-tile.e-custom-tile {
  height: 24px;
  width: 24px;
  margin: 4px;
}

h4, #preview {
    font-family: 'Helvetica Neue', 'Helvetica', 'Arial', 'sans-serif';
    font-size: 14px;
}
</style>
```

{% endtab %}
