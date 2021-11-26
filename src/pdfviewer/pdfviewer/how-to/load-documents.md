---
title: "Load PDF documents dynamically"
component: "PDF Viewer"
description: "Learn how to load PDF documents dynamically in PDF Viewer control."
---

# Load PDF documents dynamically

The PDF Viewer library allows you to switch or load  PDF documents dynamically after the initial load operation. To achieve this, load the PDF document as a base64 string or file name into the PDF Viewer control using the [**Load()**](https://ej2.syncfusion.com/vue/documentation/api/pdfviewer/#load) method dynamically.

The following steps are used to load the PDF document dynamically.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/vue/documentation/pdfviewer/getting-started/) to create a simple PDF Viewer sample.

**Step 2:** Use the following code snippet to load the PDF document using a base64 string.

```html
<template>
 <div>
   <button v-on:click="load_1">LoadDocumentFromBase64</button>
  <div>
  <ejs-pdfviewer id="pdfViewer" :serviceUrl="serviceUrl" :documentPath="documentPath"> </ejs-pdfviewer>
  </div>
</div>
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
};
  },
  provide: {
PdfViewer: [Toolbar, Magnification, Navigation, LinkAnnotation, BookmarkView, ThumbnailView, Print, TextSelection, TextSearch,Annotation, FormDesigner, FormFields]
  },
 methods: {
   // Load the PDF document from a Base64 string
   load_1: function (event) {
    var viewer = document.getElementById('pdfViewer').ej2_instances[0];
    viewer.load('data:application/pdf;base64,'+ AddBase64String, null);
   }
 }
}
```

**Step 3:** Use the following code snippet to load the PDF document using the document name.

```html
<template>
 <div>
   <button v-on:click="load_2">LoadDocument</button>
 <div>
  <ejs-pdfviewer id="pdfViewer" :serviceUrl="serviceUrl" :documentPath="documentPath"> </ejs-pdfviewer>
 </div>
</div>
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
};
  },
provide: {
PdfViewer: [Toolbar, Magnification, Navigation, LinkAnnotation, BookmarkView, ThumbnailView, Print, TextSelection, TextSearch,Annotation, FormDesigner, FormFields]
},
methods: {
  load_2: function (event) {
    // Load the PDF document using the file name
    var viewer = document.getElementById('pdfViewer').ej2_instances[0];
    viewer.load('PDF_Succinctly.pdf', null);
  }
 }
}
```

Find the sample, [how to load PDF documents dynamically](https://www.syncfusion.com/downloads/support/directtrac/general/ze/quickstart433655736.zip)