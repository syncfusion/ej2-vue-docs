# Form slider with FormValidator

The Slider component can be validated using our [FormValidator](https://ej2.syncfusion.com/documentation/form-validator/?lang=typescript). The following steps walk-through slider validation.

* Render slider component inside a form.
* Bind [changed]../api/slider#changed) event in the slider component to validate the slider value when the value changes.
* Initialize and render FormValidator for the form using form ID.

```typescript

// Initialize Form validation
let formObj: FormValidator;
formObj = new FormValidator("#formId", options);

```

* Set the required property in the FormValidator [rules](../api/form-validator#rules) collection. Here, the [min](../api/slider#min) property of slider that sets the minimum value in the slider component is set, and it has hidden input as enable `validateHidden` property is set to true.

```typescript

// Slider element
<ejs-slider id="default" name="slider"></ejs-slider>

// sets required property in the FormValidator rules collection
let options: FormValidatorModel = {
  rules: {
    'default': {
      validateHidden: true,
      min: [6, "You must select value greater than 5"]
    }
  }
};

```

> Form validation is done either by ID or name value of the slider component. Above ID of the slider is used to validate it.

Using slider name: Render slider with name attribute. In the following code snippet, name attribute value of ?slider? is used for form validation.

```typescript

// Slider element
<ejs-slider id="default" name="slider"></ejs-slider>

// sets required property in the FormValidator rules collection
let options: FormValidatorModel = {
  rules: {
    'slider': {
      validateHidden: true,
      min: [6, "You must select value greater than 5"]
    }
  }
};

```

* Validate the form using [validate](https://ej2.syncfusion.com/documentation/api/form-validator#validate) method, and it validates the slider value with the defined rules collection and returns the result. If user selects the value less than the minimum value, form will not submit.

```typescript

formObj.validate();

```

* Slider validation can be done during value changes in slider. Refer to the following code snippet.

```typescript

// change event handler for slider
onChanged(args) {
  formObj.validate();
}

```

The `FormValidator` has following default validation rules, which are used to validate the Slider component.

| Rules | Description | Example |
| ------------- | ------------- | ------------- |
| `max` | Slider component must have value less than or equal to `max` number | if `max: 3`, **3** is valid and **4** is invalid |
| `min` | Slider component must have value greater than or equal to `min` number | if `min: 4`, **5** is valid and **2** is invalid |
| `regex` | Slider component must have valid value in `regex` format | if `regex: '/4/`, **4** is valid and **1** is invalid |
| `range` | Slider component must have value between `range` number | if `range: [4,5]`, **4** is valid and **6** is invalid |

{% tab template="range-slider/thumb", isDefaultActive=true %}

```html
<template>
   <div id='app'>
     <div class="col-lg-12 control-section">
            <div class="content-wrapper" style="margin-bottom: 25px;overflow-x: hidden">
                <div class="form-title">
                    <span>Min</span>
                </div>
                <form id="formMinId" class="form-horizontal">
                    <div class="form-group">
                        <div class="e-float-input">
                            <ejs-slider id="min-slider" name="min-slider" type='MinRange'  value= 30 :ticks='ticks' v-on:changed='onMinChanged'></ejs-slider>
                        </div>
                    </div>
                </form>
                <div class="form-title">
                    <span>Max</span>
                </div>
                <form id="formMaxId" class="form-horizontal">
                    <div class="form-group">
                        <div class="e-float-input">
                            <ejs-slider id="max-slider" name="max-slider" type='MinRange'  value= 30 :ticks='ticks' v-on:changed='onMaxChanged'></ejs-slider>
                        </div>
                    </div>
                </form>
                <div class="form-title">
                    <span>Value</span>
                </div>
                <form id="formValId" class="form-horizontal">
                    <div class="form-group">
                        <div class="e-float-input">
                            <ejs-slider id="val-slider" name="val-slider" type='MinRange'  value= 30 :ticks='ticks' v-on:changed='onValChanged'></ejs-slider>
                        </div>
                    </div>
                </form>
                <div class="form-title">
                    <span>Range</span>
                </div>
                <form id="formRangeId" class="form-horizontal">
                    <div class="form-group">
                        <div class="e-float-input">
                            <ejs-slider id="range-slider" name="range-slider" type='MinRange'  value= 30 :ticks='ticks' v-on:changed='onRangeChanged'></ejs-slider>
                        </div>
                    </div>
                </form>
            </div>
        </div>
   </div>
</template>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
  @import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
    #app {
        height: 40px;
        position: absolute;
        width: 98%;
    }

    .highcontrast form {
        background: #000000
    }

    /* csslint ignore:start */
    .highcontrast label.e-custom-label,
    .highcontrast label.e-float-text,
    .highcontrast label.salary,
    .highcontrast input::placeholder,
    .highcontrast .e-float-input label.e-float-text {
        color: #fff !important;
        line-height: 2.3;
    }
    /* csslint ignore:end */

    .e-error,
    .e-float-text {
        font-weight: 500;
    }

    table,
    td,
    th {
        padding: 5px;
    }

    .form-horizontal .form-group {
        margin-left: 0;
        margin-right: 0;
    }

    form {
        border: 1px solid #ccc;
        box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.36);
        border-radius: 5px;
        background: #f9f9f9;
        padding: 23px;
        padding-bottom: 20px;
        margin: auto;
        max-width: 650px;
    }

    .form-title {
        width: 100%;
        text-align: center;
        padding: 10px;
        font-size: 16px;
        font-weight: 600;
        color: black;
    }
</style>
<script>
import Vue from 'vue';
import { SliderPlugin } from "@syncfusion/ej2-vue-inputs";
Vue.use(SliderPlugin);
import { FormValidator, FormValidatorModel } from '@syncfusion/ej2-inputs';
export default {
  data: function() {
   return {
            ticks:{ placement: 'Before', largeStep: 20, smallStep: 5, showSmallTicks: true }
    };
  },
  methods:{
        onMinChanged(args) {
            // sets required property in the FormValidator rules collection
            let minOptions = {
            rules: {
                'min-slider': {
                validateHidden: true,
                min: [40, "You must select value greater than or equal to 40"]
                }
            }
            };
            // Initialize Form validation
            let formMinObj;
            formMinObj = new FormValidator("#formMinId", minOptions);
            // validate the slider value in the form
            formMinObj.validate();
        },
        onMaxChanged(args) {
            // sets required property in the FormValidator rules collection
            let maxOptions = {
            rules: {
                'max-slider': {
                validateHidden: true,
                max: [40, "You must select value less than or equal to 40"]
                }
            }
            };
                // Initialize Form validation
            let formMaxObj;
            formMaxObj = new FormValidator("#formMaxId", maxOptions);
            // validate the slider value in the form
            formMaxObj.validate();
        },
        onValChanged(args) {
            // sets required property in the FormValidator rules collection
            let valOptions = {
            rules: {
                'val-slider': {
                validateHidden: true,
                regex: [/40/, "You must select value equal to 40"]
                }
            }
            };
                // Initialize Form validation
            let formValObj;
            formValObj = new FormValidator("#formValId", valOptions);
            // validate the slider value in the form
            formValObj.validate();
        },
        onRangeChanged(args) {
            // sets required property in the FormValidator rules collection
            let rangeOptions = {
            rules: {
                'range-slider': {
                validateHidden: true,
                range: [40, 80, "You must select values between 40 and 80"]
                }
            }
            };
                // Initialize Form validation
            let formRangeObj;
            formRangeObj = new FormValidator("#formRangeId", rangeOptions);
            // validate the slider value in the form
            formRangeObj.validate();
        }
    }
}
</script>

```

{% endtab %}
