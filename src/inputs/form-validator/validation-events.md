# Validation Events

Validation events have two types of events. These are

* validationBegin
* validationComplete

## Validation Begin

`validationBegin` event triggers before the validation starts and also it invoke for each rules in validation process. Please find the below code snippet.

```typescript

validationBegin: function(args) {
        // ("Validation begin");
      },
```

The following values are passed in `args`. You can use this values in event validation.

| Fields  | Description |
|---------|-------------|
|`element`| Specifies the input element |
|`name`   | Specifies the event name (validationBegin)  |
|`param`  | Specifies the param value (true/false)  |
|`value`  | Specifies the input value  |

## Validation Complete

`validationComplete` event triggered after validation is completed and also it invoke  for each rules in validation process. Please find the below code snippet.

```typescript

validationComplete: function(args) {
        // ("Validation complete");
      }
```

The following values are passed in `args`. You can use this values in event validation.

| Fields  | Description |
|---------|-------------|
|`element`| Specifies the input element |
|`name`   | Specifies the event name (validationComplete)  |
|`param`  | Specifies the param value (true/false)  |
|`value`  | Specifies the input value  |
|`status` | Specifies the status (success/failure) |
|`inputName` | Specifies the type of input  |

Please find the simple sample for validation events.

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

      <div id="list_event">
        <h4>
          <b>Event Trace</b>
        </h4>
        <div id="evt">
          <ul id="eList"></ul>
        </div>
      </div>
    </form>

    <div class="evtbtn">
      <ejs-button id="clear" @click.native="onClick">Clear</ejs-button>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import { DatePickerPlugin } from "@syncfusion/ej2-vue-calendars";
import { FormValidator } from "@syncfusion/ej2-vue-inputs";
import { queryParams } from "@syncfusion/ej2-base";
import { ButtonPlugin } from "@syncfusion/ej2-vue-buttons";
import { throws } from "assert";
Vue.use(DatePickerPlugin);
Vue.use(ButtonPlugin);

export default {
  name: "App",
  methods:{
     onClick: function(event) {
        document.getElementById("eList").innerHTML = "";
      },

  },
  mounted() {
    var options = {
      rules: {
        date: { required: true }
      },
      validationBegin: function(args) {
        this.appendElement("Validation begin <hr>");
      },
      appendElement: function(html) {
        let span = document.createElement("span");
        span.innerHTML = html;
        let log = document.getElementById("eList");
        log.insertBefore(span, log.firstChild);
      },
      customPlacement: function(element, errorElement) {
        document.querySelector(".error-element").appendChild(errorElement);
      },
      validationComplete: function(args) {
        if (args.status === "success") {
          this.appendElement("Validation complete success <hr>");
        } else {
          this.appendElement("Validation complete failure <hr>");
        }
      },
    };
    // defines FormValidator to validate the TimePicker
    var formObject = new FormValidator("#form-element", options);
  }
};
</script>

<style>
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

In the above code example, after completion of validation, the status of the validation process is passed as arguments to validationComplete method and the values are assigned according to the status of the validation.
