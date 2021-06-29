---
title: "Date Masking"
component: "DatePicker"
description: "Miscellaneous aspects of customizing the date picker"
---

# Enable the Masked Input

The DatePicker has built-in support to masking the date value, when `enableMask` property set as `true`.

To use mask support, inject the MaskedDateTime module in the DatePicker.

{% tab template="datepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.ts" %}

```typescript

<template>
<div id="app">
        <div class='wrapper'>
         <ejs-datepicker id="datepicker" :enableMask="mask"></ejs-datepicker>
     </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DatePickerPlugin, MaskedDateTime } from "@syncfusion/ej2-vue-calendars";

Vue.use(DatePickerPlugin);
export default Vue.extend({
  data: function() {
    return {
      mask: true
    };
  },
  provide: {
      datepicker: [MaskedDateTime]
  }  
});
</script>
<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
  .wrapper {
    max-width: 250px;
    margin: 0 auto;
  }
</style>

```

{% endtab %}

The mask pattern is defined based on the provided date format to the component. If the format is not specified, the mask pattern is formed based on the default format of the current culture.

The selected portions of date and time co-ordinates  can  be incremented and decremented using the Up/Down arrow keys. You can also use Right/Left arrow keys to navigate from one segment to another.

The following example demonstrates default and custom format of DatePicker component with mask module.

{% tab template="datepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.ts,app/**/format.html,styles.css" %}

```typescript

<template>
<div id="app">
        <div class='wrapper1'>
         // Specifies the masked datepicker without format property.
         <ejs-datepicker id="datepicker" :enableMask="mask" ></ejs-datepicker>
     </div>
     <div class='wrapper2'>
          // Specifies the masked datepicker with format property.
         <ejs-datepicker id="datepicker" :enableMask="mask" :format="dateFormat"></ejs-datepicker>
     </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DatePickerPlugin, MaskedDateTime } from "@syncfusion/ej2-vue-calendars";

Vue.use(DatePickerPlugin);
export default Vue.extend({
  data: function() {
    return {
      mask: true,
      dateFormat: 'M/d/yyyy'
    };
  },
  provide: {
      datepicker: [MaskedDateTime]
  }  
});
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
#wrapper1{
  min-width: 250px;
    float: left;
    margin-left: 100px;
}
#wrapper2{
  min-width: 250px;
    float: right;
     margin-right: 100px;
}
</style>
```

{% endtab %}

# Configure Mask Placeholder

You can change mask placeholder value through property `maskPlaceholder`. By default , it takes the full name of date and time co-ordinates such as `day`, `month`, `year`, `hour` etc.

The following example demonstrates default and customized mask placeholder value.

{% tab template="datepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.ts,app/**/maskplaceholder.html,styles.css" %}

```typescript

<template>
<div id="app">
        <div class='wrapper1'>
         // Specifies the masked datepicker without mask placeholder.
         <ejs-datepicker id="datepicker" :enableMask="mask" ></ejs-datepicker>
     </div>
     <div class='wrapper2'>
          //// Specifies the masked datepicker with mask placeholder.
         <ejs-datepicker id="datepicker" :enableMask="mask" :maskPlaceholder="maskPlaceholderValue"></ejs-datepicker>
     </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DatePickerPlugin, MaskedDateTime } from "@syncfusion/ej2-vue-calendars";

Vue.use(DatePickerPlugin);
export default Vue.extend({
  data: function() {
    return {
      mask: true,
      maskPlaceholderValue: {day: 'd', month: 'M', year: 'y'}
    };
  },
  provide: {
      datepicker: [MaskedDateTime]
  }  
});
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
#wrapper1{
  min-width: 250px;
    float: left;
    margin-left: 100px;
}
#wrapper2{
  min-width: 250px;
    float: right;
     margin-right: 100px;
}
</style>
```

{% endtab %}
