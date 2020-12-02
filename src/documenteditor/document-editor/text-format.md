---
title: "Working with Text Formatting"
component: "DocumentEditor"
description: "Learn text formatting supported in JavaScript document editor and how to apply it for selected contents."
---

# Working with Text formatting

Document editor supports several formatting options for text like bold, italic, font color, highlight color, and more. This section describes how to modify the formatting for selected text in detail.

## Bold

The bold formatting for selected text can be get or set by using the following sample code.

```typescript

//Gets the value for bold formatting of selected text.
let bold : boolean = this.$refs.documenteditor.ej2Instances.selection.characterFormat.bold;
//Sets bold formatting for selected text.
this.$refs.documenteditor.ej2Instances.selection.characterFormat.bold = true;

```

You can toggle the bold formatting based on existing value at selection. Refer to the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.editor.toggleBold();
```

## Italic

The Italic formatting for selected text can be get or set by using the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.selection.characterFormat.italic= true|false;
```

You can toggle the Italic formatting based on existing value at selection. Refer to the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.editor.toggleItalic();
```

## Underline property

The underline style for selected text can be get or set by using the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.selection.characterFormat.underline='Single' | 'None';
```

You can toggle the underline style of selected text based on existing value at selection by specifying a value. Refer to the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.editor.toggleUnderline('Single');
```

## Strikethrough property

The strikethrough style for selected text can be get or set by using the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.selection.characterFormat.strikethrough='Single' | 'Normal';
```

You can toggle the strikethrough style of selected text based on existing value at selection by specifying a value. Refer to the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.editor.toggleStrikethrough();
```

## Superscript property

The selected text can be made superscript by using the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.selection.characterFormat.baselineAlignment='Superscript';
```

Toggle the selected text as superscript or normal using the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.editor.toggleSuperscript();
```

## Subscript property

The selected text can be made subscript by using the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.selection.characterFormat.baselineAlignment='Subscript';
```

Toggle the selected text as subscript or normal using the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.editor.toggleSubscript();
```

You can make a subscript or superscript text as normal using the following code.

```typescript
this.$refs.documenteditor.ej2Instances.selection.characterFormat.baselineAlignment='Normal';
```

## Size

The size of selected text can be get or set using the following code.

```typescript
this.$refs.documenteditor.ej2Instances.selection.characterFormat.fontSize= 32;
```

## Color

The color of selected text can be get or set using the following code.

```typescript
this.$refs.documenteditor.ej2Instances.selection.characterFormat.fontColor= 'Pink';
this.$refs.documenteditor.ej2Instances.selection.characterFormat.fontColor= '#FFC0CB';
```

## Font

The font style of selected text can be get or set using the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.selection.characterFormat.fontFamily= 'Arial';
```

## Highlight color

The highlight color of the selected text can be get or set using the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.selection.characterFormat.highlightColor= 'Pink';
this.$refs.documenteditor.ej2Instances.selection.characterFormat.highlightColor= '#FFC0CB';
```

## Toolbar with options for text formatting

Refer to the following example.

```html
<template>
    <div id="app" style="height:330px">
    <div>
        <ejs-toolbar v-bind:clicked='toolbarClickHandler'>
            <e-items>
                <e-item prefixIcon="e-de-icon-Bold" tooltipText="Bold" id="bold"></e-item>
                <e-item prefixIcon="e-de-icon-Italic" tooltipText="Italic" id="italic"></e-item>
                <e-item prefixIcon="e-de-icon-Underline" tooltipText="Underline" id="underline"></e-item>
                <e-item prefixIcon="e-de-icon-Strikethrough" tooltipText="Strikethrough" id="strikethrough"></e-item>
                <e-item prefixIcon="e-de-icon-Subscript" tooltipText="Subscript" id="subscript"></e-item>
                <e-item prefixIcon="e-de-icon-Superscript" tooltipText="Superscript" id="superscript"></e-item>
                <e-item type="Seperator"></e-item>
                <e-item type="Input" :template="<ejs-colorpicker :value='#000000' :showButtons='true' v:bind:change='onFontColorChange' ></ejs-colorpicker>"></e-item>
                <e-item type="Seperator"></e-item>
                <e-item type="Input" :template="<ejs-combobox :dataSource='fontStyle' :width='120' :index='2' :allowCustom='true' v:bind:change='onFontFamilyChange'  :showClearButton='false'></ejs-combobox>"></e-item>
                <e-item type="Input" :template="<ejs-combobox :dataSource='fontSize' :width='80' :index='2' :allowCustom='true' v:bind:change='onFontSizeChange'  :showClearButton='false'></ejs-combobox>"></e-item>
            </e-items>
        </ejs-toolbar>
    </div>
    <ejs-documenteditor ref="documenteditor" v-bind:selectionChange='onSelectionChange' :isReadOnly='false' :enableEditor='true' :enableEditorHistory='true' :enableSfdtExport='true' style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin, Editor,  Selection,  EditorHistory , SfdtExport } from '@syncfusion/ej2-vue-documenteditor';
import { ToolbarPlugin } from "@syncfusion/ej2-vue-navigations";
import { ColorPickerPlugin } from '@syncfusion/ej2-vue-inputs';
import { ComboBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(DocumentEditorPlugin);
Vue.use(ToolbarPlugin);
Vue.use(ColorPickerPlugin);
Vue.use(ComboBoxPlugin);

export default {
    data: function () {
        return {
            fontStyle:['Algerian', 'Arial', 'Calibri', 'Cambria', 'Cambria Math', 'Candara', 'Courier New', 'Georgia', 'Impact', 'Segoe Print', 'Segoe Script', 'Segoe UI', 'Symbol', 'Times New Roman', 'Verdana', 'Windings'],
            fontSize:['8', '9', '10', '11', '12', '14', '16', '18','20', '22', '24', '26', '28', '36', '48', '72', '96']
        };
    },
    provide: {
        DocumentEditor: [Editor,  Selection,  EditorHistory , SfdtExport]
    },
    methods: {
        toolbarButtonClick: function(arg) {
            switch (arg.item.id) {
                case 'bold':
                    //Toggles the bold of selected content
                    this.$refs.documenteditor.ej2Instances.editor.toggleBold();
                    break;
                case 'italic':
                    //Toggles the Italic of selected content
                    this.$refs.documenteditor.ej2Instances.editor.toggleItalic();
                    break;
                case 'underline':
                    //Toggles the underline of selected content
                    this.$refs.documenteditor.ej2Instances.editor.toggleUnderline('Single');
                    break;
                case 'strikethrough':
                    //Toggles the strikethrough of selected content
                    this.$refs.documenteditor.ej2Instances.editor.toggleStrikethrough();
                    break;
                case 'subscript':
                    //Toggles the subscript of selected content
                    this.$refs.documenteditor.ej2Instances.editor.toggleSubscript();
                    break;
                case 'superscript':
                    //Toggles the superscript of selected content
                    this.$refs.documenteditor.ej2Instances.editor.toggleSuperscript();
                    break;
            }
        },
        onFontFamilyChange: function(args) {
             this.$refs.documenteditor.ej2Instances.selection.characterFormat.fontFamily = args.value;
             this.$refs.documenteditor.focusIn();
        },
        onFontSizeChange: function(args) {
             this.$refs.documenteditor.ej2Instances.selection.characterFormat.fontSize = args.value;
             this.$refs.documenteditor.focusIn();
        },
        onFontColorChange: function(args) {
             this.$refs.documenteditor.ej2Instances.selection.characterFormat.fontColor = args.currentValue.hex;
             this.$refs.documenteditor.focusIn();
        },
        onSelectionChange: function() {
            var characterformat =  this.$refs.documenteditor.ej2Instances.selection.characterFormat;
            var properties = [characterformat.bold, characterformat.italic, characterformat.underline, characterformat.strikeThrough];
            var toggleBtnId = ["bold", "italic", "underline", "strikethrough"];
            for (var i = 0; i < properties.length; i++) {
                let toggleBtn: HTMLElement = document.getElementById(toggleBtnId[i]);
                if ((typeof (properties[i]) == 'boolean' && properties[i] == true) || (typeof (properties[i]) == 'string' && properties[i] !== 'None'))
                    toggleBtn.classList.add("e-btn-toggle");
                else {
                    if (toggleBtn.classList.contains("e-btn-toggle"))
                        toggleBtn.classList.remove("e-btn-toggle");
                }
            }
        }
    },
    mounted() {
      this.$refs.documenteditor.ej2Instances.editor.insertTable(2, 2);
    }
}
</script>
<style>
 @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

## See Also

* [Feature modules](../document-editor/feature-module/)
* [Font dialog](../document-editor/dialog#font-dialog/)
* [Keyboard shortcuts](../document-editor/keyboard-shortcut#text-formatting/)