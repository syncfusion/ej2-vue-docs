---
title: "Open Thumbnail"
component: "PDF Viewer"
description: "Learn about how to open the thumbnail using openThumbnailPanel method in PDF Viewer control."
---

# Open Thumbnail

The PDF Viewer library allows you to open the thumbnail of the PDF document using the **openThumbnailPanel()** method.

The following steps are used to open the thumbnail of the PDF Document.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/vue/documentation/pdfviewer/getting-started/) to create simple PDF Viewer sample in Vue.

**Step 2:** Add the following code snippet to open the thumbnail in the resizing event of splitter.

```html

onSplitterResize: function () {
      var viewer = document.getElementById("pdfviewer").ej2_instances[0];
      viewer.updateViewerContainer();
      viewer.thumbnailViewModule.openThumbnailPane();
      debugger;
    },

```

Find the Sample [how to open thumbnail](https://codesandbox.io/s/vue-examples-forked-1h1hg?file=/App.vue:1724-1944)