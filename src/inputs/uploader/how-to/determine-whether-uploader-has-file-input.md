---
title: "Determine whether uploader has file input"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Determine whether uploader has file input (required validation)

By setting **required** attribute to uploader input element, you can validate the file input has any value in it.
In the below sample, set required attribute to the uploader input element and showcase the validation failure message using `data-required-message` attribute.

{% tab template="uploader/invisible" %}

```html
<template>
        <div class="col-lg-12 control-section">
            <h4 class="form-title">Photo Contest</h4>
        <div class="control_wrapper" id ="control_wrapper">
            <form id="form1" method="post">
                <div class="form-group" style="padding-top: 40px; float: left">
                    <div class="e-float-input">
                        <input type="text" id="name" name="name" data-required-message="* Enter your name" required="" data-msg-containerid="nameError">
                        <span class="e-float-line"></span>
                        <label class="e-float-text e-label-top" for="name">Name</label>
                    </div>
                    <div id="nameError"></div>
                </div>
                <div id="dropArea">
                    <div id="uploadError" style='float: right;'></div>
                    <div id='customBrowse' class="form-group dropUpload">   Drop image here...
                    <ejs-uploader ref="uploadObj" id='defaultfileupload' name="UploadFiles" :selected="onFileSelect" :autoUpload="autoUpload"></ejs-uploader>
                    </div>
                    </div>
                <div class="submitBtn">
                    <button type="button" class="submit-btn e-btn" id="submit-btn">Submit</button>
                    <div class="desc"><span>*This button is not a submit type and the form submit handled from externally.</span></div>
                    <ejs-dialog id='uploadAlert' :header='header' showCloseIcon=true :width= 'width' :content= 'dlgContent' :target= 'dlgTarget'
                :isModal= 'Modal' :visible="false" :animationSettings= 'animation' ref="dialogObj" >
                </ejs-dialog>
                </div>
            </form>
        </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
import { FormValidator  } from '@syncfusion/ej2-inputs';
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';
import { createElement, detach } from '@syncfusion/ej2-base';
Vue.use(UploaderPlugin);
Vue.use(DialogPlugin);

export default {
  data: function(){
        return {
          dropElement: '.control-fluid',
          extensions: '.jpg, .png',
          isAuto: false,
          formObj: '',
          header: 'Success',
          animation: {effect: 'zoom'},
          Modal: true,
          dlgTarget: '.control_wrapper',
          dlgContent: 'Your details have been updated successfully, Thank you.',
          width: '335px',
            autoUpload: false
        }
    },
    mounted: function() {
          let rules;
           let options = {
        //Initialize the CustomPlacement.
            customPlacement: function(inputElement, errorElement) {
                inputElement = inputElement.closest('.form-group').querySelector('.error');
                inputElement.parentElement.appendChild(errorElement);
            },
             rules = {
                    'Name': {
                        required: true
                    },
                    'upload': {
                        required: true
                    }
                }
            }
    this.formObj = new FormValidator('#form1', options);
let localObj = this;
document.getElementById('submit-btn').onclick =             function() {
            localObj.onFormSubmit();
        };
        document.getElementById('customBrowse').onclick = () => {
    document.getElementsByClassName('e-file-select-wrap')[0].querySelector('button').click();
};
  this.$refs.uploadObj.$el.setAttribute('data-required-message', '* Choose your image to upload');
   this.$refs.uploadObj.$el.setAttribute('required', '');
  this.$refs.uploadObj.$el.setAttribute('data-msg-containerid', 'uploadError');
    },
    methods:{
    customBrowse: function() {
        document.getElementsByClassName('e-file-select-wrap')[0].querySelector('button').click();
    },
    onFileSelect: function(args: any): void {
    if (args.filesData.length > 0) {
        if (document.getElementsByClassName('upload-image').length > 0) {
            detach(document.getElementsByClassName('imgWrapper')[0]);
        }
        let imageTag = createElement('IMG', { className: 'upload-image', attrs: { 'alt': 'Image' } });
let wrapper = createElement('span', { className: 'imgWrapper' });
        wrapper.appendChild(imageTag);
            let rootFile = document.getElementsByClassName('dropUpload')[0];
rootFile.insertBefore(wrapper, rootFile.firstChild);
        this.readURL(wrapper, args.filesData[0]);
    }
    args.cancel = true;
},
readURL: function(li, args) {
    let preview = li.querySelector('.upload-image');
    let file: File = args.rawFile;
    let reader: FileReader = new FileReader();
    reader.addEventListener('load', () => { preview.src = reader.result; }, false);
    if (file) { reader.readAsDataURL(file); }
},

onFormSubmit: function(){
let formStatus = this.formObj.validate();
if (formStatus) {
        this.formObj.element.reset();
        detach(document.getElementsByClassName('imgWrapper')[0]);
        this.$refs.dialogObj.show();
    }
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
    .address-field {
  resize: none;
}
input#fileupload {
    opacity: 0;
}
#dropArea .dropUpload .upload-image {
  height: 140px;
  width: 140px;
}
#dropArea .dropUpload {
  float: right;
  text-align: center;
  vertical-align: middle;
  line-height: 12;
  overflow: hidden;
  border: 1px dashed;
  width: 150px;
  height: 150px;
}
.e-upload {
  visibility: hidden;
}
#control_wrapper {
  max-width: 500px;
  margin: auto;
  border: 0.5px solid #BEBEBE;
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.36);
  padding: 1% 4% 7%;
  background: #f9f9f9;
}
.e-error {
  padding-top:3px;
}
.control_wrapper .e-upload .e-upload-drag-hover {
  margin: 0;
}

.submit-btn {
  margin-top: 145px;
}
.submitBtn .desc {
  margin: 2% 23% 0 18%;
}
.submitBtn {
  text-align: center;
}
.form-support {
  width: 100%;
}
.success .form-support {
  display: none;
}
.success .successmsg {
  border: 0.5px solid green;
  padding: 10%;
  color: green;
}
#form1 {
  position: relative;
  top: 14%;
}
.form-support td {
  width: 100%;
  padding-top:4%;
}
.e-upload {
  float: none;
}
.choose-file{
  width: 60%;
}
#browse {
  float: right;
  margin-right: -113px;
  margin-top: -27px;
}
.form-title {
  text-align: center;
}

</style>
```

{% endtab %}

>You can also explore [Vue File Upload](https://www.syncfusion.com/vue-ui-components/vue-file-upload) feature tour page for its groundbreaking features. You can also explore our [Vue File Upload example](https://ej2.syncfusion.com/vue/demos/#/material/uploader/default.html) to understand how to browse the files which you want to upload to the server.
