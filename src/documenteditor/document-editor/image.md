---
title: "Images"
component: "DocumentEditor"
description: "Learn the supported image types in JavaScript document editor and how to insert, resize, format images."
---

# Images

Document editor supports common raster format images like PNG, BMP, JPEG, and GIF. You can insert an image file or online image in the document using the `insertImage()` method. Refer to the following sample code.

The following example shows how to open bookmark dialog in document editor.

{% tab template="document-editor/bookmark", isDefaultActive=false %}

{% raw %}

```html
<template>
    <div id="app">
        <input id="insertImageButton" ref="insertImageButton" style="position:fixed; left:-100em" type="file" v-on:change="onInsertImage" accept=".jpeg,.jpg,.png,.gif,.bmp">
        <div>
         <button v-on:click='insertImageButtonClick' >Insert Image</button>
        </div>
        <ejs-documenteditor ref="documenteditor" :enableSfdtExport='true' :enableWordExport='true' :enableSelection='true' :enableEditor='true' :isReadOnly='false' style="width: 100%;height: 100%;"></ejs-documenteditor>
    </div>
</template>
<script>
import Vue from 'vue'
import { DocumentEditorPlugin, Selection, Editor, SfdtExport, WordExport } from '@syncfusion/ej2-vue-documenteditor';

Vue.use(DocumentEditorPlugin);

export default {
    data: function() {
        return {
        };
    },
    provide: {
        DocumentEditor : [SfdtExport, WordExport, Selection, Editor]
    }
    methods: {
         onInsertImage: function(args: any): void {
            if (navigator.userAgent.match('Chrome') || navigator.userAgent.match('Firefox') || navigator.userAgent.match('Edge') || navigator.userAgent.match('MSIE') || navigator.userAgent.match('.NET')) {
                 let documenteditor =this.$refs.documenteditor;
                if (args.target.files[0]) {
                    let path = args.target.files[0];
                    let reader = new FileReader();
                    reader.onload = function (frEvent: any) {
                        let base64String = frEvent.target.result;
                        let image = document.createElement('img');
                        image.addEventListener('load', function () {
                           documenteditor.ej2Instances.editor.insertImage(base64String, this.width, this.height);
                        })
                        image.src = base64String;
                    };
                    reader.readAsDataURL(path);
                }
                //Safari does not Support FileReader Class
            } else {
                let image = document.createElement('img');
                image.addEventListener('load', function () {
                     documenteditor.ej2Instances.editor.insertImage(args.target.value);
                })
                image.src = args.target.value;
            }
        },
        insertImageButtonClick: function() {
             this.$refs.insertImageButton.value = '';
             this.$refs.insertImageButton.click();
        }
    }
}
</script>
<style>
 @import "../../node_modules/@syncfusion/ej2-vue-documenteditor/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}

Image files will be internally converted to base64 string. Whereas, online images are preserved as URL.

## Image resizing

Document editor provides built-in image resizer that can be injected into your application based on the requirements. This allows you to resize the image by dragging the resizing points using mouse or touch interactions. This resizer appears as follows.

![Image](images/image.png)

## Changing size

Document editor expose API to get or set the size of the selected image. Refer to the following sample code.

```typescript
this.$refs.documenteditor.ej2Instances.selection.imageFormat.width = 800;
this.$refs.documenteditor.ej2Instances.selection.imageFormat.height = 800;
```

## See Also

* [Feature modules](../document-editor/feature-module/)