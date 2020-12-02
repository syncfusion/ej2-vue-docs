---
title: "How To"
component: "DatePicker"
description: "Miscellaneous aspects of customizing the date picker"
---

# Prevent the popup close

To prevent the DatePicker popup from closing, use the
preventDefault method from the
`PreventableEventArgs`.

The following example demonstrates how to prevent the popup from closing.

{% tab template="datepicker/min-max", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-datepicker id='date' placeholder="Select Date" :close='onClose' :value='dateval'></ejs-datepicker>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DatePickerPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(DatePickerPlugin);
export default {
    methods:{
        onClose: function(args){
            args.preventDefault();
        }
    }
    data () {
        return{
            dateval: new Date()
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
    margin: 35px auto;
    width: 240px;
}
</style>
```

{% endtab %}