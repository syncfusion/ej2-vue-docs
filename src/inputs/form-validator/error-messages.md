# Error Messages

The `FormValidator` provides default error messages for all default validation rules.
It is tabulated as follows

| Rules | message |
| ------------- | ------------- |
| `required` | This field is required. |
| `email` | Please enter a valid email address. |
| `url` | Please enter a valid URL. |
| `date` | Please enter a valid date. |
| `dateIso` | Please enter a valid date ( ISO ). |
| `number` | Please enter a valid number. |
| `digit` | Please enter only digits. |
| `maxLength` | Please enter no more than {0} characters. |
| `minLength` | Please enter at least {0} characters. |
| `rangeLength` | Please enter a value between {0} and {1} characters long. |
| `range` | Please enter a value between {0} and {1}. |
| `max` | Please enter a value less than or equal to {0}. |
| `min` | Please enter a value greater than or equal to {0}. |
| `regex` | Please enter a correct value. |

## Customizing Error Messages

The default error message for a rule can be customizable by defining it along with concern rule object as follows.

{% tab template="form-validator/form-validation-events", iframeHeight="600px" %}

```html

<template>
  <div class="wrap">

    <form id="form-element" class="form-horizontal">
      <div class="form-group">
        <div class="col-sm-3 control-label">Select Date</div>
        <div class="col-sm-6">
          <ejs-datepicker
            id="datepicker"
            name="date"
            class="form-control"
            placeholder="Select a date"
          ></ejs-datepicker>
          <div class="error-element"></div>
        </div>
      </div>
    </form>
      </template>

<script>
import Vue from "vue";
import { DatePickerPlugin } from "@syncfusion/ej2-vue-calendars";
import { FormValidator } from "@syncfusion/ej2-vue-inputs";
import { queryParams } from "@syncfusion/ej2-base";
import { throws } from "assert";
Vue.use(DatePickerPlugin);

export default {
  name: "App",
  mounted() {
      var options = {
      rules: {
        date: { required: [true, "Select any value"] }
      },
      customPlacement: function(element, errorElement) {
        document.querySelector(".error-element").appendChild(errorElement);
      },
    };
     // defines FormValidator to validate the TimePicker
        var formObject = new FormValidator("#form-element", options);
  }
}
</script>
<style>
@import "../../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
.wrap {
  margin-top: 10px;
}
.error-element {
  margin-top: 5px;
}
#list_event {
  margin-top: 60px;
  padding-left: 5px;
  min-width: 200px;
}

#evt {
  border: 1px solid #dcdcdc;
  padding: 10px;
  min-width: 10px;
}

.eventarea {
  min-width: 250px;
}

#EventLog b {
  color: #388e3c;
}

.evtbtn {
  margin-top: 40px;
  margin-left: 70px;
}
</style>

```

{% endtab %}
