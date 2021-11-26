---
title: "Extract Text"
component: "PDF Viewer"
description: "Learn how to extract text programmatically for PDF Viewer control."
---

# Extract Text

The PDF Viewer library allows you to extract the text from a page along with the bounds. Text extraction can be done using the [**isExtractText**](https://ej2.syncfusion.com/vue/documentation/api/pdfviewer/#isextracttext) property and [**extractTextCompleted**](https://ej2.syncfusion.com/vue/documentation/api/pdfviewer/#extracttextcompleted) event.

The following steps are used to extract the text from the page.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/vue/documentation/pdfviewer/getting-started/) to create a simple PDF Viewer sample.

**Step 2:** The following code snippet explains how to extract the text from a page .

```html
<template>
  <ejs-pdfviewer id="pdfViewer" :serviceUrl="serviceUrl" :documentPath="documentPath" :isExtractText="true" :extractTextCompleted
="extractTextCompleted"></ejs-pdfviewer>
</template>

<script>
import Vue from 'vue';
import { PdfViewerPlugin, Toolbar, Magnification, Navigation, LinkAnnotation, BookmarkView, ThumbnailView, Print, TextSelection, TextSearch, Annotation, FormDesigner, FormFields} from '@syncfusion/ej2-vue-pdfviewer';
Vue.use(PdfViewerPlugin);
export default {
  data () {
return {
    serviceUrl:"https://ej2services.syncfusion.com/production/web-services/api/pdfviewer",
    documentPath:"PDF_Succinctly.pdf",
    extractTextCompleted: function (args) {
    // Extract the Complete text of load document
    console.log(args);
    console.log(args.documentTextCollection[1]);
    // Extract the Text data.
    console.log(args.documentTextCollection[1][1].TextData);
    // Extract Text in the Page.
    console.log(args.documentTextCollection[1][1].PageText);
    // Extracts the first text of the PDF document along with its bounds
    console.log(args.documentTextCollection[1][1].TextData[0].Bounds);
  }
};
  },
  provide: {
PdfViewer: [Toolbar, Magnification, Navigation, LinkAnnotation, BookmarkView, ThumbnailView, Print, TextSelection, TextSearch,Annotation, FormDesigner, FormFields]
  }
}
</script>
```

Find the Sample, [how to Extract Text](https://www.syncfusion.com/downloads/support/directtrac/general/ze/quickstart-1590348162.zip)