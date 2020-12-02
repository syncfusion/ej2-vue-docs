---
title: "Vue Rich Text Editor Insert link"
component: "Rich Text Editor"
description: "This section for Syncfusion vue Rich Text Editor component demonstrates on how to add or remove hyperlinks with customized options."
---

# Link

A hyperlink can be insert into the editor for quick access to the related information. The hyperlink itself can be a text or an image.

## Insert link

Point the cursor anywhere within the editor where you would like to insert the link. It is also possible to select a text or an image within the editor and can be converted to the hyperlink. Click the Insert HyperLink tool on the toolbar. The Insert Link Dialog will be open. The dialog has the following options.

```typescript
To use use image and link tool, inject `ImageService, LinkService` in the provider section of `AppModule`.
```

| Options | Description |
|----------------|--------------------------------------|
| Web Address | Type or paste the destination for the link you are creating |
| Display Text | Type or edit the required text that you want to display text for the link|
| Tooltip | To display additional helpful information when you place the pointer on the hyperlink, type the required text in the “Tooltip” field. |
| Open Link in New Window | Specify whether, the given link will be open in new window or not |

{% tab template="rich-text-editor/markdown", isDefaultActive=true %}

```html
<template>
<div>
<div class="control-section">
    <div class="sample-container">
        <div class="default-section">
        <ejs-richtexteditor ref="rteObj" :toolbarSettings="toolbarSettings"><p>Rich
        Text Editorallows to insert images from online source as well as local
            computer where you want to insert the image in your content.</p>
            <p><b>Get started Quick Toolbar to click on the image</b></p>
            <p>It is possible to add custom style on the selected image inside the Rich Text Editor through quick toolbar.</p>
        </ejs-richtexteditor>
        </div>
    </div>
</div>
</div>
</template>
<script>
import Vue from "vue";
import { RichTextEditorPlugin, Toolbar, Image,  Link, HtmlEditor } from "@syncfusion/ej2-vue-richtexteditor";

Vue.use(RichTextEditorPlugin);

export default {
    data: function() {
        return {
            toolbarSettings: {
                items: ['CreateLink']
            }
        };
    },
    provide:{
        richtexteditor:[Toolbar, Image,  Link, HtmlEditor]
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

> The Rich Text Editor link tool validates the URLs, as you type in the Web Address. URLs considered invalid will be highlighted with red color by clicking the insert button in the `Insert Link` dialog.

## Remove link

If you want to remove a hyperlink from a text or image, select the text or image with the hyperlink and click “Remove Hyperlink” tool from toolbar. It will keep the text or image.

## Auto-link

When you type URL and Enter key to the Rich Text Editor, the typed URL will be automatically changed into the hyperlink.

## Manipulation

Add the custom tools on the selected link inside the Rich Text Editor through the quick toolbar.

![link-quick](./images/link-quick.png)

The quick toolbar for the Link has the following options.

| Tools | Description |
|----------------|--------------------------------------|
| Open | The given link page, will be open in new window. |
| Edit Link | Used to edit the link in the Rich Text Editor content. |
| Remove Link | Used to remove link from the content of Rich Text Editor. |
| Custom Tool | Used to add the custom options in the quick toolbar. |

{% tab template="rich-text-editor/markdown", isDefaultActive=true %}

```html
<template>
<div>
<div class="control-section">
    <div class="sample-container">
        <div class="default-section">
        <ejs-richtexteditor ref="rteObj" :toolbarSettings="toolbarSettings"><p>Rich
        Text Editor allows to insert images from online source as well as local
            computer where you want to insert the image in your content.</p>
            <p><b>Get started Quick Toolbar to click on the image</b></p>
            <p>It is possible to add custom style on the selected image inside the Rich Text Editor through quick toolbar.</p>
        </ejs-richtexteditor>
        </div>
    </div>
</div>
</div>
</template>
<script>
import Vue from "vue";
import { RichTextEditorPlugin, Toolbar, Image,  Link, HtmlEditor, QuickToolbar } from "@syncfusion/ej2-vue-richtexteditor";

Vue.use(RichTextEditorPlugin);

export default {
    data: function() {
        return {
            toolbarSettings: {
                items: ['CreateLink']
            }
        };
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

## See Also

* [How to edit the quick toolbar settings](./toolbar/#quick-inline-toolbar)
* [How to insert image link editing option in the toolbar items](./image/#image-with-link)