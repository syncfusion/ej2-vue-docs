---
title: "How To"
component: "TimePicker"
description: "Miscellaneous aspects of customizing the time picker"
---

# CSS customization

TimePicker allows you to customize the textbox and popup list appearance to suit your
application by using
[`cssClass`](../../api/timepicker#cssclass) property.

The below sample demonstrates customization of text appearance in a textbox, popup button, and popup list along with hover and active
state by using `e-custom-style` class. Following is the list of available classes used to customize the entire TimePicker component.

| **Class Name** | **Description** |
| --- | --- |
| e-time-wrapper | Applied to TimePicker wrapper element. |
| e-timepicker |  Applied to input element and TimePicker popup element. |
| e-time-wrapper.e-timepicker | Applied to input element only. |
| e-input-group-icon.e-time-icon | Applied to popup button. |
| e-float-text | Applied to floating label text element. |
| e-popup | Applied to popup element. |
| e-timepicker.e-popup | Applied to TimePicker popup element only. |
| e-list-parent | Applied to popup UL element. |
| e-timepicker.e-list-parent | Applied to TimePicker popup UL element only. |
| e-list-item | Applied to LI elements. |
| e-hover | Applied to LI element hovering time. |
| e-active | Applied to active LI element. |

{% tab template="timepicker/strict", isDefaultActive = "true" %}

```html
<template>
  <div id="app">
        <div class='wrap'>
           <ejs-timepicker id='timepicker' placeholder='Select a time' cssClass='e-custom-style'></ejs-timepicker>
        </div>
  </div>
</template>
<script>
import Vue from "vue";
import { TimePickerPlugin } from "@syncfusion/ej2-vue-calendars";

Vue.use(TimePickerPlugin);
export default {}
</script>
<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrap {
    margin: 35px auto;
    width: 240px;
}
/*customize the input element text color*/
.e-time-wrapper.e-custom-style #element { /* csslint allow: adjoining-classes */
    display: block;
    color: blue;
}

/*customize the floating label and popup button text color*/
.e-time-wrapper.e-custom-style .e-float-text.e-label-bottom, /* csslint allow: adjoining-classes */
.e-time-wrapper.e-custom-style .e-input-group-icon.e-time-icon.e-icons { /* csslint allow: adjoining-classes */
    color: blue;
}

/*customize the input element text selection*/
.e-time-wrapper.e-custom-style.e-input-group::before, /* csslint allow: adjoining-classes */
.e-time-wrapper.e-custom-style.e-input-group::after, /* csslint allow: adjoining-classes */
.e-time-wrapper.e-custom-style.e-input-group .e-timepicker::selection { /* csslint allow: adjoining-classes */
    background: blue;
}


.e-timepicker.e-popup.e-custom-style .e-list-parent.e-ul, /* csslint allow: adjoining-classes */
.e-timepicker.e-popup.e-custom-style .e-list-parent.e-ul .e-list-item { /* csslint allow: adjoining-classes */
    background-color: #c0ebff;
}

/*customize the list item hover color*/
.e-timepicker.e-popup.e-custom-style .e-list-parent.e-ul .e-list-item.e-hover, /* csslint allow: adjoining-classes */
.e-timepicker.e-popup.e-custom-style .e-list-parent.e-ul .e-list-item.e-active.e-hover { /* csslint allow: adjoining-classes */
    background-color: blue;
    color: #fff;
}

/*customize the active element text color*/
.e-timepicker.e-popup.e-custom-style .e-list-parent.e-ul .e-list-item.e-active { /* csslint allow: adjoining-classes */
    color:#333;
    background-color: #fff;
}
</style>
```

{% endtab %}