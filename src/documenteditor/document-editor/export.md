---
title: "Export"
component: "DocumentEditor"
description: "Learn how to export the contents of JavaScript document editor as SFDT, or DOCX document in client-side."
---

# Export

Document editor exports the document into various known file formats in client-side such as Microsoft Word document (.docx), text document (.txt), and its own format called **Syncfusion Document Text (.sfdt)**.

## Sfdt export

The following example shows how to export documents in document editor as Syncfusion document text (.sfdt).

{% tab template="document-editor/export", isDefaultActive=false %}

{% raw %}

```html
<template>
    <div id="app">
        <div>
         <button v-on:click='saveAsSfdt' >Save</button>
        </div>
        <ejs-documenteditor ref="documenteditor" :enableSfdtExport='true' :enableSelection='true' :enableEditor='true' :isReadOnly='false' style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin, Selection, Editor, SfdtExport } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);

export default {
    data: function() {
        return {
        };
    },
    provide: {
        DocumentEditor : [SfdtExport, Selection, Editor]
    }
    methods: {
        saveAsSfdt: function() {
             this.$refs.documenteditor.save('sample', 'Sfdt');
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

## Word export

The following example shows how to export the document as Word document (.docx).

{% tab template="document-editor/export", isDefaultActive=false %}

{% raw %}

```html
<template>
    <div id="app">
        <div>
         <button v-on:click='saveAsDocx' >Save</button>
        </div>
        <ejs-documenteditor ref="documenteditor" :enableSfdtExport='true' :enableWordExport='true' :enableSelection='true' :enableEditor='true' :isReadOnly='false' style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin, Selection, Editor, SfdtExport, WordExport } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);

export default {
    data: function() {
        return {
        };
    },
    provide: {
        DocumentEditor : [SfdtExport, WordExport, Selection, Editor]
    }
    methods: {
        saveAsDocx: function() {
             this.$refs.documenteditor.save('sample', 'Docx');
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

## Text export

The following example shows how to export document as text document (.txt).

{% tab template="document-editor/export", isDefaultActive=false %}

{% raw %}

```html
<template>
    <div id="app">
        <div>
         <button v-on:click='saveAsTextDocument' >Save</button>
        </div>
        <ejs-documenteditor ref="documenteditor" :enableSfdtExport='true' :enableTextExport='true' :enableSelection='true' :enableEditor='true' :isReadOnly='false' style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin, Selection, Editor, SfdtExport, TextExport } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);

export default {
    data: function() {
        return {
        };
    },
    provide: {
        DocumentEditor : [SfdtExport, TextExport, Selection, Editor]
    }
    methods: {
        saveAsTextDocument: function() {
             this.$refs.documenteditor.save('sample', 'Txt');
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

## Export as blob

Document editor also supports API to store the document into a blob. Refer to the following sample to export document into blob in client-side.

```html
<template>
    <div id="app">
        <div>
         <button v-on:click='exportBlob' >Save</button>
        </div>
        <ejs-documenteditor ref="documenteditor" :enableSfdtExport='true' :enableWordExport='true' :enableSelection='true' :enableEditor='true' :isReadOnly='false' style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin, Selection, Editor, SfdtExport, WordExport } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);

export default {
    data: function() {
        return {
        };
    },
    provide: {
        DocumentEditor : [SfdtExport, WordExport, Selection, Editor]
    }
    methods: {
        exportBlob: function() {
            this.$refs.documenteditor.saveAsBlob('Docx').then((exportedDocument: Blob) => {
                // The blob can be processed further
            });
        }
    }
}
</script>
<style>
 @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

For instance, to export the document as Rich Text Format file, implement an ASP.NET MVC web API controller using DocIO library by passing the DOCX blob. Refer to the following code example.

```csharp
//API controller for the conversion.
[HttpPost]
public HttpResponseMessage ExportAsRtf()
{
    System.Web.HttpPostedFile data = HttpContext.Current.Request.Files[0];
    //Opens document stream
    WordDocument wordDocument = new WordDocument(data.InputStream);
    MemoryStream stream = new MemoryStream();
    //Converts document stream as RTF
    wordDocument.Save(stream, FormatType.Rtf);
    wordDocument.Close();
    stream.Position = 0;
    return new HttpResponseMessage() { Content = new StreamContent(stream) };
}

```

In client-side, you can consume this web service and save the document as Rich Text Format (.rtf) file. Refer to the following example.

```typescript
function exportBlob() {
    documenteditor.saveAsBlob('Docx').then((exportedDocument: Blob) => {
        // The blob can be processed further
        let formData: FormData = new FormData();
        formData.append('fileName', 'sample.docx');
        formData.append('data', exportedDocument);
        saveAsRtf(formData);
    });
});

function saveAsRtf(formData: FormData): void {
    let httpRequest: XMLHttpRequest = new XMLHttpRequest();
    httpRequest.open('POST', '/api/DocumentEditor/ExportAsRtf', true);
    httpRequest.onreadystatechange = () => {
        if (httpRequest.readyState === 4) {
            if (httpRequest.status === 200 || httpRequest.status === 304) {
                if (!(!navigator.msSaveBlob)) {
                    navigator.msSaveBlob(httpRequest.response, 'sample.rtf');
                } else {
                    let downloadLink: HTMLAnchorElement = document.createElementNS('http://www.w3.org/1999/xhtml', 'a') as HTMLAnchorElement;
                    download('sample.rtf', 'rtf', httpRequest.response, downloadLink, 'download' in downloadLink);
                }
            } else {
                console.error(httpRequest.response);
            }
        }
    }
    httpRequest.responseType = 'blob';
    httpRequest.send(formData);
}

function download(fileName: string, extension: string, buffer: Blob, downloadLink: HTMLAnchorElement, hasDownloadAttribute: Boolean): void {
    if (hasDownloadAttribute) {
        downloadLink.download = fileName;
        let dataUrl: string = window.URL.createObjectURL(buffer);
        downloadLink.href = dataUrl;
        let event: MouseEvent = document.createEvent('MouseEvent');
        event.initEvent('click', true, true);
        downloadLink.dispatchEvent(event);
        setTimeout((): void => {
            window.URL.revokeObjectURL(dataUrl);
            dataUrl = undefined;
        });
    } else {
        if (extension !== 'docx' && extension !== 'xlsx') {
            let url: string = window.URL.createObjectURL(buffer);
            let isPopupBlocked: Window = window.open(url, '_blank');
            if (!isPopupBlocked) {
                window.location.href = url;
            }
        }
    }
}
```

## See Also

* [Feature modules](../document-editor/feature-module/)