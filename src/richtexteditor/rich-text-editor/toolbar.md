---
title: "Vue Rich Text Editor Toolbar configuration"
component: "Rich Text Editor"
description: "This section for Syncfusion vue Rich Text Editor control explains the toolbar which provides a set of commands for editing and formatting the content."
---

# Toolbar

The Rich Text Editor toolbar contains a collection of tools such as bold, italic, and text alignment buttons that are used to format the content. However, in most integrations, you can customize the toolbar configurations easily to suit your needs.

To create Rich Text Editor with Markdown editing feature, inject the [`Toolbar`](../api/rich-text-editor/toolbar/#toolbar) module to the Rich Text Editor using the `RichTextEditor.Inject(Toolbar)` method.

The Rich Text Editor allows you to configure different types of toolbar using [`toolbarSettings.type`](../api/rich-text-editor/toolbarType/#toolbartype) property. The types of toolbar are:

1. Expand
2. MultiRow

## Expand Toolbar

The default mode of [`toolbarSettings.type`](../api/rich-text-editor/toolbarType/#toolbartype) is Expand, it will hide the overflowing items in the next row. By clicking the expand arrow, view the overflowing toolbar items.

{% tab template="rich-text-editor/toolbar", isDefaultActive=true %}

```html
<template>
<div>
<div class="control-section">
    <div class="sample-container">
        <div class="default-section">
        <ejs-richtexteditor ref="rteObj" :height="340" :toolbarSettings="toolbarSettings"><p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
        <p><b>Key features:</b></p>
          <ul>
            <li><p>Provides IFRAME and DIV modes</p></li>
            <li><p>Capable of handling markdown editing.</p></li>
            <li><p>Contains a modular library to load the necessary functionality on demand.</p></li>
            <li><p>Provides a fully customizable toolbar.</p></li>
            <li><p>Provides HTML view to edit the source directly for developers.</p></li>
            <li><p>Supports third-party library integration.</p></li>
            <li><p>Allows preview of modified content before saving it.</p></li>
            <li><p>Handles images, hyperlinks, video, hyperlinks, uploads, etc.</p></li>
          </ul></ejs-richtexteditor>
        </div>
    </div>
</div>

</div>
</template>
<script>
import Vue from "vue";
import { RichTextEditorPlugin, Toolbar, HtmlEditor } from "@syncfusion/ej2-vue-richtexteditor";

Vue.use(RichTextEditorPlugin);

export default {
     data: function() {
        return {
        toolbarSettings: {
            type: 'Expand',
            items: ['Bold', 'Italic', 'Underline', 'StrikeThrough',
            'FontName', 'FontSize', 'FontColor', 'BackgroundColor',
            'LowerCase', 'UpperCase', '|',
            'Formats', 'Alignments', 'OrderedList', 'UnorderedList',
            'Outdent', 'Indent', '|',
            'CreateLink', 'Image', '|', 'ClearFormat', 'Print',
            'SourceCode', 'FullScreen', '|', 'Undo', 'Redo'
          ]
        },
        };
    },
    provide:{
        richtexteditor:[Toolbar, HtmlEditor]
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
</style>
```

{% endtab %}

## Multi-row Toolbar

Set the type as MultiRow in [toolbarSettings](../api/rich-text-editor/toolbarSettings/#toolbarsettings) to hide the overflowing items in the next row. All toolbar items are visible.

{% tab template="rich-text-editor/toolbar", isDefaultActive=true %}

```html
<template>
<div>
<div class="control-section">
    <div class="sample-container">
        <div class="default-section">
        <ejs-richtexteditor ref="rteObj" :height="340" :toolbarSettings="toolbarSettings"><p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
        <p><b>Key features:</b></p>
          <ul>
            <li><p>Provides IFRAME and DIV modes</p></li>
            <li><p>Capable of handling markdown editing.</p></li>
            <li><p>Contains a modular library to load the necessary functionality on demand.</p></li>
            <li><p>Provides a fully customizable toolbar.</p></li>
            <li><p>Provides HTML view to edit the source directly for developers.</p></li>
            <li><p>Supports third-party library integration.</p></li>
            <li><p>Allows preview of modified content before saving it.</p></li>
            <li><p>Handles images, hyperlinks, video, hyperlinks, uploads, etc.</p></li>
          </ul></ejs-richtexteditor>
        </div>
    </div>
</div>

</div>
</template>
<script>
import Vue from "vue";
import { RichTextEditorPlugin, Toolbar, HtmlEditor } from "@syncfusion/ej2-vue-richtexteditor";

Vue.use(RichTextEditorPlugin);

export default {
     data: function() {
        return {
        toolbarSettings: {
            type: 'MultiRow',
            items: ['Bold', 'Italic', 'Underline', 'StrikeThrough',
            'FontName', 'FontSize', 'FontColor', 'BackgroundColor',
            'LowerCase', 'UpperCase', '|',
            'Formats', 'Alignments', 'OrderedList', 'UnorderedList',
            'Outdent', 'Indent', '|',
            'CreateLink', 'Image', '|', 'ClearFormat', 'Print',
            'SourceCode', 'FullScreen', '|', 'Undo', 'Redo'
          ]
        },
        };
    },
    provide:{
        richtexteditor:[Toolbar, HtmlEditor]
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
</style>
```

{% endtab %}

## Floating Toolbar

By default, toolbar is float at the top of the Rich Text Editor on scrolling. It can be customized by specifying the offset of the floating toolbar from documents top position using  [`floatingToolbarOffset`](../api/rich-text-editor/#floatingtoolbaroffset).

Enable or disable the floating toolbar using [`enableFloating`](../api/rich-text-editor/toolbarSettings/#enablefloating) of the[`toolbarSettings`](../api/rich-text-editor/toolbarSettings/#toolbarsettings) property.

{% tab template="rich-text-editor/toolbar", isDefaultActive=true %}

```html
<template>
    <div>
        <div class="col-lg-4 property-section">
            <div title="Properties" id="property">
                <table title="Properties" id="property">
                    <tbody>
                        <tr>
                            <td>
                                <div>
                                    <ejs-checkbox label='Enable Floating' ref="checkInstance" :change="onFloatChange" id="float" :checked="false"></ejs-checkbox>
                                </div>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
        <div class="control-section">
            <div class="sample-container">
                <div class="default-section">
                    <ejs-richtexteditor ref="rteInstance" :height="340" :toolbarSettings="toolbarSettings"><p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
                        <p><b>Key features:</b></p>
                        <ul>
                            <li><p>Provides IFRAME and DIV modes</p></li>
                            <li><p>Capable of handling markdown editing.</p></li>
                            <li><p>Contains a modular library to load the necessary functionality on demand.</p></li>
                            <li><p>Provides a fully customizable toolbar.</p></li>
                            <li><p>Provides HTML view to edit the source directly for developers.</p></li>
                            <li><p>Supports third-party library integration.</p></li>
                            <li><p>Allows preview of modified content before saving it.</p></li>
                            <li><p>Handles images, hyperlinks, video, hyperlinks, uploads, etc.</p></li>
                        </ul>
                    </ejs-richtexteditor>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Vue from "vue";
import { RichTextEditorPlugin, Toolbar, HtmlEditor } from "@syncfusion/ej2-vue-richtexteditor";
import { CheckBoxPlugin } from "@syncfusion/ej2-vue-buttons";

Vue.use(RichTextEditorPlugin);
Vue.use(CheckBoxPlugin);

export default {
    data: function() {
        return {
        toolbarSettings: {
            enableFloating: false
        },
        };
    },
        methods: {
        onFloatChange: function(args) {
            this.$refs.rteInstance.ej2Instances.toolbarSettings.enableFloating = args.checked;
            this.$refs.rteInstance.dataBind();
        }
    },
    provide:{
        richtexteditor:[Toolbar, HtmlEditor]
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
</style>
```

{% endtab %}

## Toolbar items

The following table lists the tools available in the toolbar.

| **Name** | **Summary** | **Initialization** |
| --- | --- | --- |
| Undo | Allows to undo the actions. | toolbarSettings: { <br /> items: ['Undo'] <br /> } |
| Redo | Allows to redo the actions. | toolbarSettings: { <br /> items: ['Redo'] <br /> } |
| Alignment | Align the content with left, center, and right margin. | toolbarSettings: { <br /> items: ['Alignments'] <br /> } |
| OrderedList | Create a new list item (numbered). | toolbarSettings: { <br /> items: ['OrderedList'] <br /> } |
| UnorderedList | Create a new list item (bulleted). | toolbarSettings: { <br /> items: ['UnorderedList'] <br /> } |
| Indent |Allows to increase the indent level of the content. | toolbarSettings: { <br /> items: ['Indent'] <br /> } |
| Outdent | Allows to decrease the indent level of the content. | toolbarSettings: { <br /> items: ['Outdent'] <br /> } |
| Hyperlink | Creates a hyperlink to a text or image to a specific location in the content. | toolbarSettings: { <br /> items: ['CreateLink'] <br /> } |
| Images | Inserts an image from an online source or local computer. | toolbarSettings: { <br /> items: ['Image'] <br /> } |
| LowerCase | Change the case of selected text to lower in the content. | toolbarSettings: { <br /> items: ['LowerCase'] <br /> } |
| UpperCase | Change the case of selected text to upper in the content. | toolbarSettings: { <br /> items: ['UpperCase'] <br /> } |
| SubScript | Makes the selected text as subscript (lower). | toolbarSettings: { <br /> items: ['SubScript'] <br /> } |
| SuperScript | Makes the selected text as superscript (higher). | toolbarSettings: { <br /> items: ['SuperScript'] <br /> } |
| Print  | Allows to print the editor content. | toolbarSettings: { <br /> items: ['Print'] <br /> } |
| FontName | Defines the fonts that appear under the Font Family DropDownList from the Rich Text Editor's toolbar. | toolbarSettings: { <br /> items: ['FontName'] <br /> } |
| FontSize | Defines the font sizes that appear under the Font Size DropDownList from the Rich Text Editor's toolbar. | toolbarSettings: { <br /> items: ['FontSize'] <br /> } |
| FontColor | Specifies an array of colors can be used in the colors pop-up for font color. | toolbarSettings: { <br /> items: ['FontColor'] <br /> } |
| BackgroundColor | Specifies an array of colors can be used in the colors pop-up for background color. | toolbarSettings: { <br /> items: ['BackgroundColor'] <br /> } |
| Format | An object with the options that will appear in the paragraph format drop-down from the toolbar. | toolbarSettings: { <br /> items: ['Formats'] <br /> } |
| StrikeThrough | Apply double line strike through formatting for the selected text. | toolbarSettings: { <br /> items: ['StrikeThrough'] <br /> } |
| ClearFormat | The clear format tool is used to remove all formatting styles (such as bold, italic, underline, color, superscript, subscript, and more) from currently selected text. As a result, all the formatting text will be cleared and return to its default formatting styles. | toolbarSettings: { <br /> items: ['ClearFormat'] <br /> } |
| FullScreen | Stretches the editor to the maximum width and height of the browser window. | toolbarSettings: { <br /> items: ['FullScreen'] <br /> } |
| SourceCode | The RichTextBox includes the ability for users to directly edit the HTML code via Source View. If you made any modification in source view directly, synchronize with design view. | toolbarSettings: { <br /> items: ['SourceCode'] <br /> } |
| NumberFormatList | Allows to create list items with various list style types(numbered)|toolbarSettings: { <br /> items: ['NumberFormatList'] <br /> } |
| BulletFormatList | Allows to create list items with various list style types(bulleted)|toolbarSettings: { <br /> items: ['BulletFormatList'] <br /> } |

By default, tools will be arranged in following order.

> items: ['Bold', 'Italic', 'Underline', '|', 'Formats', 'Alignments', 'OrderedList', 'UnorderedList', '|', 'CreateLink', 'Image', '|', 'SourceCode', 'Undo', 'Redo']

The tools order can be customized as our application requirement. If you are not specifying any tools order, the editor will create the toolbar with default items.

## Custom tool

The Rich Text Editor allows you to configure your own commands to its toolbar using the [`toolbarSettings`](../api/rich-text-editor/toolbarSettings/#toolbarsettings) property. The command can be plain text, icon, or HTML template. The order and the group can also be defined where the command should be included. Bind the action to the command by getting its instance.

This sample shows how to add your own commands to the toolbar of the Rich Text Editor. The **Ω** command is added to insert special characters in the editor. By clicking the **Ω** command, it will show the special characters list, and then choose the character to be inserted in the editor.

The following code snippet illustrates custom tool with tooltip text which will be included in [`items`](../api/rich-text-editor/toolbarSettings/#items) field of the [`toolbarSettings`](../api/rich-text-editor/toolbarSettings/#toolbarsettings) property.

In the following sample, once Rich Text Editor control is created, the concern event will be [`created`](../api/rich-text-editor/#created) the Dialog component can be rendered and target as Rich Text Editor content.

```javascript
{
    tooltipText: 'Insert Symbol',
    undo: true,
    click: this.onClick.bind(this),
    template: '<button class="e-tbar-btn e-btn" tabindex="-1" id="custom_tbar" style="width:100%"><div class="e-tbar-btn-text" style="font-weight: 500;"> &#937;</div></button>'
}

```

Click the **Ω** command to show the special characters list, and then choose the character to be inserted in the editor.

{% tab template="rich-text-editor/toolbar", isDefaultActive=true %}

```html
<template>
<div>
<div class="control-section">
    <div class="sample-container">
        <div class="default-section" id="rteSection" style="min-height: 360px;">
        <ejs-richtexteditor ref="customObj" :toolbarSettings="toolbarSettings" :created="onCreate"><p style="margin-right:10px">The custom command "insert special character" is configured as the last item of the toolbar. Click on the command and choose the special character you want to include from the popup.</p></ejs-richtexteditor>
        <ejs-dialog id='rteDialog' :buttons='dlgButtons' :width='width' :height="height" :header='header' ref="dialogObj" :overlayClick='dialogOverlay' :visible='visible' :showCloseIcon='showCloseIcon' :isModal='modal'  target='#rteSection' :created="dialogCreate">
        </ejs-dialog>
        <div id="customTbarDialog" style="display: none">
                <div id="rteSpecial_char">
                   <div class="char_block" title="&#94;">&#94;</div>
                    <div class="char_block" title="&#95;">&#95;</div>
                    <div class="char_block" title="&#96;">&#96;</div>
                    <div class="char_block" title="&#123;">&#123;</div>
                    <div class="char_block" title="&#124;">&#124;</div>
                    <div class="char_block" title="&#125;">&#125;</div>
                    <div class="char_block" title="&#126;">&#126;</div>
                    <div class="char_block" title="&#160;">&#160;</div>
                    <div class="char_block" title="&#161;">&#161;</div>
                    <div class="char_block" title="&#162;">&#162;</div>
                    <div class="char_block" title="&#163;">&#163;</div>
                    <div class="char_block" title="&#164;">&#164;</div>
                    <div class="char_block" title="&#165;">&#165;</div>
                    <div class="char_block" title="&#x20B9;">&#x20B9;</div>
                    <div class="char_block" title="&#166;">&#166;</div>
                    <div class="char_block" title="&#167;">&#167;</div>
                    <div class="char_block" title="&#168;">&#168;</div>
                    <div class="char_block" title="&#169;">&#169;</div>
                    <div class="char_block" title="&#170;">&#170;</div>
                    <div class="char_block" title="&#171;">&#171;</div>
                    <div class="char_block" title="&#172;">&#172;</div>
                    <div class="char_block" title="&#173;">&#173;</div>
                    <div class="char_block" title="&#174;">&#174;</div>
                    <div class="char_block" title="&#175;">&#175;</div>
                    <div class="char_block" title="&#176;">&#176;</div>
                    <div class="char_block" title="&#177;">&#177;</div>
                    <div class="char_block" title="&#178;">&#178;</div>
                    <div class="char_block" title="&#179;">&#179;</div>
                    <div class="char_block" title="&#180;">&#180;</div>
                    <div class="char_block" title="&#181;">&#181;</div>
                    <div class="char_block" title="&#182;">&#182;</div>
                    <div class="char_block" title="&#183;">&#183;</div>
                    <div class="char_block" title="&#184;">&#184;</div>
                    <div class="char_block" title="&#185;">&#185;</div>
                    <div class="char_block" title="&#186;">&#186;</div>
                    <div class="char_block" title="&#187;">&#187;</div>
                    <div class="char_block" title="&#188;">&#188;</div>
                    <div class="char_block" title="&#189;">&#189;</div>
                    <div class="char_block" title="&#190;">&#190;</div>
                    <div class="char_block" title="&#191;">&#191;</div>
                    <div class="char_block" title="&#192;">&#192;</div>
                    <div class="char_block" title="&#193;">&#193;</div>
                    <div class="char_block" title="&#194;">&#194;</div>
                    <div class="char_block" title="&#195;">&#195;</div>
                </div>
            </div>
        </div>
    </div>
</div>

</div>
</template>

<style>
    #rteSpecial_char .char_block {
        display: inline-block;
    }

    #custom_tbar,
    #custom_tbar div{
        cursor: pointer;
        font-size: 16px;
    }

    #rteSpecial_char {
        padding: 15px 0 15px 0;
    }

    #rteSpecial_char .char_block.e-active {
        outline: 1px solid #e3165b;
        border-color: #e3165b;
    }

    #rteSpecial_char .char_block {
        width: 30px;
        height: 30px;
        line-height: 30px;
        margin: 0 5px 5px 0;
        text-align: center;
        vertical-align: middle;
        border: 1px solid #DDDDDD;
        font-size: 20px;
        cursor: pointer;
        user-select: none;
    }
</style>

<script>
import Vue from "vue";
import { Browser, addClass, removeClass } from "@syncfusion/ej2-base";
import { RichTextEditorPlugin, Toolbar, Link, NodeSelection, Image, QuickToolbar, HtmlEditor } from "@syncfusion/ej2-vue-richtexteditor";
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';
let proxy = undefined;

Vue.use(RichTextEditorPlugin);
Vue.use(DialogPlugin);

export default {
    data: function() {
        return {
            selection: new NodeSelection(),
            ranges: null,
            header: 'Special Characters',
            visible: false,
            modal: true,
            showCloseIcon: false,
            width: '520px',
            height: '310px',
            dlgButtons: [{ click: this.onInsert.bind(this), buttonModel: { isPrimary:'true', content: 'Insert' } }, { buttonModel: { content: 'Cancel' }, click: this.dialogOverlay.bind(this) }],
            toolbarSettings: {
                items: ['Bold', 'Italic', 'Underline', '|', 'Formats', 'Alignments', 'OrderedList',
                'UnorderedList', '|', 'CreateLink', 'Image', '|', 'SourceCode',
                {
                    tooltipText: 'Insert Symbol',
                    undo: true,
                    click: this.onClick.bind(this),
                    template: '<button class="e-tbar-btn e-btn" tabindex="-1" id="custom_tbar"  style="width:100%"><div class="e-tbar-btn-text" style="font-weight: 500;"> &#937;</div></button>'
                }, '|', 'Undo', 'Redo']
            },
        };
    },
    methods: {
        onCreate: function(e) {
        var customBtn = document.getElementById('custom_tbar');
         this.$refs.dialogObj.ej2Instances.target = document.getElementById('rteSection');
         proxy = this;
        },
        onClick: function() {
            proxy.$refs.customObj.ej2Instances.focusIn();
            proxy.ranges = proxy.selection.getRange(document);
            proxy.$refs.dialogObj.ej2Instances.width = proxy.$refs.customObj.ej2Instances.element.offsetWidth * 0.5;
            proxy.$refs.dialogObj.ej2Instances.content = document.getElementById('rteSpecial_char');
            proxy.$refs.dialogObj.ej2Instances.dataBind();
            proxy.$refs.dialogObj.ej2Instances.show();
        }
        dialogCreate: function() {
            var dialogCtn = document.getElementById('rteSpecial_char');
            proxy = this;
            dialogCtn.onclick = function (e) {
            var target = e.target;
            var activeEle = proxy.$refs.dialogObj.ej2Instances.element.querySelector('.char_block.e-active');
            if (target.classList.contains('char_block')) {
                target.classList.add('e-active');
                if (activeEle) {
                    activeEle.classList.remove('e-active');
                }
            }
        };
        },
        onInsert: function() {
            var activeEle = this.$refs.dialogObj.ej2Instances.element.querySelector('.char_block.e-active');
            if (activeEle) {
                  proxy.$refs.customObj.ej2Instances.executeCommand('insertText', activeEle.textContent , {undo: true});
            }
            this.dialogOverlay();
        },
        dialogOverlay: function() {
             var activeEle = this.$refs.dialogObj.ej2Instances.element.querySelector('.char_block.e-active');
            if (activeEle) {
                activeEle.classList.remove('e-active');
            }
            this.$refs.dialogObj.ej2Instances.hide();
        }
    },
    provide:{
        richtexteditor:[Toolbar, Link, Image, QuickToolbar, HtmlEditor]
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
</style>
```

{% endtab %}

## Quick inline toolbar

Quick commands are opened as context-menu on clicking the corresponding element. The commands must be passed as string collection to image, text, link and table attributes of the [`quickToolbarSettings`](../api/rich-text-editor/quickToolbarSettings/#quicktoolbarsettings) property.

| Target Element | Default Quick Toolbar items |
|----------------|---------|
|image | 'Replace', 'Align', 'Caption', 'Remove', 'InsertLink', 'Display', 'AltText','Dimension'.|
| link | 'Open', 'Edit', 'UnLink'.|
| text (`Deprecated`) | 'Cut', 'Copy', 'Paste'.|
| table | 'TableHeader', 'TableRows', 'TableColumns', 'BackgroundColor', 'TableRemove', 'Alignments', 'TableCellVerticalAlign', 'Styles'.|

Custom tool can be added to the corresponding quick toolbar, using [`quickToolbarSettings`](../api/rich-text-editor/quickToolbarSettings/#quicktoolbarsettings) property.

The following sample demonstrates the option to insert the image to the Rich Text Editor content as well as option to rotate the image through the quick toolbar. The image rotation functionalities have been achieved through the [`toolbarClick`](../api/rich-text-editor/#toolbarclick) event.

{% tab template="rich-text-editor/toolbar", isDefaultActive=true %}

```html
<template>
<div>
<div class="control-section">
    <div class="sample-container">
        <div class="default-section" id="rteSection">
        <ejs-richtexteditor ref="rteObj" :quickToolbarSettings="quickToolbarSettings" :toolbarClick="onToolbarClick">
        <p>Rich Text Editor allows to insert images from online source as well as local
            computer where you want to insert the image in your content.</p>
        <p><b>Get started Quick Toolbar to click on the image</b></p>
        <p>It is possible to add custom style on the selected image inside the Rich Text Editor through quick toolbar.</p>
        <img id="rteImageID" style="width:300px; height:300px;transform: rotate(0deg);" alt="Logo" src="https://ej2.syncfusion.com/demos/src/rich-text-editor/images/RTEImage-Feather.png"></ejs-richtexteditor>
        </div>
    </div>
</div>

</div>
</template>

<style>
.e-rte-quick-popup .e-rte-quick-toolbar .e-rotate-left::before {
    content: "\e341";
}

.e-rte-quick-popup .e-rte-quick-toolbar .e-rotate-right::before {
    content: "\e354";
}
</style>

<script>
import Vue from "vue";
import { RichTextEditorPlugin, Toolbar, Image,  Link, HtmlEditor, QuickToolbar, NodeSelection } from "@syncfusion/ej2-vue-richtexteditor";

Vue.use(RichTextEditorPlugin);

export default {
    data: function() {
        return {
        quickToolbarSettings: {
            image: [
                'Replace', 'Align', 'Caption', 'Remove', 'InsertLink', 'OpenImageLink', '-',
                'EditImageLink', 'RemoveImageLink', 'Display', 'AltText', 'Dimension',
                {
                    tooltipText: 'Rotate Left',
                    template: '<button class="e-tbar-btn e-btn" id="roatateLeft"><span class="e-btn-icon e-icons e-rotate-left"></span>'
                },
                {
                    tooltipText: 'Rotate Right',
                    template: '<button class="e-tbar-btn e-btn" id="roatateRight"><span class="e-btn-icon e-icons e-rotate-right"></span>'
                }
            ]
        }
        };
        },
        methods: {
            onToolbarClick: function(e) {
            var nodeObj = new NodeSelection();
            var range = nodeObj.getRange(this.$refs.rteObj.ej2Instances.contentModule.getDocument());
            var imgEle = nodeObj.getNodeCollection(range)[0];
            if (e.item.tooltipText === 'Rotate Right') {
                var transform = (imgEle.style.transform === '') ? 0 :
                    parseInt(imgEle.style.transform.split('(')[1].split(')')[0], 10);
                imgEle.style.transform = 'rotate(' + (transform + 90) + 'deg)';
            }
            else if (e.item.tooltipText === 'Rotate Left') {
                var transform = (imgEle.style.transform === '') ? 0 :
                    Math.abs(parseInt(imgEle.style.transform.split('(')[1].split(')')[0], 10));
                imgEle.style.transform = 'rotate(-' + (transform + 90) + 'deg)';
            }
            }
        },
    provide:{
        richtexteditor:[Toolbar, Image,  Link, HtmlEditor, QuickToolbar]
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
</style>
```

{% endtab %}

> Rich Text Editor features are segregated into individual feature-wise modules. To use quick toolbar, inject the quick toolbar module using the `RichTextEditor.Inject(image, link)`.

## See Also

* [How to render the toolbar in inline mode](./inline-mode/)
* [How to customize the toolbar items shortcut key](./how-to/customize-shortcut-keys)