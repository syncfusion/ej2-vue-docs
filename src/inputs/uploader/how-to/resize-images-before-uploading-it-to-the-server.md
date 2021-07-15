---
title: "Resize images before uploading it to the server"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Resize images before uploading it to the server

You can customize the dimension of the images before uploading it to the server.
By using selected event, you can get the selected file information as type of an object. From the obtained image file information, create a new canvas and render an image with the custom dimensions. Refer the corresponding code snippet as follows.

```html
<template>
  <div>
    <div id="dropTarget">
        <span id="dropElement" class="droparea">Drop files here or <a href="" id="browse"><u>Browse</u></a> </span>
        <ejs-uploader id='template' :multiple='false' name="UploadFiles" :asyncSettings= "path" ref="uploadObj"
            :dropArea= "dropElement" :selected= "onFileSelect" :progress= "onFileUpload"
            :success= "onUploadSuccess" :failure= "onUploadFailed" :removing= "onFileRemove">
        </ejs-uploader>
    </div>
</div>
</template>

```

```typescript
<script>
import Vue from "vue";
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
import { FileInfo } from '@syncfusion/ej2-vue-inputs/uploader';
import { createSpinner, showSpinner, hideSpinner } from '@syncfusion/ej2-popups';
import { createElement, isNullOrUndefined, detach, EventHandler } from '@syncfusion/ej2-base';

Vue.use(UploaderPlugin);

export default Vue.extend({
    data: function() {
        return {
          path:  {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
          },
          dropElement: '#dropElement',
          filesList: [],
          filesDetails: [],
          parentElement: '',
          progressbarContainer: ''
        }
    },
    mounted: function () {
        document.getElementById('browse').onclick = function() {
        document.getElementsByClassName('e-file-select-wrap')[0].querySelector('button').click();
        return false;
    };
    },
    methods:{
        onFileSelect: function (args) {
            args.cancel = true;
            if (isNullOrUndefined(document.getElementById('dropTarget').querySelector('.upload-list-root'))) {
                this.parentElement = createElement('div', { className: 'upload-list-root' });
                this.parentElement.appendChild(createElement('ul', {className: 'ul-element' }));
                document.getElementById('dropTarget').appendChild(this.parentElement);
            }
            for (let i = 0; i < args.filesData.length; i++) {
                this.formSelectedData(args.filesData[i]);
            }
            this.filesDetails = this.filesDetails.concat(args.filesData);
            let file = args.filesData[0].rawFile;
            let width;
            let height;
            let img = document.createElement("img");
            let reader = new FileReader();
            reader.onload = function(e) { img.src = e.target.result; };
            reader.readAsDataURL(file);
            let imgs = new Image();
            let localObj = this;
            img.onload = function() {
                console.log(this);
                width = this.width;
                height = this.height;
                localObj.onNewImg(height, width, img, args.filesData[0]);
            },
            imgs.src = img.src;
        },

        // to create canvas and update our custom dimensions
        onNewImg(height, width, img, file) {
            let canvas = document.createElement("canvas");
            let ctx = canvas.getContext("2d");
            ctx.drawImage(img, 0, 0);
            let MAX_WIDTH = 1000;
            let MAX_HEIGHT = 600;
            if (width > height) {
                if (width > MAX_WIDTH) {
                    height *= MAX_WIDTH / width;
                    width = MAX_WIDTH;
                }
            } else {
                if (height > MAX_HEIGHT) {
                    width *= MAX_HEIGHT / height;
                    height = MAX_HEIGHT;
                }
            }
            canvas.width = width;
            canvas.height = height;
            let ctx1 = canvas.getContext("2d");
            ctx1.drawImage(img, 0, 0, width, height);
            let newImage = canvas.toDataURL("image/png");
            let blobBin = atob(newImage.split(',')[1]);
            let array = [];
            for(var i = 0; i < blobBin.length; i++) {
                array.push(blobBin.charCodeAt(i));
            }
            let newBlob = new Blob([new Uint8Array(array)], {type: 'image/png'});
            let newFile = this.createFile(newBlob, file);
             this.$refs.uploadObj.upload(newFile, true);
        },
        // To create File object to upload
        createFile(image, file) {
            let newFile = {
                name: file.name,
                rawFile: image,
                size: image.size,
                type: file.type,
                validationMessage: '',
                statusCode: '1',
                status: 'Ready to Upload'
            }
            return newFile;
        },
        formSelectedData: function ( selectedFiles) {
            let liEle = createElement('li',  { className: 'file-lists', attrs: {'data-file-name' : selectedFiles.name} });
            liEle.appendChild(createElement('span', {className: 'file-name ', innerHTML: selectedFiles.name }));
            liEle.appendChild(createElement('span', {className: 'file-size ', innerHTML: this.$refs.uploadObj.bytesToSize(selectedFiles.size) }));
            if (selectedFiles.statusCode === '1') {
                this.progressbarContainer = createElement('span', {className: 'progress-bar-container'});
                this.progressbarContainer.appendChild(createElement('progress', {className: 'progress', attrs: {value : '0', max : '100'}} ));
                liEle.appendChild(this.progressbarContainer);
            } else { liEle.querySelector('.file-name').classList.add('upload-fails'); }
            let closeIconContainer = createElement('span', {className: 'e-icons close-icon-container'});
            let localObj = this;
            closeIconContainer.addEventListener( 'click', function(e) {
                localObj.removeFiles(e);
            });
            liEle.appendChild(closeIconContainer); document.querySelector('.ul-element').appendChild(liEle);
            this.filesList.push(liEle);
        },

        onFileUpload: function(args) {
            let li = document.getElementById('dropTarget').querySelector('[data-file-name="' + args.file.name + '"]');
            let localObj = this;
            let progressValue = Math.round((args.e.loaded / args.e.total) * 100);
            if (!isNaN(progressValue)) {
                li.getElementsByTagName('progress')[0].value = progressValue;
            }
        },

        onUploadSuccess: function(args) {
            let spinnerElement = document.getElementById('dropTarget');
            let li= document.getElementById('dropTarget').querySelector('[data-file-name="' + args.file.name + '"]');
            if (!isNullOrUndefined(li.querySelector('.progress-bar-container'))) {
                detach(li.querySelector('.progress-bar-container'));
            }
            let localObj = this;
            if (args.operation === 'upload') {
                li.querySelector('.file-name').classList.add('upload-success');
                li.querySelector('.close-icon-container').classList.remove('remove-btn');
                li.querySelector('.close-icon-container').classList.add('delete-icon');
                (li.querySelector('.close-icon-container')).onclick = function() {
                    localObj.generateSpinner(li.querySelector('.close-icon-container'));
                };
                (li.querySelector('.close-icon-container')).onkeydown = function(e) {
                    if (e.keyCode === 13) {
                        localObj.generateSpinner(e.target.closest('.e-upload'));
                    }
                };
            }
            if (args.operation === 'remove') {
                this.filesDetails.splice(this.filesList.indexOf(li), 1);
                this.filesList.splice(this.filesList.indexOf(li), 1);
                detach(li);
                hideSpinner(li.querySelector('.close-icon-container'));
                detach(li.querySelector('.e-spinner-pane'));
            }
            alert(args.file.size);
        },

        generateSpinner: function(targetElement) {
            createSpinner({ target: targetElement, width: '25px' });
            showSpinner(targetElement);
        },

        onUploadFailed: function(args) {
            let li = document.getElementById('dropTarget').querySelector('[data-file-name="' + args.file.name + '"]');
            let localObj = this;
            li.querySelector('.file-name').classList.add('upload-fails');
            li.querySelector('.close-icon-container').classList.remove('remove-btn');
            if (args.operation === 'remove') {
                if (!isNullOrUndefined(li)) {
                    this.filesDetails.splice(this.filesList.indexOf(li), 1);
                    this.filesList.splice(this.filesList.indexOf(li), 1);
                    detach(li);
                }
            }
            if (args.operation === 'upload') {
                detach(li.querySelector('.progress-bar-container'));
            }
        },

        removeFiles: function(args) {
            if (!isNullOrUndefined(args.currentTarget)) {
                if (this.filesDetails[this.filesList.indexOf(args.currentTarget.parentElement)].statusCode === '3') { return;}
                if (this.filesDetails[this.filesList.indexOf(args.currentTarget.parentElement)].statusCode === '2' ) {
                    this.$refs.uploadObj.remove(this.filesDetails[this.filesList.indexOf(args.currentTarget.parentElement)]);
                } else  {
                    this.onFileRemove(args);
                }
            }
        },

        onFileRemove: function(args) {
            args.postRawFile = false;
            if (!isNullOrUndefined(args.currentTarget)) {
                if (this.filesDetails[this.filesList.indexOf(args.currentTarget.parentElement)].statusCode !== '2') {
                    detach(args.currentTarget.parentElement);
                    this.filesList.splice(this.filesList.indexOf(args.currentTarget.parentElement), 1);
                }
            }
        }
    }
});

</script>

```

```html

<style>
    @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
    #dropTarget {
        min-height: 50px;
        padding-top: 15px;
        position: relative;
    }

    #dropElement {
        padding: 3% 30% 3%;
        display: inherit;
        border: 1px dashed #c3c3cc
    }

    .droparea {
       font-size: 13px;
    }

    .e-file-select-wrap {
        display: none;
    }

    .e-upload {
        float: none;
        border: none;
    }

    .ul-element {
        list-style: none;
        width: 100%;
        padding-left: 0;
    }

    .file-name {
        padding: 8px 6px 8px 0;
        font-size: 13px;
        width: 46%;
        display: inline-block;
        position: relative;
        top: 4px;
    }

    .file-size {
        padding: 4px;
        font-size: 13px;
        width: 18%;
        display: inline-block;
        position: relative;
    }

    .file-lists {
        border: 1px solid lightgray;
        padding: 0 6px 0 14px;
        margin-top: 15px;
        position: relative;
        background: rgba(0, 0, 0, 0.04);
    }

    .file-size, .file-name {
        font-family: "Helvetica Neue", "Helvetica", "Arial", "sans-serif";
        text-overflow: ellipsis;
        overflow: hidden;
        white-space: nowrap;
    }

    span.progress-bar-container {
        display: block;
        float: right;
        height: 20px;
        right: 13%;
        top: 14px;
        position: relative;
        width: 20%;
    }

    .progress{
        width: 100%;
        height: 15px;
        -webkit-appearance: none;
    }

    .close-icon-container
    {
        cursor: pointer;
        font-size: 11px;
        height: 24px;
        margin: 0 12px 0 22px;
        padding: 0;
        position: absolute;
        right: 0;
        width: 24px;
        top: 6px;
    }
    .close-icon-container.remove-btn {
       display: none;
    }

    .close-icon-container.e-icons::before {
        left: 7px;
        position: inherit;
        top: 7px;
        content: '\e932';
    }

    .close-icon-container.delete-icon::before {
        content: '\e94a';
    }

    .close-icon-container:hover {
        background-color: rgba(0, 0, 0, 0.12);
        border-color: transparent;
        border-radius: 50%;
        box-shadow: 0 0 0 transparent;
    }
    .upload-success {
       color: #2bc700;
    }

    .upload-fails {
        color: #f44336;
    }

    progress::-webkit-progress-bar {
        border: 1px solid lightgrey;
        background-color: #ffffff;
        border-radius: 2px;
    }
    #dropTarget progress {
        border: 1px solid lightgrey;
        background-color: #ffffff;
        border-radius: 2px;
    }
    progress::-webkit-progress-value {
        border-radius: 2px;
        background-color: #ff4081;
    }
    #dropTarget span a {
        color:#ff4081;
    }
</style>

```

>You can also explore [Vue File Upload](https://www.syncfusion.com/vue-ui-components/vue-file-upload) feature tour page for its groundbreaking features. You can also explore our [Vue File Upload example](https://ej2.syncfusion.com/vue/demos/#/material/uploader/default.html) to understand how to browse the files which you want to upload to the server.