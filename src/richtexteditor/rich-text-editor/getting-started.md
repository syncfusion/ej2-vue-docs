---
title: "Rich Text Editor Getting started"
component: "Rich Text Editor"
description: "This section explains how to create a Syncfusion vue Rich Text Editor component and configure it's functionalities in vue application."
---

# Getting started

This section explains the steps to create a simple **RichTextEditor** and demonstrates the basic usage of the Rich Text Editor component in a Vue environment.

## Dependencies

The following list of dependencies are required to use the Rich Text Editor.

```js
|-- @syncfusion/ej2-vue-richtexteditor
    |-- @syncfusion/ej2
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-splitbuttons
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-vue-base

```

## Installation and configuration

You can use [`Vue CLI`](https://github.com/vuejs/vue-cli) to setup your vue applications.
To install Vue CLI use the following command.

```bash
npm install -g @vue/cli

npm install -g @vue/cli-init
```

Start a new project using below Vue CLI command.

```bash
vue init webpack-simple quickstart

cd quickstart

npm install

```

Install Syncfusion `RichTextEditor` packages using below command. Also need to install dependency packages as mentioned at top of this documentation.

```bash
npm install @syncfusion/ej2-vue-richtexteditor --save
```

## Registering Rich Text Editor component using `Vue.use()`

Import the Rich Text Editor Plugin from the Essential JS 2 Vue package and register the same using `Vue.use()` with Component Plugin as its argument.

Refer to the code snippet given below.

```typescript
import Vue from 'vue';
import { RichTextEditorPlugin } from '@syncfusion/ej2-vue-richtexteditor';

Vue.use(RichTextEditorPlugin);

export default {}
```

> By registering component plugin in Vue, all child directives are also globally registered.
We can also use `Vue.Component()` to register `RichTextEditor`.
Refer [here](../base/getting-started/#registering-vue-component) to know more about component registration.

## Adding CSS Reference

Add Rich Text Editor component's styles as given below in `<style>` section of the `App.vue` file.

```html
<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
</style>
```

## Adding Rich Text Editor component

Initialize the EJ2 Vue Rich Text Editor by adding `<ejs-richtexteditor>` into the `<template>` section of the `App.vue` file.

```html
<template>
    <ejs-richtexteditor ref="defaultRTE" :height="400">
        <p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content.Users can format their content using standard toolbar commands.</p>
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
            <li><p>Contains undo/redo manager.</p></li>
            <li><p>Creates bulleted and numbered lists.</p></li>
        </ul>
    </ejs-richtexteditor>
</template>

<script>
    import Vue from "vue";
    import { RichTextEditorPlugin, Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar } from "@syncfusion/ej2-vue-richtexteditor";

    Vue.use(RichTextEditorPlugin);

    export default {
        provide: {
            richtexteditor:[Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar]
        }
    }
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
</style>
```

### Initialize from `<div>` element

Rich Text Editor can be initialized on div element.

{% tab template="rich-text-editor/getting-started", isDefaultActive=true %}

```html
<template>
  <div id="defaultRTE">
    <ejs-richtexteditor ref="defaultRTE" :height="340">
        <p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content.Users can format their content using standard toolbar commands.</p>
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
</template>

<script>
    import Vue from 'vue';
    import { RichTextEditorPlugin, Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-vue-richtexteditor';

    Vue.use(RichTextEditorPlugin);

    export default {
        provide: {
            richtexteditor:[Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar]
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

### Initialize from `<IFRAME>` element

The Rich Text Editor’s content is placed in an iframe and isolated from the rest of the page.

Initialize the Rich Text Editor on div element and set the `enable` field of `iframeSettings` property as true.

{% tab template="rich-text-editor/getting-started", isDefaultActive=true %}

```html
<template>
    <ejs-richtexteditor ref="defaultRTE" :height="350" :iframeSettings="iframeConfig">
        <p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content.Users can format their content using standard toolbar commands.</p>
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
</template>

<script>
    import Vue from 'vue';
    import { RichTextEditorPlugin, Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-vue-richtexteditor';

    Vue.use(RichTextEditorPlugin);

    export default {
        data() {
            return {
                iframeConfig: {
                    enable: true
                }
            }
        },
        provide: {
            richtexteditor:[Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar]
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

## Module injection

To create Rich Text Editor with additional features, inject the required modules. The following modules are used to extend Rich Text Editor's basic functionality.

* `Toolbar` - Inject this module to use Toolbar feature.
* `Link` - Inject this module to use link in Rich Text Editor feature.
* `Image`- Inject this module to use image in Rich Text Editor feature.
* `Count` - Inject this module to use character count in Rich Text Editor.
* `MarkdownEditor`-Inject this module to use Rich Text Editor as markdown editor.
* `HtmlEditor` - Inject this module to use Rich Text Editor as html editor.
* `QuickToolbar` - Inject this module to use quick toolbar feature for the target element.

These modules should be injected into the Rich Text Editor using the `RichTextEditor.Inject` method.

## Configure the toolbar

Configure the toolbar with the tools using items field of the [`toolbarSettings`](../api/rich-text-editor/toolbarSettings/#toolbarsettings) property as your application requires.

{% tab template="rich-text-editor/getting-started", isDefaultActive=true %}

```html
<template>
<div>
<div class="control-section">
    <div class="sample-container">
        <div class="default-section">
        <ejs-richtexteditor :height="340"><p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
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

> `|` and `-` can insert a vertical and horizontal separator lines in the toolbar.

## Insert images and links

The [`image`](../api/rich-text-editor/image/#image) module inserts an image into Rich Text Editor’s content area, and the [`link`](../api/rich-text-editor/link/#link) module links external resources such as website URLs, to selected text in the Rich Text Editor’s content, respectively.

The link inject module adds a link icon to the toolbar and the image inject module adds an image icon to the toolbar.

Specifies the items to be rendered in the quick toolbar based on the target element such image, link and text element. The quick toolbar opens to customize the element by clicking the target element.

{% tab template="rich-text-editor/getting-started", isDefaultActive=true %}

```html
<template>
<div>
<div class="control-section">
    <div class="sample-container">
        <div class="default-section">
        <ejs-richtexteditor ref="rteObj" :quickToolbarSettings="quickToolbarSettings" :height="340" :toolbarSettings="toolbarSettings">
        <p>The Rich Text Editor is WYSIWYG ("what you see is what you get") editor useful to create and edit content, and return the valid <a href="https://ej2.syncfusion.com/home/" target="_blank">HTML markup</a> or
        <a href="https://ej2.syncfusion.com/home/" target="_blank">markdown</a>
        of the content</p>
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
import { RichTextEditorPlugin, Toolbar, Image, Link, HtmlEditor, QuickToolbar } from "@syncfusion/ej2-vue-richtexteditor";

Vue.use(RichTextEditorPlugin);

export default {
     data: function() {
        return {
        height: 400,
        quickToolbarSettings: {
            image: [
                'Replace', 'Align', 'Caption', 'Remove', 'InsertLink', 'OpenImageLink', '-',
                'EditImageLink', 'RemoveImageLink', 'Display', 'AltText', 'Dimension',
            ]
        },
        toolbarSettings: {
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
        richtexteditor:[Toolbar, Image, Link, HtmlEditor, QuickToolbar]
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

## Retrieve the formatted content

To retrieve the editor contents, use [`value`](../api/rich-text-editor/#value) property of Rich Text Editor.

```typescript
  var rteValue = this.$refs.rteObj.ej2Instances.value;
```

Or, you can use the public method, [`getHtml`](../api/rich-text-editor/#gethtml) to retrieve the Rich Text Editor content.

```typescript
  var rteValue = this.$refs.rteObj.ej2Instances.getHtml();
```

To fetch the Rich Text Editor's text content, use [`getText`](../api/rich-text-editor/#gettext) method of Rich Text Editor.

```typescript
  var rteValue = this.$refs.rteObj.ej2Instances.getText();
```

## Run the Application

Now run the `npm run dev` command in the console, it will build your application and open in the browser.

{% tab template="rich-text-editor/getting-started", isDefaultActive=true %}

```html
<template>
<div>
<div class="control-section">
    <div class="sample-container">
        <div class="default-section">
        <ejs-richtexteditor ref="rteObj":quickToolbarSettings="quickToolbarSettings" :height="340" :toolbarSettings="toolbarSettings">
        <p>The Rich Text Editor is WYSIWYG ("what you see is what you get") editor useful to create and edit content,and return the valid <a href="https://ej2.syncfusion.com/home/" target="_blank">HTML markup</a> or
        <a href="https://ej2.syncfusion.com/home/" target="_blank">markdown</a>
        of the content</p>
        <p><b>Key features:</b></p>
          <ul><li><p>Provides IFRAME and DIV modes</p></li>
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
import { RichTextEditorPlugin, Toolbar, Image, Link, HtmlEditor, QuickToolbar } from "@syncfusion/ej2-vue-richtexteditor";

Vue.use(RichTextEditorPlugin);

export default {
     data: function() {
        return {
        height: 400,
        quickToolbarSettings: {
            image: [
                'Replace', 'Align', 'Caption', 'Remove', 'InsertLink', 'OpenImageLink', '-',
                'EditImageLink', 'RemoveImageLink', 'Display', 'AltText', 'Dimension',
            ],
            link: ['Open', 'Edit', 'UnLink']
        },
        toolbarSettings: {
            items: ['Bold', 'Italic', 'Underline', 'StrikeThrough',
            'FontName', 'FontSize', 'FontColor', 'BackgroundColor',
            'LowerCase', 'UpperCase', '|',
            'Formats', 'Alignments', 'OrderedList', 'UnorderedList',
            'Outdent', 'Indent', '|',
            'CreateLink', 'Image', '|', 'ClearFormat', 'Print',
            'SourceCode', 'FullScreen', '|', 'Undo', 'Redo']
        },
        };
    },
    provide:{
        richtexteditor:[Toolbar, Image, Link, HtmlEditor, QuickToolbar]
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

## Add content using valueTemplate property

Rich Text Editor content can be added using valueTemplate property as given below

{% tab template="rich-text-editor/getting-started", isDefaultActive=true %}

```html
<template>
  <div id="defaultRTE">
    <ejs-richtexteditor :valueTemplate="vueTemplate"  ref="defaultRTE" :height="340">
    </ejs-richtexteditor>
  </div>
</template>
<script>
    import Vue from 'vue';
    import { RichTextEditorPlugin, Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-vue-richtexteditor';
    Vue.use(RichTextEditorPlugin);

        var templateContent  = Vue.component("templateContent", {
            template: '<p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content.Users can format their content using standard toolbar commands.</p>',
            data() {
                return {
                    data: {}
                };
            }
        });

    export default {
         data: function() {
    return {
         vueTemplate: function() {
                return { template: templateContent };
               }
            };
        },
        provide: {
            richtexteditor:[Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar]
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

* [How to change the editor type](./editor-modes/)
* [How to render the iframe](./iframe/)
* [How to render the toolbar in inline mode](./inline-mode/)