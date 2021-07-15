---
title: "Localization"
component: "Uploader"
description: "Explains how to localize (locale) all the static text of the file upload control using L10n library that helps to adapt with different cultures."
---

# Localization

The Localization library allows you to localize static text content of the uploader.
The static text contains default text content of action buttons, file status, clear icon title, tooltips,
and text content of drag area. Define the [locale](../api/uploader/#locale) object for a culture and assign it to L10n load method.

The following are the list of keys and its values used in the uploader.

| Key | Description |
|------------------------|---------|
| Browse | To customize the browse button text.|
| Clear | To customize the clear button text.|
| Upload | To customize the upload button text. |
| dropFilesHint | To customize the drop area text. |
| uploadFailedMessage | To customize the status text when  the file is failed to upload.|
| uploadSuccessMessage | To customize the status text when  the file is uploaded successfully.|
| removedSuccessMessage | To customize the status text when  the file is removed the successfully from the server.|
| removedFailedMessage | To customize the status text while the file is failed to remove.|
| inProgress | To customize the status text while the upload is in progress.|
| pauseUpload | To customize the status text while the uploading is paused.|
| fileUploadCancel | To customize the status text when uploading is cancelled.|
| readyToUploadMessage | To customize the status text when the file is selected and ready to upload.|
| invalidMaxFileSize | To customize the status text when the file size is greater than the maximum file size.|
| invalidFileType | To customize the status text when the file type is invalid.|
| invalidMinFileSize | To customize the status text when the file size is less than the minimum file size. |
| remove | To customize tooltip text for remove icon. |
| cancel | To customize tooltip text for cancel icon. |
| delete | To customize tooltip text for delete icon. |

{% tab template="uploader/localization" %}

```html
<template>
    <div class="col-lg-8 control-section uploader chunk">
        <div class="control_wrapper">
            <ejs-uploader id='validation' name="UploadFiles" :asyncSettings= "path" ref="uploadObj" :locale='locale' :autoUpload = 'false'>
            </ejs-uploader>
        </div>
    </div>
</template>
<script>
import Vue from "vue";
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
import { FileInfo } from '@syncfusion/ej2-vue-inputs/uploader';
import { detach, L10n } from '@syncfusion/ej2-base';
Vue.use(UploaderPlugin);
    L10n.load({
    "fr-CH": {
        "uploader": {
            "invalidMinFileSize" : "La taille du fichier est trop petite! S'il vous plaît télécharger des fichiers avec une taille minimale de 10 Ko",
            "invalidMaxFileSize" : "La taille du fichier dépasse 28 Mo",
            "invalidFileType" : "Le type de fichier n'est pas autorisé",
            "Browse"  : "Feuilleter",
            "Clear" : "Clair",
            "Upload" : "Télécharger",
            "dropFilesHint" : "ou Déposer des fichiers ici",
            "uploadFailedMessage" : "Impossible d'importer le fichier",
            "uploadSuccessMessage" : "Fichier téléchargé avec succès",
            "removedSuccessMessage": "Fichier supprimé avec succès",
            "removedFailedMessage": "Le fichier n'a pas pu être supprimé",
            "inProgress": "Téléchargement",
            "readyToUploadMessage": "Prêt à télécharger",
            "remove": "Retirer",
            "cancel": "Annuler",
            "delete": "Supprimer le fichier"
        }
    }
})
export default {
 data: function(){
        return {
          path:  {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
          },
          extensions: '.doc, .docx, .xls, .xlsx',
          locale: 'fr-CH'
        }
    }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
    #container {
        visibility: hidden;
        padding-left: 5%;
        width: 100%;
    }
    #loader {
        color: #008cff;
        font-family: 'Helvetica Neue','calibiri';
        font-size: 14px;
        height: 40px;
        left: 45%;
        position: absolute;
        top: 45%;
        width: 30%;
    }
</style>
```

{% endtab %}

>You can also explore [Vue File Upload](https://www.syncfusion.com/vue-ui-components/vue-file-upload) feature tour page for its groundbreaking features. You can also explore our [Vue File Upload example](https://ej2.syncfusion.com/vue/demos/#/material/uploader/default.html) to understand how to browse the files which you want to upload to the server.
