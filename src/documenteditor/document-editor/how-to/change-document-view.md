---
title: "How to"
component: "DocumentEditor"
description: "Learn how to change the document view to web layout and print view in document editor."
---

# Change document view

## How to change the document view in DocumentEditor component

DocumentEditor allows you to change the view to web layout and print using the [`layoutType`](../../api/document-editor#layouttype) property with the supported [`LayoutType`](../../api/document-editor/layouttype/).

```typescript
<ejs-documenteditor :layoutType='Continuous' id='container'></ejs-documenteditor>
```

>Note: Default value of `layoutType` in DocumentEditor component is `Pages`.

## How to change the document view in DocumentEditorContainer component

DocumentEditorContainer component allows you to change the view to web layout and print using the [`layoutType`](../../api/document-editor-container#layouttype) property with the supported [`LayoutType`](../../api/document-editor/layouttype/).

```typescript
<ejs-documenteditorcontainer :layoutType='Continuous' id='container'></ejs-documenteditorcontainer>
```

>Note: Default value of `layoutType` in DocumentEditorContainer component is `Pages`.