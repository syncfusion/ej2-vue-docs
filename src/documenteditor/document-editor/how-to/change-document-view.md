---
title: "How to"
component: "DocumentEditor"
description: "Learn how to change the document view to web layout and print view in document editor."
---

# Change document view

## How to change the document view in DocumentEditor component

Document Editor allows you to change the view to web layout and print using the [`layoutType`](../../api/document-editor#layouttype) property with the supported [`LayoutType`](../../api/document-editor/layouttype/).

```html
<ejs-documenteditor :layoutType='Continuous' id='container'></ejs-documenteditor>
```

>Note: Default value of `layoutType` in Document Editor component is `Pages`.

## How to change the document view in DocumentEditorContainer component

Document Editor Container component allows you to change the view to web layout and print using the [`layoutType`](../../api/document-editor-container#layouttype) property with the supported [`LayoutType`](../../api/document-editor/layouttype/).

```html
<ejs-documenteditorcontainer :layoutType='Continuous' id='container'></ejs-documenteditorcontainer>
```

>Note: Default value of `layoutType` in Document Editor Container component is `Pages`.