---
title: "Import"
component: "DocumentEditor"
description: "Learn how to import SFDT and word documents in JavaScript document editor using supported APIs."
---

# Import

In Document Editor, the documents are stored in its own format called **Syncfusion Document Text (SFDT)**.

The following example shows how to open SFDT data in Document Editor.

{% tab template="document-editor/import", isDefaultActive=false %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-documenteditor ref="documenteditor" id="container_1" style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);

export default {
    data: function() {
        return {
        };
    },
    mounted: function() {
        let sfdt: string = `{
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

## Import document from local machine

The following example shows how to import document from local machine.

{% tab template="document-editor/import-sfdt", isDefaultActive=false %}

{% raw %}

```html
<template>
    <div id="app">
        <input type="file" ref="fileUpload" v-on:change="onFileUpload" accept=".sfdt" style="position:fixed; left:-100em" />
        <div>
         <button v-on:click='insertImageButtonClickHandler' >Import</button>
        </div>
        <ejs-documenteditor ref="documenteditor" style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);

export default {
    data: function() {
        return {
        };
    },
    methods: {
        insertImageButtonClickHandler: function() {
            this.$refs.fileUpload.click();
        },
        onFileUpload: function(e) {
            if (e.target.files[0]) {
                let file = e.target.files[0];
                if (file.name.substr(file.name.lastIndexOf('.')) === '.sfdt') {
                    let fileReader: FileReader = new FileReader();
                    fileReader.onload = (e: any) => {
                        let contents: string = e.target.result;
                        this.$refs.documenteditor.open(contents);
                    };
                    fileReader.readAsText(file);
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

{% endraw %}

{% endtab %}

## Convert word documents into SFDT

You can convert word documents into SFDT format using the .NET Standard library [`Syncfusion.EJ2.WordEditor.AspNet.Core`](<https://www.nuget.org/packages/Syncfusion.EJ2.WordEditor.AspNet.Core/>) by the web API service implementation. This library helps you to convert word documents (.dotx,.docx,.docm,.dot,.doc), rich text format documents (.rtf), and text documents (.txt) into SFDT format. Refer to the following example.

```html
<template>
    <input type="file" ref="fileUpload" v-on:change="onFileUpload" accept=".dotx,.docx,.docm,.dot,.doc,.rtf,.txt,.xml,.sfdt" style="position:fixed; left:-100em" />
    <div>
        <div>
            <button v-on:click='insertImageButtonClickHandler'>Import</button>
        </div>
        <ejs-documenteditor ref="documenteditor" style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
    </div>
</template>
<script>
    import Vue from 'vue'
    import { DocumentEditorPlugin } from '@syncfusion/ej2-vue-documenteditor';

    Vue.use(DocumentEditorPlugin);

    export default {
        data: function() {
            return {
            };
        },
        methods: {
            loadFile: function(file: File): void {
                let ajax: XMLHttpRequest = new XMLHttpRequest();
                ajax.open('POST', 'https://localhost:4000/api/documenteditor/Import', true);
                ajax.onreadystatechange = () => {
                    if (ajax.readyState === 4) {
                        if (ajax.status === 200 || ajax.status === 304) {
                            // open SFDT text in document editor
                            this.$refs.documenteditor.open(ajax.responseText);
                        }
                    }
                }
                let formData: FormData = new FormData();
                formData.append('files', file);
                ajax.send(formData);
            },
            insertImageButtonClickHandler: function() {
                this.$refs.fileUpload.click();
            },
            onFileUpload: function(e) {
                if (e.target.files[0]) {
                    let file = e.target.files[0];
                    if (file.name.substr(file.name.lastIndexOf('.')) === '.sfdt') {
                        let fileReader: FileReader = new FileReader();
                        fileReader.onload = (e: any) => {
                            let contents: string = e.target.result;
                            this.$refs.documenteditor.open(contents);
                        };
                        fileReader.readAsText(file);
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

Here’s how to handle the server-side action for converting word document in to SFDT.

```csharp
[AcceptVerbs("Post")]
public string Import(IFormCollection data)
{
    if (data.Files.Count == 0)
        return null;
    Stream stream = new MemoryStream();
    IFormFile file = data.Files[0];
    int index = file.FileName.LastIndexOf('.');
    string type = index > -1 && index < file.FileName.Length - 1 ?
        file.FileName.Substring(index) : ".docx";
    file.CopyTo(stream);
    stream.Position = 0;

    WordDocument document = WordDocument.Load(stream, GetFormatType(type.ToLower()));
    string sfdt = Newtonsoft.Json.JsonConvert.SerializeObject(document);
    document.Dispose();
    return sdft;
}

internal static FormatType GetFormatType(string format)
{
    if (string.IsNullOrEmpty(format))
        throw new NotSupportedException("EJ2 DocumentEditor does not support this file format.");
    switch (format.ToLower()) {
        case ".dotx":
        case ".docx":
        case ".docm":
        case ".dotm":
            return FormatType.Docx;
        case ".dot":
        case ".doc":
            return FormatType.Doc;
        case ".rtf":
            return FormatType.Rtf;
        case ".txt":
            return FormatType.Txt;
        case ".xml":
            return FormatType.WordML;
        default:
            throw new NotSupportedException("EJ2 DocumentEditor does not support this file format.");
    }
}

```

## See Also

* [Feature modules](../document-editor/feature-module/)