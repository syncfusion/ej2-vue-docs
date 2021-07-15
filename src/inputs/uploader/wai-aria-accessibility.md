---
title: "wia-aria-accessibility"
component: "Uploader"
description: "Describes the accessibility standard of the file upload control such as WAI-ARIA attributes, keyboard interaction, theming, etc."
---

# Accessibility

The uploader component characterized with complete ARIA accessibility support that helps to be accessible by on-screen readers and other assistive technology devices.

## Keyboard interaction

The following are the standard keys that works on uploader component:

| **Keyboard shortcuts** | **Actions** |
| --- | --- |
| <kbd>Tab</kbd> | Move focus to next element. |
| <kbd>Shift + Tab</kbd> | Move focus to previous element. |
| <kbd>Enter</kbd> | Triggers corresponding action to button element. |
| <kbd>Esc</kbd> | Close the file browser dialog alone and cancels the upload on drop the file.

{% tab template="uploader/accessibility" %}

```html
<template>
  <div>
    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :asyncSettings= "path" ></ejs-uploader>
  </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
Vue.use(UploaderPlugin);

export default {
    data: function() {
        return {
            path:  {
                saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
                removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
            }
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
</style>
```

{% endtab %}

>You can also explore [Vue File Upload](https://www.syncfusion.com/vue-ui-components/vue-file-upload) feature tour page for its groundbreaking features. You can also explore our [Vue File Upload example](https://ej2.syncfusion.com/vue/demos/#/material/uploader/default.html) to understand how to browse the files which you want to upload to the server.
