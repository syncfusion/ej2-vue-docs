---
title: "Feature modules"
component: "DocumentEditor"
description: "Learn the feature-wise modules in JavaScript document editor and how to integrate it in your application."
---

# Feature modules

Document editor features are segregated into individual feature-wise modules to enable selective referencing. By default, the document editor displays the document in read-only mode. The required modules should be injected to extend its functionality. The following are the selective modules of document editor that can be included as required:
* **Print** - Prints the document.
* **SfdtExport** - Exports the document as Syncfusion Document Text (.SFDT) file.
* **Selection** - Selects a portion of the document and copy it to the clipboard.
* **Search** - Searches specific text and navigate between the results.
* **WordExport** - Exports the document as Word Document (.DOCX) file.
* **TextExport** - Exports the document as Text Document (.TXT) file.
* **Editor** - Performs all kind of editing operations.
* **EditorHistory** - Maintains the history of editing operations so that you can perform undo and redo at any time.
* User interface options such as context menu, options pane, image resizer, and dialog are available as individual modules.

>In addition to injecting the required modules in your application, enable corresponding properties to extend the functionality for a document editor instance.
Refer to the following table.

| Module | Dependent modules to be injected for extending the functionality of document editor in your application | Property to enable the functionality for a document editor instance |
|---|---|---|
|Print|`Print`|`<ejs-documenteditor :enablePrint='true'></ejs-documenteditor>`|
|SfdtExport|`SfdtExport`|`<ejs-documenteditor :enableSfdtExport='true'></ejs-documenteditor>`|
|Selection|`Selection`|`<ejs-documenteditor :enableSelection='true'></ejs-documenteditor>`|
|Search|`Selection, Search`|`<ejs-documenteditor :enableSearch='true'></ejs-documenteditor>`|
|WordExport|`SfdtExport, WordExport`|`<ejs-documenteditor :enableWordExport='true'></ejs-documenteditor>`|
|TextExport|`SfdtExport, TextExport`|`<ejs-documenteditor :enableTextExport='true'></ejs-documenteditor>`|
|Editor|`Selection, Editor`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true'></ejs-documenteditor>`|
|EditorHistory|`Selection, Editor, EditorHistory`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableEditorHistory='true'></ejs-documenteditor>`|
|OptionsPane(Find)|`Selection, Search, OptionsPane`|`<ejs-documenteditor :enableSearch='true' :enableOptionsPane='true'></ejs-documenteditor>`|
|OptionsPane(Find and Replace)|`Selection, Search, Editor, OptionsPane`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableSearch='true' :enableOptionsPane='true'></ejs-documenteditor>`|
|ContextMenu|`Selection, ContextMenu`|`<ejs-documenteditor :enableSelection='true' :enableContextMenu='true'></ejs-documenteditor>`|
|ImageResizer|`Selection, Editor, ImageResizer`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableImageResizer='true'></ejs-documenteditor>`|
|HyperlinkDialog|`Selection, Editor, HyperlinkDialog`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableHyperlinkDialog='true'></ejs-documenteditor>`|
|TableDialog|`Selection, Editor, TableDialog`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableTableDialog='true'></ejs-documenteditor>`|
|FontDialog|`Selection, Editor, FontDialog`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableFontDialog='true'></ejs-documenteditor>`|
|ParagraphDialog|`Selection, Editor, ParagraphDialog`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableParagraphDialog='true'></ejs-documenteditor>`|
|BookmarkDialog|`Selection, Editor, BookmarkDialog`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableBookmarkDialog='true'></ejs-documenteditor>`|
|PageSetupDialog|`Selection, Editor, PageSetupDialog`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enablePageSetupDialog='true'></ejs-documenteditor>`|
|TableOfContentsDialog|`Selection, Editor, TableOfContentsDialog`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableTableOfContentsDialog='true'></ejs-documenteditor>`|
|ListDialog|`Selection, Editor, ListDialog`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableListDialog='true'></ejs-documenteditor>`|
|TablePropertiesDialog|`Selection, Editor, TablePropertiesDialog`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableTablePropertiesDialog='true'></ejs-documenteditor>`|
|CellOptionsDialog|`Selection, Editor, CellOptionsDialog`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableTablePropertiesDialog='true'></ejs-documenteditor>`|
|BordersAndShadingDialog|`Selection, Editor, BordersAndShadingDialog`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableBordersAndShadingDialog='true'></ejs-documenteditor>`|
|TableOptionsDialog|`Selection, Editor, TableOptionsDialog`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableTableOptionsDialog='true'></ejs-documenteditor>`|
|StylesDialog|`Selection, Editor, StylesDialog,StyleDialog`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableStyleDialog='true' :enableStylesDialog='true'></ejs-documenteditor>`|
|StyleDialog|`Selection, Editor, StyleDialog`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableStyleDialog='true'></ejs-documenteditor>`|
|BulletsAndNumberingDialog|`Selection, Editor, BulletsAndNumberingDialog`|`<ejs-documenteditor :isReadOnly='false' :enableEditor='true' :enableStyleDialog='true'></ejs-documenteditor>`|

These modules should be injected into the `provide` section and use `DocumentEditor` as a key of the object.