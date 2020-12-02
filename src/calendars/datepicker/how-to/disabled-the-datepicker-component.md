---
title: "How To"
component: "DatePicker"
description: "Miscellaneous aspects of customizing the date picker"
---

# Disabled State

To disable the DatePicker, use its
[`enable`](../../api/datepicker#enabled)
property.

The following example demonstrates the DatePicker in
a disabled state.

{% tab template="datepicker/access", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-datepicker id='date' :enabled="enable"></ejs-datepicker>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DatePickerPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(DatePickerPlugin);
export default {
    data () {
        return{
            enable: false
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