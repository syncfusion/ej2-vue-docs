---
title: "Hyperlink"
component: "DocumentEditor"
description: "Learn how to insert, delete, or navigate links in JavaScript document editor."
---

# Working with Hyperlink

Document editor supports hyperlink field. You can link a part of the document content to Internet or file location, mail address, or any text within the document.

## Navigate a hyperlink

Document editor triggers ‘requestNavigate’ event whenever user clicks Ctrl key or tap a hyperlink within the document. This event provides necessary details about link type, navigation URL, and local URL (if any) as arguments, and allows you to easily customize the hyperlink navigation functionality. Refer to the following example.

{% tab template="document-editor/link", isDefaultActive=false %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-documenteditor ref="documenteditor" :enableSelection='true' :isReadOnly='false' v-bind:requestNavigate="onRequestNavigate" style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin, Selection, RequestNavigateEventArgs } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);

export default {
    data: function() {
        return {
        };
    },
    provide: {
        DocumentEditor : [Selection]
    }
    methods: {
        onRequestNavigate: function(args: RequestNavigateEventArgs) {
           if (args.linkType !== 'Bookmark') {
                let link: string = args.navigationLink;
                if (args.localReference.length > 0) {
                link += '#' + args.localReference;
                }
                window.open(link);
                args.isHandled = true;
            }
        }
    }
}
</script>
<style>
 @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

If the selection is in hyperlink, trigger this event by calling `navigateHyperlink` method of `Selection` instance. Refer to the following example.

> `documenteditor.selection.navigateHyperlink()`;

## Copy link

Document editor copies link text of a hyperlink field to the clipboard if the selection is in hyperlink. Refer to the following example.

> `documenteditor .selection.copyHyperlink();`

## Add hyperlink

To create a basic hyperlink in the document, press `ENTER` / `SPACEBAR` / `SHIFT + ENTER` / `TAB` key after typing the address, for instance `http://www.google.com`. Document editor automatically converts this address to a hyperlink field. The text can be considered as a valid URL if it starts with any of the following.

>`http://`<br>
>`https://`<br>
>`file:///`<br>
>`www.`<br>
>`mailto:`<br>

Refer to the following example.

{% tab template="document-editor/link", isDefaultActive=false %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-documenteditor ref="documenteditor" :enableSelection='true' :isReadOnly='false' :enableEditor='true' v-bind:requestNavigate="onRequestNavigate" style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin, Selection, Editor, RequestNavigateEventArgs } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);

export default {
    data: function() {
        return {
        };
    },
    provide: {
        DocumentEditor : [Selection, Editor]
    }
    methods: {
        onRequestNavigate: function(args: RequestNavigateEventArgs) {
           if (args.linkType !== 'Bookmark') {
                let link: string = args.navigationLink;
                if (args.localReference.length > 0) {
                link += '#' + args.localReference;
                }
                window.open(link);
                args.isHandled = true;
            }
        }
    }
}
</script>
<style>
 @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

## Remove hyperlink

To remove link from hyperlink in the document, press Backspace key at the end of a hyperlink. By removing the link, it will be converted as plain text. You can use `removeHyperlink` method of `Editor` instance if the selection is in hyperlink. Refer to the following example.

> `this.$refs.documenteditor.ej2Instances.editor.removeHyperlink()`;

## Hyperlink dialog

Document editor provides dialog support to insert or edit a hyperlink. Refer to the following example.

{% tab template="document-editor/link", isDefaultActive=false %}

{% raw %}

```html
<template>
    <div id="app" style="height:330px">
        <div>
         <button v-on:click='showHyperlinkDialog' >Open dialog</button>
        </div>
        <ejs-documenteditor ref="documenteditor" :enableSelection='true' :isReadOnly='false' :enableEditor='true' :enableEditorHistory='true' :enableHyperlinkDialog='true' :enableSfdtExport='true' style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin, Selection, Editor, EditorHistory, HyperlinkDialog, SfdtExport, RequestNavigateEventArgs } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);

export default {
    data: function() {
        return {
        };
    },
    provide: {
        DocumentEditor : [Selection, Editor, EditorHistory, HyperlinkDialog, SfdtExport]
    }
    methods: {
        showHyperlinkDialog: function() {
            this.$refs.documenteditor.showDialog('Hyperlink');
        }
    }
}
</script>
<style>
 @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

You can use the following keyboard shortcut to open the hyperlink dialog if the selection is in hyperlink.

| Key Combination | Description |
|-----------------|-------------|
|Ctrl + K | Open hyperlink dialog that allows you to create or edit hyperlink|

## See Also

* [Feature modules](../document-editor/feature-module/)
* [Hyperlink dialog](../document-editor/dialog#hyperlink-dialog/)