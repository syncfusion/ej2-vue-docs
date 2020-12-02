# Validation Rules

## Default Rules

The `FormValidator` has following default validation rules, which are used to validate the form.

| Rules | Description | Example |
| ------------- | ------------- | ------------- |
| `required` | The form input element must have any input values | a or 1 or - |
| `email` | The form input element must have valid `email` format values | `form@syncfusion.com` |
| `url` | The form input element must have valid `url` format values | <http://syncfusion.com/> |
| `date` | The form input element must have valid `date` format values | 05/15/2017 |
| `dateIso` | The form input element must have valid `dateISO` format values | 2017-05-15 |
| `number` | The form input element must have valid `number` format values | 1.0 or 1 |
| `digit` | The form input element must have valid `digit` values | 1 |
| `maxLength` | Input value must have less than or equal to `maxLength` character length | if `maxLength: 5`, **check** is valid and **checking** is invalid |
| `minLength` | Input value must have greater than or equal to `minLength` character length | if `minLength: 5`, **testing** is valid and **test** is invalid |
| `rangeLength` | Input value must have value between `rangeLength` character length | if `rangeLength: [4,5]`, **test** is valid and **key** is invalid |
| `range` | Input value must have value between `range` number | if `range: [4,5]`, **4** is valid and **6** is invalid |
| `max` | Input value must have less than or equal to `max` number | if `max: 3`, **3** is valid and **4** is invalid |
| `min` | Input value must have greater than or equal to `min` number | if `min: 4`, **5** is valid and **2** is invalid |
| `regex` | Input value must have valid `regex` format | if `regex: '^[A-z]+$'`, **a** is valid and **1** is invalid |

> The [`rules`](https://ej2.syncfusion.com/documentation/api/form-validator/#rules) option should map the input element's `name` attribute.
> The `FormValidator` library only validates the mapped input elements.

## Defining Custom Rules

You can also define custom rules in the [`rules`](https://ej2.syncfusion.com/documentation/api/form-validator/#rules) property and validate the form with custom logics.

The custom validation method need to return the boolean value for validating an input.

{% tab template="form-validator/form-validation", iframeHeight="600px" %}

```html
<template>
    <div>
        <div class="col-lg-12 control-section form-support">
            <div class="control_wrapper" id="control_wrapper">
                <!-- Initialize Uploader -->
                <form id="form1" action="saveFiles.ashx" method="post">
                    <h4 class="form-title">Form Validator</h4>
                    <div class="form-group" style="padding-top: 11px;">
                        <div class="e-float-input">
                            <input type="text" id="name" name="Name" data-required-message="* Enter your name" required="" data-msg-containerid="nameError">
                                <span class="e-float-line"></span>
                                <label class="e-float-text e-label-top" for="name">Name</label>
                        </div>
                        <div id="nameError"></div>
                    </div>
                    <div class="form-group" style="padding-top: 11px;">
                        <div class="e-float-input">
                            <input type="email" id="email" name="Email" data-validation="email" data-required-message="* Enter your email" required="" data-msg-containerid="mailError">
                                <span class="e-float-line"></span>
                                <label class="e-float-text e-label-top" for="email">Email</label>
                        </div>
                        <div id="mailError"></div>
                    </div>
                    <div class="form-group" style="padding-top: 11px;">
                        <div class="e-float-input">
                            <input type="number" id="mobileno" name="MobileNo" data-required-message="* Enter your mobile number" required="" data-msg-containerid="noError">
                                <span class="e-float-line"></span>
                                <label class="e-float-text e-label-top" for="mobileno">Mobile No</label>
                        </div>
                        <div id="noError"></div>
                    </div>
                    <div class="form-group" style="padding-top: 11px;">
                        <div class="e-float-input upload-area">
                            <input type="text" id="upload" name="upload" readonly="" data-required-message="* Choose any file" required="" data-msg-containerid="uploadError">
                            <ejs-uploader id='fileupload' name="UploadFiles" :autoUpload= "isAuto" :selected= "onFileSelect"
                            allowedExtensions= "image/*" :dropArea = "dropElement" :multiple= 'false' ></ejs-uploader>
                            <button id="browse" class="e-control e-btn e-info">Browse...</button>
                            <span class="e-float-line"></span>
                            <label class="e-float-text e-label-top" for="upload">Choose a file</label>
                        </div>
                        <div id="uploadError"></div>
                    </div>
                    <div class="form-group" style="padding-top: 11px;">
                        <div class="e-float-input">
                            <textarea class="address-field" rows="4" id="Address" name="Address"></textarea>
                            <span class="e-float-line"></span>
                            <label class="e-float-text e-label-top" for="address">Address</label>
                        </div>
                    </div>
                </form>
                <div class="submitBtn">
                    <button class="submit-btn e-btn" id="submit-btn">Submit</button>
                </div>
                <ejs-dialog id='uploadAlert' :header='header' showCloseIcon=true :width= 'width' :content= 'dlgContent' :target= 'dlgTarget'
                :isModal= 'Modal' :visible="false" :animationSettings= 'animation' ref="dialogObj" >
                </ejs-dialog>
            </div>
        </div>
    </div>
</template>

<script>
import Vue from 'vue';
import { UploaderPlugin } from '@syncfusion/ej2-vue-inputs';
import { FormValidator  } from '@syncfusion/ej2-vue-inputs';
import { DialogPlugin } from '@syncfusion/ej2-vue-popups';
Vue.use(UploaderPlugin);
Vue.use(DialogPlugin);

export default {
    data: function() {
        return {
          path:  {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
          },
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
          options : {
        //Initialize the CustomPlacement.
            customPlacement: function(inputElement, errorElement) {
                inputElement = inputElement.closest('.form-group').querySelector('.error');
                inputElement.parentElement.appendChild(errorElement);
            },
                rules: {
                    'Name': {
                        required: true
                    },
                    'Email': {
                        required: true
                    },
                    'upload': {
                        required: true
                    }
                }
            }
        }
    },
    mounted: function () {
        document.getElementById('browse').onclick = () => {
            document.getElementsByClassName('e-file-select-wrap')[0].querySelector('button').click();
            return false;
        };
        let localObj = this;
        document.getElementById('submit-btn').onclick = function() {
            localObj.onFormSubmit();
        };
        this.formObj = new FormValidator('#form1', this.options);
    },
    methods:{
        onFormSubmit: function() {
            let formStatus = this.formObj.validate();
            if (formStatus) {
                this.formObj.element.reset();
                this.$refs.dialogObj.show();
            }
        },
        onFileSelect: function(args) {
            let inputElement = document.getElementById('upload');
            inputElement.value = args.filesData[0].name;
        },
    }
}
</script>
<style>
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
    .form-support .control_wrapper {
            max-width: 400px;
            margin: auto;
        }
        .form-support .address-field {
            max-height: 50px;
            resize: none;
        }
        .form-support #control_wrapper {
                max-width: 500px;
                margin: auto;
                border: 0.5px solid #BEBEBE;
                box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.36);
                padding: 1% 4% 2%;
                background: #f9f9f9;
        }

        .form-support .e-error {
            padding-top:3px;
        }
        .form-support .e-upload {
            width: 100%;
            position: relative;
            margin-top: 15px;
        }
        .form-support .control_wrapper .e-upload .e-upload-drag-hover {
            margin: 0;
        }

        .form-support .submit-btn {
            margin-top: 15px;
        }
        .form-support .submitBtn .desc {
            margin: 2% 20% 0% 18%;
        }
        @media only screen and (max-width: 500px) {
            .form-support .submitBtn .desc {
                margin: 12px;
            }
            .form-support .upload-area, .e-bigger .upload-area {
                width: 60%;
            }
        }
        .form-support .submitBtn {
            position: relative;
            text-align: center;
        }
        .form-support .success .successmsg {
            border: 0.5px solid green;
            padding: 10%;
            color: green;
        }
        .form-support form#form1 {
            position: relative;
            top: 14%;
        }
        .form-support .e-upload {
            display: none;
        }
        .form-support input.choose-file{
            width: 60%;
        }
        .form-support button#browse {
            float: right;
            margin-right: -115px;
            margin-top: -29px;
            position: relative;
        }
        .fabric .form-support #browse, .highcontrast .form-support #browse {
            top: -3px;
        }
        .bootstrap .form-support #browse {
            top: -6px;
        }
        .form-support .form-title {
            text-align: center;
        }
        #form1 .e-float-input:not(.e-input-group), #form1 .e-float-input.e-control-wrapper:not(.e-input-group) {
            display: inherit;
        }

         input#mobileno::-webkit-inner-spin-button, input#mobileno::-webkit-outer-spin-button {
            -webkit-appearance: none;
            margin: 0;
        }

        .e-float-input.upload-area {
            width: 70%;
        }
    </style>
```

{% endtab %}

## Adding or Removing Rules

After creating `FormValidator` object, you can add
more rules to an input element by using [`addRules`](https://ej2.syncfusion.com/documentation/api/form-validator/#addrules)
method and you can also remove an existing rule from the input element by using [`removeRules`](https://ej2.syncfusion.com/documentation/api/form-validator/#removerules)
method.

```typescript

import {FormValidator, FormValidatorModel} from '@syncfusion/ej2-vue-inputs';

export default {
    data: function() {
        return {
          options : {
        //Initialize the CustomPlacement.
            customPlacement: function(inputElement, errorElement) {
                inputElement = inputElement.closest('.form-group').querySelector('.error');
                inputElement.parentElement.appendChild(errorElement);
            },
                rules: {
                    'Name': {
                        required: true
                    },
                    'Email': {
                        required: true
                    },
                    'upload': {
                        required: true
                    }
                }
            }
        }
    }
let formObject: FormValidator = new FormValidator('#form-element', options);
// Add email rule to user element
formObject.addRules('user', { maxLength: 7 });
// Remove number rule from age element
formObject.removeRules('age', ['number']);
```

## Validating a Single Element

The [`validate`](https://ej2.syncfusion.com/documentation/api/form-validator/#validate) method have an optional argument, where you can pass an input element's
name attribute to validate its value against the defined rule.

```typescript
import {FormValidator, FormValidatorModel} from '@syncfusion/ej2-vue-inputs';

export default {
    data: function() {
        return {
          options : {
        //Initialize the CustomPlacement.
            customPlacement: function(inputElement, errorElement) {
                inputElement = inputElement.closest('.form-group').querySelector('.error');
                inputElement.parentElement.appendChild(errorElement);
            },
                rules: {
                    'Name': {
                        required: true
                    },
                    'Email': {
                        required: true
                    },
                    'upload': {
                        required: true
                    }
                }
            }
        }
    }
let formObject: FormValidator = new FormValidator('#form-element', options);
// Add email rule to user element
formObject.validate('user');

```