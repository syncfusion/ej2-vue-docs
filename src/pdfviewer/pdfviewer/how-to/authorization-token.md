---
title: "Include the Authorization Token"
component: "PDF Viewer"
description: "Learn about how to include the authorization token in PDF viewer Control."
---

# Include the Authorization token

The PDF Viewer library allows you to include the authorization token in the PDF viewer AJAX request using the properties of the ajaxRequest header available in `AjaxRequestSettings`, and it will be included in every AJAX request send from PDF Viewer.

The following steps are used to include the authorization token to the PDF viewer control.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/vue/documentation/pdfviewer/getting-started/) to create simple PDF Viewer sample in React.

**Step 2:** Add the following code snippet to include the authorization token.

```html
<template>
 <div>
  <ejs-pdfviewer id="pdfViewer" :serviceUrl="serviceUrl" :documentPath="documentPath" :ajaxRequestSettings=ajaxRequestSettings> </ejs-pdfviewer>
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

    // Include Authorization Token.
    ajaxRequestSettings:{
      ajaxHeaders: [
      {
      headerName: 'Authorization',

      headerValue: 'Bearer 64565dfgfdsjweiuvbiuyhiueygf'
      }
      ],
      withCredentials: false
    },
  };
  },
  provide: {
PdfViewer: [Toolbar, Magnification, Navigation, LinkAnnotation, BookmarkView, ThumbnailView, Print, TextSelection, TextSearch,Annotation, FormDesigner, FormFields]
  }
}
</script>
```

Find the Sample, [how to include authorization token](https://www.syncfusion.com/downloads/support/directtrac/general/ze/quickstart-1627983082.zip)