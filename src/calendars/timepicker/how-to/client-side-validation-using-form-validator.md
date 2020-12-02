---
title: "How To"
component: "TimePicker"
description: "Miscellaneous aspects of customizing the time picker"
---

# Client side validation using FormValidator

To achieve client side validation in a TimePicker component, use
[Essential JavaScript 2 FormValidator](https://ej2.syncfusion.com/documentation/form-validator). It provides an option to customize feedback error messages to the corresponding
fields for taking action and resolving the issue.

In the following example, the required field validation is implemented by mapping the name attribute
value to the rules property. It validates the TimePicker component and displays the validation
message when the textbox value is empty during form post back or focus out.

{% tab template="timepicker/validation", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
    <div class='wrap'>
      <form id="form-element" class="form-horizontal">
           <div class="form-group" style="padding-top: 11px;">
                <div class="col-lg-8">
                     <ejs-timepicker id="time" name="time" :change="onTimeChange" class="form-control" placeholder='Select a Time'></ejs-timepicker>
                </div>
            </div>
      </form>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { TimePickerPlugin } from "@syncfusion/ej2-vue-calendars";
import { FormValidator } from '@syncfusion/ej2-inputs';

Vue.use(TimePickerPlugin);
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
                'time': {
                    required: true
                }
            }
          }
        }
    },
  mounted: function () {
      this.formObj = new FormValidator('#form-element', this.options);
  },
  methods: {
      onTimeChange: function() {
          this.formObj.validate();
      }
  }
}
</script>
<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrap {
    margin: 0 auto;
    width: 240px;
}
</style>
```

{% endtab %}