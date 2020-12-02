---
title: "SpellCheck"
component: "DocumentEditor"
description: "Learn how to perform spell check in JavaScript document editor"
---

# Spell Check

Document editor supports performing spell checking for any input text. You can perform spell checking for the text in Document Editor and it will provide suggestions for the mis-spelled words through dialog and in context menu.

```html
<template>
  <div id="app">
     <ejs-documenteditor ref="documenteditor" id="container_1" style='height:600px;' :enableSpellCheck='true'></ejs-documenteditor>
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
        this.$refs.documenteditor.ej2Instances.spellChecker.languageID = 1033; //LCID of "en-us"
        this.$refs.documenteditor.ej2Instances.spellChecker.removeUnderline = false;
        this.$refs.documenteditor.ej2Instances.spellChecker.allowSpellCheckAndSuggestion = true;
    }
}
</script>
<style>
 @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

## Features

* Supports context menu suggestions.
* Provides build-in options to Ignore, Ignore All, Change, Change All for error words in spell checker        dialog.

## Spell check settings

### Remove Underline

By default, mis-spelled words are marked with squiggly line. You can also disable this behavior by enabling the `removeUnderline` API and now, the squiggly lines will never be rendered for mis-spelled words.

```typescript
this.$refs.documenteditor.ej2Instances.spellChecker.removeUnderline = false;
```

### AllowSpellCheckAndSuggestion

By default, on performing spell check in Document Editor, both spelling and suggestions of the mis-spelled words will be retrieved, and this mis-spelled words can be corrected through context menu suggestions. You can modify this behavior using the `allowSpellCheckAndSuggestion` API, which will perform only spell check.

```typescript
this.$refs.documenteditor.ej2Instances.spellChecker.allowSpellCheckAndSuggestion = false;
```

### LanguageID

Document Editor provides multi-language spell check support. You can add as many languages (dictionaries) in the server-side and to use that language for spell checking in Document Editor, it must be matched with `languageID` you pass in the Document Editor.

```typescript
this.$refs.documenteditor.ej2Instances.spellChecker.languageID = 1033 //LCID of "en-us";
```

* Refer to the [Spell checker](https://github.com/SyncfusionExamples/EJ2-DocumentEditor-WebServices) link for configuring spell checker in server-side.