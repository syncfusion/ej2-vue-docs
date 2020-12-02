---
title: "How To"
component: "DatePicker"
description: "Miscellaneous aspects of customizing the date picker"
---

# Client side validation

To achieve the client side validation in a DatePicker component by using
[Essential JavaScript 2 FormValidator](http://ej2.syncfusion.com/documentation/form-validator). It provides an option to customize the feedback error messages to the corresponding
fields to take action to resolve the issue.

In the below example, the required field validation is implemented by mapping
the name attribute
value to the rules property. It will validate the DatePicker component and display the validation
message when the textbox value is empty during form post back or focus out.

{% tab template="datepicker/getting-started", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
    <div class='wrap'>
      <form id="form-element" class="form-horizontal">
           <div class="form-group" style="padding-top: 11px;">
                <div class="col-lg-8">
                    <ejs-datepicker id="datepicker" name="date" :change="onValueChange" class="form-control" placeholder='Select a date'></ejs-datepicker>
                </div>
            </div>
      </form>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DatePickerPlugin } from "@syncfusion/ej2-vue-calendars";
import { FormValidator } from '@syncfusion/ej2-inputs';

Vue.use(DatePickerPlugin);
export default {
    data: function() {
        return {
          formObj: '',
          options : {
            customPlacement: function(inputelement, errorElement) {
                var parentElement = inputelement.closest('.form-group');
                parentElement.appendChild(errorElement);
            },
            rules: {
                'date': {
                    required: true
                }
            }
          }
        }
    },
  mounted: function () {
      this.formObj = new FormValidator('#form-element', this.options);
  },
    methods:  {
       onValueChange: function(args) {
           this.formObj.validate();
        }
    }
}
</script>
<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrap {
    margin: 0 auto;
    width: 240px;
}
</style>
```

{% endtab %}