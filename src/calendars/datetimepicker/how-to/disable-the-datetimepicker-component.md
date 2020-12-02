---
title: "How To"
component: "DateTimePicker"
description: "Miscellaneous aspects of customizing the date time picker"
---

# Disable the component

To disable the DateTimePicker, use its
[`enable`](../../api/datetimepicker#enabled)
property to `false`.

{% tab template="datetimepicker/getting-started", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-datetimepicker :enabled="enable" :placeholder="waterMark" ></ejs-datetimepicker>
      </div>
    </div>
</template>
<script>
import Vue from 'vue';
import { DateTimePickerPlugin } from '@syncfusion/ej2-vue-calendars';

Vue.use(DateTimePickerPlugin);
export default {
   data () {
        return {
           enable : false,
           waterMark: "Select a date and time"
        }
    }
}
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
   .wrapper {
    max-width: 250px;
    margin: 0 auto;
  }
</style>
```

{% endtab %}