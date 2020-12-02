---
title: "Vue Rich Text Editor Miscellaneous"
component: "Rich Text Editor"
description: "This section for Syncfusion vue Rich Text Editor component explains on how to directly edit HTML code via `Source View` in the text area."
---

# Miscellaneous

## Placeholder

Specifies the placeholder for the Rich Text Editor’s content used when the Rich Text Editor body is empty through the [placeholder](../api/rich-text-editor/#placeholder) property.

Through the `e-rte-placeholder` class to define our custom font family, font color, and styles to the placeholder text.

``` css
  .e-richtexteditor .e-rte-placeholder {
    font-family: monospace;
  }
```

{% tab template="rich-text-editor/getting-started", isDefaultActive=true %}

```html
<template>
  <ejs-richtexteditor ref="defaultRTE" :height="200" placeholder="Type Something">
  </ejs-richtexteditor>
</template>

<style>
  .e-richtexteditor .rte-placeholder {
    font-family: monospace;
  }
</style>

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

## Character count

The Rich Text Editor automatically counts the number of characters in the content are while typing using the [showCharCount](../api/rich-text-editor/#showcharcount) property. The characters count displayed at the bottom of the editor. You can limit the number of characters in your content using the [maxLength](../api/rich-text-editor/#maxlength) property. By default, the editor sets the characters limit value is infinity.

The character count color will be modified based on the characters in the Rich Text Editor.

| **Status** | **Description** |
| --- | --- |
| Normal | Till 70% of given maxLength value, character count color is black. |
| Warning | Once the number of character count in the Rich Text Editor reached 70% of given maxLength value, the character count color will be orange, indicating that, the count value going to reach the maximum count. |
| Error | Once the number of character count in the Rich Text Editor reached 90% of given maxLength value, the character count color will be red, indicating that, the count value reached the maximum count. |

> To create Rich Text Editor with character count feature, inject the Count module to the Rich Text Editor using the `RichTextEditor.Inject(Count)` method.

{% tab template="rich-text-editor/getting-started", isDefaultActive=true %}

```html
<template>
  <ejs-richtexteditor ref="defaultRTE" :height="340" :showCharCount="showCharCount"
  :maxLength="maxLength" :value="value"></ejs-richtexteditor>
</template>

<script>
  import Vue from 'vue';
  import { RichTextEditorPlugin, Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-vue-richtexteditor';

  Vue.use(RichTextEditorPlugin);

  export default {
     data: function() {
      return {
        showCharCount: true,
        maxLength: 2000,
        value: `<p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
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
          </ul>`,
      }
    },
    provide: {
      richtexteditor: [Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar]
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

## Code view

Rich Text Editor includes the ability for users to directly edit HTML code via `Source View` in the text area. If you made any modification in Source view directly, the changes will be reflected in the Rich Text Editor's content. So, the users will have more flexibility over the content they have created.

{% tab template="rich-text-editor/code-mirror", isDefaultActive=true %}

```html
<template>
  <ejs-richtexteditor ref="rteObj" :value="value" :height="340" :toolbarSettings="toolbarSettings" :actionComplete="actionCompleteHandler" :showCharCount="showCharCount" :maxLength="maxLength"></ejs-richtexteditor>
</template>

<script>
  import Vue from "vue";
  import CodeMirror from "https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.3.0/codemirror.js";
  import CodeMirror from "https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.3.0/mode/css/css.js";
  import CodeMirror from "https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.3.0/mode/xml/xml.js";
  import CodeMirror from "https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.3.0/mode/htmlmixed/htmlmixed.js";
  import CodeMirror from "https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.3.0/mode/javascript/javascript.js";
  import { Browser, addClass, removeClass } from "@syncfusion/ej2-base";
  import { RichTextEditorPlugin, Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar } from "@syncfusion/ej2-vue-richtexteditor";

  Vue.use(RichTextEditorPlugin);

  export default {
    data: function() {
      return {
        showCharCount: true,
        myCodeMirror: '',
        value: `<p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
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
          </ul>`,
        maxLength: 2000,
        toolbarSettings: {
          items: ['Bold', 'Italic', 'Underline', 'StrikeThrough',
            'FontName', 'FontSize', 'FontColor', 'BackgroundColor',
            'LowerCase', 'UpperCase', '|',
            'Formats', 'Alignments', 'OrderedList', 'UnorderedList',
            'Outdent', 'Indent', '|',
            'CreateLink', 'Image', '|', 'ClearFormat', 'Print', 'SourceCode',
            'FullScreen', '|', 'Undo', 'Redo'
          ]
        },
      };
    },
    methods: {
      mirrorConversion: function(e) {
        var textArea = this.$refs.rteObj.ej2Instances.contentModule.getEditPanel();
        var id = this.$refs.rteObj.getID() +  'mirror-view';
        var mirrorView = this.$refs.rteObj.$el.querySelector('#' + id);
        var charCount = this.$refs.rteObj.$el.querySelector('.e-rte-character-count');
        if (e.targetItem === 'Preview') {
          textArea.style.display = 'block';
          mirrorView.style.display = 'none';
          textArea.innerHTML = this.myCodeMirror.getValue();
          charCount.style.display = 'block';
        } else {
          if (!mirrorView) {
            mirrorView = document.createElement('div', { className: 'e-content' });
            mirrorView.id = id;
            textArea.parentNode.appendChild(mirrorView);
          } else {
            mirrorView.innerHTML = '';
          }
          textArea.style.display = 'none';
          mirrorView.style.display = 'block';
          this.renderCodeMirror(mirrorView, this.$refs.rteObj.ej2Instances.value);
          charCount.style.display = 'none';
        }
      },
      renderCodeMirror: function(mirrorView, content) {
        this.myCodeMirror = CodeMirror(mirrorView, {
          value: content,
          lineNumbers: true,
          mode: 'text/html',
          lineWrapping: true,
        });
      },
      actionCompleteHandler: function(e) {
        if (e.targetItem && (e.targetItem === 'SourceCode' || e.targetItem === 'Preview')) {
          this.$refs.rteObj.ej2Instances.sourceCodeModule.getPanel().style.display = 'none';
          this.mirrorConversion(e);
        }
        else {
          var proxy = this;
          setTimeout(function () {
            proxy.$refs.rteObj.ej2Instances.toolbarModule.refreshToolbarOverflow();
          }, 400);
        }
      }
    },
    provide:{
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
@import "https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.3.0/codemirror.min.css";

  .e-code-mirror::before {
    content: '\e345';
  }

  .e-html-preview::before {
    content: '\e350';
  }

  .CodeMirror-linenumber,
  .CodeMirror-gutters {
    display: none;
  }
</style>

```

{% endtab %}

## Undo/Redo manager

Undo and redo tools allow you to edit the text by disregard/cancel the recently made changes and restore it to previous state. It is a useful tool to restore the performed action which got changed by mistake. By default, upto 30 actions can be undo/redo in the editor.

To undo and redo operations, do one of the following:
* Press the undo/redo button on the toolbar.
* Press the **Ctrl + Z/Ctrl + Y** combination on the keyboard.

Customize the undo/redo step count using the [undoRedoSteps](../api/rich-text-editor/#undoredosteps) property. By default, undo/redo actions take 300ms time interval for store the action to the undoRedoManager. The time interval can be customized by using the [undoRedoTimer](../api/rich-text-editor/#undoredotimer).

{% tab template="rich-text-editor/getting-started", isDefaultActive=true %}

```html
<template>
  <ejs-richtexteditor ref="defaultRTE" :height="340" :toolbarSettings="toolbarData" :UndoRedoSteps="50" :UndoRedoTimer="400">
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
    data() {
      return {
        toolbarData: {
          items: ['Undo', 'Redo']
        }
      }
    },
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

## Prevention of cross-site scripting (XSS)

The Rich Text Editor allows the users to edit the content with security by preventing cross-site
scripting (XSS). By default, provided built-in support to remove the elements from editor content, which cause XSS
attack. The editor removes the elements based on the attributes if it is possible to execute script.

In the following sample, removed `script` tag and `onmouseover` attribute from content of the Rich Text Editor.

{% tab template="rich-text-editor/getting-started", isDefaultActive=true %}

```html
<template>
   <ejs-richtexteditor :value="value"></ejs-richtexteditor>
</template>

<script>
  import Vue from 'vue';
  import { RichTextEditorPlugin, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-vue-richtexteditor';

  Vue.use(RichTextEditorPlugin);

  export default {
    data() {
      return {
        value: `<div onmouseover='javascript:alert(1)'>Prevention of Cross Sit Scripting (XSS) </div> <script>alert('hi')<\/script>`
      }
    },
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

> It is only applicable to editorMode as HTML.

### Custom cross-site scripting

You can also filter the elements and attributes additionally, which cause the XSS attack through
[`beforeSanitizeHtml`](../api/rich-text-editor/#beforesanitizehtml) event. Return the value from the event argument `helper` function to apply in the editor. To prevent the built-in support and make own cross-site scripting rules, set `cancel` argument to true.

The following sample demonstrates how to filter `script` tag from value.

{% tab template="rich-text-editor/getting-started", isDefaultActive=true %}

```html
<template>
   <ejs-richtexteditor :value="value" :beforeSanitizeHtml="beforeSanitizeHtml"></ejs-richtexteditor>
</template>

<script>
  import Vue from 'vue';
  import { RichTextEditorPlugin, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-vue-richtexteditor';
  import { detach } from "@syncfusion/ej2-base";

  Vue.use(RichTextEditorPlugin);

  export default {
    data() {
      return {
        value: `<div>Prevention of Cross Sit Scripting (XSS) </div> <script>alert('hi')<\/script>`
      }
    },
    provide: {
      richtexteditor: [Toolbar, Link, Image, HtmlEditor, QuickToolbar]
    },
    methods: {
    beforeSanitizeHtml: function(e) {
      e.helper = value => {
        e.cancel = true;
        let temp = document.createElement("div");
        temp.innerHTML = value;
        let scriptTag = temp.querySelector("script");
        if (scriptTag) {
          detach(scriptTag);
        }
        return temp.innerHTML;
      };
    }
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

## Resizable support

This feature allows the editor to be resized dynamically. The users can enable or disable this feature using the `enableResize` property in the Rich Text Editor. If `enableResize` is set to true, the Rich Text Editor component creates grip at the bottom right corner, which allows resizing the component in the diagonal direction. The following sample demonstrates the resizable feature.

### Enabling the resizable support

To render the Rich Text Editor in the resizable mode, set the `enableResize` property to true. The above feature is built as module and hence the `Resize` module needs to be included in your application.

{% tab template="rich-text-editor/toolbar", isDefaultActive=true %}

```html
<template>
    <div class="control-section">
        <div class="sample-container">
            <div class="default-section">
            <ejs-richtexteditor :enableResize="true"><p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content.
                    Users can format their content using standard toolbar commands.</p>
            </ejs-richtexteditor>
            </div>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { RichTextEditorPlugin, Toolbar, Link, Image, Resize, HtmlEditor } from "@syncfusion/ej2-vue-richtexteditor";

Vue.use(RichTextEditorPlugin);

export default {
    provide:{
        richtexteditor:[Toolbar, Image, Resize HtmlEditor, Link]
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

### Specifying the Minimum and Maximum width and height for Resize

To have a restricted resizable area for the Rich Text Editor, you need to specify the min-width, max-width, min-height, and max-height CSS properties for the control's wrapper element. By default, the control is capable of resizing upto the current viewport. The `e-richtexteditor` CSS class will be available in the component's wrapper and can be used for applying the above mentioned styles.

{% tab template="rich-text-editor/toolbar", isDefaultActive=true %}

```html
<template>
    <div class="control-section">
        <div class="sample-container">
            <div class="default-section">
            <ejs-richtexteditor :enableResize="true"><p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content.
                    Users can format their content using standard toolbar commands.</p>
            </ejs-richtexteditor>
            </div>
        </div>
    </div>
</template>
<style>
  .e-richtexteditor {
      min-width: 200px;
      max-width: 800px;
      min-height: 100px;
      max-height: 300px;
  }
</style>
<script>
import Vue from "vue";
import { RichTextEditorPlugin, Toolbar, Link, Image, Resize, HtmlEditor } from "@syncfusion/ej2-vue-richtexteditor";

Vue.use(RichTextEditorPlugin);

export default {
    provide:{
        richtexteditor:[Toolbar, Image, Resize HtmlEditor, Link]
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
