---
title: "Rich Text Editor Markdown"
component: "Rich Text Editor"
description: "This section for Syncfusion vue Rich Text Editor component explains the markdown editing and custom formatting."
---

# Markdown

When you format the word in Markdown format, you should add Markdown syntax to the word to indicate the words and phrases that looks different from each other.

Rich Text Editor supports markdown editing when the [`editorMode`](../api/rich-text-editor/#editormode) set as **markdown** and using both *keyboard interaction* and *toolbar action*, you can apply the formatting to text

To use quick Markdown editing feature, inject `MarkdownEditorService` in the provider section of `AppModule`.

## Supported Commands

The Vue Markdown editor supports the following commands to format the markdown content:

|Commands|Syntax| Description |
|--------|------------------------------------------|------------|
| Bold | Sample content for `**`bold text`**`. | For bold, add `**` or `__` to front and back of the text. | For order list, precede each line with a number. |
| Italic | Sample content for `*`Italic text`*`. | For Italic, add `*` or `_` to front and back of the text. |
| Bold and Italics | Sample content for `***`bold and Italic text`***`. | For bold and Italics, add `***` to the front and back of the text. |
| Heading 1 | `#` Heading 1 content | For heading 1, add `#` to start of the line. |
| Heading 2 | `##` Heading 2 content | For heading 2, add `##` to start of the line. |
| Heading 3 | `###` Heading 3 content | For heading 3, add `###` to start of the line. |
| Heading 4 | `####` Heading 4 content | For heading 4, add `####` to start of the line. |
| Heading 5 | `#####` Heading 5 content | For heading 5, add `#####` to start of the line. |
| Heading 6 | `######` Heading 6 content | For heading 6, add `######` to start of the line. |
| Line Break | First line `<br>`Second line | For line break, press enter two times (or) add `<br>` in between the first and the second line. |
| Blockquotes | `>` Blockquotes text | For blockquotes, add `>` to start of the line. |
| Strike Through | Sample content for `~~`strike through text`~~`. | For strike through, add `~~` to front and back of the text. |
| Code (Single line) | \`Single line code\` | For single line code, add \` to front and back of the text. |
| Code block (Multi Line) | \`\`\`<br>Multi line code text<br>Multi line code text<br>\`\`\` | For multiple line code, add \`\`\` in the new line before and after the content. |
| Subscript | `<sub>`Subscript text`</sub>` | For subscript, add `<sub>` to the front and `</sub>` to the back of the text. |
| Superscript | `<sup>`Superscript text`</sup>` | For superscript, add `<sup>` to the front and `</sup>` to the back of the text. |
| Ordered List | `1.` First<br>`1.` Second | For ordered list, preceding one or more lines of text with `1.` |
| Unordered List | `*` First<br>`*` second | For unordered list, preceding one or more lines of text with `*`. |
| Links | **Link text without title text**<br>`[` Link text `](`URL`)`<br> **Link text with title text**<br>`[` Link text `](`URL , “title text”`)` | Create an inline link by wrapping link text in brackets `[ ]`, and then wrapping the URL as first parameter and title as second parameter in the parentheses `()`.<br>**Note:** The title text is optional, if needed it can be given manually.|
| Table | `|` Heading 1 `|` Heading 2 `|`<br>`|---------|---------|`<br>`|` Col A1 `|` Col A2 `|`<br>`|` Col B1 `|` Col B2 `|` | Create a table using the pipes and underscores as given in the syntax to create 2 x 2 table. |
| Horizontal Line | `***` (three asterix in new line)<br>(or)<br>`___` (three underscores in new line) | For horizontal line, add `***` or `___` to the start of the new line. |
| Image | `![](`URL path`)` | Create an image by wrapping the image source in parentheses `()`. |
| Image with alternate text | `![` alternate text `](`URL path`)` | Create an image with alternate text by wrapping an alternative text in brackets `[]`, and then link of the image source in parentheses `()`.<br>**Note:** When inserting the image using toolbar, the alternate text cannot be provided that needs to be given manually. |
| Escape tick marks supported | Sample text content with `**`bold and `**`not bold`**` text can be in the same line.`**` | In the syntax, the whole content is made as bold where the content `not bold` can be made as normal text by adding the bold syntax to the start and end of the respective text. Likewise you can do the same for various inline commands. |
| Escape Character | `\(`any syntax`)` | Escape any markdown syntax by prefix `\` to the syntax.<br>Example:<br>`\**`Bold text`**`|
| HTML Entities | Copyright: &copy; - `&copy;` <br>Trade mark: &trade; - `&trade;`<br>Registered: &reg; - `&reg;`<br>Ampersand: &amp; - `&amp;`<br>Less than: &lt; - `&lt;`<br>Greater than: &gt; - `&gt;` | For HTML entities, add & and ; to the front and back of the respective entities. |

> The above listed commands alone are supported in Syncfusion Markdown editor. For other unsupported commands, you can achieve using the HTML tags in Markdown editor. The foot notes, definitions, math, and check list markdown syntax are also not supported.

## Markdown to HTML

The Rich Text Editor allows you to preview markdown changes immediately using preview. In this sample, the third-party library [`Marked`](https://marked.js.org/#/README.md#README.md) is used to convert markdown into HTML content.

This sample demonstrates how to preview markdown changes in Rich Text Editor. Type or edit the display text, and apply format to view the preview of markdown. The `actionComplete` event can be used to convert Markdown to HTML.

{% tab template="rich-text-editor/markdown", isDefaultActive=true %}

```html
<template>
  <div id="defaultRTE">
    <ejs-richtexteditor id="preview" ref="rteInstance" :toolbarSettings="toolbarSettings" :created="created" :actionComplete='actionComplete' :editorMode="editorMode" :height="height">
In Rich Text Editor , you click the toolbar buttons to format the words and the changes
are visible immediately.
Markdown is not like that. When you format the word in Markdown format, you need to
add Markdown syntax to the word to indicate which words
and phrases should look different from each other
Rich Text Editor supports markdown editing when the editorMode set as **markdown** and using both *keyboard interaction* and *toolbar action*, you can apply the formatting to text.
We can add our own custom formation syntax for the Markdown formation, [sample link](https://ej2.syncfusion.com/home/).
The third-party library <b>Marked</b> is used in this sample to convert markdown into HTML content.
      </ejs-richtexteditor>
  </div>
</template>
    <style>
    .e-richtexteditor .e-rte-content .e-content{
        min-height: 150px;
    }
    .e-richtexteditor .e-rte-content textarea.e-content {
        float: left;
        border-right: 1px solid rgba(0, 0, 0, 0.12);
    }
    .e-richtexteditor .e-rte-content {
        overflow: hidden;
    }
    .e-md-preview::before {
        content: '\e345';
    }

    .e-rte-content .e-content.e-pre-source {
        width: 100%;
    }
    .e-icon-btn.e-active .e-md-preview.e-icons::before {
        content: '\e350';
    }
</style>
<script>
import Vue from "vue";
import { Browser, addClass, removeClass, isNullOrUndefined } from "@syncfusion/ej2-base";
import { RichTextEditorPlugin, Toolbar, Link, Image, MarkdownEditor } from "@syncfusion/ej2-vue-richtexteditor";
import { createElement, KeyboardEventArgs } from '@syncfusion/ej2-vue-base';

Vue.use(RichTextEditorPlugin);

export default {
    data: function() {
        return {
            textArea: '',
            height: '300px',
        toolbarSettings: {
            items: ['Bold', 'Italic', 'StrikeThrough', '|', 'Formats', 'OrderedList', 'UnorderedList', '|', 'CreateLink', 'Image', '|',
                { tooltipText: 'Preview', template: '<button id="preview-code" class="e-tbar-btn e-control e-btn e-icon-btn">' +
                    '<span class="e-btn-icon e-md-preview e-icons"></span></button>' },
                { tooltipText: 'Split Editor', template: '<button id="MD_Preview" class="e-tbar-btn e-control e-btn e-icon-btn">' +
                    '<span class="e-btn-icon e-view-side e-icons"></span></button>' }, 'FullScreen', '|', 'Undo', 'Redo']
        },
        editorMode: 'Markdown',
        };
    },
    methods: {
        created: function() {
            var script = document.createElement('script');
            script.src = 'https://cdn.jsdelivr.net/npm/marked/marked.min.js';
            document.head.appendChild(script);
            this.textArea = this.$refs.rteInstance.$el.parentNode.querySelector('.e-content');
            this.textArea.onkeyup = (Event) => {
                this.markDownConversion();
            };
            document.getElementById('preview-code').onclick = () => {
                this.fullPreview({ mode: true, type: 'preview'});
                 if (event.target.parentElement.classList.contains('e-active')) {
                    this.$refs.rteInstance.ej2Instances.disableToolbarItem(['Bold', 'Italic', 'StrikeThrough', 'Formats', 'OrderedList',
                     'UnorderedList', 'CreateLink', 'Image']);
                     event.target.parentElement.parentElement.nextElementSibling.classList.add('e-overlay');
                } else {
                    this.$refs.rteInstance.ej2Instances.enableToolbarItem(['Bold', 'Italic', 'StrikeThrough', 'Formats', 'OrderedList',
                     'UnorderedList', 'CreateLink', 'Image']);
                      event.target.parentElement.parentElement.nextElementSibling.classList.remove('e-overlay');
                }
            };
            document.getElementById('MD_Preview').onclick = () => {
                if (this.$refs.rteInstance.$el.classList.contains('e-rte-full-screen')) {
                    this.fullPreview({ mode: true, type: '' });
                }
                document.getElementById('preview-code').classList.remove('e-active');
                this.$refs.rteInstance.ej2Instances.showFullScreen();
            };
        },
        markDownConversion: function(){
        if (document.getElementById('MD_Preview').classList.contains('e-active')) {
            var id = this.$refs.rteInstance.ej2Instances.getID() + 'html-view';
            var htmlPreview = this.$refs.rteInstance.$el.parentNode.querySelector('#' + id);
            htmlPreview.innerHTML = marked(this.textArea.value);
        }
    },
    actionComplete: function(e) {
        var mdsource = document.getElementById('preview-code');
        var mdSplit = document.getElementById('MD_Preview');
        var id = this.$refs.rteInstance.ej2Instances.getID() + 'html-view';
        var htmlPreview = this.$refs.rteInstance.$el.parentNode.querySelector('#' + id);
            if (e.targetItem === 'Maximize' && isNullOrUndefined(e.args)) {
                this.fullPreview({ mode: true, type: '' });
            } else if (!mdSplit.parentElement.classList.contains('e-overlay')) {
                if (e.targetItem === 'Minimize') {
                this.textArea.style.display = 'block';
                this.textArea.style.width = '100%';
                if (htmlPreview) { htmlPreview.style.display = 'none'; }
                mdSplit.classList.remove('e-active');
                mdsource.classList.remove('e-active');
                }
            this.markDownConversion();
            }
        },
        fullPreview: function(event){
            var mdsource = document.getElementById('preview-code');
            var mdSplit = document.getElementById('MD_Preview');
            var id = this.$refs.rteInstance.ej2Instances.getID() + 'html-view';
            var htmlPreview = this.$refs.rteInstance.$el.parentNode.querySelector('#' + id);
        if ((mdsource.classList.contains('e-active') || mdSplit.classList.contains('e-active')) && event.mode) {
            mdsource.classList.remove('e-active');
            mdSplit.classList.remove('e-active');
            this.textArea.style.display = 'block';
            this.textArea.style.width = '100%';
            htmlPreview.style.display = 'none';
        } else {
            mdsource.classList.add('e-active');
             mdSplit.classList.add('e-active');
            if (!htmlPreview) {
                htmlPreview = document.createElement('div');
                htmlPreview.id = id;
                htmlPreview.setAttribute('class', 'e-content');
                this.textArea.parentNode.appendChild(htmlPreview);
            }
            if (event.type === 'preview') {
                this.textArea.style.display = 'none';
                htmlPreview.classList.add('e-pre-source');
            } else {
                htmlPreview.classList.remove('e-pre-source');
                this.textArea.style.width = '50%';
            }
            htmlPreview.style.display = 'block';
            htmlPreview.innerHTML = marked(this.$refs.rteInstance.ej2Instances.contentModule.getEditPanel().value);
            mdsource.parentElement.title = 'Code View';
        }
    }
    },
    provide:{
        richtexteditor:[Toolbar, Link, Image, MarkdownEditor]
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

## Table

Rich Text Editor allows to insert Markdown table in edit panel with 2 X 2 rows and columns along with the heading.
To use table tool, add the `CreateTable` item in toolbar items.

### Insert table

To insert the table in Rich Text Editor, click the `table` toolbar option to insert the table into Rich Text Editor content and this is the default way in all the devices.
Please refer the below sample and code snippets to add the table in Markdown editor

{% tab template="rich-text-editor/markdown", isDefaultActive=true %}

```html
<template>
  <div id="defaultRTE">
    <ejs-richtexteditor id="preview" ref="rteInstance" :toolbarSettings="toolbarSettings" :created="created" :actionComplete='actionComplete' :editorMode="editorMode" :height="height">
In Rich Text Editor , you click the toolbar buttons to format the words and the changes
are visible immediately.
Markdown is not like that. When you format the word in Markdown format, you need to
add Markdown syntax to the word to indicate which words
and phrases should look different from each other
Rich Text Editor supports markdown editing when the editorMode set as **markdown** and using both *keyboard interaction* and *toolbar action*, you can apply the formatting to text.
We can add our own custom formation syntax for the Markdown formation, [sample link](https://ej2.syncfusion.com/home/).
The third-party library <b>Marked</b> is used in this sample to convert markdown into HTML content.
      </ejs-richtexteditor>
  </div>
</template>
    <style>
    .e-richtexteditor .e-rte-content .e-content{
        min-height: 150px;
    }
    .e-richtexteditor .e-rte-content textarea.e-content {
        float: left;
        border-right: 1px solid rgba(0, 0, 0, 0.12);
    }
    .e-richtexteditor .e-rte-content {
        overflow: hidden;
    }
    .e-md-preview::before {
        content: '\e345';
    }

    .e-rte-content .e-content.e-pre-source {
        width: 100%;
    }
    .e-icon-btn.e-active .e-md-preview.e-icons::before {
        content: '\e350';
    }
</style>
<script>
import Vue from "vue";
import { Browser, addClass, removeClass, isNullOrUndefined } from "@syncfusion/ej2-base";
import { RichTextEditorPlugin, Toolbar, Link, Image, MarkdownEditor } from "@syncfusion/ej2-vue-richtexteditor";
import { createElement, KeyboardEventArgs } from '@syncfusion/ej2-vue-base';

Vue.use(RichTextEditorPlugin);

export default {
    data: function() {
        return {
            textArea: '',
            height: '300px',
        toolbarSettings: {
            items: ['Bold', 'Italic', 'StrikeThrough', '|', 'Formats', 'OrderedList', 'UnorderedList', '|', 'CreateLink', 'Image', 'CreateTable', '|',
                { tooltipText: 'Preview', template: '<button id="preview-code" class="e-tbar-btn e-control e-btn e-icon-btn">' +
                    '<span class="e-btn-icon e-md-preview e-icons"></span></button>' },
                { tooltipText: 'Split Editor', template: '<button id="MD_Preview" class="e-tbar-btn e-control e-btn e-icon-btn">' +
                    '<span class="e-btn-icon e-view-side e-icons"></span></button>' }, 'FullScreen', '|', 'Undo', 'Redo']
        },
        editorMode: 'Markdown',
        };
    },
    methods: {
        created: function() {
            var script = document.createElement('script');
            script.src = 'https://cdn.jsdelivr.net/npm/marked/marked.min.js';
            document.head.appendChild(script);
            this.textArea = this.$refs.rteInstance.$el.parentNode.querySelector('.e-content');
            this.textArea.onkeyup = (Event) => {
                this.markDownConversion();
            };
            document.getElementById('preview-code').onclick = () => {
                this.fullPreview({ mode: true, type: 'preview'});
                 if (event.target.parentElement.classList.contains('e-active')) {
                    this.$refs.rteInstance.ej2Instances.disableToolbarItem(['Bold', 'Italic', 'StrikeThrough', 'Formats', 'OrderedList',
                     'UnorderedList', 'CreateLink', 'Image', 'CreateTable']);
                     event.target.parentElement.parentElement.nextElementSibling.classList.add('e-overlay');
                } else {
                    this.$refs.rteInstance.ej2Instances.enableToolbarItem(['Bold', 'Italic', 'StrikeThrough', 'Formats', 'OrderedList',
                     'UnorderedList', 'CreateLink', 'Image', 'CreateTable']);
                      event.target.parentElement.parentElement.nextElementSibling.classList.remove('e-overlay');
                }
            };
            document.getElementById('MD_Preview').onclick = () => {
                if (this.$refs.rteInstance.$el.classList.contains('e-rte-full-screen')) {
                    this.fullPreview({ mode: true, type: '' });
                }
                document.getElementById('preview-code').classList.remove('e-active');
                this.$refs.rteInstance.ej2Instances.showFullScreen();
            };
        },
        markDownConversion: function(){
        if (document.getElementById('MD_Preview').classList.contains('e-active')) {
            var id = this.$refs.rteInstance.ej2Instances.getID() + 'html-view';
            var htmlPreview = this.$refs.rteInstance.$el.parentNode.querySelector('#' + id);
            htmlPreview.innerHTML = marked(this.textArea.value);
        }
    },
    actionComplete: function(e) {
        var mdsource = document.getElementById('preview-code');
        var mdSplit = document.getElementById('MD_Preview');
        var id = this.$refs.rteInstance.ej2Instances.getID() + 'html-view';
        var htmlPreview = this.$refs.rteInstance.$el.parentNode.querySelector('#' + id);
            if (e.targetItem === 'Maximize' && isNullOrUndefined(e.args)) {
                this.fullPreview({ mode: true, type: '' });
            } else if (!mdSplit.parentElement.classList.contains('e-overlay')) {
                if (e.targetItem === 'Minimize') {
                this.textArea.style.display = 'block';
                this.textArea.style.width = '100%';
                if (htmlPreview) { htmlPreview.style.display = 'none'; }
                mdSplit.classList.remove('e-active');
                mdsource.classList.remove('e-active');
                }
            this.markDownConversion();
            }
        },
        fullPreview: function(event){
            var mdsource = document.getElementById('preview-code');
             var mdSplit = document.getElementById('MD_Preview');
            var id = this.$refs.rteInstance.ej2Instances.getID() + 'html-view';
            var htmlPreview = this.$refs.rteInstance.$el.parentNode.querySelector('#' + id);
        if ((mdsource.classList.contains('e-active') || mdSplit.classList.contains('e-active')) && event.mode) {
            mdsource.classList.remove('e-active');
            mdSplit.classList.remove('e-active');
            this.textArea.style.display = 'block';
            this.textArea.style.width = '100%';
            htmlPreview.style.display = 'none';
        } else {
            mdsource.classList.add('e-active');
             mdSplit.classList.add('e-active');
            if (!htmlPreview) {
                htmlPreview = document.createElement('div');
                htmlPreview.id = id;
                htmlPreview.setAttribute('class', 'e-content');
                this.textArea.parentNode.appendChild(htmlPreview);
            }
            if (event.type === 'preview') {
                this.textArea.style.display = 'none';
                htmlPreview.classList.add('e-pre-source');
            } else {
                htmlPreview.classList.remove('e-pre-source');
                this.textArea.style.width = '50%';
            }
            htmlPreview.style.display = 'block';
            htmlPreview.innerHTML = marked(this.$refs.rteInstance.ej2Instances.contentModule.getEditPanel().value);
            mdsource.parentElement.title = 'Code View';
        }
    }
    },
    provide:{
        richtexteditor:[Toolbar, Link, Image, MarkdownEditor]
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

### Changing table constants

The Markdown table constants can be changed for the table heading and the column names.

{% tab template="rich-text-editor/markdown", isDefaultActive=true %}

```html
<template>
  <div id="defaultRTE">
    <ejs-richtexteditor id="preview" ref="rteInstance" :toolbarSettings="toolbarSettings" :created="created" :actionComplete='actionComplete' :editorMode="editorMode" :height="height">
In Rich Text Editor , you click the toolbar buttons to format the words and the changes
are visible immediately.
Markdown is not like that. When you format the word in Markdown format, you need to
add Markdown syntax to the word to indicate which words
and phrases should look different from each other
Rich Text Editor supports markdown editing when the editorMode set as **markdown** and using both *keyboard interaction* and *toolbar action*, you can apply the formatting to text.
We can add our own custom formation syntax for the Markdown formation, [sample link](https://ej2.syncfusion.com/home/).
The third-party library <b>Marked</b> is used in this sample to convert markdown into HTML content.
      </ejs-richtexteditor>
  </div>
</template>
    <style>
    .e-richtexteditor .e-rte-content .e-content{
        min-height: 150px;
    }
    .e-richtexteditor .e-rte-content textarea.e-content {
        float: left;
        border-right: 1px solid rgba(0, 0, 0, 0.12);
    }
    .e-richtexteditor .e-rte-content {
        overflow: hidden;
    }
    .e-md-preview::before {
        content: '\e345';
    }

    .e-rte-content .e-content.e-pre-source {
        width: 100%;
    }
    .e-icon-btn.e-active .e-md-preview.e-icons::before {
        content: '\e350';
    }
</style>
<script>
import Vue from "vue";
import { Browser, addClass, removeClass, isNullOrUndefined } from "@syncfusion/ej2-base";
import { RichTextEditorPlugin, Toolbar, Link, Image, MarkdownEditor } from "@syncfusion/ej2-vue-richtexteditor";
import { createElement, KeyboardEventArgs } from '@syncfusion/ej2-vue-base';
import { L10n } from '@syncfusion/ej2-base';
L10n.load({
    'en-US': {
        'richtexteditor': {
            'TableHeadingText': 'Header',
            'TableColText': 'Cell'
         }
     }
});
Vue.use(RichTextEditorPlugin);

export default {
    data: function() {
        return {
            textArea: '',
            height: '300px',
        toolbarSettings: {
            items: ['Bold', 'Italic', 'StrikeThrough', '|', 'Formats', 'OrderedList', 'UnorderedList', '|', 'CreateLink', 'Image', 'CreateTable', '|',
                { tooltipText: 'Preview', template: '<button id="preview-code" class="e-tbar-btn e-control e-btn e-icon-btn">' +
                    '<span class="e-btn-icon e-md-preview e-icons"></span></button>' },
                { tooltipText: 'Split Editor', template: '<button id="MD_Preview" class="e-tbar-btn e-control e-btn e-icon-btn">' +
                    '<span class="e-btn-icon e-view-side e-icons"></span></button>' }, 'FullScreen', '|', 'Undo', 'Redo']
        },
        editorMode: 'Markdown',
        };
    },
    methods: {
        created: function() {
            var script = document.createElement('script');
            script.src = 'https://cdn.jsdelivr.net/npm/marked/marked.min.js';
            document.head.appendChild(script);
            this.textArea = this.$refs.rteInstance.$el.parentNode.querySelector('.e-content');
            this.textArea.onkeyup = (Event) => {
                this.markDownConversion();
            };
            document.getElementById('preview-code').onclick = () => {
                this.fullPreview({ mode: true, type: 'preview'});
                 if (event.target.parentElement.classList.contains('e-active')) {
                    this.$refs.rteInstance.ej2Instances.disableToolbarItem(['Bold', 'Italic', 'StrikeThrough', 'Formats', 'OrderedList',
                     'UnorderedList', 'CreateLink', 'Image', 'CreateTable']);
                     event.target.parentElement.parentElement.nextElementSibling.classList.add('e-overlay');
                } else {
                    this.$refs.rteInstance.ej2Instances.enableToolbarItem(['Bold', 'Italic', 'StrikeThrough', 'Formats', 'OrderedList',
                     'UnorderedList', 'CreateLink', 'Image', 'CreateTable']);
                      event.target.parentElement.parentElement.nextElementSibling.classList.remove('e-overlay');
                }
            };
            document.getElementById('MD_Preview').onclick = () => {
                if (this.$refs.rteInstance.$el.classList.contains('e-rte-full-screen')) {
                    this.fullPreview({ mode: true, type: '' });
                }
                document.getElementById('preview-code').classList.remove('e-active');
                this.$refs.rteInstance.ej2Instances.showFullScreen();
            };
        },
        markDownConversion: function(){
        if (document.getElementById('MD_Preview').classList.contains('e-active')) {
            var id = this.$refs.rteInstance.ej2Instances.getID() + 'html-view';
            var htmlPreview = this.$refs.rteInstance.$el.parentNode.querySelector('#' + id);
            htmlPreview.innerHTML = marked(this.textArea.value);
        }
    },
    actionComplete: function(e) {
        var mdsource = document.getElementById('preview-code');
        var mdSplit = document.getElementById('MD_Preview');
        var id = this.$refs.rteInstance.ej2Instances.getID() + 'html-view';
        var htmlPreview = this.$refs.rteInstance.$el.parentNode.querySelector('#' + id);
            if (e.targetItem === 'Maximize' && isNullOrUndefined(e.args)) {
                this.fullPreview({ mode: true, type: '' });
            } else if (!mdSplit.parentElement.classList.contains('e-overlay')) {
                if (e.targetItem === 'Minimize') {
                this.textArea.style.display = 'block';
                this.textArea.style.width = '100%';
                if (htmlPreview) { htmlPreview.style.display = 'none'; }
                mdSplit.classList.remove('e-active');
                mdsource.classList.remove('e-active');
                }
            this.markDownConversion();
            }
        },
        fullPreview: function(event){
            var mdsource = document.getElementById('preview-code');
             var mdSplit = document.getElementById('MD_Preview');
            var id = this.$refs.rteInstance.ej2Instances.getID() + 'html-view';
            var htmlPreview = this.$refs.rteInstance.$el.parentNode.querySelector('#' + id);
        if ((mdsource.classList.contains('e-active') || mdSplit.classList.contains('e-active')) && event.mode) {
            mdsource.classList.remove('e-active');
            mdSplit.classList.remove('e-active');
            this.textArea.style.display = 'block';
            this.textArea.style.width = '100%';
            htmlPreview.style.display = 'none';
        } else {
            mdsource.classList.add('e-active');
             mdSplit.classList.add('e-active');
            if (!htmlPreview) {
                htmlPreview = document.createElement('div');
                htmlPreview.id = id;
                htmlPreview.setAttribute('class', 'e-content');
                this.textArea.parentNode.appendChild(htmlPreview);
            }
            if (event.type === 'preview') {
                this.textArea.style.display = 'none';
                htmlPreview.classList.add('e-pre-source');
            } else {
                htmlPreview.classList.remove('e-pre-source');
                this.textArea.style.width = '50%';
            }
            htmlPreview.style.display = 'block';
            htmlPreview.innerHTML = marked(this.$refs.rteInstance.ej2Instances.contentModule.getEditPanel().value);
            mdsource.parentElement.title = 'Code View';
        }
    }
    },
    provide:{
        richtexteditor:[Toolbar, Link, Image, MarkdownEditor]
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

## Custom formation

The Rich Text Editor allows you to customize the markdown syntax by overriding its default syntax. Configure the customized markdown syntax using the [`formatter`](../api/rich-text-editor/#formatter)property.

This sample demonstrates how to customize tags of markdown formatting.

For example, apply  `+` to Unordered list, apply `1., 2., 3.` to Ordered list, for bold, `__`, and for italic `_`.

{% tab template="rich-text-editor/markdown", isDefaultActive=true %}

```html
<template>
  <ejs-richtexteditor ref="rteInstance" height="350" editorMode="Markdown" :value="value" :toolbarSettings="toolbarConfig" :created="created" :formatter="formatter">
  </ejs-richtexteditor>
</template>

<style>
  .e-richtexteditor .e-rte-content .e-content{
        min-height: 150px;
    }
    .e-richtexteditor .e-rte-content textarea.e-content {
        float: left;
        border-right: 1px solid rgba(0, 0, 0, 0.12);
    }
    .e-richtexteditor .e-rte-content {
        overflow: hidden;
    }
    .e-md-preview::before {
        content: '\e345';
    }

    .e-rte-content .e-content.e-pre-source {
        width: 100%;
    }
    .e-icon-btn.e-active .e-md-preview.e-icons::before {
        content: '\e350';
    } content: '\e350';
  }
</style>

<script>
  import Vue from 'vue';
  import { createElement, KeyboardEventArgs } from "@syncfusion/ej2-base";
  import { RichTextEditorPlugin, Toolbar, Link, Image, MarkdownEditor, MarkdownFormatter } from '@syncfusion/ej2-vue-richtexteditor';

  Vue.use(RichTextEditorPlugin);

  export default {
    data() {
      return {
        value: `***Overview***
  The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor used to create and edit the content and return valid HTML markup or markdown (MD) of the content. The editor provides a standard toolbar to format content using its commands. Modular library features to load the necessary functionality on demand. The toolbar contains commands to align the text, insert link, insert image, insert list, undo/redo operation, HTML view, and more.

  ***Key features***
  - *Mode*: Provides IFRAME and DIV mode.
  - *Module*: Modular library to load the necessary functionality on demand.
  - *Toolbar*: Provide a fully customizable toolbar.
  - *Editing*: HTML view to edit the source directly for developers.
  - *Third-party Integration*: Supports to integrate third-party library.
  - *Preview*: Preview the modified content before saving it.
  - *Tools*: Handling images, hyperlinks, video, uploads and more.
  - *Undo and Redo*: Undo/redo manager.
  - *Lists*:Creates bulleted and numbered list.`,
        toolbarConfig: {
          items: [
            'Bold', 'Italic', 'StrikeThrough', '|',
            'Formats', 'OrderedList', 'UnorderedList', '|',
            'CreateLink', 'Image', '|',
            {
              tooltipText: 'Preview',
              template: '<button id="preview-code" class="e-tbar-btn e-control e-btn e-icon-btn">' +
                '<span class="e-btn-icon e-md-preview e-icons"></span></button>'
            },
            '|', 'Undo', 'Redo'
          ]
        },
        formatter: new MarkdownFormatter({
            listTags: { 'OL': '1., 2., 3.', 'UL': '+ ' },
            formatTags: {
                'Blockquote': '> '
            },
            selectionTags: {'Bold': ' __ ',  'Italic': ' _ '}
        }),
      }
    },
    methods: {
      created: function() {
        var script = document.createElement('script');
        script.src = 'https://cdn.jsdelivr.net/npm/marked/marked.min.js';
        document.head.appendChild(script);
        this.textArea = this.$refs.rteInstance.$el.parentNode.querySelector('.e-content');
        this.textArea.onkeyup = (Event) => {
        this.markDownConversion();
        };
        document.getElementById('preview-code').onclick = () => {
          this.fullPreview({ mode: true, type: 'preview'});
          if (event.target.parentElement.classList.contains('e-active')) {
            this.$refs.rteInstance.ej2Instances.disableToolbarItem([
              'Bold', 'Italic', 'StrikeThrough', 'Formats', 'OrderedList',
              'UnorderedList', 'CreateLink', 'Image'
            ]);
            event.target.parentElement.parentElement.nextElementSibling.classList.add('e-overlay');
          } else {
            this.$refs.rteInstance.ej2Instances.enableToolbarItem([
              'Bold', 'Italic', 'StrikeThrough', 'Formats', 'OrderedList',
              'UnorderedList', 'CreateLink', 'Image'
            ]);
            event.target.parentElement.parentElement.nextElementSibling.classList.remove('e-overlay');
          }
        };
      },
      markDownConversion: function() {
        if (document.getElementById('MD_Preview').classList.contains('e-active')) {
          var id = this.$refs.rteInstance.ej2Instances.getID() + 'html-view';
          var htmlPreview = this.$refs.rteInstance.$el.querySelector('#' + id);
          htmlPreview.innerHTML = marked(this.textArea.value);
        }
      },
      fullPreview: function(event){
        var mdSource = document.getElementById('preview-code');
        var id = this.$refs.rteInstance.ej2Instances.getID() + 'html-view';
        var htmlPreview = this.$refs.rteInstance.$el.parentNode.querySelector('#' + id);
        if ((mdSource.classList.contains('e-active')) && event.mode) {
          mdSource.classList.remove('e-active');
          this.textArea.style.display = 'block';
          this.textArea.style.width = '100%';
          htmlPreview.style.display = 'none';
        } else {
          mdSource.classList.add('e-active');
          if (!htmlPreview) {
            htmlPreview = document.createElement('div');
            htmlPreview.id = id;
            htmlPreview.setAttribute('class', 'e-content');
            this.textArea.parentNode.appendChild(htmlPreview);
          }
          if (event.type === 'preview') {
            this.textArea.style.display = 'none';
            htmlPreview.classList.add('e-pre-source');
          } else {
            htmlPreview.classList.remove('e-pre-source');
            this.textArea.style.width = '50%';
          }
          htmlPreview.style.display = 'block';
          htmlPreview.innerHTML = marked(this.$refs.rteInstance.ej2Instances.contentModule.getEditPanel().value);
          mdSource.parentElement.title = 'Code View';
        }
      }
    },
    provide: {
      richtexteditor: [Toolbar, Link, Image, MarkdownEditor]
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

## See Also

* [How to integrate the third party library](./third-party-integration/)
* [How to change the editor mode](./editor-modes/#markdown-editor)