---
title: "How To"
component: "DateTimePicker"
description: "Miscellaneous aspects of customizing the date time picker"
---

# Customize the datetimepicker day header

You can change the format of the day that to be displayed in header using [`dayHeaderFormat`](../../api/datetimepicker#dayheaderformat) property. By default, the format is `Short`.

You can find the possible formats on below.

| **Name** | **Description** |
|------|---------------------|
| `Short` | Sets the short format of day name (like Su ) in day header. |
| `Narrow` | Sets the single character of day name (like S ) in day header. |
| `Abbreviated` | Sets the min format of day name (like Sun ) in day header. |
| `Wide` | Sets the long format of day name (like Sunday ) in day header. |

{% tab template="datetimepicker/header-format", isDefaultActive = "true" %}

```html
<template>
  <div id="container">
        <div id='datetimepicker'>
           <ejs-datetimepicker dayHeaderFormat="Short" ref="datetimepickerObj"></ejs-datetimepicker>
        </div>
        <div id="format">
            <label id="custom-input-label">Header Format Types</label>
            <ejs-dropdownlist id="select" :fields = "fields" :index = "currentIndex" :dataSource = "items" :popupHeight= "popupHeight" :change= "formatHandler">
            </ejs-dropdownlist>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DateTimePickerPlugin } from "@syncfusion/ej2-vue-calendars";
import { DropDownListPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(DateTimePickerPlugin);
Vue.use(DropDownListPlugin);
export default {
   data () {
        return {
           items: [
            { sizeVal: 'Short' , sizeTxt: 'Short' },
            { sizeVal: 'Narrow' , sizeTxt: 'Narrow' },
            { sizeVal: 'Abbreviated' , sizeTxt: 'Abbreviated' },
            { sizeVal: 'Wide' , sizeTxt: 'Wide' },
            ],
            fields: { text: 'sizeTxt', value: 'sizeVal' },
            popupHeight: 200,
            currentIndex: 0,
            formatHandler: (args) => {
                 this.$refs.datetimepickerObj.dayHeaderFormat = args.value;
            }
        }
    }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
#container{
    width: 100%;
}
#datetimepicker {
    width: 25%;
    margin-left: 30px;
    margin-top: 30px;
    display: inline-flex;
}
#format {
    width: 180px;
    margin-left: 400px;
    display: inline-block;
}
#select {
    height: 30px;
    width: 150px;
    margin-top: 10px;
}
#custom-input-label{
    font-size: 15px;
    font-weight: bold
}



</style>
```

{% endtab %}