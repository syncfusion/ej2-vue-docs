---
title: "Rich Text Editor Editor modes"
component: "Rich Text Editor"
description: "This section for Syncfusion vue Rich Text Editor component explains the markdown and HTML editing of the content throughout the page."
---

# Editor modes

The Rich Text Editor component used to create and edit the content and return valid HTML markup or markdown (MD) of the content. It supports the following two editing formation.

* HTML editor
* Markdown editor

## HTML editor

Rich Text Editor is a WYSIWYG editing control for formatting the word content as HTML.

The HTML editing mode is the default mode in Rich Text Editor to format the content through the available toolbar items to return the valid HTML markup. Set the [editorMode](../api/rich-text-editor/#editormode) property as **HTML**.

> To create Rich Text Editor with HTML editing feature, inject the `HtmlEditor` module to the Rich Text Editor using the `RichTextEditor.Inject(HtmlEditor)` method.

{% tab template="rich-text-editor/getting-started", isDefaultActive=true %}

```html
<template>
  <ejs-richtexteditor ref="defaultRTE" :height="340">
    <p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
    <p><b>Key features:</b></p>
    <ul>
      <li>
        <p>Provides IFRAME and DIV modes</p>
      </li>
      <li>
        <p>Capable of handling markdown editing.</p>
      </li>
      <li>
        <p>Contains a modular library to load the necessary functionality on demand.</p>
      </li>
      <li>
        <p>Provides a fully customizable toolbar.</p>
      </li>
      <li>
        <p>Provides HTML view to edit the source directly for developers.</p>
      </li>
      <li>
        <p>Supports third-party library integration.</p>
      </li>
      <li>
        <p>Allows preview of modified content before saving it.</p>
      </li>
      <li>
        <p>Handles images, hyperlinks, video, hyperlinks, uploads, etc.</p>
      </li>
    </ul>
  </ejs-richtexteditor>
</template>

<script>
  import Vue from 'vue';
  import { RichTextEditorPlugin, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-vue-richtexteditor';

  Vue.use(RichTextEditorPlugin);

  export default {
    provide: {
      richtexteditor: [Toolbar, Link, Image, HtmlEditor, QuickToolbar]
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

## Markdown editor

Set the [editorMode](../api/rich-text-editor/#editormode) property as **Markdown**, to create or edit the content and apply formatting to view markdown formatted content.

The third-party library such as `Marked` or any other library is used to convert markdown into HTML content.

* Supported tags are `h6`, `h5`, `h4`, `h3`, `h2`, `h1`, `blockquote`, `pre`, `p`, `OL`, and `UL`.
* Supported selection tags are `Bold`, `Italic`, `StrikeThrough`, `InlineCode`, `SubScript`, `SuperScript`, `UpperCase`, and `LowerCase`.

{% tab template="rich-text-editor/markdown", isDefaultActive=true %}

```html
<template>
  <ejs-richtexteditor ref="rteInstance" :height="350" editorMode="Markdown" :value="value" :toolbarSettings="toolbarConfig" :created="created">
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
  }
</style>

<script>
  import Vue from 'vue';
  import { createElement, KeyboardEventArgs } from "@syncfusion/ej2-base";
  import { RichTextEditorPlugin, Toolbar, Link, Image, MarkdownEditor } from '@syncfusion/ej2-vue-richtexteditor';

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
        }
      }
    },
    methods: {
      created: function() {
        this.textArea = this.$refs.rteInstance.$el.querySelector('.e-content');
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
          var id = this.$refs.rteInstance.getID() + 'html-view';
          var htmlPreview = this.$refs.rteInstance.$el.querySelector('#' + id);
          htmlPreview.innerHTML = marked(this.textArea.value);
        }
      },
      fullPreview: function(event){
        var mdSource = document.getElementById('preview-code');
        var id = this.$refs.rteInstance.getID() + 'html-view';
        var htmlPreview = this.$refs.rteInstance.$el.querySelector('#' + id);
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

> To create Rich Text Editor with Markdown editing feature, inject the `MarkdownEditor` module to the Rich Text Editor using the `RichTextEditor.Inject(MarkdownEditor)` method.

For further details on Markdown editing, refer to the [`Markdown`](./markdown/) section.

## See Also

* [How to integrate the third party library](./third-party-integration/)
* [How to render the iframe](./iframe/)