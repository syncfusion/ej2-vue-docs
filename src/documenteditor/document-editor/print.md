---
title: "Print"
component: "DocumentEditor"
description: "Learn how to print the document in JavaScript document editor and customize page size, margins, and more during print."
---

# Print

To print the document, use the `print` method from document editor instance.

Refer to the following example for showing a document and print it.

{% tab template="document-editor/print", isDefaultActive=false %}

{% raw %}

```html
<template>
    <div id="app">
        <div>
         <button v-on:click='print' >Print</button>
        </div>
        <ejs-documenteditor ref="documenteditor" :enablePrint='true' style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin, Print } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);

export default {
    data: function() {
        return {
        };
    },
    provide: {
        DocumentEditor : [Print]
    }
    methods: {
        print: function() {
             this.$refs.documenteditor.print();
        }
    },
    mounted: function() {
        let sfdt: string =`{
            "sections": [
                {
                    "blocks": [
                        {
                            "inlines": [
                                {
                                    "characterFormat": {
                                        "bold": true,
                                        "italic": true
                                    },
                                    "text": "Hello World"
                                }
                            ]
                        }
                    ],
                    "headersFooters": {
                    }
                }
            ]
        }`;
        this.$refs.documenteditor.open(sfdt);
    }
}
</script>
<style>
 @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

Refer to the following example for creating a document and print it.

{% tab template="document-editor/print", isDefaultActive=false %}

{% raw %}

```html
<template>
    <div id="app">
        <div>
         <button v-on:click='print' >Print</button>
        </div>
        <ejs-documenteditor ref="documenteditor" :isReadOnly='false' :enablePrint='true'  :enableEditor='true' :enableSelection='true' :enableEditorHistory='true' style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin, Print, Editor, Selection, EditorHistory } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);

export default {
    data: function() {
        return {
        };
    },
    provide: {
        DocumentEditor : [Print, Editor, Selection, EditorHistory]
    }
    methods: {
        print: function() {
             this.$refs.documenteditor.print();
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

## Print using window object

You can print the document in document editor by passing the window instance. This is useful to implement print in third party frameworks such as electron, where the window instance will not be available. Refer to the following example.

> `this.$refs.documenteditor.print(window)`;

## Page setup

Some of the print options cannot be configured using JavaScript. Refer to the following links to learn more about the browser page setup:

* [`Chrome`](https://support.google.com/chrome/answer/1069693?hl=en&visit_id=1-636335333734668335-3165046395&rd=1/)
* [`Firefox`](https://support.mozilla.org/en-US/kb/how-print-web-pages-firefox/)

However, you can customize margins, paper, and layout options by modifying the section format properties using page setup dialog

```html
<template>
    <div id="app">
        <ejs-documenteditor ref="documenteditor" :isReadOnly='false' :enablePrint='true'  :enableEditor='true' :enableSelection='true' :enableEditorHistory='true' :enablePageSetupDialog='true' style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin, Print, Editor, Selection, EditorHistory, PageSetupDialog } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);

export default {
    data: function() {
        return {
        };
    },
    provide: {
        DocumentEditor : [Print, Editor, Selection, EditorHistory, PageSetupDialog]
    },
    mounted: function() {
        this.$refs.documenteditor.showPageSetupDialog();
    }
}
</script>
<style>
 @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

By customizing margins, papers, and layouts, the layout of the document will be changed in document editor. To modify these options during print operation, serialize the document as SFDT using the `serialize` method in document editor instance and open the SFDT data in another instance of document editor in separate window.

The following example shows how to customize layout options only for printing.

{% tab template="document-editor/print", isDefaultActive=false %}

{% raw %}

```html
<template>
    <div id="app">
        <div>
         <button v-on:click='print' >Print</button>
        </div>
        <ejs-documenteditor ref="documenteditor" :isReadOnly='false' :enablePrint='true'  :enableEditor='true' :enableSelection='true' :enableEditorHistory='true' :enableSfdtExport='true' style="width: 100%;height: 100%;"></ejs-documenteditor>

         <ejs-documenteditor ref="pagesetup_documenteditor" :isReadOnly='false' :enablePrint='true'  :enableEditor='true' :enableSelection='true' :enableEditorHistory='true' :enableSfdtExport='true' style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin, Print, Editor, Selection, EditorHistory, SfdtExport } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);

export default {
    data: function() {
        return {
        };
    },
    provide: {
        DocumentEditor : [Print, Editor, Selection, EditorHistory, SfdtExport]
    }
    methods: {
        print: function() {
            let sfdtData =  this.$refs.documenteditor.serialize();
            this.$refs.pagesetup_documenteditor.open(sfdtData);
            //Set A5 paper size
            this.$refs.pagesetup_documenteditor.ej2Instances.selection.sectionFormat.pageWidth = 419.55;
            this.$refs.pagesetup_documenteditor.ej2Instances.selection.sectionFormat.pageHeight = 595.30;
            this.$refs.pagesetup_documenteditor.print();
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
