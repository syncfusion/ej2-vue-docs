---
title: "Date and Time masking"
component: "DateTimePicker"
description: "Miscellaneous aspects of customizing the datetimepicker"
---

# Enable the Masked Input

The DateTimePicker has built-in support to masking the date value, when `enableMask` property set as `true`.

To use mask support, inject the MaskedDateTime module in the DateTimePicker.

{% tab template="datetimepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.ts" %}

```typescript

<template>
<div id="app">
        <div class='wrapper'>
         <ejs-datetimepicker id="datetimepicker" :enableMask="mask"></ejs-datetimepicker>
     </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DateTimePickerPlugin, MaskedDateTime } from "@syncfusion/ej2-vue-calendars";

Vue.use(DateTimePickerPlugin);
export default Vue.extend({
  data: function() {
    return {
      mask: true
    };
  },
  provide: {
      datetimepicker: [MaskedDateTime]
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

The following example demonstrates default and custom format of DateTimePicker component with mask module.

{% tab template="datetimepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.ts,app/**/format.html,styles.css" %}

```typescript

<template>
<div id="app">
        <div class='wrapper1'>
         // Specifies the masked datetimepicker without format property.
         <ejs-datetimepicker id="datetimepicker" :enableMask="mask" ></ejs-datetimepicker>
     </div>
     <div class='wrapper2'>
          // Specifies the masked datetimepicker with format property.
         <ejs-datetimepicker id="datetimepicker" :enableMask="mask" :format="dateFormat"></ejs-datetimepicker>
     </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DateTimePickerPlugin, MaskedDateTime } from "@syncfusion/ej2-vue-calendars";

Vue.use(DateTimePickerPlugin);
export default Vue.extend({
  data: function() {
    return {
      mask: true,
      dateFormat: 'M/d/yyyy hh:mm a'
    };
  },
  provide: {
      datetimepicker: [MaskedDateTime]
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

{% tab template="datetimepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.ts,app/**/maskplaceholder.html,styles.css" %}

```typescript

<template>
<div id="app">
        <div class='wrapper1'>
         // Specifies the masked datetimepicker without mask placeholder.
         <ejs-datetimepicker id="datetimepicker" :enableMask="mask" ></ejs-datetimepicker>
     </div>
     <div class='wrapper2'>
          // Specifies the masked datetimepicker with mask placeholder.
         <ejs-datetimepicker id="datetimepicker" :enableMask="mask" :maskPlaceholder="maskPlaceholderValue"></ejs-datetimepicker>
     </div>
  </div>
</template>
<script>
import Vue from "vue";
import { DateTimePickerPlugin, MaskedDateTime } from "@syncfusion/ej2-vue-calendars";

Vue.use(DateTimePickerPlugin);
export default Vue.extend({
  data: function() {
    return {
      mask: true,
      maskPlaceholderValue: {day: 'd', month: 'M', year: 'y', hour: 'h', minute: 'm', second: 's'}
    };
  },
  provide: {
      datetimepicker: [MaskedDateTime]
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
