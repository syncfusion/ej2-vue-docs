---
title: "Web Services for Vue Word Processor (Document Editor)"
component: "DocumentEditor"
description: "Learn about the web services required for server-side dependent functionalities of Vue Word Processor component (Document Editor)."
---

# Supported platforms for server-side dependencies

You can deploy web APIs for server-side dependencies of Document Editor component in the following platforms.

* [ASP.NET Core](../document-editor/web-services/core)
* [ASP.NET MVC](../document-editor/web-services/mvc)
* [Java](../document-editor/web-services/java)

## Which operations require server-side interaction

|Operations|When client-server communication will be triggered?|What type of data will be transferred between client and server?|
|------------|--------------------------------------|------------------------|
|[Open file formats other than SFDT](../document-editor/import#convert-word-documents-into-sfdt)|When opening the document other than SFDT (Syncfusion Document Editor's native file format), the server-side web API is invoked from client-side script.|**Client**: Sends the input file.<br>**Server**: Receives the input file and sends the converted SFDT back to the client.<br><br>The server-side web API internally extracts the content from the document (DOCX, DOC, WordML, RTF, HTML) using Syncfusion Word library (DocIO) and converts it into SFDT for opening the document in Document Editor.|
|[Paste with formatting](../document-editor/clipboard#paste-with-formatting)|When pasting the formatted content (HTML/RTF) received from system clipboard. For converting HTML/RTF to SFDT format.<br><br> **Note**: Whereas plain text received from system clipboard will be pasted directly in the client-side.|**Client**: Sends the input Html or Rtf string. <br>**Server**: Receives the input Html or Rtf string and sends the converted SFDT back to the client.|
|[Restrict editing](../document-editor/document-management)|When protecting the document, for generating hash.|**Client**: Sends the input data for hashing algorithm.<br> **Server**: Receives the input data for hashing algorithm and sends the result hash information back to the client.|
|[Spellcheck](../document-editor/spell-check)(default)|When the spellchecker is enabled on client-side Document Editor, and it performs the spell check validation for words in the document.|**Client**: Sends the words (string) with their language for spelling validation.<br> **Server**: Receives the words (string) with their language for spelling validation and sends the validation result as JSON back to the client.|
|[SpellCheckByPage](../document-editor/spell-check)|Document editor provides options to spellcheck page by page when loading the documents. By [enabling optimized spell check](../document-editor/spell-check#enableoptimizedspellcheck) in client-side, you can perform spellcheck page by page when loading the documents.|**Client**: Sends the words (string) with their language for spelling validation.<br> **Server**: Receives the words (string) with their language for spelling validation and sends the validation result as JSON back to the client.|
|[Save as file formats other than SFDT and DOCX](../document-editor/server-side-export) (optional API)|You can configure this API, if you want to save the document in file format other than DOCX and SFDT.<br><br> For saving the files as WordML, DOC, RTF, HTML, ODT, Text using Syncfusion Word library (DocIO) and PDF using  Syncfusion Word (DocIO) and PDF libraries.|You can transfer document from client to server either as SFDT or DOCX format.<br><br>First option (SFDT):<br>**Client**: Sends the SFDT.<br>**Server**: Receives the SFDT and saves the converted document as any file format supported by [Syncfusion Word library (DocIO)](https://www.syncfusion.com/word-framework/net/word-library) in server or sends the saved file to the client browser.<br><br>Second option (DOCX):<br>**Client**: Sends the DOCX file.<br>**Server**: Receives the DOCX file and saves the converted document as any file format supported by [Syncfusion Word library (DocIO)](https://www.syncfusion.com/word-framework/net/word-library) in server or sends the saved file to the client browser.|

>Note: If you don't require the above functionalities then you can deploy as pure client-side component without any server-side interactions.

Please refer the [example from GitHub](https://github.com/SyncfusionExamples/EJ2-DocumentEditor-WebServices) to configure the web service and set the [serviceUrl](../api/document-editor-container#serviceurl).

If your running web service Url is <http://localhost:62869/>, set the serviceUrl like below:

```typescript
this.$refs.container.serviceUrl== "http://localhost:62869/api/documenteditor/";
```

## Required Web API structure

Please check below table for expected web API structure.

|Expected method name |Parameters |Return type |
|-----|----|----|
|Import |Files(IFormCollection) |json(sfdt format) |
|SystemClipboard|CustomerParameter: content(type string either rtf or html) and type(either .rtf or .html) |json(sfdt format) |
|RestrictEditing |Parameter of type CustomRestrictParameter<br>public class CustomRestrictParameter<br>        {<br>            public string passwordBase64 { get; set; }<br>            public string saltBase64 { get; set; }<br>            public int spinCount { get; set; }<br>        } |result hash information |
|SpellCheck(default) |Parameter: SpellCheckJsonData<br>public class SpellCheckJsonData <br>{<br>            public int LanguageID { get; set; }<br>            public string TexttoCheck { get; set; }<br>            public bool CheckSpelling { get; set; }<br>            public bool CheckSuggestion { get; set; }<br>            public bool AddWord { get; set; }<br>        }  |Json type of Spellcheck containing details of spell checked word |
|SpellCheckByPage |Parameter: SpellCheckJsonData<br>public class SpellCheckJsonData <br>{<br>            public int LanguageID { get; set; }<br>            public string TexttoCheck { get; set; }<br>            public bool CheckSpelling { get; set; }<br>            public bool CheckSuggestion { get; set; }<br>            public bool AddWord { get; set; }<br>        }  |Json type of Spellcheck containing details of spell checked word <br><br> **Note**: Document editor provides options to spellcheck page by page when loading the documents. By [enabling optimized spell check](../document-editor/spell-check#enableoptimizedspellcheck) in client-side, you can perform spellcheck page by page when loading the documents. |
|Save(optional API) |parameter: SaveParameter <br>public class SaveParameter<br>{<br>public string Content { get; set; }<br> public string FileName { get; set; }<br> } |void(Save the file as file stream) |
|ExportSFDT(optional API) |parameter: SaveParameter <br>public class SaveParameter<br>{<br>public string Content { get; set; }<br> public string FileName { get; set; }<br> } |FileStreamResult (to save the document in client-side) |
|Export(optional API) |Files(IFormCollection) |FileStreamResult (to save the document in client-side) |

## ServerActionSettings

Document editor component provides an option to customize the expected method name for Import, SystemClipboard, RestrictEditing and SpellCheck using [serverActionSettings](../api/document-editor-container/documentEditorContainerModel/#serveractionsettings).

The following example code illustrates how to customize the method name using serverActionSettings.

```html
<template>
    <div id="app">
        <ejs-documenteditorcontainer height="590px" :serviceUrl='serviceUrl' :enableToolbar='true' :serverActionSettings='settings'> </ejs-documenteditorcontainer>
    </div>
</template>

<script>
  import Vue from 'vue';
  import { DocumentEditorContainerPlugin, DocumentEditorContainerComponent,Toolbar } from '@syncfusion/ej2-vue-documenteditor';

  Vue.use(DocumentEditorContainerPlugin);
  export default {
    data(){
      return { serviceUrl:'https://ej2services.syncfusion.com/production/web-services/api/documenteditor/',
      settings : { import: 'Import1', systemClipboard: 'SystemClipboard1', spellCheck: 'SpellCheck1', restrictEditing: 'RestrictEditing1' } }
    },
    provide: {
      //Inject require modules.
      DocumentEditorContainer: [Toolbar]
    }
  }
</script>
```