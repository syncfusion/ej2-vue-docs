---
title: "Working with Paragraph Formatting"
component: "DocumentEditor"
description: "Learn paragraph formatting supported in JavaScript document editor and how to apply it for selected contents."
---

# Working with Paragraph formatting

Document editor supports various paragraph formatting options such as text alignment, indentation, paragraph spacing, and more.

## Indentation

You can modify the left or right indentation of selected paragraphs using the following sample code.

```javascript
this.$refs.documenteditor.ej2Instances.selection.paragraphFormat.leftIndent= 24;
this.$refs.documenteditor.ej2Instances.selection.paragraphFormat.rightIndent= 24;
```

## Special indentation

You can define special indent for first line of the paragraph using the following sample code.

```javascript
this.$refs.documenteditor.ej2Instances.selection.paragraphFormat.firstLineIndent= 24;
```

## Increase indent

You can increase the left indent of selected paragraphs by a factor of 36 points using the following sample code.

```javascript
this.$refs.documenteditor.ej2Instances.editor.increaseIndent()
```

## Decrease indent

You can decrease the left indent of selected paragraphs by a factor of 36 points using the following sample code.

```javascript
this.$refs.documenteditor.ej2Instances.editor.decreaseIndent()
```

## Text alignment

You can get or set the text alignment of selected paragraphs using the following sample code.

```javascript
this.$refs.documenteditor.ej2Instances.selection.paragraphFormat.textAlignment= 'Center' | 'Left' | 'Right' | 'Justify';
```

You can toggle the text alignment of selected paragraphs by specifying a value using the following sample code.

```javascript
this.$refs.documenteditor.ej2Instances.editor.toggleTextAlignment('Center' | 'Left' | 'Right' | 'Justify');
```

## Line spacing and its type

You can define the line spacing and its type for selected paragraphs using the following sample code.

```javascript
this.$refs.documenteditor.ej2Instances.selection.paragraphFormat.lineSpacingType='AtLeast';
this.$refs.documenteditor.ej2Instances.selection.paragraphFormat.lineSpacing= 6;
```

## Paragraph spacing

You can define the spacing before or after the paragraph by using the following sample code.

```javascript
this.$refs.documenteditor.ej2Instances.selection.paragraphFormat.beforeSpacing= 24;
this.$refs.documenteditor.ej2Instances.selection.paragraphFormat.afterSpacing= 24;
```

## Toolbar with paragraph formatting options

The following sample demonstrates the paragraph formatting options using a toolbar.

```html
<template>
    <div id="app" style="height:330px">
    <div>
        <ejs-toolbar v-bind:clicked='toolbarButtonClick'>
            <e-items>
                <e-item prefixIcon='e-de-icon-AlignLeft' id='AlignLeft' tooltipText='Align Left'></e-item>
                <e-item prefixIcon='e-de-icon-AlignCenter' id='Align Center' tooltipText='AlignCenter'></e-item>
                <e-item prefixIcon='e-de-icon-AlignRight' id='Align Right' tooltipText='AlignRight'></e-item>
                <e-item prefixIcon='e-de-icon-Justify' id='Justify' tooltipText='Justify'></e-item>
                <e-item prefixIcon='e-de-icon-IncreaseIndent' id='IncreaseIndent' tooltipText='Increase Indent'></e-item>
                <e-item prefixIcon='e-de-icon-DecreaseIndent' id='DecreaseIndent' tooltipText='Decrease Indent'></e-item>
                <e-item type='Separator'></e-item>
                <e-item prefixIcon='e-de-icon-ClearAll' id='ClearFormat' tooltipText='ClearFormatting'></e-item>
            </e-items>
        </ejs-toolbar>
    </div>
    <ejs-documenteditor ref="documenteditor" v-bind:selectionChange='onSelectionChange' :enableSelection='true' :isReadOnly='false' :enableEditor='true' :enableEditorHistory='true' :enableSfdtExport='true' :enableContextMenu='true' style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin, Editor, Selection, EditorHistory, SfdtExport, ContextMenu } from '@syncfusion/ej2-vue-documenteditor';
import { ToolbarPlugin } from "@syncfusion/ej2-vue-navigations";

Vue.use(DocumentEditorPlugin);
Vue.use(ToolbarPlugin);

export default {
    data: function () {
        return {
        };
    },
    provide: {
        DocumentEditor: [Editor, Selection, EditorHistory, SfdtExport, ContextMenu]
    },
    methods: {
        toolbarButtonClick: function (arg) {
            switch (arg.item.id) {
                case 'AlignLeft':
                    //Toggle the Left alignment for selected or current paragraph
                    this.$refs.documenteditor.ej2Instances.editor.toggleTextAlignment('Left');
                    break;
                case 'AlignRight':
                    //Toggle the Right alignment for selected or current paragraph
                    this.$refs.documenteditor.ej2Instances.editor.toggleTextAlignment('Right');
                    break;
                case 'AlignCenter':
                    //Toggle the Center alignment for selected or current paragraph
                    this.$refs.documenteditor.ej2Instances.editor.toggleTextAlignment('Center');
                    break;
                case 'Justify':
                    //Toggle the Justify alignment for selected or current paragraph
                    this.$refs.documenteditor.ej2Instances.editor.toggleTextAlignment('Justify');
                    break;
                case 'IncreaseIndent':
                    //Increase the left indent of selected or current paragraph
                    this.$refs.documenteditor.ej2Instances.editor.increaseIndent();
                    break;
                case 'DecreaseIndent':
                    //Decrease the left indent of selected or current paragraph
                    this.$refs.documenteditor.ej2Instances.editor.decreaseIndent();
                    break;
                case 'ClearFormat':
                    this.$refs.documenteditor.ej2Instances.editor.clearFormatting();
                    break;
            }
        },
        onSelectionChange: function () {
            if (this.$refs.documenteditor.ej2Instances.selection) {
                var paragraphFormat = this.$refs.documenteditor.ej2Instances.selection.paragraphFormat;
                var toggleBtnId = ['AlignLeft', 'AlignCenter', 'AlignRight', 'Justify'];
                for (var i = 0; i < toggleBtnId.length; i++) {
                    let toggleBtn: HTMLElement = document.getElementById(
                        toggleBtnId[i]
                    );
                    toggleBtn.classList.remove('e-btn-toggle');
                }
                if (paragraphFormat.textAlignment === 'Left') {
                    document.getElementById('AlignLeft').classList.add('e-btn-toggle');
                } else if (paragraphFormat.textAlignment === 'Right') {
                    document.getElementById('AlignRight').classList.add('e-btn-toggle');
                } else if (paragraphFormat.textAlignment === 'Center') {
                    document
                        .getElementById('AlignCenter')
                        .classList.add('e-btn-toggle');
                } else {
                    document.getElementById('Justify').classList.add('e-btn-toggle');
                }
            }
        }
    }
}
</script>
<style>
 @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

## See Also

* [Feature modules](../document-editor/feature-module/)
* [Paragraph dialog](../document-editor/dialog#paragraph-dialog/)
* [Keyboard shortcuts](../document-editor/keyboard-shortcut#paragraph-formatting/)